# 📺 YouTube Channel Monitor Workflow (n8n)

This repository contains an **n8n workflow** (`YouTube_Channel_Monitor.json`) that monitors a YouTube channel for newly published videos and sends email alerts when a new video is detected.

---

## 📌 Features

- ⏱️ Periodically checks a YouTube channel using its RSS feed
- 📨 Sends an email alert for each new video
- ✏️ Custom email content formatting using dynamic data
- 🔧 Built using low-code automation tool [n8n](https://n8n.io/)

---

## 🛠️ How It Works

### Workflow Nodes:

| Node              | Description |
|-------------------|-------------|
| `Schedule Trigger` | Triggers the workflow every 1 minute |
| `RSS Read`        | Fetches latest videos from YouTube RSS feed |
| `Code`            | Passes the latest video as a single item |
| `Edit Fields`     | Formats message text dynamically (title, link, date) |
| `Gmail`           | Sends the formatted email to the configured address |
| `END`             | Ends the workflow |

---

## 🧪 YouTube Channel RSS Feed

The YouTube channel feed is fetched from:

```
https://www.youtube.com/feeds/videos.xml?channel_id=UCnnQ3ybuyFdzvgv2Ky5jnAA
```

---

## 🧷 Gmail Configuration

The email node uses Gmail OAuth2 credentials to send alerts.  
Example message format:

```
Subject: Apologies for the Earlier Emails – Final Version Now Working

Body:
New video alert! 🎬  
Title: {video title}  
Watch now: {video link}  
Published at: {published date}
```

You can customize the content in the **Gmail** node > message section.

---

## ⚙️ Prerequisites

- n8n instance (self-hosted or cloud)
- A Gmail account authorized via OAuth2
- A valid YouTube channel ID
- Internet access to fetch the RSS feed

---

## ▶️ Getting Started

1. Open your n8n instance
2. Go to **Workflows > Import**
3. Upload `YouTube_Channel_Monitor.json`
4. Update the Gmail node credentials and recipient address
5. Activate the workflow

---

## 🛡️ Notes

- Make sure your Gmail credentials have `send` permission.
- You can adjust the interval in the **Schedule Trigger** (default: every 1 minute).
- RSS feeds may cache results; test with recent video uploads.

---

## 📄 License

This workflow is open-sourced under the [MIT License](LICENSE).

---

## 🙋‍♀️ Support

For issues or questions, open an issue on this repository or contact the workflow author.