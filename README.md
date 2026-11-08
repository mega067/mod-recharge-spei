# 💳 Módulo de Recargas Bancarias & Validación SPEI (mod-recharge-spei)

<p align="center">
  <img src="https://megaunlockphone-panel.alwaysdata.net/logo.png" width="130" alt="Recargas Logo">
</p>

<p align="center">
  <strong>Conciliación Automática de Transferencias SPEI, Consulta CEP Banxico y Acreditación Inmediata</strong>
</p>

<p align="center">
  <a href="https://github.com/mega067/MegaUnlockPhone"><img src="https://img.shields.io/github/stars/mega067/MegaUnlockPhone?style=for-the-badge&color=f59e0b&logo=github" alt="Stars"></a>
  <a href="https://github.com/mega067/MegaUnlockPhone/releases"><img src="https://img.shields.io/github/downloads/mega067/MegaUnlockPhone/total?style=for-the-badge&color=10b981&logo=github" alt="Downloads"></a>
  <a href="https://megaunlockphone-panel.alwaysdata.net/"><img src="https://img.shields.io/badge/SPEI_Gateway-Active-emerald?style=for-the-badge" alt="Gateway Status"></a>
  <img src="https://img.shields.io/badge/Banxico_CEP-Verified-blue?style=for-the-badge" alt="CEP Verified">
</p>

---

## 📌 1. ¿Qué es `mod-recharge-spei`?

**`mod-recharge-spei`** es el módulo bancario del ecosistema **[MegaUnlockPhone](https://github.com/mega067/MegaUnlockPhone)**. Se encarga de procesar las recargas de saldo de clientes y revendedores sin requerir intervención manual para validar comprobantes falsos o editados.

### Principales Ventajas:
- 🏦 **Validación Real de Claves de Rastreo:** Consulta directamente los certificados electrónicos de pago (CEP) de **Banxico** en tiempo real.
- 🚫 **Anti-Fraude y Prevención de Pagos Duplicados:** Almacena la clave de rastreo bancaria en la tabla SQLite `BankTransactions`; si un cliente intenta ingresar el mismo comprobante dos veces, el sistema lo bloquea automáticamente.
- ⚡ **Acreditación Atómica de Saldo:** El balance del usuario se incrementa en SQLite de forma atómica y se emite un recibo digital por WhatsApp al instante vía [mod-whatsapp-bot](file:///home/angel/Projects/REPOS/dhru-client-web/packages/mod-whatsapp-bot/README.md).

---

## 🏛️ Conexión con MegaUnlockPhone

```
┌───────────────────────────┐
│     👤 CLIENTE WEB        │
│   Ingresa Clave de Rastreo│
└─────────────┬─────────────┘
              │ POST /api/recharge/spei
              ▼
┌───────────────────────────┐       ┌───────────────────────┐
│   💳 MOD-RECHARGE-SPEI    │◄─────►│ 🏦 BANXICO CEP API    │
│   Valida Clave y Banco    │       │ Certificado Electrón. │
└─────────────┬─────────────┘       └───────────────────────┘
              │ Saldo Validado
              ▼
┌───────────────────────────┐
│     🏛️ MUP-CORE (SQLite)  │
│   Acredita Billetera      │
└───────────────────────────┘
```

---

## ⚙️ Configuración de Cuentas (`bankConfig.json`)

```json
{
  "accounts": [
    {
      "bankName": "NU MÉXICO",
      "bankCode": "40638",
      "clabe": "638180000147867948",
      "beneficiary": "MegaUnlockPhone Admin",
      "minDeposit": 50
    }
  ],
  "banxicoValidation": true
}
```

---

<p align="center">
  <sub>SPEI Recharge Engine &copy; 2026. Módulo Oficial de MegaUnlockPhone.</sub>
</p>
