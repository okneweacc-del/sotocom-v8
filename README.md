# 🔐 SOTOCOM-V8 — Python Source Code Obfuscator

![Python](https://img.shields.io/badge/Python-3.12+-blue?logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20Termux-green)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Version](https://img.shields.io/badge/Version-v8-purple)

> **Tool bảo vệ mã nguồn Python** với stack crypto nhiều lớp: **AES-256-GCM + ChaCha20 + Xorshift + Byte Shuffle + HKDF**, kèm anti-debug / anti-VM / anti-hook.

---

## ⚠️ CẢNH BÁO / DISCLAIMER
TOOL NÀY ĐƯỢC TẠO RA ĐỂ BẢO VỆ MÃ NGUỒN BẢN QUYỀN.
CÓ VÀI NGƯỜI SẼ LỢI DỤNG ĐỂ ADD BOTNET.
NGƯỜI TẠO TOOL SẼ KHÔNG CHỊU TRÁCH NHIỆM VỀ BẤT KỲ
MỤC ĐÍCH SỬ DỤNG SAI TRÁI PHÁP LUẬT NÀO!



> 🚫 **KHÔNG** dùng tool này cho mục đích phát tán malware, botnet, ransomware hay bất kỳ hành vi vi phạm pháp luật nào.
> ✅ Chỉ dùng để bảo vệ code cá nhân / sản phẩm thương mại của bạn.

---

## ✨ Tính năng nổi bật

| Nhóm | Chi tiết |
|------|----------|
| 🔐 **Crypto Stack** | AES-256-GCM → ChaCha20 → Xorshift → Byte Shuffle → Base85 |
| 🔑 **Key Derivation** | HKDF-SHA256 (salt riêng cho từng layer) |
| 🧬 **AST Obfuscation** | String XOR, Bool, BinOp, Sub, FloorDiv, Mod, BitXor, LShift, Compare, Not |
| 🈳 **~70 Alphabets** | Emoji, CJK, Hiragana, Katakana, Hangul, Cyrillic, Greek, Arabic, Thai, Devanagari, Braille, Runic, Box Drawing... |
| 🛡️ **Anti-Analysis** | Anti-Debug (Windows / Linux) + Anti-VM + Anti-Hook (Frida, Xposed, LD_PRELOAD) |
| 🎭 **Junk Code** | Fake comments đa ngôn ngữ, fake functions, fake classes, noise lines |
| 📱 **Cross-Platform** | Windows · Linux · macOS · **Termux Android** |
| 🎨 **Gradient CLI** | Banner RGB true-color, đẹp mắt |

---

## 📸 Demo
/ // __ / // __ / __ / | / // __ / __
_ / / / / / / / / / / // / |/ // / / / / / /
/ / // / / / / // / , / /| // // / // /
//_/ // _// |// |///_/

sotocom-v8 (Phase crypto stack)
github.com/okneweacc-del
platform : termux
python : 3.12.10
alphabets: 68
crypto : AES-GCM + ChaCha20 + Xorshift + Shuffle + HKDF
anti : debug + vm + hook

[+] done



---

## 🚀 Cài đặt

### Yêu cầu
- Python **3.12+**
- Không cần thư viện ngoài (chỉ dùng stdlib)

### Clone repo
```bash
git clone https://github.com/okneweacc-del/sotocom-v8.git
cd sotocom-v8
Termux Android
bash
pkg update && pkg upgrade -y
pkg install python git -y
git clone https://github.com/okneweacc-del/sotocom-v8.git
cd sotocom-v8
🎮 Cách dùng
1️⃣ Interactive mode (khuyên dùng)
bash
python sotoronv2.py
Tool sẽ hỏi:

File input

File output

Chọn preset (fast → nuke hoặc A = auto strongest)

Số dòng tối thiểu

Có hiện banner hay không

2️⃣ CLI mode
bash
python sotoronv2.py input.py output.py [alphabet] [depth] [ast] [junk]
Ví dụ:

bash
# Mặc định (auto strongest)
python sotoronv2.py tool.py tool_obf.py

# Custom đầy đủ
python sotoronv2.py tool.py tool_obf.py mixed6 8 3 3
3️⃣ Các flag tiện ích
Flag	Mô tả
--test, -t	Self-test toàn bộ alphabets × depths
--list, -l	Liệt kê tất cả alphabets
--help, -h	Trợ giúp
📊 Presets có sẵn
Preset	Depth	AST	Junk	Alphabet	Junk Funcs	Junk Classes
fast	4	1	1	emoji_cjk	0	0
normal	6	2	2	emoji_cjk	0	0
strong	8	2	2	mixed	5	3
extreme	8	3	3	emoji_cjk	15	10
paranoid	8	3	3	mixed5	25	20
insane	8	3	3	mixed6	40	30
bloated	8	3	3	pure_emoji	60	40
nuke	8	3	3	pure_animals	100	60
A (auto)	8	3	3	mixed6	40	25
🈳 Danh sách Alphabets (một số)
text
emoji_cjk          cjk_only           cjk_ext_a          cjk_ext_b
cjk_compat         hiragana           katakana           katakana_phonetic
hangul             hangul_jamo        hangul_compat      kanji_radicals
math_symbols       arrows             supplement_arrows  box_drawing
block_elements     geometric_shapes   cyrillic           cyrillic_supp
greek              greek_ext          coptic             arabic
arabic_supp        hebrew             thai               lao
tibetan            myanmar            georgian           ethiopic
cherokee           ogham              runic              mongolian
braille            devanagari         bengali            gurmukhi
gujarati           oriya              tamil              telugu
kannada            malayalam          sinhala            khmer
fullwidth          halfwidth          numeric            special
dingbats           misc_symbols       currency           letterlike
glagolitic         armenian           pure_emoji         pure_faces
pure_hands         pure_animals       pure_symbols       mixed
mixed2..mixed7
Xem đầy đủ: python sotoronv2.py --list

🛡️ Anti-Analysis
Tool inject các lớp bảo vệ khi file output chạy:

Anti-Debug: sys.gettrace, PYTHONINSPECT, pdb, debugpy, IsDebuggerPresent (Win), TracerPid (Linux)

Anti-VM: check DMI strings, MAC address (VMware / VirtualBox / QEMU / Xen / Hyper-V)

Anti-Hook: scan /proc/self/maps tìm frida, xposed, substrate, magisk, LD_PRELOAD

Timeout: nếu decode > 180 giây → exit

Nếu phát hiện môi trường khả nghi → sys.exit(1).

📁 Cấu trúc project

sotocom-v8/
├── sotoronv2.py       # Main tool
├── README.md          # File này
├── LICENSE            # MIT License
├── demo.gif           # Ảnh demo (thêm vào)
└── examples/
    ├── hello.py
    └── hello_obf.py
🧪 Self-test
bash
python sotoronv2.py --test
Chạy build toàn bộ alphabets × depth (1,3,5,8) và verify syntax → đảm bảo mọi config hoạt động.

❓ FAQ
Q: File output có chạy được trên PC không?
A: Có. File encode ra chạy được trên cả Termux Android và PC (Windows / Linux / macOS).

Q: Có cần cài thư viện ngoài không?
A: Không. Toàn bộ crypto (AES-GCM, ChaCha20, HKDF) đều viết tay bằng pure Python stdlib.

Q: Tại sao file output to thế?
A: Do junk code + runtime crypto + Base85 encoding. Có thể giảm bằng cách chọn preset thấp hơn hoặc min_lines nhỏ hơn.

Q: Có decompile ngược được không?
A: Về lý thuyết là có (Python là interpreted), nhưng với multi-layer crypto + AST obfuscation + anti-analysis thì rất khó và tốn thời gian.

📜 License
MIT License — xem file LICENSE.

👤 Author
sotoron20 + Phase

GitHub: @okneweacc-del

⭐ Nếu thấy hữu ích, hãy star repo!
text
⭐ Star  •  🍴 Fork  •  🐛 Issue  •  📩 PR