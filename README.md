# 📱 SmartLIB — Mobile App

A full-featured **React Native mobile companion** to the SmartLIB Library Management System, built as a university project at **Fatima Jinnah Women University (FJWU)**. The app provides role-based access for Students, Faculty, and Librarians, all powered by a live **Supabase** backend.

---

## 🔗 Related Project

> **SmartLIB Web** — the web-based version of this system (HTML, CSS, JS, phpMyAdmin) was built alongside this mobile app as part of the same university project.

---

## ✨ Features by Role

### 🎓 Student
| Feature | Description |
|---------|-------------|
| Dashboard | Overview of borrowed books and account status |
| Browse Books | Search and filter the full library catalog |
| My Books | View currently issued books and due dates |
| Request Issue | Request a book from the catalog |
| Return Book | Submit a return request |
| Profile | View and manage student profile |

### 👩‍🏫 Faculty
| Feature | Description |
|---------|-------------|
| Browse Books | Search the full library catalog as a guest |
| My Loans | View currently borrowed books |
| Profile | View and manage faculty profile |

### 📚 Librarian
| Feature | Description |
|---------|-------------|
| Dashboard | Live stats — total books and total members |
| Book Management | Add, edit, and remove books from the catalog |
| Member Management | View and manage student and faculty members |
| Issue / Return | Approve and process issue/return requests |
| Recommend Books | Push book recommendations to students |
| Profile | Manage librarian account |

---

## 🛠️ Built With

| Technology | Usage |
|------------|-------|
| **React Native** | Cross-platform mobile UI |
| **Expo (~52.0.48)** | Development toolchain and build system |
| **Supabase** | Backend database with real-time queries |
| **React Navigation** | Stack + Bottom Tab navigation |
| **AsyncStorage** | Local session persistence |
| **@expo/vector-icons (MaterialIcons)** | Icons throughout the UI |
| **@react-native-picker/picker** | Dropdown/role selector UI |

---

## 🗂️ Project Structure

```
project_lib/
│
├── App.js                    # Entry point — Splash, Login screens + stack navigator
├── student.js                # Student tab navigator + all student screens
├── faculty.js                # Faculty tab navigator + all faculty screens
├── librarian.js              # Librarian tab navigator + all librarian screens
├── BrowseBooksGuestScreen.js # Shared book browsing screen (guest/faculty)
│
├── supabase.js               # Supabase client initialisation
├── theme.js                  # Shared colour tokens
├── styles.js                 # Global stylesheet (Expo Web support)
│
├── assets/
│   ├── icon.png              # App icon
│   ├── splash-icon.png       # Splash screen icon
│   ├── adaptive-icon.png     # Android adaptive icon
│   └── favicon.png           # Web favicon
│
├── app.json                  # Expo app configuration
├── package.json              # Dependencies
└── index.js                  # Expo registerRootComponent entry
```

---

## 🎨 Design / Theme

The app uses a consistent dark-green library theme throughout:

| Token | Value | Usage |
|-------|-------|-------|
| `dark` | `#061d17` | Primary dark background |
| `dark2` | `#3a5a40` | Active tab, buttons |
| `bg` | `#f9fafb` | Screen background |
| `accent` | `#b5a820` | Highlight / warning |
| `accent2` | `#10b981` | Success / active states |
| `muted` | `#777` | Placeholder, inactive text |

---

## 🚀 Getting Started

### Prerequisites
- Node.js ≥ 18
- Expo CLI: `npm install -g expo-cli`
- Expo Go app on your phone (iOS or Android)


### Running the App
- **On your phone:** Scan the QR code with the **Expo Go** app
- **Android emulator:** Press `a` in the terminal
- **iOS simulator:** Press `i` in the terminal (macOS only)
- **Web browser:** Press `w` in the terminal

---

## ⚙️ Environment Setup (Supabase)

The app connects to a Supabase project. Create a `supabase.js` file at the root:

```js
import { createClient } from '@supabase/supabase-js';

const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';

export const supabase = createClient(SUPABASE_URL, SUPABASE_ANON_KEY);
```

### Required Database Tables

| Table | Key Columns |
|-------|-------------|
| `members` | `email`, `password`, `role`, `name` |
| `books` | `id`, `title`, `author`, `available` |
| `loans` | `member_email`, `book_id`, `issued_at`, `due_date`, `status` |
| `recommendations` | `book_id`, `message`, `created_at` |

---

## 📱 Screens Overview

```
SplashScreen
    └── LoginScreen
            ├── StudentTabNavigator
            │       ├── Home (Dashboard)
            │       ├── Browse Books
            │       ├── My Books
            │       ├── Request Issue
            │       ├── Return Book
            │       └── Profile
            │
            ├── FacultyTabNavigator
            │       ├── Browse Books
            │       ├── My Loans
            │       └── Profile
            │
            └── LibrarianTabNavigator
                    ├── Dashboard (live stats)
                    ├── Book Management
                    ├── Member Management
                    ├── Issue / Return Requests
                    ├── Recommend Books
                    └── Profile
```
