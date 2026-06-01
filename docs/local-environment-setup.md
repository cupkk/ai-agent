# Safe Local Environment Setup

This guide gives contributors a safe way to configure the project
locally without committing API keys, OAuth secrets, user files,
meeting recordings, or calendar data.

## 1. Create a local server environment file

The backend loads `server/.env`, so start from the tracked example
file and keep your real values only on your machine:

```bash
cp server/.env.example server/.env
```

If you are testing the hardened security paths, you can also review
`server/.env.security.example` and copy only the variables you need
into `server/.env`.

## 2. Use placeholder-only values until you need a real integration

For basic local development, these values are enough to boot the app
without exposing external credentials:

```bash
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://localhost:27017/intelligent-work-assistant
DB_NAME=intelligent_work_assistant

JWT_SECRET=replace-with-a-locally-generated-random-string
JWT_EXPIRE=7d

AI_PROVIDER=openai
OPENAI_API_KEY=your-openai-api-key
OPENAI_ORGANIZATION=your-openai-organization
OPENAI_MODEL=gpt-3.5-turbo
OPENAI_API_URL=https://api.openai.com

MAX_FILE_SIZE=10485760
UPLOAD_PATH=./uploads
LOG_LEVEL=info
LOG_FILE=logs/app.log
```

Generate a local JWT secret with Node.js:

```bash
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

## 3. Enable integrations one at a time

Only add the integration values you are actively testing. Leave the
rest as placeholders.

### WeChat

```bash
WECHAT_APPID=your-wechat-appid
WECHAT_APPSECRET=your-wechat-appsecret
WECHAT_TOKEN=your-wechat-token
WECHAT_ENCODING_AES_KEY=your-wechat-encoding-aes-key
```

### Google Calendar

```bash
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
GOOGLE_REDIRECT_URI=http://localhost:5000/auth/google/callback
```

### Microsoft Graph

```bash
MICROSOFT_CLIENT_ID=your-microsoft-client-id
MICROSOFT_CLIENT_SECRET=your-microsoft-client-secret
MICROSOFT_TENANT_ID=your-microsoft-tenant-id
```

### Optional mail and Redis services

```bash
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@example.com
SMTP_PASS=your-app-password

REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=
```

## 4. Keep local data out of version control

Do not commit any of the following:

- populated `server/.env` files
- real API keys, OAuth secrets, access tokens, or webhook secrets
- exported calendar data
- uploaded user documents
- meeting recordings or transcripts captured from real users

The repository already ignores common local env files, uploads, temp
files, logs, and build output through `.gitignore`.

## 5. Use synthetic test data for demos and debugging

When validating workflows locally:

- use fake meeting notes or generated sample recordings instead of real
  customer data
- use test calendar accounts instead of personal or company calendars
- replace production callback URLs with localhost or test domains
- scrub screenshots and logs before sharing them in issues or pull requests

## 6. Quick validation checklist

Before opening a pull request:

1. Confirm `git status` does not include `server/.env`, uploads,
   recordings, or exported data.
2. Confirm all secrets still use placeholders in any tracked example files.
3. Note in the PR description which integrations you actually tested
   locally.
