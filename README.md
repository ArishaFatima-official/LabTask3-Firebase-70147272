# UOL Lab Fault Desk

Android application for reporting and tracking faulty computers in university labs.
Built for **Mobile Application Development – Lab Task 03 (Firebase + RecyclerView)**.

## Overview
Students can report a problem with a lab computer, and everyone can see all reports on a shared live board. Staff can tap a report to mark it as **Fixed**. All changes appear instantly on every device because the data is stored in Firebase Realtime Database.

## Features
- Welcome screen with a clean green theme
- **Report a Fault** form: lab room, PC number, problem and priority (High / Normal)
- Input validation using `setError()` for empty fields
- **Live Fault Board** that updates automatically, with no refresh button
- Card for each report showing lab room, PC number, problem, priority and status
- Tap a card to mark it as Fixed (the card turns grey)
- Loading indicator while data is being fetched
- Works offline: reports are saved locally and synced when the internet returns

## Tech Stack
- Java, Android Studio
- Firebase Realtime Database
- RecyclerView, CardView, Material Components

## Project Structure
| File | Purpose |
|---|---|
| `WelcomeActivity.java` | Welcome screen |
| `MainActivity.java` | Live fault board (reads data from Firebase) |
| `ReportFaultActivity.java` | Form to submit a new report |
| `FaultReport.java` | Model class for one report |
| `FaultAdapter.java` | Connects report data to RecyclerView cards |
| `item_fault.xml` | Layout of one report card |

## How It Works
1. The student fills in the form and taps **Submit Report**.
2. `push().getKey()` creates a unique ID and `setValue()` saves the report in Firebase.
3. `addValueEventListener()` detects the new data and the report appears on the board.
4. A staff member taps the card, and only the `status` field is changed to `Fixed`.
5. Every device sees the update automatically.

The listener is removed in `onDestroy()` using `removeEventListener()`.

## Setup Instructions
1. Clone this repository and open it in Android Studio.
2. Create a project in the [Firebase Console](https://console.firebase.google.com).
3. Add an Android app with the package name `com.uol.labfaultdesk`.
4. Download `google-services.json` and place it inside the `app/` folder.
5. Create a **Realtime Database** and start it in **test mode**.
6. Run the app on an emulator or a real device.

> `google-services.json` is not included in this repository for security reasons. It is listed in `.gitignore`.

## Database Structure
```
faults
 └── <unique-id>
      ├── id
      ├── labRoom
      ├── pcNumber
      ├── problem
      ├── priority
      └── status
```

## Author
- **Name:** Arisha  Fatima
- **SAP ID:** 70147272
- **Section:** T
- **Course:** Mobile Application Development, University of Lahore
