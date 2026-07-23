# CyberMail — Phishing Simulation & Awareness Tool
A small desktop application that recreates a realistic phishing login page to demonstrate, hands-on, how easily these attacks work — and then immediately teaches the user what they missed.This is my **HACKTECH** internship project. 

# Why I built this
Most people know phishing "exists," but knowing about something in theory and actually falling for it in the moment are two very different experiences. I wanted to build something that closes that gap — a safe, local simulation where someone types in their email and password on what looks like a normal login page, and right after submitting, they see exactly which red flags they walked past.
It's built with plain Python and Tkinter, no web hosting, no real backend — everything runs and stays on your own machine.

# What it does
1. Opens a fake login screen for a made-up email service called **CyberMail**, styled to look like a typical webmail sign-in page — logo, tagline, email/password fields, and a "Verify Account" button.
2. Includes a fabricated urgency banner ("Unusual sign-in activity detected") — this is one of the most common psychological tricks used in real phishing emails.
3. Once the user submits the form, their input is logged locally to a CSV file (`submissions.csv`) with a timestamp, purely so the "victim" can later see what they typed.
4. Immediately after, the screen switches to an **awareness page** that reveals it was a simulation, and walks through:
   - The red flags present in the fake page (urgency, generic greeting, unfamiliar sender, credential re-entry via a link, etc.)
   - Practical habits to avoid falling for real phishing attempts (checking sender addresses, hovering over links, enabling MFA, and so on)
5. A "Try Again" button resets the flow so it can be demoed multiple times.

# Tech stack
- **Python 3**
- **Tkinter** — for the GUI (login screen + awareness screen)
- **CSV module** — for lightweight local logging
- **datetime** — for timestamping each submission
No external libraries, no internet connection required, no real data ever leaves your computer.

# Running it locally
```bash
python phishing_simulation.py
```
That's it — no installation steps beyond having Python installed, since Tkinter ships with the standard library.

# Project structure
```
├── phishing_simulation.py   # main application
├── submissions.csv          # auto-generated log of simulated submissions (gitignored)
└── README.md
```

# What I learned building this
This was my first time combining GUI development with a security-awareness concept rather than just a script. Building the state-switching between screens (destroying and rebuilding widgets on the same root window instead of opening new windows) took some trial and error, as did getting the CSV logging to append correctly without overwriting previous entries. It also pushed me to think about phishing not just as "a fake email" but as a set of deliberate psychological triggers — urgency, authority, and familiarity — which is what I tried to encode into the fake CyberMail page itself.

# Disclaimer
This project is strictly for educational purposes. It does not send data anywhere, does not use a real domain, and is not intended to be deployed against anyone without their knowledge or consent. It exists to demonstrate phishing mechanics in a controlled, self-contained environment.

# Possible future additions
- A scoring/reflection screen showing how many red flags the user could identify before being told
- Multiple phishing templates (bank, social media, delivery notification) to compare patterns
- A short quiz at the end to reinforce the awareness points
