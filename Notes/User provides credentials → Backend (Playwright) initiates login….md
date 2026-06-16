# User provides credentials → Backend (Playwright) initiates login…

User provides credentials → Backend (Playwright) initiates login →
LMS sends 2FA code to user → User inputs 2FA on your UI →
Playwright continues login using entered 2FA →
Backend securely stores session cookies/token →
Backend periodically renews session as needed.