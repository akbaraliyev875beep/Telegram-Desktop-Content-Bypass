# Telegram Desktop - Content Restriction Bypass (Logic Flaw)

## 🛡️ Executive Summary
This report documents a critical logic vulnerability discovered in **Telegram Desktop (v6.7.3)**. Despite the "Restrict Saving Content" feature being enabled in a channel, users can still access and save files locally.

## 🧱 The Logic Flaw
Telegram Dgfghesktop correctly blocks "Save As" and "Forwarding," but it fails to hide the **"Show in Folder"** option in the context menu. Since the client automatically caches the file to display it, the file already exists on the local disk.

**Analogy:** *It is like putting an unpickable lock on the front door but leaving the key right under the doormat (the 'Show in Folder' option).*

## 🧪 Proof of Concept (PoC)
1. Open a Telegram channel where **"Restrict Saving Content"** is active.
2. Locate any document or PDF file.
3. Right-click the file.
4. Notice the warning: *"Copying and forwarding is not allowed..."*
5. **The Bypass:** Click **"Show in Folder"**.
6. Windows Explorer/Ubuntu Files opens, highlighting the original file in the `Telegram Desktop` cache folder. You now have full access to copy/move the file.

## 💻 Environment Tested
- **Windows 10/11** (Confirmed)
- **Ubuntu Linux** (Confirmed)
- **Telegram Version:** v6.7.3 (Original)

## 📢 Disclosure Timeline
- **Reported to Telegram:** Reported via official security channels.
- **Status:** Closed as N/A / Acknowledged as client-side behavior.
- **Public Disclosure:** April 6, 2026.
## Screenshots
![Step 1](Screenshot%20from%202026-04-06%2022-03-19.png)
![Step 2](Screenshot%20from%202026-04-06%2022-03-29.png)
