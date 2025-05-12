# 📺 YouTube Channel Monitor — n8n Workflow

This repository contains an **automation workflow** built with [n8n](https://n8n.io), a low-code tool, to **monitor a YouTube channel** and **send an email alert** every time a new video is published.

This can be helpful if:
- You run a YouTube channel and want instant alerts about new uploads.
- You manage multiple channels and want to track updates centrally.
- You want to forward updates to clients, teams, or subscribers via email.

---

## 🌟 What the Workflow Does

This workflow automatically performs the following steps:

1. **Every minute**, it checks the RSS feed of a specific YouTube channel.
2. It **reads the latest videos** in that feed.
3. It selects only the **most recent video** (avoiding duplicates).
4. It formats an **email message** that includes:
   - The video title
   - A link to watch it
   - The date and time it was published
5. It sends the alert using **Gmail**, with the subject:
   > **🎬 Just Released: A Fresh Video Awaits You!**
6. The workflow completes and waits for the next scheduled trigger.

> ✅ You can keep this workflow **active**, and it will continue to **monitor every new upload** on the YouTube channel automatically.

---

## 🔧 Workflow Breakdown

| Node Name        | Role in Workflow |
|------------------|------------------|
| 🕒 **Schedule Trigger** | Fires the workflow every 1 minute |
| 📡 **RSS Read** | Fetches the YouTube channel's RSS feed |
| 🧠 **Code** | Filters to select only the latest video |
| 🛠️ **Edit Fields** | Creates a formatted text message with video info |
| ✉️ **Gmail** | Sends the email to the recipient |
| ✅ **END** | Marks the end of the automation |

---

## 📬 Example Email Output

**Subject**:  
```
🎬 Just Released: A Fresh Video Awaits You!
```

**Body**:
```
New video alert! 🎬  
Title: How to Build a YouTube Monitor  
Watch now: https://www.youtube.com/watch?v=abcd1234  
Published at: 2025-05-12T08:00:00Z
```

*(Exact content will change depending on the latest video.)*

---

## 📦 RSS Feed Details

The workflow uses YouTube’s public RSS feed format:

```
https://www.youtube.com/feeds/videos.xml?channel_id=UCnnQ3ybuyFdzvgv2Ky5jnAA
```

> 🔁 Replace `UCnnQ3ybuyFdzvgv2Ky5jnAA` with your desired **YouTube channel ID**.

### 📍 How to Find the Channel ID:

1. Go to the YouTube channel in a browser.
2. Look at the URL — it will be in the format:
   ```
   https://www.youtube.com/channel/UCxxxxxxxxxxxxxxxxx
   ```
3. Copy everything after `/channel/` — that’s the **channel ID**.

---

## ⚙️ How to Set Up

Follow these steps to install and use the workflow in your n8n environment:

### 1. **Import the Workflow**
- Open your n8n instance
- Go to **Workflows > Import from File**
- Upload `YouTube_Channel_Monitor.json`

### 2. **Configure Gmail**
- Go to **Credentials > Gmail OAuth2**
- Add a new credential using your Google account
- In the **Gmail node**, select your Gmail credential
- Make sure the “sendTo” field is your desired recipient

### 3. **Customize If Needed**
- You can edit the Gmail subject, message, and formatting in the **Edit Fields** node
- You can change how often it checks (default is every 1 minute)

### 4. **Activate the Workflow**
- Click **Activate**
- It will now **continuously monitor the YouTube channel** for new uploads and send alerts

---

## 🔐 Security & Best Practices

- Your Gmail OAuth2 credentials must be kept private. Never share them or store in public repos.
- Avoid hardcoding sensitive email addresses or keys.
- YouTube RSS feeds are public but still avoid sharing private channel IDs if applicable.
- Gmail has daily sending limits—this workflow is lightweight but keep it in mind.

---

## 🧪 Testing Tips

To test the workflow:
- Temporarily change the RSS feed to a channel that uploads frequently
- Run the workflow manually in n8n ("Execute Workflow")
- Observe the logs and email output

---

## 📄 License

This project is open-sourced under the **MIT License**. You are free to modify, distribute, and use it for personal or commercial purposes.

---

## 🙋 Support

If you encounter issues or need help:
- Create an issue in this repository
- Reach out via email (configured recipient)
- Or ask in the [n8n community](https://community.n8n.io/)