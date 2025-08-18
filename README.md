# Number Converter – Dec ⇄ Hex ⇄ Bin ⇄ DNA ⇄ Base64

A lightweight, browser‑based converter that keeps **Decimal**, **Hexadecimal**, **Binary**, **DNA** and **Base64** in sync.  
Built on JavaScript **BigInt**, so it handles arbitrarily large signed integers.

DNA mapping: **A=00, T=01, C=10, G=11** (2‑bit chunks). If the binary length is odd, the binary string is **left‑padded** with one leading `0` so full bases can be formed.

---

## ✨ Features

- Convert between **Decimal ⇄ Hex ⇄ Binary ⇄ DNA ⇄ Base64** in real time.
- **BigInt** support → works for very large positive/negative integers.
- **Hex case toggle** (A–F ↔ a–f).
- **Preserve formatting toggle** (default **on**):
  - keeps **leading zeros** in *Binary* and **leading A’s** in *DNA* while editing;
  - other fields (including *Base64*) stay numerically consistent.
- **Base64** specifics:
  - always **canonical** (no special “preserve” mode);
  - encodes the **minimal big‑endian magnitude bytes** of the value;
  - minus sign (if any) is shown **outside** the Base64 text;
  - input is normalized: whitespace removed, `=`‑padding auto‑completed (length % 4), only the standard alphabet `[A–Za–z0–9+/=]` accepted.
  - supports an optional **A‑prefix sidecar (~A<n>)**:
    - the numeric sidecar specifies how many leading `A` bases are logically prepended to the DNA representation.
    - when copying Base64 with the special button, the value is exported together with the marker (e.g. `YWJjZA== ~A3`).
    - when pasting such a string, the tool restores the correct DNA sequence including the leading `A`s.
- **Copy** buttons for each field.
- **“Clear all”** button that resets the page state to start clean.
- Input UX:
  - **DNA field** blocks non‑ATCG characters and gives a gentle **nudge** on invalid input; paste is sanitized.
  - **Caret/selection** behavior is preserved while typing in Binary/DNA.
- **Responsive layout** (fields left, compact info panel right; single‑column on mobile).
- **About** button and inline **Disclaimer** panel.
- **Privacy‑friendly analytics** with GoatCounter (opt‑in; no cookies; minimal telemetry).

---

## 🚀 Usage

Enter a value in **one** field — the others update automatically.

### Accepted input formats
- **Decimal**: `-42`, `12345678901234567890`
- **Hex**: `3039`, `0x3039`, `-0xFF`
- **Binary**: `1111`, `0b1111`, `-101010`
- **DNA**: letters `A/T/C/G` (case‑insensitive). Other characters are rejected; whitespace is ignored.
- **Base64**: standard alphabet; optional `=` padding (the tool pads automatically). A leading `-` denotes negatives.  
  Optionally, a sidecar marker `~A<n>` can be appended or pasted to preserve leading `A`s in DNA.

### DNA mapping details
- Binary is grouped into 2‑bit chunks: `00→A`, `01→T`, `10→C`, `11→G`.
- If binary has an **odd** number of bits, it is **left‑padded** with one leading `0` before mapping.
- **Zero** is represented as a single `A` (i.e., `00 → A`).

### Preserve formatting (toggle)
- **On (default):** While you edit *Binary* or *DNA*, the entered formatting is preserved (e.g., `000101` stays `000101`, leading `A`s are kept). Other fields mirror the same numeric value.
- **Off:** All fields switch to a **canonical** form (Binary without leading zeros except for `0`; DNA at minimal length implied by the bit‑length). Base64 is always canonical.

### Examples
- `42 (dec)` → `2A (hex)` → `101010 (bin)` → `CCC (DNA)` → `Kg== (base64)`  
- `0 (dec)` → `0 (hex)` → `0 (bin)` → `A (DNA)` → `AA== (base64)`  
- `A245030B7C9A0B603FB002B6463FB1FA8 (hex)` → `CiRQMLfJoLYD+wArZGP7H6g= (base64)`  
- `DNA = AAACT (with 3 leading A’s)` → Base64 export: `XYZ...== ~A3`

---

## ℹ️ Info panel

- **Significant bits** (actual bit length)  
- **Nominal bits (hex nibbles)** and **Nominal leading zero bits**  
- **Displayed leading zeros** (with *Preserve* on)  
- **Byte length**  
- **Hex length (displayed)** — derived from the current binary display **including** Preserve/A‑prefix (rounded to full nibbles).  
- **Hex length (canonical)** — minimal hex digits required for the numeric value: `ceil(significant_bits / 4)`.  
- **Hex length (bytes‑aligned)** — hex digits implied by the byte storage: `2 × Byte length`.  
- **Binary length**, **DNA length (bases)**  
- **A‑prefix** count and **Sidecar marker (~A<n>)**  
- **Base64 length (chars)**

> Notes  
> • “Byte length” equals the number of bytes encoded by the Base64 value (decoded length).  
> • “Displayed” reflects what you currently see with Preserve/A‑prefix applied; “canonical” ignores formatting and uses the minimal representation; “bytes‑aligned” comes from Base64/byte storage.

---

## 🔐 Privacy & Disclaimer

- All inputs are processed **locally** in your browser. **Nothing is uploaded** and no sequences/numbers are stored.
- Optional analytics via **GoatCounter** (opt‑in; no cookies). See the Disclaimer panel in the UI for details.

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
