# ResumeMatch

Live app: https://resumematch.org

An AI-powered resume optimization web app that analyzes resumes against job descriptions, identifies ATS keyword gaps, and generates tailored, section-by-section improvement suggestions — with resume templates, cover letter generation, PDF export, and job board integrations.

## What it does

Upload a resume (PDF) and paste in a target job description

Gap analysis — the app compares the resume against the job description and identifies missing keywords, skills, and ATS-relevant phrasing

Tailored suggestions — generates specific bullet/summary/skills rewrites (one per work experience, plus summary and skills) that the user reviews and approves individually before anything is applied

Template selection — pick from multiple resume templates and preview live

Export — download a polished, ATS-friendly PDF

Cover letter generation — generate a tailored cover letter for the same job description

Job board integration — quick-search links to Indeed, LinkedIn, Glassdoor, and ZipRecruiter pre-filled with the target role and location

## How it was built

The entire app is a single self-contained HTML/CSS/JavaScript file, with AI reasoning offloaded to the Claude API through a serverless proxy so the API key never touches the client.

Frontend: Vanilla HTML, CSS, and JavaScript (no framework) for a lightweight, dependency-light client

AI/tailoring engine: Claude API (claude-sonnet-4) — used for resume parsing, job description gap analysis, generating tailored suggestions, and drafting cover letters

PDF parsing: PDF.js for client-side text extraction, with a fallback to Claude's native PDF reading when a PDF's embedded fonts cause corrupted text extraction (a font-ligature edge case some PDF exporters produce)

PDF export: html2pdf.js to render the finished resume/cover letter to a downloadable PDF

Fonts/icons: Google Fonts (DM Sans, DM Serif Display) and Tabler Icons

Backend: A minimal serverless function (/api/claude) that holds the Anthropic API key server-side and proxies requests from the client
Hosting/deployment: Vercel, with a custom domain (resumematch.org)

# Tools

Frontend	HTML, CSS, JavaScript

AI	Claude API (Anthropic)

PDF handling	PDF.js, html2pdf.js

Hosting	Vercel

Backend	Vercel serverless function (Node.js)

# Status

Live and free to use. Currently gathering user feedback before adding a paid tier.

Built by Ritesh Penumatsa — Statistics & Data Science student at UT Austin.
