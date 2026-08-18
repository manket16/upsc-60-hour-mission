# UPSC 60-Hour Mission — GitHub Pages + Supabase

## What this version does

- Light pink UPSC dashboard
- LBSNAA hero image
- 22 May 2027 live countdown
- 50-minute focus + 10-minute break
- Every completed 50-minute session = 1 hour
- 60-hour weekly tracker
- Today's tasks and subtasks
- Cloud-synced weekly progress and tasks
- Email/password login
- In-site study ambience
- Break options: Spotify, Talk to Mom, Stretch & Walk

## Setup

### 1. Create a free Supabase project

Go to https://supabase.com and create a free project.

### 2. Create the database

Open:

Supabase Dashboard → SQL Editor → New query

Copy all contents of `supabase_schema.sql` into the editor and click Run.

### 3. Get your Supabase credentials

Open:

Supabase Dashboard → Project Settings → API

Copy:

- Project URL
- Publishable/anon key

The browser app must use the publishable/anon key, NOT a service-role secret.

### 4. Put the credentials into index.html

At the top of the JavaScript in `index.html`, replace:

YOUR_SUPABASE_URL

and

YOUR_SUPABASE_ANON_KEY

with your Supabase Project URL and publishable/anon key.

Do not put a Supabase service-role key in this website.

### 5. Create a GitHub repository

Create a new repository on GitHub, for example:

upsc-60-hour-mission

Upload:

index.html

You can also upload `supabase_schema.sql` and this README, although only `index.html` is required for the website.

### 6. Enable GitHub Pages

GitHub repository:

Settings → Pages

Under "Build and deployment":

Source: Deploy from a branch

Branch: main

Folder: / (root)

Save.

GitHub will give you a website address such as:

https://YOUR-USERNAME.github.io/upsc-60-hour-mission/

### 7. Supabase authentication

In Supabase:

Authentication → Providers → Email

Enable Email.

For easiest setup during testing, you can disable "Confirm email". For a public personal site, keeping email confirmation enabled is safer.

## Important

GitHub Pages only hosts the website.

Supabase stores the synchronized data.

Your browser never receives the Supabase service-role key. The app uses the public publishable/anon key together with Row Level Security policies.

Each account can only access its own weekly progress, tasks, and subtasks.

## What is synchronized

Across laptop and phone:

- weekly completed sessions
- weekly hour count
- today's tasks
- task completion
- subtasks
- subtask completion

The Pomodoro timer itself is intentionally local to the device. The moment a 50-minute session completes, the +1 hour is written to Supabase.

## Free usage

For a single personal tracker, the free tiers of GitHub Pages and Supabase should be more than sufficient for normal use. Check the providers' current free-tier limits before relying on them for long-term use.

## One security rule

Never paste a Supabase `service_role` key into `index.html`.

Only use the browser-safe publishable/anon key with Row Level Security enabled.
