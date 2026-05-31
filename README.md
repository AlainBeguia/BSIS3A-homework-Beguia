📱 Business AI Pro — AI-Powered Business Assistant App

Smart business management for small businesses, powered by OpenAI GPT and Firebase.


---

## 📱 About the App

*Business AI Pro* is an Android mobile app built with Flutter that helps small business owners manage their operations intelligently. It combines an AI-powered business assistant with inventory tracking and record management — all connected to the cloud in real time.

### 🎯 Business Problem Solved
Small business owners in the Philippines often make decisions without data or expert guidance. This leads to:
- Poor inventory control causing stockouts or overstock
- No access to affordable business consulting
- Difficulty tracking and organizing business records
- No system for logging or analyzing stock movements

### 👥 Target Users
- Small to medium business owners
- Store managers and inventory staff
- Entrepreneurs who need quick business advice
- Any business needing an affordable AI-powered Android management tool

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🤖 AI Business Assistant | OpenAI GPT-3.5-turbo answers business questions, suggests strategies, and helps solve common business problems |
| 🔐 Firebase Authentication | Secure login and registration with email and password |
| ☁️ Cloud Database | Real-time Firestore database — inventory and business records synced instantly |
| 📦 Inventory Management | Add, monitor, and manage inventory items together with their quantities |
| 📋 Business Records (CRUD) | Create, read, update, and delete business records within the system |
| ⚠️ API Error Handling | Graceful error messages when the AI service is unavailable or quota is exceeded |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Flutter (Dart) | Android mobile app framework |
| Firebase Authentication | User login and registration |
| Cloud Firestore | NoSQL cloud database |
| OpenAI GPT-3.5-turbo | AI business assistant and response generation |
| HTTP (Dart) | API communication with OpenAI |
| flutter_test | Unit and widget testing |

---

## 🚀 How to Run the App

