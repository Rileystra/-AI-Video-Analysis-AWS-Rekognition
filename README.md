# -AI-Video-Analysis-AWS-Rekognition

# 🎬 AI Video Analysis – AWS Rekognition

An automated video analysis pipeline that uses **AWS Rekognition** and **Python** to extract meaningful metadata from video files — replacing manual review with scalable machine intelligence.

---

## 📌 What It Does

This project automates the process of analysing video content by:

- Detecting and tagging objects, scenes and activities in video footage
- Extracting metadata and labels from each segment at scale
- Classifying video content without any manual intervention
- Outputting structured results ready for downstream use (databases, dashboards, search indexes)

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3 |
| AI / ML | AWS Rekognition |
| Cloud Storage | AWS S3 |
| Access Control | AWS IAM |
| SDK | boto3 |

---

## 🏗️ Architecture Overview

```
Video File
    │
    ▼
AWS S3 Bucket          ← Video uploaded / stored here
    │
    ▼
AWS Rekognition        ← Start label detection job
    │
    ▼
Python Pipeline        ← Poll job status → retrieve results
    │
    ▼
Structured Output      ← JSON metadata (labels, confidence scores, timestamps)
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- An AWS account with Rekognition and S3 access
- AWS CLI configured (`aws configure`)
- boto3 installed

### Installation

```bash
git clone https://github.com/YOUR-USERNAME/aws-rekognition-video-analysis.git
cd aws-rekognition-video-analysis
pip install -r requirements.txt
```

### Configuration

Set your AWS credentials and bucket name as environment variables:

```bash
export AWS_ACCESS_KEY_ID=your_access_key
export AWS_SECRET_ACCESS_KEY=your_secret_key
export AWS_DEFAULT_REGION=eu-west-1
export S3_BUCKET_NAME=your-bucket-name
```

> ⚠️ Never commit credentials to GitHub. Use environment variables or AWS IAM roles.

### Usage

**1. Upload your video to S3:**
```bash
aws s3 cp your-video.mp4 s3://your-bucket-name/
```

**2. Run the analysis pipeline:**
```bash
python analyse.py --video your-video.mp4
```

**3. View results:**
Results are saved to `output/results.json` with labels, confidence scores and timestamps.

---

## 📂 Project Structure

```
aws-rekognition-video-analysis/
│
├── analyse.py          # Main pipeline script
├── rekognition.py      # AWS Rekognition helper functions
├── s3_utils.py         # S3 upload / download helpers
├── requirements.txt    # Python dependencies
├── output/             # Generated results (gitignored)
└── README.md
```

---

## 📊 Example Output

```json
{
  "video": "example.mp4",
  "duration_seconds": 42,
  "labels": [
    {
      "name": "Car",
      "confidence": 98.4,
      "timestamp_ms": 1200
    },
    {
      "name": "Road",
      "confidence": 96.1,
      "timestamp_ms": 1200
    },
    {
      "name": "Person",
      "confidence": 91.7,
      "timestamp_ms": 3400
    }
  ]
}
```

---

## ☁️ AWS Services Used

- **Amazon S3** — video storage and retrieval
- **Amazon Rekognition** — label detection, scene analysis, activity recognition
- **AWS IAM** — least-privilege access control for all service interactions

---

## 🔐 Security Notes

- IAM roles follow the **least-privilege principle** — Rekognition and S3 permissions are scoped to only what is needed
- No credentials are hardcoded — all secrets managed via environment variables or IAM instance roles
- S3 bucket access is restricted; no public read enabled

---

## 📈 Future Improvements

- [ ] Add face detection and moderation labels
- [ ] Stream results to a DynamoDB table for querying
- [ ] Build a simple dashboard to visualise labels over time
- [ ] Add support for batch processing multiple videos

---



---

## 📄 Licence

MIT — free to use, modify and distribute.
