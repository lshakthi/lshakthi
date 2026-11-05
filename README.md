# Hi, I'm Lahari Shakthi Arun 👋

Full-Stack AI-Enabled Engineer & UI/UX Designer — I design the experience first, then build it end to end.

---

## About me

- 👋 Hi, I'm @lshakthi, my name is Lahari Shakthi Arun, and I'm a senior at Arizona State University, Tempe, AZ 🇺🇸
- 🎓 B.S. Graphic Information Technology (UI/UX), expected Dec 2026
- 💼 Full Stack Product Designer @ Amazon AI Cloud Innovation Center (AWS), Apr 2024 – Present
- 🤖 I'm interested in Generative AI and its practical applications — building AI products people actually use
- 🌱 I began as a UI/UX designer and grew into full-stack development, owning products end to end
- ☁️ AWS AI Certified Practitioner (exp. Oct 2027)
- 🤝 I'm looking to collaborate on AI projects and get feedback on work in progress
- 📫 How to reach me — the best way is to email me at lsarun@asu.edu, I'll be sure to respond very shortly

---

## Tech Stack

- 💻 **Languages:** Python, TypeScript, JavaScript, HTML, CSS
- 🤖 **AI / ML:** AWS Bedrock, Bedrock RAG / Knowledge Bases, AgentCore, multi-agent systems, LLM integration
- 🌐 **Frontend:** React, Next.js, WebSocket streaming APIs, REST APIs
- ☁️ **Cloud & Backend:** AWS serverless (Lambda, API Gateway, DynamoDB, S3, Cognito, CDK, Amplify), S3 Vector
- 🛠️ **Dev Tools:** Kiro, Claude Code, Figma MCP, VS Code, Git, CI/CD
- 🎨 **Design:** Figma, Figma Make, Adobe Photoshop, Adobe Illustrator, Adobe InDesign, wireframing, prototyping, task flows, usability testing
- 🗄️ **Databases:** DynamoDB, S3 Vector, session and metadata stores

---

## Featured Projects

### Dev Projects

