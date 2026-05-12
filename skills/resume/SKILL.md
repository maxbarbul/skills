---
name: resume
description: User wants to build or improve a resume/CV from scratch or from fragments (files, notes, LinkedIn), and produce a Markdown file for editing or conversion.
---
Goal: Help the user collect, structure, and produce an ATS-friendly and recruiter-ready CV in Markdown. Guides the conversation to fill gaps, applies job-market best practices (metrics, action verbs, keywords), and writes a polished Markdown CV file that can be iterated.

Inputs (what the agent will ask for / accept):
- Personal details: full name, preferred display name, contact (email, phone), location, LinkedIn/GitHub/portfolio URLs.
- Work experience items: company, role/title, start/end dates, location/remote, team size, responsibilities, measurable achievements, tech/tools used, promotion history.
- Education: institution, degree, dates, honours, relevant coursework.
- Skills: hard skills, tools, languages, frameworks, proficiency level.
- Certifications and courses: name, issuer, date, ID/URL.
- Publications, patents, talks, awards, OSS contributions, projects (with URLs and short descriptions).
- Preferences: target roles, industries, seniority, keywords to emphasize, length (1/2 pages), ATS vs recruiter focus.
- Any attached files: past resumes, job descriptions, LinkedIn URLs, portfolio items.

Outputs:
- A recruiter- and ATS-optimized Markdown CV saved to `skills/resume/CV_<username|timestamp>.md` (or a user-specified path).
- A filled `assets/resume_template.md` (if invoked) or a tailored version based on the user's inputs.
- A short checklist of suggested edits (keywords to add, sections to expand, roles to tailor for specific job descriptions).

Conversation / Workflow (step-by-step):
1. Collect basics: name, contact, target role(s), and any files/URLs to import.
2. Import and scan any attached resume/LinkedIn or job description to extract data and keywords.
3. For each employment entry, ask targeted questions to create one strong bullet set: context (what), action (what you did), result (quantified outcome). If user provides sparse input, the agent suggests plausible, conservative defaults and asks for confirmation.
4. Build Education, Certifications, Projects and Skills sections using short structured prompts.
5. Run ATS/keyword pass: highlight missing keywords from target JD(s) and suggest edits.
6. Produce final Markdown CV and save into the workspace; provide a one-paragraph summary and a checklist of next edits.

Decision points & branching logic:
- If the user supplies existing resume(s): parse and propose an initial draft; ask for clarifications on ambiguous or missing dates, metrics, and tech stack items.
- If target job descriptions are provided: perform a keyword alignment pass and propose an alternate tailored version.
- If user prefers recruiter-friendly style vs strict ATS: adjust formatting (one-column, minimal tables, plain text headings) and length recommendations.

Quality criteria / completion checks:
- Each experience entry has at least 2–4 accomplishment bullets and one quantified result when possible.
- Top 6–8 skills are highlighted near the top (summary or skills section) to improve ATS hit rate.
- Use strong action verbs, consistent tense (past for previous roles, present for current), and concise bullets (max 2 lines each).
- No unexplained gaps: the agent asks about gaps longer than 3 months.

Clarifying questions the agent should ask (examples):
- What full name and contact should appear on the CV?
- Which role(s) or industry are you targeting? Any JD(s) to match?
- For each job: What was your job title, team size, reporting line, and top 3 responsibilities?
- Can you give one or two measurable outcomes (%, $ impact, time saved, growth, scale)? If unsure, give conservative estimates and mark them for verification.
- Any promotions, job title changes, or concurrent roles we should represent?
- Which skills/tools should be prioritized for ATS/role matching?

Examples of prompts to invoke this skill:
- "Help me build a resume from scratch for a senior backend engineer role — here's my LinkedIn URL."
- "Import this resume file and convert it to ATS-friendly Markdown, then ask me questions to fill missing metrics."
- "Tailor my CV to this job description: [JD URL] — highlight matching keywords and suggest bullets."

Assets and templates:
- The repository includes `assets/resume_template.md` as the base Markdown template to produce final CV files.

Iteration and finalize:
1. Draft the CV using gathered inputs.
2. Present the draft and list ambiguous items (dates, metrics, role scope) as a short question list.
3. Accept corrections and re-run the pass until all ambiguous items are resolved.
4. Offer optional outputs: one-page condensed version, ATS-focused plain text, and a tailored variant for a specific JD.

Privacy / safety notes:
- Do not invent legal names, credentials, or certifications. When plausible defaults are suggested, clearly flag them as estimates requiring user verification.

Next actions for the agent when the skill is invoked:
- Ask for the user's name and contact details (if not provided).
- Ask for target role(s) and any job descriptions to align to.
- Request any existing resume files or LinkedIn/portfolio URLs to import.

What this skill produces:
- A polished Markdown CV file ready for further editing and conversion.
- A short checklist of follow-ups (verify metrics, add references, tailor for JD).

Related customizations to add later:
- Auto-export to PDF via a preferred Markdown-to-PDF pipeline.
- Role-specific bullet libraries (e.g., SRE, PM, Data Science) to speed drafting.
- Integration with LinkedIn scraper or resume parsers for bulk imports.
