# Job Scheduler & Automation System

A Frontend of job scheduling and automation dashboard built for Dotix Technologies.

## 🚀 Tech Stack

### Frontend
- Next.js 14 (App Router)
- React 18
- TypeScript
- Tailwind CSS
- Shadcn/ui Components
- Axios for API calls

## 📋 Features

1. ✅ Create jobs with taskName, payload (JSON), and priority
2. ✅ Job runner that simulates processing (3-second delay)
3. ✅ Dashboard with job listing and filters
4. ✅ Status tracking (pending → running → completed)
5. ✅ Outbound webhook integration
6. ✅ Job detail view with formatted payload
7. ✅ Real-time status updates

## 🏗️ Architecture

```
┌─────────────┐         ┌─────────────┐         ┌─────────────┐
│   Next.js   │────────▶│  Express.js │────────▶│    MySQL    │
│  Frontend   │◀────────│   Backend   │◀────────│   Database  │
└─────────────┘         └─────────────┘         └─────────────┘
                               │
                               ▼
                        ┌─────────────┐
                        │  Webhook.site│
                        │  (External)  │
                        └─────────────┘
```


## 📦 Installation & Setup

### Prerequisites
- Node.js 18+ installed
- Git

### 1. Frontend Setup

```bash
cd frontend
npm install
```

Create `.env.local` file in frontend directory:
```env
NEXT_PUBLIC_API_URL=http://localhost:5000
```

Start the frontend:
```bash
npm run dev
```

Frontend will run on `http://localhost:3000`

## 🪝 Webhook Behavior

When a job completes, the system automatically sends a POST request to the configured webhook URL with the following payload:

```json
{
  "jobId": 1,
  "taskName": "Send Welcome Email",
  "priority": "High",
  "payload": {
    "email": "user@example.com",
    "template": "welcome"
  },
  "completedAt": "2024-01-15T10:30:03Z"
}
```

### Testing Webhooks
1. Go to https://webhook.site
2. Copy your unique URL
3. Update `WEBHOOK_URL` in backend `.env`
4. Run a job and check webhook.site to see the incoming request

## 🎨 UI Features

- **Modern Dashboard**: Clean, responsive design using Tailwind CSS
- **Job List Table**: Displays all jobs with key information
- **Filters**: Filter by status and priority
- **Job Details Modal**: View complete job information including formatted JSON payload
- **Run Job Button**: Execute jobs directly from the dashboard
- **Status Badges**: Color-coded status indicators
- **Priority Badges**: Visual priority indicators


## 🐛 Known Issues & Future Improvements

- [ ] Add authentication/authorization
- [ ] Implement job cancellation
- [ ] Add scheduled/cron jobs
- [ ] Real-time updates via WebSocket
- [ ] Job retry mechanism on failure
- [ ] Pagination for large job lists
- [ ] Export jobs to CSV
- [ ] Job logs and history

## 📸 Screenshots
<img width="1893" height="1028" alt="Screenshot 2025-12-18 192048" src="https://github.com/user-attachments/assets/611be39e-67d0-4051-9ff8-71d914015484" />
<img width="1919" height="1078" alt="Screenshot 2025-12-18 192056" src="https://github.com/user-attachments/assets/f5b6b798-72de-4446-b09e-92f67bf08031" />
<img width="1896" height="1071" alt="Screenshot 2025-12-18 192115" src="https://github.com/user-attachments/assets/04b4a948-8a8b-48a4-b932-f51f0ad3b304" />



## 📄 License

MIT

## 👨‍💻 Author

Created as part of Dotix Technologies Full Stack Developer Skill Test

## 🙏 Acknowledgments

- Shadcn/ui for beautiful components
- Next.js team for amazing framework
- Express.js for reliable backend framework
