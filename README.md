# Angell Study 📚

Ton workspace d'étude personnel — style Notion, construit pour toi.

## Features
- **Éditeur Notion-style** — blocs, titres, listes, tableaux, code
- **Organisation** — Matière → Chapitres → Pages + Tags + Recherche globale
- **Flashcards** — Spaced repetition (Again / Hard / Good / Easy)
- **To-do** par cours — priorités + deadline
- **Export PDF** de n'importe quelle note
- **Mode sombre** natif

---

## Setup — Build l'APK

### 1. Installe Flutter
```bash
# macOS
brew install flutter

# ou télécharge depuis flutter.dev/install
```

### 2. Vérifie ton environnement
```bash
flutter doctor
```
S'assure que Android SDK et un émulateur/device sont connectés.

### 3. Clone et install les dépendances
```bash
cd angell_study
flutter pub get
```

### 4. Build l'APK
```bash
# Debug (pour tester)
flutter build apk --debug

# Release (pour installer sur ton phone)
flutter build apk --release
```

L'APK se trouve dans :
```
build/app/outputs/flutter-apk/app-release.apk
```

### 5. Installe sur ton Android
```bash
adb install build/app/outputs/flutter-apk/app-release.apk
```
Ou transfère le fichier APK directement sur ton téléphone et installe-le.

---

## Structure du projet

```
lib/
├── main.dart               # Entry point
├── models/models.dart      # Subject, Chapter, NotePage, Flashcard, Task
├── services/
│   ├── database_service.dart  # SQLite
│   └── app_state.dart         # Provider state
├── theme/app_theme.dart    # Dark/Light themes
├── screens/
│   ├── home_screen.dart    # Liste des matières
│   ├── subject_screen.dart # Sidebar chapitres + pages
│   ├── editor_screen.dart  # Éditeur Quill
│   ├── flashcard_screen.dart  # Session de révision
│   ├── search_screen.dart  # Recherche globale
│   └── tasks_screen.dart   # Vue toutes les tâches
└── widgets/
    ├── subject_card.dart   # Card matière
    └── dialogs.dart        # Modals de création
```

---

## Customisation rapide

**Changer la couleur principale** → `lib/theme/app_theme.dart`, ligne `_primary`

**Ajouter des emojis** → `lib/widgets/dialogs.dart`, liste `emojis`

**Modifier le spaced repetition** → `lib/services/app_state.dart`, méthode `reviewFlashcard`
