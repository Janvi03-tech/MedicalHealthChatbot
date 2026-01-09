
{
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Janvi03-tech/MedicalHealthChatbot/blob/main/Untitled1.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 2,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "4djPvLOt0RKN",
        "outputId": "5d8c405f-2a3a-4e78-d76b-caba62d8758e"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Medical Chatbot (type 'bye' to exit)\n",
            "You: janvi\n",
            "Bot: Sorry, I dont understand. Common symptoms: fever, cough, headache, stomach pain.\n",
            "You: fever\n",
            "Bot: Possible: Dengue. Advice: Rest, drink fluids, paracetamol. Consult doctor if persists >3 days.\n",
            "You: bye\n",
            "Bot: Take care! Consult a real doctor.\n"
          ]
        }
      ],
      "source": [
        "import re\n",
        "import random\n",
        "\n",
        "# Knowledge base: symptoms mapped to possible diseases and advice\n",
        "knowledge_base = {\n",
        "    'fever': {\n",
        "        'diseases': ['Flu', 'Malaria', 'Dengue'],\n",
        "        'advice': 'Rest, drink fluids, paracetamol. Consult doctor if persists >3 days.'\n",
        "    },\n",
        "    'cough': {\n",
        "        'diseases': ['Cold', 'Bronchitis', 'COVID-19'],\n",
        "        'advice': 'Honey with warm water, steam inhalation. See doctor for persistent cough.'\n",
        "    },\n",
        "    'headache': {\n",
        "        'diseases': ['Migraine', 'Tension', 'Dehydration'],\n",
        "        'advice': 'Hydrate, rest in dark room, OTC painkillers. Urgent if severe with vomiting.'\n",
        "    },\n",
        "    'stomach pain': {\n",
        "        'diseases': ['Gastritis', 'Appendicitis', 'Food poisoning'],\n",
        "        'advice': 'Avoid spicy food, antacids. Seek immediate help for sharp pain.'\n",
        "    }\n",
        "}\n",
        "\n",
        "responses = {\n",
        "    'greeting': ['Hello! I am Medical Chatbot. Describe your symptoms.', 'Hi! Tell me your health issue.'],\n",
        "    'no_match': ['Sorry, I dont understand. Common symptoms: fever, cough, headache, stomach pain.',\n",
        "                 'Please rephrase or list specific symptoms. Not a doctor substitute!'],\n",
        "    'bye': ['Take care! Consult a real doctor.', 'Goodbye! Stay healthy.']\n",
        "}\n",
        "\n",
        "def extract_symptoms(user_input):\n",
        "    user_input = user_input.lower()\n",
        "    symptoms = []\n",
        "    for symptom in knowledge_base:\n",
        "        if re.search(r'\\b' + re.escape(symptom) + r'\\b', user_input):\n",
        "            symptoms.append(symptom)\n",
        "    return symptoms\n",
        "\n",
        "def get_response(user_input):\n",
        "    user_input_lower = user_input.lower()\n",
        "\n",
        "    if any(g in user_input_lower for g in ['hi', 'hello', 'hey']):\n",
        "        return random.choice(responses['greeting'])\n",
        "\n",
        "    symptoms = extract_symptoms(user_input)\n",
        "    if symptoms:\n",
        "        response = []\n",
        "        for symptom in symptoms:\n",
        "            kb = knowledge_base[symptom]\n",
        "            disease = random.choice(kb['diseases'])\n",
        "            response.append(f\"Possible: {disease}. Advice: {kb['advice']}\")\n",
        "        return ' | '.join(response)\n",
        "\n",
        "    if 'bye' in user_input_lower or 'quit' in user_input_lower:\n",
        "        return random.choice(responses['bye'])\n",
        "\n",
        "    return random.choice(responses['no_match'])\n",
        "\n",
        "def main():\n",
        "    print(\"Medical Chatbot (type 'bye' to exit)\")\n",
        "    while True:\n",
        "        user_input = input(\"You: \")\n",
        "        if 'bye' in user_input.lower():\n",
        "            print(\"Bot:\", get_response(user_input))\n",
        "            break\n",
        "        response = get_response(user_input)\n",
        "        print(\"Bot:\", response)\n",
        "\n",
        "if __name__ == \"__main__\":\n",
        "    main()\n"
      ]
    }
  ],
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyP3W27jQww0VW37fjkIkyQf",
      "include_colab_link": true
    },
    "kernelspec": {
      "display_name": "Python 3",
      "name": "python3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "nbformat": 4,
  "nbformat_minor": 0
}

