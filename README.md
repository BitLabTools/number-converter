# Number Converter – Dec ⇄ Hex ⇄ Bin ⇄ DNA

A lightweight, browser‑based converter that keeps **Decimal**, **Hexadecimal**, **Binary**, and **DNA code** in sync.  
Built on JavaScript **BigInt** so it handles arbitrarily large signed integers.

DNA mapping: **A=00, T=01, C=10, G=11** (2‑bit chunks). If the binary length is odd, the binary string is **left‑padded** with one leading `0` so full bases can be formed.

---

## ✨ Features

- Convert between **Decimal ⇄ Hex ⇄ Binary ⇄ DNA** in real time.
- **BigInt** support → works for very large positive/negative integers.
- **Hex case toggle** (A–F ↔ a–f).
- **Preserve formatting toggle** (default **on**): keep **leading zeros** in *Binary* and **leading A’s** in *DNA* while editing; other fields stay numerically consistent.
- **Copy** buttons for each field.
- **“Clear all”** button that resets the page state (hard refresh with cache‑buster) to start clean.
- Input UX:
  - **DNA field** blocks non‑ATCG characters and gently **nudges** on invalid input; paste is sanitized.
  - **Caret/selection** behavior is preserved while typing in Binary/DNA.
- **Responsive layout** (fields left, compact info panel right; single‑column on mobile).
- **About** button and inline **Disclaimer** panel.
- **Privacy‑friendly analytics** with GoatCounter (no cookies; minimal technical telemetry). See the Disclaimer toggle in the UI.

---

## 🚀 Usage

Enter a value in **one** field — the others update automatically.

### Accepted input formats
- **Decimal**: `-42`, `12345678901234567890`
- **Hex**: `3039`, `0x3039`, `-0xFF`
- **Binary**: `1111`, `0b1111`, `-101010`
- **DNA**: letters `A/T/C/G` (case‑insensitive). Other characters are rejected; whitespace is ignored.

### DNA mapping details
- Binary is grouped into 2‑bit chunks: `00→A`, `01→T`, `10→C`, `11→G`.
- If binary has an **odd** number of bits, it is **left‑padded** with one leading `0` before mapping.
- **Zero** is represented as a single `A` (i.e., `00 → A`).
- A leading minus sign (`-`) indicates a negative number across all fields.

### Preserve formatting (toggle)
- **On (default):** While you edit *Binary* or *DNA*, the entered formatting is preserved:  
  - *Binary* keeps **leading zeros** (`000101` stays `000101`).  
  - *DNA* keeps **leading A’s** as implied by left‑padding (`AAA…`).  
  Other fields update to the same numeric value.
- **Off:** All fields switch to a **canonical** form:  
  - *Binary* without leading zeros (except for `0`).  
  - *DNA* with the minimal bases implied by the bit‑length (left‑padded with a single `0` only when needed for an even bit count).

### Examples
- `42 (dec)` → `2A (hex)` → `101010 (bin)` → `CCC (DNA)`  
- `0 (dec)` → `0 (hex)` → `0 (bin)` → `A (DNA)`

---

## ℹ️ Info panel

- **Significant bits** (actual bit length)  
- **Nominal bits (hex nibbles)** and **Nominal leading zero bits**  
- **Displayed leading zeros** (with *Preserve* on)  
- **Byte length**, **Hex length**, **Binary length**  
- **DNA length (bases)**

---


## 🔐 Privacy & Disclaimer

- All inputs are processed **locally** in your browser. **Nothing is uploaded** and no sequences/numbers are stored.
- The site uses **GoatCounter** for privacy‑friendly page‑view analytics (no cookies; no personal data). See the Disclaimer panel in the UI for details.

---

## 🛠️ Development

Just open `index.html` in a modern browser — no build step or server required.

---

## 📧 Contact

For feedback, suggestions, or bug reports:  
📨 **bitlabtools@proton.me**

---

## 🔒 Licensing & Use

- Open for **academic/non‑commercial** use.  
- For commercial use, please contact the author.
