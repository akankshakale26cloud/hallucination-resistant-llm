**TruthNet-Lite**

A Hallucination-Resistant LLM Inference Layer with Retrieval-Augmented Generation (RAG)

**Project Overview**

TruthNet-Lite is a hands-on project focused on building a hallucination-aware LLM query system using Retrieval-Augmented Generation (RAG). The system fetches relevant context from a vector database before generating answers, verifies output quality, and detects hallucinations using entailment checks.

**Project Summary**

This 10-day hands-on project walks through building a LLM query system from scratch. Using Qdrant for vector search and SentenceTransformers for embeddings, the system retrieves factual context before sending prompts to an LLM. It verifies claims using DeBERTa-based entailment classification, scores hallucination likelihood, and recommends fallback responses when confidence is low.

The notebook demo compares RAG vs Non-RAG performance over 25 questions, analyzing correctness, hallucination rate, and the number of “I don’t know” responses. RAG shows improved accuracy and fewer hallucinations, demonstrating the value of retrieval-based prompting.

**Core Features**

\- Context Retrieval using SentenceTransformers + Qdrant

\- Prompt Generation with constraints to reduce hallucination

\- LLM Inference via OpenAI GPT / local model

\- Entailment Verification with DeBERTa

\- Hallucination Scoring

\- Fallback Logic to suggest rephrasing when uncertain

\- Source Tagging for traceability

\- Jupyter Notebook demo with evaluation metrics

**Tech Stack**

**Component** **Tool**

Embeddings SentenceTransformers (all-MiniLM-L6-v2)

Vector DB Qdrant via Docker

LLM API OpenAI GPT (used as env variable)

Entailment Model DeBERTa via HuggingFace Transformers

Memory/Fallback JSON log

Dashboard (Optional) Streamlit

Language Python

**Folder Structure**

truthnet-lite/  
├── api/ # LLM interface & prompt builder  
├── retrieval/ # Vector DB operations  
├── verifier/ # NLI entailment check  
├── scoring/ # Hallucination scoring logic  
├── fallback/ # Fallback messaging  
├── tracing/ # Source tagging  
├── notebook/ # Demo + Evaluation notebook  
├── config/ # Config files  
└── README.md # Project documentation

**Install Dependencies**

pip install -r requirements.txt

**Start Qdrant**

docker run -p 6333:6333 qdrant/qdrant

**Insert Sample Docs**

for row in tqdm(movie\_dialogues, desc="Inserting documents"):

insert\_doc(row\["doc\_id"\], row\["text"\], {"source": row\["source"\]})

**Run Notebook Demo**

jupyter notebook notebook/main.ipynb

**Sample Output**

'question\_14': {'question': 'What are the names of the six Infinity Stones shown on the holo-board?',

'answer': 'The names of the six Infinity Stones shown on the holo-board are MIND, SPACE, TIME, POWER, REALITY, and SOUL.',

'score': {'supported': 0, 'contradicted': 0, 'hallucination\_score': 0.0},

'trace': {'answer': 'The names of the six Infinity Stones shown on the holo-board are MIND, SPACE, TIME, POWER, REALITY, and SOUL.',

'sources': \[('INT. AVENGERS COMPOUND, LIVING AREA, DAY 1 - DAY (MOCO)',

'On a HOLO-BOARD: "MIND, SPACE, TIME, POWER, REALITY, SOUL." Above each word hovers...ITS ARTIFACT: LOKI\\'S SCEPTER, THE TESSERACT, THE EYE OF AGAMOTTO, THE ORB, THE AETHER CONTAINER, AND A QUESTION MARK.51 52STEVE Okay. Now that we\\'ve got how, we\\'re going to need where and when. NEBULA, TONY, RHODEY, SCOTT, SMART HULK, ROCKET, NATASHA, and CLINT look on. STEVE(CONT\\'D) Most folks here have encountered at least one of the six Infinity Stones- TONY I think you mean nearly been killed by one of the six Infinity Stones. SCOTT LANG I haven\\'t. (off their looks) Just...saying. SMART HULK Regardless, we\\'ve only got enough Pym Particles for one round trip, each. And the Stones have been in a lot of places throughout history. TONY Our history. Not all of them are going to be a fun drop-in. CLINT BARTON Which means we\\'ve got to pick our targets. STEVE Exactly. (he taps "REALITY") Let\\'s start with the Aether. Thor, what do we know? Everyone looks toward...THOR, slumped over. NATASHA Is he asleep? RHODEY I\\'m pretty sure he\\'s dead. DISSOLVE TO: THOR sulks, looking at the Aether Container Holo: "REALITY" Locations are listed: "SVARTALFHEIM, KNOWHERE, LONDON."52 (MORE)53THOR The Aether\\'s not a stone, it\\'s more of an angry sludge. My grandfather hid it from Dark Elves in a rock between dimensions that can only be accessed every 5000 years. HIS ROBOTIC EYE drifts off in the wrong direction. Thor bangs his head, resetting his eye. THOR(CONT\\'D) Or...by Jane. She stuck her hand in a rock. Then the Aether stuck itself inside her. Then I took her to Asgard. We were dating... (depressed) We\\'re not anymore. Everyone stares. DISSOLVE TO:')\],

'model\_version': 'gpt-3.5-turbo',

'verified': True},

'fallback': '✅ Looks good.'}

**Evaluation Summary**

*   Compared RAG vs Non-RAG performance across 25 questions
*   RAG answered 17 correctly, vs 15 for Non-RAG
*   RAG reduced “I don’t know” answers from 17 to 9
*   Both hallucinated 8 times, but RAG’s mistakes were more plausible (paraphrased)

**Learning Goals & Reflections**

This project helped me:

*   Gain hands-on experience with retrieval-based prompting using vector search
*   Understand and apply entailment models to verify LLM outputs
*   Build a practical fallback mechanism to handle low-confidence answers
*   See firsthand how RAG improves output quality compared to naive LLM use
*   Learn modular code design and multi-component LLM systems

**Contact**

Thanks for checking out this project!  
Feel free to reach out if you'd like a walkthrough or have feedback.

**Akanksha**

[(25) Akanksha Kale | LinkedIn](https://www.linkedin.com/in/akankshakale26/) | akankshakale2025@gmail.com