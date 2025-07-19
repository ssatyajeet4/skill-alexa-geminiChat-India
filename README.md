# Alexa Gemini Chat Skill

An Alexa skill that integrates Google's Gemini AI with Amazon Alexa devices, allowing users to have conversational interactions with Gemini 1.5 Flash model through voice commands in Portuguese (Brazil).

**Visit [Scintilla Hub](https://www.youtube.com/@scintillahub) on YouTube**

## Features

- **Voice-powered AI conversations** through Alexa devices
- **Google Gemini 1.5 Flash integration** for intelligent responses
- **Conversation history** that maintains context across interactions
- **Portuguese (Brazil) language support**
- **AWS Lambda hosting** for scalable deployment

## Prerequisites

- **Google AI API Key**: Create a Google account and generate an authentication API key at [Google AI Developer](https://ai.google.dev/). Copy and save the key as it will only be visible at the moment of creation.
- **Amazon Developer Account**: Create an account on [Amazon](https://www.amazon.com/ap/signin?openid.pape.preferred_auth_policies=Singlefactor&clientContext=132-2293245-7926858&openid.pape.max_auth_age=7200000&openid.return_to=https%3A%2F%2Fdeveloper.amazon.com%2Falexa%2Fconsole%2Fask&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.assoc_handle=amzn_dante_us&openid.mode=checkid_setup&marketPlaceId=ATVPDKIKX0DER&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&) and log in to the _Alexa Developer Console_.

## Setup Instructions

### Creating the Alexa Skill

Create an Alexa-hosted (Python) skill in Alexa Developer Console:

1. **Name your Skill**: Choose a name of your preference (e.g., GeminiGPT)
2. **Choose a primary locale**: Portuguese (BR)
3. Click _Next_. For experience type select: Other > Custom > _Alexa-hosted (Python)_
4. **Hosting region**: You can leave the default _US East (N. Virginia)_
5. In _Templates_: Click _Import Skill_
6. Enter the repository address: `https://github.com/Machally/skill-alexa-geminiChat.git` and confirm

### Configuring the Skill

After completing the import, go to _Invocations_ > _Skill Invocation Name_:

1. Edit _Skill Invocation Name_. This will be the invocation command for your skill. Ensure it meets the requirements and word restrictions
2. Click _Save_
3. Build the skill by clicking _Build Skill_. When finished, go to the **Code** tab
4. Create a file inside the Lambda folder called `.env` and add the line with your generated API key:
   ```shell
   GOOGLE_API_KEY=YourGoogleAIApiKey
   ```
5. Click _Save_ and then _Deploy_

### Testing the Skill

After completing the _deploy_, go to the **Test** tab:

1. In _Skill testing is enabled in_, change from _Off_ to _Development_
2. To use voice commands, accept the microphone usage request from the website. To speak, click and hold the mic icon, then release to send
3. Use the configured activation command to start the skill, and you're now interacting with Gemini through Alexa!

The skill will be available on all Alexa devices linked to your account.

## Architecture

### Core Components

- **Lambda Function** (`lambda/lambda_function.py`) - Main skill handler using Alexa Skills Kit SDK
- **Interaction Model** (`interactionModels/custom/pt-BR.json`) - Defines skill invocation and intents
- **Utils** (`lambda/utils.py`) - S3 utility functions

### Dependencies

- `boto3==1.28.78` - AWS SDK
- `ask-sdk-core==1.19.0` - Alexa Skills Kit SDK
- `python-dotenv==1.0.1` - Environment variable management
- `requests==2.31.0` - HTTP client for Gemini API

## Usage Examples

### Skill Invocation

Say: *"Alexa, abra assistente inteligente"* (Portuguese: "Alexa, open intelligent assistant")

### Example Interactions

- **User**: "Qual é a capital do Brasil?"
- **Alexa**: *Gemini AI response about Brazil's capital*

- **User**: "Me conte uma piada"
- **Alexa**: *Gemini AI tells a joke*

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for improvements and bug fixes.

## License

This project is open source. Please check the repository for specific license terms.
