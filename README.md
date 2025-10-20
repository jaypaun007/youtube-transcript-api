# YouTube Transcript API

![YouTube Transcript API](https://i.postimg.cc/hSFD7yq8/You-Tube-Transcript-API.png?dl=1)

A FastAPI service to fetch YouTube transcripts with automatic language detection and fallback support.

**Note:** The hosted transcript API ([https://youtube-transcript-api-tau-one.vercel.app/](https://youtube-transcript-api-tau-one.vercel.app/)) has a **rate limit of 5 requests per minute**. For heavy usage or production applications, consider hosting your own instance.

---

## 🚀 Quick Start

```bash
# Make a POST request to fetch transcript
curl -X POST "https://youtube-transcript-api-tau-one.vercel.app/transcript" \
  -H "Content-Type: application/json" \
  -d '{"video_url": "https://www.youtube.com/watch?v=UrsmFxEIp5k"}'
```

---

## 📡 API Endpoints

### 🎬 Fetch Transcript

Retrieves the transcript for any YouTube video with available captions.

**Endpoint:** `POST /transcript`

**Headers:**
```
Content-Type: application/json
```

**Request Body:**
```json
{
  "video_url": "https://www.youtube.com/watch?v=VIDEO_ID"
}
```

### Request Example

#### cURL
```bash
curl -X POST "http://localhost:8000/transcript" \
  -H "Content-Type: application/json" \
  -d '{
    "video_url": "https://www.youtube.com/watch?v=UrsmFxEIp5k"
  }'
```

#### Python
```python
import requests

url = "https://youtube-transcript-api-tau-one.vercel.app/transcript"
payload = {"video_url": "https://www.youtube.com/watch?v=UrsmFxEIp5k"}

response = requests.post(url, json=payload)
print(response.json())
```

#### JavaScript
```javascript
fetch('https://youtube-transcript-api-tau-one.vercel.app/transcript', {
  method: 'POST',
  headers: {'Content-Type': 'application/json'},
  body: JSON.stringify({
    video_url: 'https://www.youtube.com/watch?v=UrsmFxEIp5k'
  })
})
.then(res => res.json())
.then(data => console.log(data));
```

### Response Example

**Success (200 OK):**
```json
{
  "video_url": "https://www.youtube.com/watch?v=UrsmFxEIp5k",
  "transcript": "Full transcript text with all the spoken content from the video..."
}
```

**Error (404):**
```json
{
  "detail": "No transcript available for this video"
}
```

---

## ⚠️ Rate Limiting

**Important:** The hosted API enforces a **rate limit of 5 requests per minute** for security and to prevent concurrent request abuse.

- **Limit:** 5 requests/minute per IP
- **Reset:** Every 60 seconds
- **Exceeded Response:** `429 Too Many Requests`
- **Recommendation:** Implement caching or host your own instance

---

## 💡 What is the Use of This API?

### 1. **Video Summarization & AI Chat**
Extract transcripts to create AI-powered video summaries or enable chat interfaces where users can ask questions about video content using LLMs like GPT, Claude, or Gemini.

```python
# Example: Summarize with OpenAI
transcript = get_youtube_transcript(video_url)
summary = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[{
        "role": "user",
        "content": f"Summarize this video: {transcript}"
    }]
)
```

### 2. **Multi-Language Video Translation**
Create translated versions of videos by extracting the original transcript and translating it to multiple languages for global audiences.

### 3. **AI Training Data Collection**
Gather large-scale transcription data from educational, tutorial, or documentary videos to train machine learning models, especially for NLP tasks.

### 4. **Instant Script Formatting**
Convert video content into readable, searchable text format for documentation, blog posts, or accessibility purposes.

**Note:** This API allows commercial use but does **not** promise 99.99% uptime or guarantee 100% accuracy for all videos.

---

## ✅ Pros

- 🎯 **Easy to Use** - Simple REST API with minimal setup
- 💰 **Free** - No cost for basic usage (rate-limited)
- 🌐 **Multilingual Support** - Works with transcripts in multiple languages
- ⚡ **Better Than Old Libraries** - Modern FastAPI implementation with better error handling
- 🚫 **No Language Barrier** - Automatically detects and retrieves available languages

---

## ❌ Cons

- ⏰ **Not Always Uptime** - Hosted version may experience downtime
- 📹 **Limited Video Support** - Doesn't work on private, age-restricted, or videos without transcripts
- 🐌 **Rate Limited** - Only 5 requests/minute on hosted version
- 🎯 **Accuracy Varies** - Auto-generated transcripts may have errors
- 🔒 **No Authentication** - Public API without user-specific quotas

---




## 📚 Use Cases

| Use Case | Description |
|----------|-------------|
| 📝 Content Analysis | Extract and analyze video content for SEO, research, or insights |
| 🔍 Search & Discovery | Make video libraries searchable by transcript content |
| 🌐 Translation | Generate multilingual subtitles and translations |
| 📊 Data Collection | Build datasets for AI/ML training from video content |
| ♿ Accessibility | Provide text alternatives for hearing-impaired users |
| 🤖 Chatbots | Create AI assistants that can answer questions about videos |
| 📖 Documentation | Convert tutorial videos into written guides |

---

## 🔒 Limitations

- Only works with videos that have transcripts (manual or auto-generated)
- Cannot access private, unlisted (without link sharing), or age-restricted videos
- Subject to YouTube's Terms of Service
- Rate limited on hosted version (5 req/min)
- Auto-generated transcripts may contain errors
- No guarantee of 99.99% uptime on free hosted version

---





## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs or issues
- Suggest new features
- Submit pull requests
- Improve documentation

---

## 📄 License

This project is provided as-is for educational and personal use. Ensure compliance with YouTube's Terms of Service when using this API.

**Disclaimer:** This API does not store or redistribute YouTube content. It simply provides programmatic access to publicly available transcript data.

---

## 🔗 Links

- **Hosted API:** [https://youtube-transcript-api-tau-one.vercel.app/](https://youtube-transcript-api-tau-one.vercel.app/)
- **API Docs:** [https://youtube-transcript-api-tau-one.vercel.app/docs](https://youtube-transcript-api-tau-one.vercel.app/docs)

---

**Made with ❤️ for developers**
