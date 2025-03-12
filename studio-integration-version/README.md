```markdown
# Project Setup Guide

## Prerequisites

Before you begin, make sure you have the following installed and set up:

- **Python 3.11+**
- **OpenAI API key**: You will need an API key from OpenAI to use their models.
- **Supabase account and project**: You will need a Supabase account and project for database and authentication management.

## Setup Instructions

### 1. Create and Activate a Virtual Environment

Create a Python virtual environment to isolate your project dependencies.

#### On Windows:
```bash
python -m venv venv
venv\Scripts\activate
```

#### On macOS/Linux:
```bash
python -m venv venv
source venv/bin/activate
```

### 2. Install Dependencies

Install the required dependencies listed in the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### 3. Set Up Environment Variables

Copy the `.env.example` file to `.env` and fill in your API keys and credentials.

```bash
cp .env.example .env
```

Edit the `.env` file and configure the following environment variables:

- **OPENAI_API_KEY**: Your OpenAI API key.
- **MODEL_CHOICE**: The OpenAI model to use (defaults to `gpt-4o-mini`).
- **DATABASE_URL**: Your Supabase PostgreSQL connection string.
- **SUPABASE_URL**: Your Supabase project URL.
- **SUPABASE_KEY**: Your Supabase service role key.

### 4. Run the Application

Once the environment is set up, run the application using Streamlit:

```bash
streamlit run iterations/v3-streamlit-supabase-mem0.py
```

## Supabase Setup

Follow these steps to configure Supabase with your project:

1. **Create a Supabase account and project** at [supabase.com](https://supabase.com).
2. **Get your Database URL** from:  
   Project Settings > Database.
3. **Get your API keys** from:  
   Project Settings > API.
4. **Enable Email Auth** in:  
   Authentication > Providers > Email.

## How It Works

The application uses the following components:

- **Mem0**: For memory management and retrieval.
- **OpenAI**: For generating AI responses.
- **Supabase**: For authentication and vector storage.
- **Streamlit**: For the web interface.

### Application Flow:
1. A user sends a message.
2. The system retrieves relevant memories based on the query.
3. These memories are included in the prompt to OpenAI.
4. The conversation is stored as a new memory in Supabase.
5. The AI response is displayed to the user.

## Studio Integration

The `studio-integration-version` folder contains everything needed to deploy this agent to the Live Agent Studio:

- **mem0_agent.py**: Core agent implementation.
- **mem0_agent_endpoint.py**: FastAPI endpoint for the agent.
- **Dockerfile**: Container configuration for deployment.
- **.env.example**: Template for required environment variables.

## Troubleshooting

### Authentication Issues:

- Verify that your **Supabase credentials** are correctly set in the `.env` file.
- Ensure that your Supabase project has **Email Auth** enabled.

### Database Connection Issues:

- Verify that your **DATABASE_URL** is correctly formatted.
- Avoid using special characters in your database password. For more information, refer to the note in `.env.example`.
