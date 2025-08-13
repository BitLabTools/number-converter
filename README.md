# Number Converter – Dec ⇄ Hex ⇄ Bin ⇄ DNA

A lightweight, browser‑based converter that keeps **Decimal**, **Hexadecimal**, **Binary**, and **DNA code** in sync — powered by JavaScript **BigInt** for arbitrarily large signed integers.

DNA mapping: **A=00, T=01, C=10, G=11** (two‑bit chunks). If the binary length is odd, the binary string is **left‑padded** with one leading `0` so full bases can be formed.

---

## ✨ Features

- Convert between **Decimal ⇄ Hex ⇄ Binary ⇄ DNA** in real time
- **BigInt** support → handles very large positive/negative integers
- **Hex case toggle** (A–F ↔ a–f)
- **Preserve formatting toggle** (default **on**): keep **leading zeros** in *Binary* and **leading A’s** in *DNA* while editing
- **Copy** buttons for each field
- **Responsive layout** (fields left, compact info panel right; single‑column on mobile)
- **About** and **Disclaimer** modals
- **Privacy‑friendly**: runs completely in your browser, no backend

---

## 🚀 Usage

Enter a value in **one** field — the others update automatically.

### Accepted input formats
- **Decimal**: `-42`, `12345678901234567890`
- **Hex**: `3039`, `0x3039`, `-0xFF`
- **Binary**: `1111`, `0b1111`, `-101010`
- **DNA**: letters `A/T/C/G` (case‑insensitive). Other characters are rejected.  
  Whitespace is ignored.

### DNA mapping details
- Binary is grouped into 2‑bit chunks: `00→A`, `01→T`, `10→C`, `11→G`
- If binary has an **odd** number of bits, it is **left‑padded** with one leading `0` before mapping
- **Zero** is represented as a single `A` (i.e., `00 → A`)
- A leading minus sign (`-`) indicates a negative number across all fields

### Preserve formatting (toggle)
- **On (default):** While you edit *Binary* or *DNA*, the entered formatting is preserved:  
  - *Binary* keeps **leading zeros** (`000101` stays `000101`).  
  - *DNA* keeps **leading A’s** as implied by left‑padding (`AAA…`).  
  Other fields update consistently to the same numeric value.
- **Off:** All fields switch to a **canonical** form:  
  - *Binary* without leading zeros (except for `0`).  
  - *DNA* with the minimal number of bases implied by the bit‑length (left‑padded with a single `0` only when needed for an even bit count).

### Examples
- `42 (dec)` → `2A (hex)` → `101010 (bin)` → `C C C (DNA)` → `CCC`
- `0 (dec)` → `0 (hex)` → `0 (bin)` → `A (DNA)`

---

## ℹ️ Info panel

- **Significant bits** (actual bit length)  
- **Nominal bits (hex nibbles)** and **Leading zero bits**  
- **Byte length**, **Hex length**, **Binary length**  
- **DNA length (bases)**

---

## 🔐 Privacy

All inputs are processed **locally** in your browser. **Nothing is uploaded** and no sequences/numbers are stored.

### Analytics (GoatCounter)
- Optional, privacy‑friendly page‑view analytics via **GoatCounter** (no cookies, no personal data).  
- **Do Not Track (DNT)** is respected.  
- Analytics loads **only if enabled**; you can change this via the **checkbox in the Disclaimer** modal.

---

## ⚠️ Disclaimer (summary)

This tool is intended for **educational and general utility** purposes. It is provided **"as is"** without warranties. Do **not** use it for safety‑critical, medical, or legal applications; verify important results independently. See *Disclaimer.md* for full text.

---

## 📧 Contact

For feedback, suggestions, or bug reports:  
📨 **bitlabtools@proton.me**

---

## 🔒 Licensing & Use

- Open for **academic/non‑commercial** use.
- For commercial use, please contact the author.
