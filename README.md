# EU CBAM & Carbon Tax Calculation Engine — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-cbam-carbon.svg)](https://crates.io/crates/stanzaapi-cbam-carbon)
[![Documentation](https://docs.rs/stanzaapi-cbam-carbon/badge.svg)](https://docs.rs/stanzaapi-cbam-carbon)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> EU CBAM Scope 1/2 embedded emissions and EU ETS carbon tax liability calculator across Iron, Steel, Aluminum, Cement, Fertilizers, and Hydrogen.

Official high-performance, asynchronous Rust client library for **EU CBAM & Carbon Tax Calculation Engine**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/cbam-carbon)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/cbam-carbon)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-cbam-carbon = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-cbam-carbon
```

---

## 🚀 Quickstart

```rust
use stanzaapi_cbam_carbon::CbamCarbonClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    // Public edge default: https://api.stanzaapi.com/cbam-carbon
    let client = CbamCarbonClient::new(None, None);

    let response = client.validate({"goods_category":"iron_and_steel","production_country":"TR","quantity_tonnes":500}).await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "goods_category": "iron_and_steel",
    "direct_emissions_tco2e": 950,
    "estimated_ets_liability_eur": 71250
  }
}
```

---

## 🔗 Useful Links

* [EU CBAM & Carbon Tax Calculation Engine Interactive Sandbox](https://stanzaapi.com/tools/cbam-carbon)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/StanzaAPI/cbam-carbon-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
