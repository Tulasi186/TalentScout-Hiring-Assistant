# TalentScout Hiring Assistant

## Project Overview

TalentScout Hiring Assistant is an intelligent chatbot designed to assist in the initial screening of candidates for technical positions. This application uses the Llama 3 model via the Groq API to create a conversational interface that collects essential candidate information and generates relevant technical questions based on the candidate's declared tech stack.

The chatbot follows a structured conversation flow:
1. Greeting and introduction
2. Collection of candidate information (name, contact, experience, etc.)
3. Tech stack assessment
4. Technical question generation based on the declared tech stack
5. Conversation closure

## Installation Instructions

### Prerequisites
- Python 
- Streamlit
- Groq API key

### Setup

1. Clone the repository
```bash
git clone https://github.com/yourusername/talentscout-hiring-assistant.git
cd talentscout-hiring-assistant
```

2. Install required packages
```bash
pip install -r requirements.txt
```

3. Create a `.streamlit/secrets.toml` file with your Groq API key
```toml
GROQ_API_KEY = "your-groq-api-key-here"
```

4. Run the application
```bash
streamlit run app.py
```

## Usage Guide

1. The chatbot will automatically greet the candidate when the application loads.
2. Respond to the chatbot's questions to provide your information.
3. When asked about your tech stack, provide details about your programming languages, frameworks, databases, and tools.
4. The chatbot will generate technical questions based on your tech stack.
5. Answer the technical questions to demonstrate your knowledge.
6. To end the conversation, use keywords like "bye", "exit", "quit", etc.

## Technical Details

### Libraries and Technologies
- **Streamlit**: Frontend UI framework
- **Groq API**: API for accessing the Llama 3 language model
- **Llama3-8b-8192**: Large language model used for generating responses
- **Python**: Core programming language
- **Session State**: For maintaining conversation context

### Architecture
The application follows a simple client-server architecture:
1. **Client**: Streamlit web interface
2. **Server**: Python backend handling API calls and conversation logic
3. **External API**: Groq API for language model access

### Key Components
- **get_completion()**: Handles API calls to Groq
- **create_system_prompt()**: Dynamically creates system prompts based on conversation stage
- **update_candidate_info()**: Extracts and updates candidate information
- **determine_stage()**: Manages conversation flow based on collected information
- **check_exit_intent()**: Detects user intent to end the conversation

## Prompt Design

The application uses dynamic system prompts that adapt based on the current conversation stage:

1. **Base Prompt**: Contains core instructions for the chatbot's behavior and information collection goals.
2. **Stage-Specific Prompts**: Additional instructions based on the current stage (greeting, information collection, tech questions, etc.).
3. **Context Enhancement**: Includes previously collected information to maintain context.
4. **Extraction Prompts**: Structured prompts for extracting specific information from user responses.

This approach ensures that the language model receives clear guidance on what information to collect and how to respond at each stage of the conversation.

## Challenges & Solutions

### Challenges
1. **Context Management**: Maintaining conversation context across multiple exchanges.
   - **Solution**: Used session state to store conversation history and candidate information.

2. **Information Extraction**: Reliably extracting structured information from free-form text responses.
   - **Solution**: Created specialized extraction prompts and used regex to parse JSON responses.

3. **Conversation Flow**: Ensuring a natural progression through different stages of the conversation.
   - **Solution**: Implemented a stage-based system that dynamically adjusts prompts based on collected information.

4. **API Response Handling**: Dealing with varying API response formats and potential errors.
   - **Solution**: Added comprehensive error handling and response parsing logic.

## Future Enhancements

1. **Sentiment Analysis**: Analyze candidate responses for emotional cues.
2. **Multi-lingual Support**: Add support for multiple languages.
3. **Data Persistence**: Implement database storage for candidate information.
4. **UI Enhancements**: Add custom styling and interactive elements.
5. **Response Optimization**: Improve response times and handling of edge cases.
6. **Integration**: Connect with ATS (Applicant Tracking Systems) for seamless recruitment workflows.


