# 📚 Library Management System

> **A clean, interactive, and fully persistent console-based Python application** to manage your personal, school, or small community library's book collection with ease.

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey)]()

---

## 🌟 Overview

This **Library Management System** demonstrates excellent object-oriented programming (OOP) practices in pure Python. It offers a beautiful menu-driven command-line interface that lets you:

- Build and maintain a digital book catalog
- Track real-time availability (Available vs Issued)
- Perform everyday library operations safely
- Search instantly across your entire collection

**Zero external dependencies.** Everything — including data persistence — is handled with Python's standard library (`json` + `os`). Your library data lives safely in a local `books.json` file and survives between sessions.

Ideal for:
- Students learning Python & OOP
- Teachers demonstrating real-world file handling
- Anyone who wants a simple offline library tracker

---

## ✨ Features

| Feature              | Description                                                                 | Status     |
|----------------------|-----------------------------------------------------------------------------|------------|
| **Add Book**         | Register new books with unique numeric ID, title & author                   | ✅ Full    |
| **View Books**       | Clean, sorted list with ID • Title • Author • Status (Available/Issued)     | ✅ Full    |
| **Issue Book**       | Borrow a book (prevents issuing already borrowed books)                     | ✅ Full    |
| **Return Book**      | Return an issued book and make it available again                           | ✅ Full    |
| **Search Book**      | Powerful partial-match search by ID, title, or author (case-insensitive)    | ✅ Full    |
| **Delete Book**      | Remove books with confirmation prompt (blocked if currently issued)         | ✅ Full    |
| **Data Persistence** | Automatic JSON save/load with corruption recovery                           | ✅ Full    |
| **Input Validation** | Numeric IDs only, no empty fields, duplicate prevention, smart normalization| ✅ Full    |
| **User Experience**  | Emoji-rich feedback, clear menus, helpful error messages                    | ✅ Full    |

---

## 🛠️ Tech Stack

- **Python 3.6+** (100% standard library)
  - `json` — Data storage & retrieval
  - `os` — File system checks
- **No pip install required** — Truly portable and lightweight

---

## 📋 Prerequisites

- Python 3 installed on your computer
- Terminal / Command Prompt / PowerShell
- (Optional) A code editor like VS Code, PyCharm, or IDLE for viewing the code

---

## 🚀 Getting Started (60 seconds)

### Step 1: Get the files
Place `Library_Management_system.py` and this `README.md` in the same folder (e.g. `MyLibraryApp/`).

### Step 2: Run it
Open your terminal and run:

```bash
cd path/to/MyLibraryApp
python Library_Management_system.py
```

> On some systems (Linux/macOS) you may need `python3` instead of `python`.

The first time you add or modify data, a `books.json` file will be created automatically in the same folder.

---

## 📖 Complete Usage Guide

When you start the program you will see this beautiful menu:

```
===================================
      LIBRARY MANAGEMENT SYSTEM
===================================
1. View Books
2. Add Book
3. Issue Book
4. Search Book
5. Return Book
6. Delete Book
7. Exit

Enter choice (1-7): 
```

### 1. View Books
Shows every book in your library, sorted by ID.

**Example output:**
```
========== LIBRARY BOOKS ==========
ID: 101 | Harry Potter and the Philosopher's Stone by J.K. Rowling [Available]
ID: 102 | The Hobbit by J.R.R. Tolkien [Issued]
```

### 2. Add Book
```bash
Enter choice (1-7): 2

Book ID: 103
Book Title: Atomic Habits
Author: James Clear

✅ 'Atomic Habits' added successfully.
```

**Rules enforced:**
- Book ID must be numeric only
- Title and Author cannot be empty
- Duplicate IDs are rejected

### 3. Issue Book (Borrow)
```bash
Enter choice (1-7): 3

Book ID to issue: 101

✅ 'Harry Potter and the Philosopher's Stone' issued successfully.
```

- Book status changes to `[Issued]`
- You cannot issue a book that is already issued