- 💬 **HOPE Chatbot — WestCare Foundation** — Trauma-informed, bilingual English/Spanish AI chatbot offering 24/7 access to behavioral health, housing, substance use recovery, and domestic violence support, with safety-escalation routing to crisis lines. Featured on WestCare.com. Built with Bedrock, Lambda, DynamoDB, S3, API Gateway. — [repo](https://github.com/ASUCICREPO/crisis-help-chatbot)
  - **What it does:** HOPE (Helpful Online Positive Engagement), a serverless AI chatbot that lowers barriers for users reaching out in vulnerable moments, giving them 24/7 access to behavioral health, housing, substance use recovery, and domestic violence support. WestCare supports people across Arizona and a 17-state footprint, and many who most need services never make the call because of stigma, safety concerns, language barriers, transportation, or because the crisis happens at 2 a.m.
  - **What I did:** As UI/UX Designer at the Amazon AI Cloud Innovation Center, I was responsible for the questionnaire design and the full conversation flow, in a one-day chatbot-a-thon. I designed the intake questionnaire and end-to-end chatbot UI flow using a strengths-based, trauma-informed approach, shipped bilingual English and Spanish flows, designed the safety-escalation path (how the interface detects risk language and surfaces crisis hotlines and resources at the right moment), mapped the three core experiences (Client Chat, Safety Escalation and Routing, and Knowledge/Content Management), and designed for location-aware service recommendations. I reused existing CIC chatbot frameworks to hit the one-day deadline, worked directly with the Cloud Developer so the design translated onto the serverless AWS stack, and documented handoff friction, recommending Figma Make to compress the design-to-development loop.
  - **Architecture:** Fully serverless on AWS, in one CDK stack, pay-per-request. User flow: API Gateway → Lambda → Bedrock Knowledge Base (vector retrieval against OpenSearch, answers generated with Nova 2 Lite, locked to WestCare's own content). Location flow: a geo-search Lambda takes the user's coordinates and finds the nearest WestCare facilities, starting with a tight radius and widening until it hits matches, then sorting by actual distance, and injects them into the prompt. Content ingest: WestCare uploads documents into S3 and a web crawler reads their site, then Bedrock Data Automation chunks it and Titan embeds it into the vector store.
  - **Safety:** The system prompt enforces strict grounding to the Knowledge Base plus geo-search results only, addresses come from a verified service locations table, and Bedrock Guardrails sit on top as a safety net. Encryption at rest and in transit, IAM least privilege, session data stored only for conversation context with configurable retention, and Comprehend Medical for PHI detection in compliance logging.
  - **Result:** The prototype shipped in a single day and is featured on WestCare.com, with WestCare planning to adapt and deploy it across all of their web properties. WestCare's VP of Software Development, Diane Ludens, described the collaboration as seamless.
- 🏫 **School Board Chatbot (The Beam)** — Serverless RAG platform letting parents and community members query school board meeting transcripts in natural language. Built with Bedrock Knowledge Base, S3 Vector, Lambda, API Gateway, Next.js, Cognito, Transcribe, CDK. — [repo](https://github.com/ASUCICREPO/schoolboard-chatbot)
  - **What it does:** A serverless AI-powered platform for school districts to upload, manage, and query board meeting transcripts — a chatbot interface for querying transcripts, an admin dashboard for managing transcripts and districts, a backend pipeline for transcript ingestion and processing, and query logging for analytics.
  - **What I did:** Cloned the repo into Kiro IDE, wrote the scope document, asked Kiro for a cost-effective backend solution, collaborated with a teammate, took part in the architecture diagram, and learned how to write technical documentation.
  - **Architecture:** S3 stores transcripts and uploaded media · DynamoDB stores metadata and query logs (`schoolbot-transcripts`, `schoolbot-districts`, `schoolbot-query-logs`) · Lambda handles APIs and processing · API Gateway exposes backend endpoints · Bedrock Knowledge Base enables RAG-based chatbot · Cognito handles admin authentication · Next.js frontend for chatbot and admin dashboard.
  - **Ingestion:** Manual transcript ingestion (text, audio, video) instead of the YouTube API for reliability, with auto-transcription via AWS Transcribe and a rolling window of max 3 transcripts per district to control cost and keep answers relevant.
  - **Data flow:** Admin → API Gateway → Lambda (admin-api) → S3 → DynamoDB → Bedrock KB · User → Chatbot API → Bedrock KB → Response.
- 🎗️ **Empathetic Chatbot — BreastCancer.org** — Trauma-informed, WCAG-accessible RAG chatbot helping breast cancer patients understand their diagnosis in a simple, personalized way. Built with Bedrock, Lambda, CDK, S3, Amplify, React. — [repo](https://github.com/ASUCICREPO/BCO)
  - **What it does:** Breastcancer.org had deep, trusted educational content but no way to deliver it conversationally, so patients facing a diagnosis were left parsing static articles at the most stressful moment of their lives. This chatbot delivers emotionally safe, accessible AI support end to end, for two distinct personas, newly diagnosed and metastatic patients.
  - **What I did:** Conducted user research into patients' emotional needs, then designed a trauma-informed conversation UX: careful disclosure pacing, non-alarming language, clear exits, and no false reassurance. Built the interface to WCAG accessibility standards, moved through digital asset gathering, wireframes, low-fi prototypes, and high-fi prototypes, including a color palette tuned for a sensitive clinical context that the client approved directly. Implemented the React front end on Amplify, with secure login and session timeout so health profile data stayed protected.
  - **Architecture:** A serverless RAG pipeline on Amazon Bedrock, with Lambda orchestrating retrieval and response workflows and S3 backing the content store, so answers stayed anchored to Breastcancer.org's own vetted content rather than open-ended model output. Infrastructure defined in AWS CDK and CI/CD wired up through Amplify, making the whole stack reproducible.
  - **Result:** Shipped a working proof of concept that Breastcancer.org's VP of Technology publicly praised as meeting their community's needs, with the design choices called out specifically. The organization is now expanding the approach into additional use cases, and the build was open-sourced as a reusable blueprint for other healthcare nonprofits, with multilingual support and knowledge base integration mapped as next steps.

### UI/UX Projects

- 🔍 **ASU Career Services Job Search Chatbot** — Job search chatbot with a clearer flow from first question to relevant results. 4 iterative high-fidelity Figma prototypes, with interactive models and UI specs refined through 3 feedback cycles with product, development, and marketing stakeholders.
- 🌐 **Kelvyn Park Multilingual Chatbot** — AI-powered English/Spanish chatbot serving internal staff and external parent-facing portals, solving communication barriers for 60%+ of non-English-speaking families. Designed low- and high-fidelity wireframes.
- 🎗️ **BreastCancer.org Chatbot (UI/UX)** — Wireframed and prototyped the personalized chatbot interface for breast cancer patients, defining user task flows, interactive models, and UI specifications with stage-specific content personalization, a soft red and white palette, and accessible typography.
- ☕ **Dutch Bros Site Redesign** — Academic redesign (GIT 340) based on usability research, personas from 16 users, heuristic evaluations, and usability testing planning.

---

## Connect

- 🔗 LinkedIn: https://www.linkedin.com/in/shakthiarun22/
- 🌐 Portfolio: https://shakthiarun.me/
- 📧 Email: lsarun@asu.edu
- 💻 GitHub: github.com/lshakthi

