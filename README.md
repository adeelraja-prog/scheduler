# Adeel Raja — YouTube Clip Scheduler

A static, browser-based tool for preparing multiple YouTube clips, optionally burning in a text/logo watermark, and scheduling uploads.

## 1. Publish with GitHub Pages

1. Open **Settings** in this repository.
2. Select **Pages** in the left sidebar.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch **main** and folder **/(root)**, then click **Save**.
5. Wait for GitHub Pages to finish publishing.

The site address will be:

https://adeelraja-prog.github.io/scheduler/

## 2. Configure Google / YouTube access

The app uses Google Identity Services in the browser. It does not contain a Google Client ID or any private API key.

1. Open the [Google Cloud Console](https://console.cloud.google.com/).
2. Create or select a Google Cloud project.
3. Enable **YouTube Data API v3**.
4. Configure the OAuth consent screen and add your Google account as a test user if the app is still in testing.
5. Create an **OAuth Client ID** with application type **Web application**.
6. Add this exact URL under **Authorized JavaScript origins**:

   `https://adeelraja-prog.github.io`

7. Copy the Client ID ending in `.apps.googleusercontent.com`.
8. Open the Scheduler website, paste the Client ID, and choose **Sign in with Google & connect YouTube**. Approve the requested YouTube upload permission.

Do not publish a client secret, access token, or private API key in this repository. The browser app needs the public OAuth Client ID only.

## 3. How scheduling works

- Select one or more video files.
- Set the watermark text and/or choose a logo image.
- Choose watermark style and position.
- Choose the first publication time and the interval between clips.
- Start the queue. Files are processed and uploaded sequentially.
- The app uploads each clip as **Private** with a future YouTube `publishAt` time.

YouTube scheduled publishing requires the video to remain private and the publication time to be in the future (at least 15 minutes ahead). The app moves a too-soon first time to the earliest allowed time after asking for confirmation.

## Important limitations

- This is **not** a server-side scheduler. Keep the browser tab open, the computer awake, and the internet connection active until all clips are uploaded.
- The Google access token is held in page memory. If it expires or the page is refreshed, sign in again.
- The app processes one video at a time. Watermark rendering uses browser media recording and outputs WebM; use a current Chrome or Edge browser for best compatibility.
- Large or long videos can require substantial memory and processing time.
- YouTube API daily quota and account/channel eligibility limits still apply.
- If a clip fails, it remains in the queue. Fix the reported issue and retry. Review the YouTube Studio schedule after uploading.

## Repository files

- `index.html` — the complete English-language Scheduler website.
- `README.md` — setup and operating instructions.

Designed for Adeel Raja.
