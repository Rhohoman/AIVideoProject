# AIVideoProject

## What This Is

An AI-powered basketball video analysis system. A user uploads a single game clip, and the system automatically tracks players, detects shot attempts, identifies made baskets, and outputs a points summary with timestamps and confidence scores.

## MVP Scenario

- **Format:** 3v3 half-court game (6 players total)
- **Input:** One YouTube video, up to ~10 minutes
- **Player identification:** Jersey color only — no OCR, no jersey numbers needed
- **Output:** Points scored per team, timestamps of made baskets, confidence scores per event

## What the System Does (v1)

1. User uploads video
2. Worker extracts frames and runs object detection (players + ball)
3. Players are tracked across frames and assigned to teams by jersey color
4. System detects shot attempts and made baskets using rule-based logic
5. Points are attributed to the shooting team
6. Results displayed on a dashboard with event timeline

## Tech Stack (Decided)

| Layer | Technology |
|---|---|
| Frontend | Next.js on Vercel |
| API | FastAPI (Python) |
| Worker | Python (same service as API at MVP scale) |
| Database | Supabase (hosted Postgres) |
| Video Storage | Cloudflare R2 |
| Queue | Postgres jobs table (polling) |
| Object Detection | YOLOv8 Nano |
| Player Tracking | ByteTrack (via Supervision library) |
| Jersey Classification | OpenCV K-means color clustering |

## Accuracy Expectation (MVP)

70–85% accuracy on made basket detection, depending on camera angle.
Confidence scores are shown on every event so users know when to verify manually.

## Planned Versions

- **v1:** Points only — team color, made baskets, timestamps, confidence
- **v2:** Rebounds, passes, shot chart, highlight clip generation
- **v3:** Assists, steals, team-level stats, multi-player tracking, brand/logo detection

## Design Notes

All planning documents are in `/Design Notes/`, numbered in reading order.
