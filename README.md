📊 Google Sheets Structure

### Laptops Tab — Columns

| Column | Description | Example |
|---|---|---|
| `id` | Unique laptop ID | LAP001 |
| `name` | Full laptop name | ASUS ROG Strix G15 |
| `cpu` | Processor | AMD Ryzen 9 7945HX |
| `ram` | Memory | 16GB DDR5 |
| `storage` | Storage | 1TB NVMe SSD |
| `gpu` | Graphics card | NVIDIA RTX 4060 8GB |
| `price` | Price in Naira (number only) | 1450000 |
| `categories` | Comma-separated use cases | gaming,design,coding |
| `budget_tier` | low / mid / high | mid |
| `reason_coding` | Why good for coding | Handles any dev stack |
| `reason_gaming` | Why good for gaming | RTX 4060 runs AAA titles |
| `reason_business` | Why good for business | *(leave blank if N/A)* |
| `reason_design` | Why good for design | Accelerates rendering |
| `reason_student` | Why good for students | *(leave blank if N/A)* |
| `in_stock` | Availability | TRUE or FALSE |

### Budget Tiers
| Tier | Range |
|---|---|
| `low` | ₦400,000 – ₦800,000 |
| `mid` | ₦800,000 – ₦1,500,000 |
| `high` | ₦1,500,000+ |

### Leads Tab — Auto-populated by bot

| Column | Description |
|---|---|
| `timestamp` | Date and time of lead |
| `first_name` | Customer's Telegram name |
| `telegram_id` | Customer's Telegram ID |
| `category` | What they need the laptop for |
| `budget` | Their budget range |
| `recommendations_shown` | Yes or No |
| `status` | New Lead / Contacted / Sold / Lost |

---

## 🔄 Workflow Architecture

```
[Telegram Trigger]
       │
[Switch: Route Incoming Update]
  ├── is_start ──────────────→ [Send Welcome + Category Buttons]
  ├── is_callback ──────────→ [What Stage is Callback?]
  │       ├── is_category ──→ [Answer CB] → [Save Category]
  │       │                 → [Build Budget Keyboard]
  │       │                 → [Send Budget Options]
  │       │
  │       ├── is_budget ───→ [Answer CB] → [Extract Budget + Category]
  │       │                → [Get All Laptops from Sheets]
  │       │                → [Filter & Match Laptops]
  │       │                → [Send Recommendations]
  │       │                → [Send CTA Buttons]
  │       │                → [Alert Admin on Telegram]
  │       │                → [Log Lead to Google Sheets]
  │       │
  │       └── is_restart ──→ [Answer CB] → [Send Welcome Again]
  │
  └── is_text ─────────────→ [Send Fallback Message]
```

---

## 💡 Possible Extensions

- [ ] Add product images to recommendation cards
- [ ] Connect to WhatsApp Business API
- [ ] Add "Reserve this laptop" button for direct lead capture
- [ ] Build admin dashboard from Leads sheet data
- [ ] Duplicate for other product categories (phones, accessories)
- [ ] Add multi-language support (English + Yoruba/Igbo/Hausa)

---

## 👨‍💻 Built By

**FlowLogicLabs**
*Automation Developer | No-Code Developer | Workflow Automation Specialist | Bot Developer*


📧 [falodiayokunle499@gmail.com](mailto:falodiayokunle499@gmail.com)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

*Built with n8n — the workflow automation platform*
