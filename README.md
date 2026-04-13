#  Calculator

A lightweight, iOS-inspired desktop calculator built with Python and Tkinter. Supports standard arithmetic, percentage calculations, and square root operations — all from a clean, keyboard-free GUI.

---

##  Preview

> Dark-themed display with operator buttons in amber and function buttons in grey, rendered natively on any platform that supports Tkinter.

---

##  Features

- **Basic arithmetic** — addition, subtraction, multiplication, division
- **Percentage** — instantly convert values to their decimal percentage equivalent
- **Square root** — compute `√x` in one click
- **Sign toggle** — flip between positive and negative with `+/-`
- **Clear** — reset the display and expression with `AC`
- **Error handling** — invalid expressions display `Error` without crashing
- **Responsive grid layout** — all buttons scale consistently within a fixed window

---

##  Getting Started

### Prerequisites

| Requirement | Version |
|---|---|
| Python | 3.6 or higher |
| Tkinter | Included in the Python standard library |

> **Note:** On some Linux distributions Tkinter must be installed separately:
> ```bash
> sudo apt-get install python3-tk   # Debian / Ubuntu
> sudo dnf install python3-tkinter  # Fedora
> ```

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/calculator.git
cd calculator
```

No third-party dependencies are required.

### Running the Application

```bash
python calculator.py
```

---

##  Project Structure

```
calculator/
├── calculator.py   # Application entry point and all source code
└── README.md       # Project documentation
```

---

##  Usage

| Button | Action |
|---|---|
| `0 – 9` | Input digits |
| `.` | Decimal point |
| `+ - × ÷` | Arithmetic operators |
| `=` | Evaluate the expression |
| `AC` | Clear all input |
| `+/-` | Toggle sign of the current value |
| `%` | Divide the current value by 100 |
| `√` | Compute the square root of the current value |

### Example Workflows

**Basic calculation:**
```
7 → × → 8 → = → 56
```

**Percentage:**
```
75 → % → 0.75
```

**Square root:**
```
144 → √ → 12.0
```

---

##  Architecture

The application is structured as a single class following a clean separation of concerns:

```
Calculator
├── __init__         Initialises state and builds the UI
├── _build_ui        Constructs the display label and button grid
├── _make_button     Creates and styles individual buttons
└── _on_click        Dispatches button presses to the correct handler
```

**Key design decisions:**

- `eval()` is used for expression evaluation with `÷` and `×` replaced by their Python equivalents before evaluation.
- Display state is managed via a `tk.StringVar`, keeping the label reactively in sync with `self.expression`.
- All operator and error branches are guarded by `try/except` to prevent unhandled exceptions from surfacing to the user.

---

##  Known Limitations

- **No keyboard input support** — interaction is mouse-only.
- **Single expression context** — there is no expression history or memory functionality.
- **`eval()` usage** — the expression evaluator uses Python's built-in `eval`. Input is constructed internally (not from free text entry), which limits injection risk, but a dedicated parser would be more robust for production use.
- **Floating-point precision** — results inherit standard IEEE 754 float behaviour (e.g., `0.1 + 0.2 = 0.30000000000000004`).

---

##  Roadmap

- [ ] Keyboard shortcut support
- [ ] Calculation history panel
- [ ] Replace `eval()` with a safe expression parser
- [ ] Unit test suite
- [ ] Packaging as a standalone executable via PyInstaller

---

##  Contributing

Contributions are welcome. Please open an issue to discuss your proposed change before submitting a pull request.

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a pull request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

##  Acknowledgements

- Inspired by the iOS Calculator UI
- Built with [Python](https://www.python.org/) and [Tkinter](https://docs.python.org/3/library/tkinter.html)
