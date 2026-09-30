# Sealdah Train Service AI Bot - Premium Full UI

This package contains the complete passenger-facing premium web interface.

## Included
- Premium railway dashboard
- Login / Sign-up
- Passenger profile
- Passenger search
- Messenger-style private chat UI
- Sealdah AI Bot chat
- Train search with station autocomplete
- Train details
- PNR status screen
- Timetable
- Live route map
- Railway alerts
- Responsive mobile bottom navigation
- Supplied Sealdah logo and station data

## Important
The current user accounts and chat are local demo mode using browser localStorage.
This means the UI works immediately, but two different phones do NOT yet share the
same accounts/messages.

For real multi-device chat, connect the UI to a shared backend/database.
Recommended production architecture:

Frontend (this app)
        |
        +--> /api/auth/signup
        +--> /api/auth/login
        +--> /api/users/search?q=
        +--> /api/chats/:username/messages
        +--> WebSocket / Socket.IO for real-time messages
        |
   PostgreSQL / Supabase / Firebase

The existing Render URL is kept as the API base in index.html. Because the exact
API routes of that service were not supplied, this package does not invent or call
undocumented endpoints.

## Deployment
Upload index.html and logo.png to your static hosting.

## Next backend endpoints
When you are ready, wire these routes to the existing Node/Render service:
POST /api/auth/signup
POST /api/auth/login
GET  /api/users/search?q=
GET  /api/users/:username
GET  /api/chats/:username/messages
POST /api/chats/:username/messages
GET  /api/trains/search?from=&to=
GET  /api/pnr/:pnr

For production, passwords must be hashed server-side and authentication should use
secure sessions/JWT. Do not store real passwords in localStorage.