### 4. Search Book
Super flexible — type any part of ID, title, or author.

```bash
Enter choice (1-7): 4

Search ID/title/author: potter

========== SEARCH RESULTS ==========
ID: 101 | Harry Potter and the Philosopher's Stone by J.K. Rowling [Issued]
```

Works with partial words: `har`, `tolkien`, `102`, etc.

### 5. Return Book
```bash
Enter choice (1-7): 5

Book ID to return: 101

✅ 'Harry Potter and the Philosopher's Stone' returned successfully.
```

### 6. Delete Book
Safety first — you must confirm, and you **cannot** delete a book that is currently issued.

```bash
Enter choice (1-7): 6

Book ID to delete: 103
Delete 'Atomic Habits'? (y/n): y

✅ Book deleted.
```

### 7. Exit
Cleanly exits with a thank-you message.

---

## 🗂️ Project Structure

```
MyLibraryApp/
├── Library_Management_system.py   ← Main application (run this)
├── books.json                     ← Your library database (auto-created)
├── README.md                      ← You are reading this!
└── (optional) LICENSE, .gitignore
```

> **Never manually edit `books.json`** unless you know JSON. Let the program handle it.

---

## 🧠 Code Architecture (for learners)

The code is beautifully organized into two main classes:

### `Book` class
- Stores `book_id`, `title`, `author`, `is_issued`
- `to_dict()` → converts object → JSON-friendly dictionary
- `from_dict()` → converts JSON data → Book object
- `__str__()` → pretty console output with status emoji

### `Library` class
- Holds all books in a dictionary (`self.books`)
- `load_books()` / `save_books()` — handles JSON persistence
- `add_book()`, `issue_book()`, `return_book()`, `search_book()`, `delete_book()`, `view_books()`
- Every change that matters is immediately saved

The `main()` function runs an infinite loop showing the menu and calling the right method.

**Design highlights:**
- IDs are normalized to clean string integers (e.g. `"007"` → `"7"`)
- Strong validation at every step
- Graceful error recovery if `books.json` is missing or corrupted

---

## 💾 Data Storage Explained

- Format: Clean, indented JSON array of book objects
- Location: Same folder as the `.py` file
- Auto-save: Triggered after every successful add/issue/return/delete
- Recovery: If file is corrupted, app starts fresh with a warning message (your previous data is usually recoverable from backup)

**Pro tip:** Regularly copy `books.json` to a backup folder if your library grows large.

---

## 🔮 Future Enhancement Ideas

Want to level up this project? Here are popular extensions:

1. **GUI Version** — Add Tkinter or PySimpleGUI for buttons & windows
2. **Member System** — Track who borrowed which book + due dates
3. **Fines & Late Fees** — Calculate overdue charges
4. **Categories & Genres** — Filter books by fiction, science, etc.
5. **Web Dashboard** — Flask/FastAPI + nice frontend
6. **Export Reports** — Generate PDF/CSV of current library status
7. **Unit Tests** — Add `pytest` coverage for reliability
8. **Dark Mode Terminal** — Use `rich` or `colorama` for colored output

Pull requests for any of these are welcome!

---

## 🤝 Contributing

This project is intentionally simple and educational. Contributions that keep it beginner-friendly are highly appreciated.

**How to contribute:**
1. Fork this repository
2. Create a new branch (`git checkout -b feature/your-cool-idea`)
3. Make your changes + test thoroughly
4. Commit with clear messages
5. Open a Pull Request

Found a bug? Open an issue with steps to reproduce. Thank you!

---

## 📜 License

Released under the **MIT License**.  
You are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of this software.

---

## 🙏 Acknowledgements

- Built with clean Python and love for simple, useful tools
- Emoji support thanks to Unicode
- Inspired by classic library management tutorials and real-world CLI best practices

---

**Thank you for using the Library Management System!** 

If this project helped you learn or made managing your books easier, consider starring it on GitHub (when you upload it) ⭐

Happy reading! 📖✨
