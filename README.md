# Leads Tracker — Mobile App

A lightweight URL leads tracker built with **Vite + Vanilla JS**, deployable as a Progressive Web App (PWA).  
Live demo: [leads-tracker-mobile-app-00.netlify.app](https://leads-tracker-mobile-app-00.netlify.app/)

---

## Getting Started

Install the dependencies and run the project:

```bash
npm install
npm start
```

Head over to [vitejs.dev](https://vitejs.dev/) to learn more about configuring Vite.

---

## App Screenshots

<details>
<summary><strong>Source</strong> — click to view screenshots</summary>
<br>

| # | Screenshot | Description |
|---|-----------|-------------|
| 1 | ![Loading Screen](images/01-loading-screen.jpg) | **Loading Screen** — App splash screen with the Leads Tracker icon centered on a white background |
| 2 | ![Mobile Home Screen](images/02-mobile-home-screen.jpg) | **Mobile Home Screen** — App icon pinned to the Android home screen, labelled "Leads Tr…" |
| 3 | ![App Empty State](images/03-app-empty-state.jpg) | **App Empty State** — The app's main UI: URL input field, SAVE INPUT and DELETE ALL buttons (no saved leads yet) |
| 4 | ![Save URL Input](images/04-save-url-input.jpg) | **Save URL Input** — Two URLs have been saved and are displayed as clickable links |
| 5 | ![Delete and Re-add Input](images/05-delete-and-re-add-input.jpg) | **Delete and Re-add Input** — After deleting all entries, a new URL is entered and saved |

</details>

---

## Firebase Key Concepts

The app uses the **Firebase Realtime Database** (CDN imports, no build-step SDK) via the following core APIs:

| API | Description |
|-----|-------------|
| `initializeApp(config)` | Bootstraps the Firebase app with the database URL |
| `getDatabase(app)` | Returns a reference to the Realtime Database instance |
| `ref(database, path)` | Creates a database reference at the given path (e.g. `"leads"`) |
| `push(ref, value)` | Appends a new child node to the reference — used to save each URL |
| `onValue(ref, callback)` | **Real-time listener** — fires immediately and on every subsequent data change; the callback receives a `snapshot` |
| `snapshot.exists()` | Returns `true` if the snapshot contains any data (guards against empty renders) |
| `snapshot.val()` | Returns the raw JavaScript value of the snapshot (an object keyed by push IDs) |
| `Object.values(obj)` | Converts the Firebase push-ID-keyed object into a plain array for rendering |
| `remove(ref)` | Deletes all data under the reference — triggered on double-click of DELETE ALL |

> **`onValue` is the heart of the app.** It subscribes to the `leads` node and re-renders the list every time data changes in Firebase, keeping the UI always in sync — no manual refresh needed.

### Recap Slides

**Firebase Basics** — `import`, `initializeApp`, `getDatabase`, `ref`, `push`, `onValue`  
![Recap — Firebase Basics](images/image.png)

**Firebase Advanced** — `snapshot`, `snapshot.exists()`, Object→Array, `remove`, viewport, favicon, Web App Manifest  
![Recap — Firebase Advanced](images/recap-firebase-advanced.png)

---

## About Scrimba

At Scrimba our goal is to create the best possible coding school at the cost of a gym membership! 💜  
If we succeed with this, it will give anyone who wants to become a software developer a realistic shot at succeeding, regardless of where they live and the size of their wallets 🎉  
The Fullstack Developer Path aims to teach you everything you need to become a Junior Developer, or you could go further with one of our advanced courses 🚀

- [Our courses](https://scrimba.com/courses)
- [The Frontend Career Path](https://scrimba.com/fullstack-path-c0fullstack)
- [Become a Scrimba Pro member](https://scrimba.com/?via=u42ff4fa)

Happy Coding!
