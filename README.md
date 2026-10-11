# Beepo

A personal AI assistant for Android, shaped like a cute robot puppy. Chat by text or talk to it out loud, and ask it to make PDFs and slide decks. It runs on free AI services, so there is nothing to pay for.

## What Beepo can do

- **Chat** about anything: ideas, advice, decisions, writing, plans, or just talking.
- **Voice conversations.** Tap the mic and talk. Beepo answers out loud and keeps listening until you end it.
- **Make files.** Ask for a PDF or a PowerPoint deck and download or share it from the chat.
- **Personalities.** Friendly, Concise, Playful or Professional, chosen in Settings.
- **Chat history.** Conversations are saved on your phone, with search and delete.
- **Free AI with a backup.** Uses Gemini, and can switch to Cerebras if one hits its free limit.

### What it can't do

Beepo works only inside its own chat. It cannot see your calendar, email or files, send messages, set alarms, or browse the web. Its facts come from the AI model's training, so it can be wrong or out of date.

## Files in this repo

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (interface, chat, voice, file making). |
| `.github/workflows/build-apk.yml` | GitHub Actions recipe that builds the Android app. |
| `README.md` | This file. |

## Build the app (no computer setup needed)

1. Create a GitHub repository and upload the files above, keeping `build-apk.yml` at `.github/workflows/build-apk.yml`.
2. Open the **Actions** tab. The build starts when you commit to `main`, or you can run **Build Beepo APK** by hand.
3. Wait for the run to turn green (a few minutes).
4. Open **Releases** on the repo page and download `beepo.apk`.
5. On your phone, open the file and allow installing from this source when asked.

To update Beepo later, replace `index.html` (and the workflow file if it changed), wait for the green build, and install the newest `beepo.apk` over the old one. Your chats and settings stay. The version shows at the bottom of Settings.

## Set up your free AI key

Open Settings in the app and paste a key.

- **Gemini (required for voice):** get a free key at <https://aistudio.google.com/apikey>.
- **Cerebras (optional backup):** get a free key at <https://cloud.cerebras.ai>.

Keys are stored only on your phone. Turn on **auto-switch** in Settings to fall back to the other service when one runs out.

## Using voice

1. Tap the mic next to the message box and allow microphone access the first time.
2. Talk. When you stop, Beepo thinks and answers out loud, then listens again.
3. Tap the face while it talks to interrupt it, or while you talk to finish your turn early.
4. Tap the X to end.

Voice uses Gemini to turn your speech into text, so it needs your Gemini key and an internet connection. If microphone access was blocked, allow it in your phone's app settings for Beepo. The spoken voice is your phone's built-in one, and Settings lets you change the voice and pitch.

## Free limits and privacy

- Free tiers have limits on requests per minute and per day. If you hit one, wait for it to reset or let Beepo switch to the other service.
- On free tiers, Google may use what you send to improve its products. Don't share anything sensitive.
- Chats and keys are saved on your phone and sent only to the AI service you chose. Voice recordings are sent to Gemini for transcription and are not kept by the app.

## Troubleshooting

- **Build fails:** open the failed run in Actions and read the red step. Re-running it often fixes a temporary download problem.
- **"Rate limited":** you reached a free limit. Wait, or switch provider in Settings.
- **Voice does nothing:** check that the mic is allowed, a Gemini key is saved, and you are online.
- **PDF or slides won't make:** the file tools load from the internet when the app opens. Check your connection and reopen the app.
- **Old version still installed:** check the version at the bottom of Settings against the latest release.

## Built with

A single HTML page wrapped as an Android app with [Capacitor](https://capacitorjs.com), [jsPDF](https://github.com/parallax/jsPDF) for PDFs, [PptxGenJS](https://gitbrent.github.io/PptxGenJS/) for slides, and the Gemini and Cerebras APIs.