### Prerequisites
Make sure you have the following installed:
- Flutter SDK (>=3.0.0)
- Android Studio or VS Code
- Android device or emulator (API 21+)
- Node.js (for Firebase CLI)
- Git
- An active OpenAI account at [platform.openai.com](https://platform.openai.com)

### Step 1 — Clone or Download the Repository
```
git clone <your-repo-url>
cd flutter_application_12
```

### Step 2 — Install Dependencies
```
flutter pub get
```

### Step 3 — Firebase Setup
The `firebase_options.dart` file is already included in `lib/`. No additional Firebase setup is needed to run the app.

If you want to connect your own Firebase project:
```
dart pub global activate flutterfire_cli
flutterfire configure
```

Then download `google-services.json` from your Firebase project and place it at:
```
android/app/google-services.json
```

Make sure **Email/Password Authentication** and **Firestore Database** are enabled in your Firebase Console.

### Step 4 — Add OpenAI API Key (Required for AI Features)
Open `lib/services/ai_service.dart` and find:
```
static const String apiKey = "sk-proj-YOUR_API_KEY_HERE";
```

Replace it with your actual OpenAI API key from:
https://platform.openai.com/api-keys

⚠️ The API key is required to use the AI Business Assistant feature. Make sure your account has available credits.

### Step 5 — Connect Android Device
- Enable **Developer Options** on your Android phone
- Turn on **USB Debugging**
- Connect via USB

Or start an Android emulator in Android Studio.

### Step 6 — Run the App
```
flutter run
```

Select your Android device when prompted.

---

## 🤖 How to Showcase the AI Feature

Follow these steps during the demo to show the OpenAI GPT integration working live:

### Step 1 — Register or Login
- Open the app on your Android device
- Login with your credentials (e.g., `adagor@gbox.com`)
- Or register a new account using any valid email and password

### Step 2 — Navigate to the Dashboard
After login, the **Business AI Dashboard** appears with three main options:
- AI Assistant
- Inventory Management
- Business Records (CRUD)

Tap **AI Assistant** to begin the AI demo.

### Step 3 — Ask a Business Question
1. In the text field labeled *"Ask Business AI"*, type a business-related question:
   - *"What is the problem of coffee shop business?"*
   - *"How can I reduce my inventory costs?"*
   - *"Give me a simple marketing strategy for a small bakery."*
   - *"How do I attract more customers to my clothing store?"*
2. Tap **Generate**
3. Wait 2–5 seconds for OpenAI to respond

You will see an AI-generated response appear directly on screen.

### Step 4 — Ask Different Types of Questions
Try various business scenarios to show the AI's range:

| Question Type | Example Prompt | Expected AI Result |
|---|---|---|
| Problem analysis | "What is the problem of coffee shop business?" | List of common pain points and causes |
| Strategy advice | "How do I attract more customers?" | Marketing strategies and tips |
| Financial guidance | "How can I reduce my inventory costs?" | Cost reduction methods |
| General consulting | "What business is profitable in the Philippines?" | Business opportunity suggestions |

### Step 5 — Demonstrate Error Handling
To show the app's reliability:
1. Temporarily replace the API key with an invalid string
2. Ask a question and tap **Generate**
3. The app will display a proper error message instead of crashing

This confirms the error-handling logic in `ai_service.dart` is working correctly.

### What the AI Does
Business AI Pro sends your prompt to OpenAI with this system context:

```
Role: system → "You are a business assistant."
Role: user   → [your question here]
Model: gpt-3.5-turbo | Temperature: 0.7
```

OpenAI responds with a business-focused answer, which the app displays directly in the chat screen.

---

## 📦 How to Showcase Inventory Management

1. Tap **Inventory Management** from the dashboard
2. Enter an item name (e.g., *"Full Cream Milk"*) and quantity (e.g., `28`)
3. Tap **Add Item**
4. The item appears in the list with its quantity
5. Add several items to show the list updating in real time

---

## 📋 How to Showcase Business Records (CRUD)

1. Tap **Business Records** from the dashboard
2. Enter a business name (e.g., *"Starbucks"*) and tap **Save Record**
3. View the saved record in the list
4. Demonstrate updating or deleting a record to show full CRUD functionality
5. All changes are instantly synced to **Cloud Firestore**

---

## 🗄️ Database Structure (Firestore)

```
users/
  └── {userId}/
        email: string
        createdAt: timestamp

products/
  └── {productId}/
        userId: string
        name: string
        quantity: int
        createdAt: timestamp
        lastUpdated: timestamp

records/
  └── {recordId}/
        userId: string
        businessName: string
        createdAt: timestamp
```

---

## 🧪 Running Unit Tests

```
flutter test
```

Expected output:
```
00:06 +3: All tests passed!
```

### What the Tests Check

| Test | What It Verifies |
|---|---|
| Widget rendering | Login and dashboard screens load without errors |
| Input validation | Empty fields are rejected before API calls |
| Error handling | Invalid API key returns error message, not a crash |

---

## 📁 Project Structure

```
flutter_application_12/
├── lib/
│   ├── screens/
│   │   ├── ai_chat_screen.dart       # AI Business Assistant UI
│   │   ├── home_screen.dart          # Dashboard / Main Menu
│   │   ├── inventory_screen.dart     # Inventory Management
│   │   ├── login_screen.dart         # Firebase Auth Login
│   │   └── records_screen.dart       # Business Records (CRUD)
│   ├── services/
│   │   ├── ai_service.dart           # OpenAI GPT-3.5-turbo integration
│   │   ├── auth_service.dart         # Firebase Authentication
│   │   └── firestore_service.dart    # Firestore database service
│   ├── main.dart                     # App entry point
│   └── firebase_options.dart         # Firebase configuration (auto-generated)
├── test/
│   ├── validation_test.dart          # Input validation tests
│   └── widget_test.dart              # Widget rendering tests
├── android/                          # Android build files
├── pubspec.yaml                      # Dependencies
└── README.md                         # This file
```

---

## 📦 Building the APK

```
flutter build apk --release
```

Output location:
```
build/app/outputs/flutter-apk/app-release.apk
```

---

## ⚠️ Troubleshooting

| Issue | Solution |
|---|---|
| `insufficient_quota` error from OpenAI | Add billing credits at platform.openai.com/billing |
| Firebase not initializing | Verify `google-services.json` is in `android/app/` |
| App not finding a connected device | Run `flutter doctor` to check your environment |
| Gradle build fails | Run `flutter clean` then `flutter pub get` |
| AI response is slow | Normal — GPT API calls take 2–5 seconds depending on connection |

---

*Group 6 – WAKE ME UP WHEN CODE IS END*
Agor, Daniel | Bondalo, Joshua | Bobis, Jan Nicolai | Beguia, Jan Alain | Navarrete, Francine Mae
