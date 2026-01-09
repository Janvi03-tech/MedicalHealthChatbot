Project Title /n
Medical Health Chatbot for System Analysis

Problem Statement
Inadequate Access to Preliminary Health Guidance in Resource-Limited Settings

People often experience common health issues like fever, cough, or headaches but lack immediate, accessible tools for basic symptom triage. Consulting a doctor for every minor symptom is time-consuming, costly, and impractical—especially in rural areas, during off-hours, or for underserved populations in India (e.g., Maharashtra regions like Airoli).

Challenges:

No simple, always-available system for symptom-based advice.

Overburdened healthcare systems; patients delay care due to uncertainty.

Existing apps require internet/data, complex UIs, or subscriptions.

Project Solution: Build a lightweight, rule-based Medical Health Chatbot for system analysis that:

Interprets user-described symptoms via natural language.

Maps to possible diseases with actionable home advice.

Promotes early doctor consultation disclaimers.

Objective
Develop a rule-based medical chatbot that identifies user-reported symptoms, suggests possible diseases, and provides basic health advice. The system demonstrates core concepts in system analysis, including knowledge representation, pattern matching, and conversational flow, while emphasizing that it is not a substitute for professional medical diagnosis.

Dataset Description
No external dataset is used. The system relies on a static, hand-crafted knowledge base—a Python dictionary mapping 4 common symptoms to possible diseases and advice:

Symptoms covered: fever, cough, headache, stomach pain

Structure: Each symptom links to a list of 2-3 diseases (randomly selected during response) and standardized advice strings

Size: Minimal (4 entries), focused on proof-of-concept rather than scale

Source: Manually curated for demonstration; expandable for real-world use

This approach avoids data privacy issues in medical domains and prioritizes simplicity for system analysis.

Methodology / Approach
Rule-based pattern matching system:

Input Processing: User query is lowercased; regex extracts exact symptom matches from the knowledge base.

Response Generation:

Greetings → Random welcome message.

Symptom match → Random disease from list + advice.

Exit keywords (bye/quit) → Farewell.

No match → Fallback suggestions.

Conversation Loop: Infinite loop until exit, simulating interactive chat.

Key Techniques: Regular expressions for symptom detection, random.choice for variability, dictionary for modular knowledge storage.

This modular design supports easy extension (e.g., adding ML for fuzzy matching).

Tools & Technologies Used
Language: Python 3

Libraries:

Library	Purpose
re	Regex for symptom extraction
random	Disease/advice randomization
Environment: Google Colab (Jupyter notebook)

Version Control: GitHub (linked repo)

No ML frameworks or databases—purely lightweight scripting.

Steps to Run the Project
Open in Google Colab via the badge link.

Run the code cell (execution_count: 2).

Interact in the console:

Type symptoms like "fever" or "cough headache".

Type "bye" to exit.

View output stream for conversation simulation.

Local run: Copy code to Python file, execute python filename.py.

Results / Output
Sample Interaction (from notebook output):

Medical Chatbot (type 'bye' to exit)
You: janvi
Bot: Sorry, I dont understand. Common symptoms: fever, cough, headache, stomach pain.
You: fever
Bot: Possible: Dengue. Advice: Rest, drink fluids, paracetamol. Consult doctor if persists >3 days.
You: bye
Bot: Take care! Consult a real doctor.


Strengths: Quick responses, handles multi-symptoms (e.g., "fever cough" → combined output).
Limitations: Exact-match only, no context/memory, basic scope. Ideal for system analysis demo.

Dataset
Inline knowledge base (copy-paste ready for expansion):

knowledge_base = {
    'fever': {
        'diseases': ['Flu', 'Malaria', 'Dengue'],
        'advice': 'Rest, drink fluids, paracetamol. Consult doctor if persists >3 days.'
    },
    'cough': {
        'diseases': ['Cold', 'Bronchitis', 'COVID-19'],
        'advice': 'Honey with warm water, steam inhalation. See doctor for persistent cough.'
    },
    'headache': {
        'diseases': ['Migraine', 'Tension', 'Dehydration'],
        'advice': 'Hydrate, rest in dark room, OTC painkillers. Urgent if severe with vomiting.'
    },
    'stomach pain': {
        'diseases': ['Gastritis', 'Appendicitis', 'Food poisoning'],
        'advice': 'Avoid spicy food, antacids. Seek immediate help for sharp pain.'
    }
}


