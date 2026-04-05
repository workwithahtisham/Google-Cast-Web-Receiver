# Custom Google Cast Web Receiver

This is a Vercel-ready static Google Cast Custom Web Receiver.

## Files

- `index.html` - the receiver app
- `vercel.json` - small Vercel config to avoid stale cached HTML

## What was fixed

- fixed broken JavaScript template-string syntax
- removed duplicate `id` attribute from the codec badge element
- switched the Cast SDK script to explicit `https://`
- cleaned up loading/error handling
- normalized media format detection for MP4, MKV, HLS, DASH, WebM, and OGG

## Deploy on Vercel

### Option 1: GitHub + Vercel

1. Create a new GitHub repo.
2. Upload these files.
3. Import the repo into Vercel.
4. Deploy.
5. Your receiver URL will be:
   - `https://YOUR-PROJECT.vercel.app/`

### Option 2: Vercel CLI

```bash
npm i -g vercel
cd cast-web-receiver
vercel --prod
```

## Register in Google Cast

1. Open the Google Cast SDK Developer Console.
2. Create a **Custom Web Receiver**.
3. Set the receiver URL to your Vercel production URL.
4. Save it and copy the generated **App ID**.
5. Send that App ID to the iOS developer.

## Notes

- Use the **production** Vercel URL, not a preview URL.
- If the iOS sender only passes `contentId`, this receiver automatically maps it to `contentUrl`.
- If `contentType` is missing, this receiver tries to infer it from the file extension.
