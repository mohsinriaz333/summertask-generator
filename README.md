# Summer Task Generator

An AI-powered web application that lets schools automatically generate summer vacation
assignments for different classes and subjects — built entirely on free-tier tools, with
no billing account required.

## Features

- AI-generated questions: MCQs, True/False, Fill-in-the-blank, Theory (short/medium/long),
  Math (with step-by-step solutions), Mind Maps
- Urdu language support: Word Meaning, Synonym/Antonym, Sentence Making, Tenses, Urdu
  Grammar, Translation, and Gender/Number grammar tables — with correct right-to-left
  script rendering in exported PDFs
- Generate from a typed topic, or from an uploaded chapter/notes file (PDF, DOCX, TXT),
  with page-range and chapter-focus targeting
- Mixed question types with independent counts in a single task
- Multi-Subject / Multi-Topic Booklet mode
- Per-question Edit and Regenerate controls
- Multi-school, multi-teacher accounts with admin roles and a school join-code system
- Task History, Question Bank (save & reuse questions), CSV export
- Public shareable links — students/parents can view/download a task without logging in
- Branded PDF and Word (.docx) export, with configurable margins, 1-sided/2-sided
  (duplex) binding margins, margin guide lines, and a school-selectable brand color
- Admin dashboard with usage statistics and a daily AI-generation quota per school
- Structural validation of AI-generated content (rejects broken/duplicate questions)

## Tech Stack

| Layer | Tool |
|---|---|
| App framework | [Streamlit](https://streamlit.io) (Python) |
| Hosting | [Streamlit Community Cloud](https://share.streamlit.io) |
| Database & Auth | [Supabase](https://supabase.com) |
| AI generation | [Google Gemini API](https://aistudio.google.com) |
| PDF generation | fpdf2 |
| Word generation | python-docx |
| Urdu/RTL support | arabic-reshaper, python-bidi |
| Mind maps | streamlit-markmap |
| Navigation | streamlit-option-menu |

## Setup (for a fresh deployment)

1. **Get a free Gemini API key** at [aistudio.google.com](https://aistudio.google.com) →
   "Get API key" → "Create API key in new project"
2. **Create a Supabase project** at [supabase.com](https://supabase.com), then run the
   full contents of `schema.sql` (in this repo) in its SQL Editor — this sets up every
   table in one go
3. **Deploy on Streamlit Community Cloud**: connect this GitHub repo, branch `main`,
   main file `app.py`
4. **Add secrets** in the app's Settings → Secrets:

```toml
GEMINI_API_KEY = "your_gemini_key"
SUPABASE_URL = "your_supabase_project_url"
SUPABASE_KEY = "your_supabase_anon_key"
SUPABASE_SERVICE_KEY = "your_supabase_service_role_key"
APP_URL = "https://your-app-name.streamlit.app"
```

5. Confirm `fonts/NotoSansArabic.ttf` is present in the repo (required for Urdu PDF
   rendering) and `.streamlit/config.toml` is present (app theme)

## Repository Structure
