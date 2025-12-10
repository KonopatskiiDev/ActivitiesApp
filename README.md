Activities App – Full-Stack Demo Application

Activities App is a full-stack learning project built with ASP.NET Core Web API, Entity Framework Core, PostgreSQL, SignalR, Vite + React, and MobX.
The application allows users to register, log in, create activities, join events, upload photos, and participate in real-time comments using WebSockets.

This project is deployed on Railway with separate services for the backend (API) and frontend (client).

# Live Demo

Frontend:
https://vigilant-caring-production.up.railway.app/

Backend API:
https://activitiesapp-production-3389.up.railway.app/api

⚠ If you see login issues in Chrome Incognito — see the “Known Browser Issues” section below.

## Features
Authentication \& Authorization

User registration and login

ASP.NET Identity

Cookie-based authentication

Protected routes

Role-based authorization logic

Activities Management

Create, edit activities

Join / leave events

Host permissions via custom authorization handler

User Profiles

Uploading profile images via Cloudinary

Following other users

Displaying activity history

Real-Time Comments (SignalR)

WebSocket connection via /comments hub

Live chat inside each activity

Automatic message broadcasting

UI/UX

Modern React SPA built with:

Vite

TypeScript

MobX state management

Semantic UI + custom styling

## Tech Stack
Backend

ASP.NET Core 8

Entity Framework Core

PostgreSQL

SignalR

Cloudinary SDK

Resend email service

Railway deployment

Frontend

Vite

React + TypeScript

MobX

Axios

React Router v6

## Deployment Setup
Backend

Hosted on Railway as a Web Service

Environment:

DATABASE\_URL

Cloudinary credentials

Resend API token

Automatic EF migrations on startup

CORS configured for both frontend and backend Railway domains

WebSockets enabled (SignalR)

Frontend

Hosted separately on Railway

Build command: npm install \&\& npm run build

Root directory: /client

Environment variables:

VITE\_API\_URL=https://activitiesapp-production-3389.up.railway.app/api
VITE\_COMMENTS\_URL=wss://activitiesapp-production-3389.up.railway.app/comments

### Limitations
The application is not optimized for mobile devices (mobile layout is not supported).

### Known Browser Issues

Because the application uses cookie-based authentication with:

options.Cookie.SameSite = SameSiteMode.None;
options.Cookie.SecurePolicy = CookieSecurePolicy.Always;

…and because the frontend and backend are served on different subdomains, some browsers apply strict 3rd-party cookie rules.

### Chrome Incognito Mode

Chrome Incognito blocks third-party cookies, even with SameSite=None.

This may result in:

Login succeeding with 200 OK,
but session cookie not being stored

Subsequent call to /account/user-info returning 204 No Content

Redirect back to the login page

### Works reliably in:

Chrome (normal mode)

Firefox (normal + private)

Edge (normal mode)

Safari (normal mode)

This is a known limitation of cookie-based auth when backend and frontend are on separate domains.

### For production, the recommended industry solution is to run frontend and backend under the same domain using a reverse proxy (Nginx, YARP, etc.).
But this is perfectly acceptable for a portfolio/demo project.

### Local Development
Backend
cd API
dotnet watch run

Frontend
cd client
npm install
npm run dev

#### Contact
If you have any questions or suggestions — feel free to reach out!


