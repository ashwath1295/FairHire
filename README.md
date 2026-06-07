# FairHire Audit

FairHire Audit is a hackathon-ready Streamlit demo for testing consistency and
potential bias in AI resume screening. It sends the same resume through a
scorer with six different candidate identities, then compares scores, flags
meaningful differences, visualizes the results, and exports an audit CSV.

The app supports Google's Gemini API and automatically uses a deterministic
mock mode when no API key is configured, so the full demo always works.

## Run locally

1. Create and activate a Python virtual environment:

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Optional: configure Gemini by copying `.env.example` to `.env` and adding
   your Google AI Studio API key:

   ```env
   GOOGLE_API_KEY=your_api_key_here
   GEMINI_MODEL=gemini-2.0-flash
   ```

4. Start the app:

   ```bash
   streamlit run app.py
   ```

Without `GOOGLE_API_KEY`, the app starts in mock demo mode and intentionally
simulates identity-based score variance to demonstrate the audit workflow.

## Deploy on Streamlit Community Cloud

1. Push these files to a GitHub repository.
2. Sign in to [Streamlit Community Cloud](https://share.streamlit.io/).
3. Create an app, select the repository, and set the entry point to `app.py`.
4. In the app's **Settings > Secrets**, add:

   ```toml
   GOOGLE_API_KEY = "your_api_key_here"
   GEMINI_MODEL = "gemini-2.0-flash"
   ```

5. Deploy. You may omit the secrets to run the public demo in mock mode.

## Hackathon pitch

AI hiring tools can appear objective while still reacting to demographic
signals and proxies. FairHire Audit turns that hidden risk into a visible,
repeatable test: one resume, multiple identities, side-by-side scores. It gives
teams a fast way to demonstrate bias testing, enforce a human review gate, and
introduce practical safeguards before an AI screener reaches production.

## Responsible use

This project is an educational audit demo. It is not a validated hiring tool
and must not be used as the sole basis for employment decisions.
