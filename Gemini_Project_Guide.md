# Gemini Guide — WhatsApp-Style School Messaging Project

## খুব গুরুত্বপূর্ণ

বর্তমান `whatsapp_style_project_base.html` হলো **শুধু frontend prototype**।

এটা GitHub-এ upload করলে UI/ডিজাইন চলবে, কিন্তু:
- real login হবে না
- mobile OTP যাবে না
- real users থাকবে না
- real-time messaging হবে না
- image online database/storage-এ যাবে না

আর আমি যে Python script দিয়ে HTML file তৈরি করেছি, **সেটা GitHub-এ upload করার দরকার নেই**। Python script শুধু HTML বানানোর জন্য ব্যবহার করা হয়েছিল।

## Gemini-কে কী করতে হবে

এই HTML-টাকে base হিসেবে রেখে project-টাকে complete web messaging application বানাতে হবে।

### Recommended stack

- HTML5
- CSS3
- Vanilla JavaScript
- Supabase Auth
- Supabase PostgreSQL
- Supabase Realtime
- Supabase Storage

### Login

User registration/login fields:
1. Name
2. Gmail/Email
3. Mobile Number

Flow:
Name + Email + Mobile
→ SMS OTP
→ OTP verification
→ Account/profile তৈরি
→ Chat screen

### Chat

দরকার:
- New Chat
- User search
- One-to-one chat
- Real-time text messages
- Timestamp
- Unread count
- Last message preview
- Online/last seen
- Logout

### Image

শুধু image upload থাকবে:
- Profile image
- Chat image
- Image preview
- Supabase Storage upload
- Database-এ image path/URL রাখা

ভিডিও, audio বা video call লাগবে না।

## UI requirement

Supplied WhatsApp screenshot-কে visual reference হিসেবে ব্যবহার করবে।

বিশেষ করে:
- dark theme
- left navigation rail
- chat list
- search bar
- filter chips
- chat rows
- responsive layout

### VERY IMPORTANT POSITION CHANGE

Original WhatsApp layout-এর মতো নয়; এই project-এ:

- **Profile button = উপরের ডানদিকে**
  - যেখানে New Chat button ছিল

- **New Chat (+) button = নিচের বামদিকে**
  - যেখানে Profile avatar ছিল

এই অবস্থান desktop এবং mobile দুটোতেই ঠিক রাখতে হবে।

## Database

Suggested tables:

### profiles
- id
- name
- email
- phone
- avatar_url
- created_at
- last_seen

### chats
- id
- chat_type
- name
- created_at

### chat_members
- chat_id
- user_id
- joined_at

### messages
- id
- chat_id
- sender_id
- message_text
- image_url
- created_at

## Security

- Supabase Row Level Security (RLS) ব্যবহার করবে
- Frontend-এ service-role key রাখবে না
- User যেন অন্য user's private data পরিবর্তন করতে না পারে
- Image upload-এর type/size validation থাকবে

## Code structure

Project-কে পরিষ্কারভাবে ভাগ করো:

- `index.html`
- `style.css`
- `app.js`
- `auth.js`
- `chat.js`
- `supabase.js`
- `README.md`

এছাড়াও Supabase-এর জন্য একটি SQL schema file দাও, যেমন:

- `supabase-schema.sql`

## Gemini instructions

কাজ করার আগে:
1. Existing HTML-এর layout বুঝবে
2. Profile/New Chat position swap নষ্ট করবে না
3. Existing UI অকারণে redesign করবে না
4. Fake/mock backend ব্যবহার করবে না
5. `localStorage`-কে primary database হিসেবে ব্যবহার করবে না
6. Real Supabase integration করবে
7. Realtime subscription ব্যবহার করবে
8. Incomplete placeholder code দেবে না
9. কোন file-এ কোন code বসাতে হবে সেটা পরিষ্কারভাবে বলবে
10. Supabase project setup-এর beginner-friendly step-by-step instructions দেবে

## GitHub

শুধু static UI test করতে:
- HTML/CSS/JS → GitHub Pages-এ চলবে

Real authentication/database/realtime chat চালাতে:
- Supabase project configure করতে হবে
- Supabase URL + anon/publishable key frontend-এ configure করতে হবে
- Authentication এবং Storage setup করতে হবে
- RLS policies চালু করতে হবে

## Final output from Gemini

Gemini যেন শেষে দেয়:
1. Complete project files
2. Complete SQL schema + RLS policies
3. Supabase setup instructions
4. OTP/SMS provider setup instructions
5. GitHub Pages deployment instructions
6. কোন জায়গায় কোন configuration বসাতে হবে
7. Beginner troubleshooting guide

**Goal:** একজন beginner যেন শুধু নির্দেশনা অনুসরণ করে project setup, Supabase connection এবং GitHub deployment করতে পারে।
