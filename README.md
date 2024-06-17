# GenAI_Hands_on_session-6-7-OpenAI-
This repository contains an intermediate hands-on that can be used to understand the functioning of OpenAI and OpenAI APIs

### Hands-On Project: Using OpenAI API for Various Tasks

#### Objective:
Students will learn how to set up and use the OpenAI API with Python. They will explore different functionalities such as text generation, chat completion, image generation, and understand the basics of tokenization, function calling, and limitations.

### Step-by-Step Instructions:

#### Step 1: Setting Up the Environment

Ensure you have Python, Pandas, and Jupyter Notebook installed. If not, install via pip:
```bash
pip install openai pandas jupyter
```

#### Step 2: Generate API Key

- Go to the [OpenAI website](https://www.openai.com) and log in.
- Navigate to the API section and generate a new API key.

#### Step 3: Setting Up OpenAI API with Python

Create a new Jupyter notebook and start by importing necessary libraries and setting up the OpenAI API key.

```python
import openai
import pandas as pd

# Set up the OpenAI API key
openai.api_key = 'your-api-key-here'
```

#### Step 4: Text Generation with GPT-3.5/4

Demonstrate how to use the OpenAI API for text generation.

```python
def generate_text(prompt):
    response = openai.Completion.create(
        engine="text-davinci-004",  # Choose between "text-davinci-003" and "text-davinci-004"
        prompt=prompt,
        max_tokens=100
    )
    return response.choices[0].text.strip()

# Example usage
prompt = "Write a poem about the sea."
generated_text = generate_text(prompt)
print(generated_text)
```

#### Step 5: Chat Completion API

Show how to create a chatbot using the Chat Completion API.

```python
def chat_with_gpt(messages):
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",  # Choose between "gpt-3.5-turbo" and "gpt-4"
        messages=messages
    )
    return response.choices[0].message['content']

# Example usage
messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the weather like today?"}
]

response = chat_with_gpt(messages)
print(response)
```

#### Step 6: Tokenizer

Explain tokenization and show how to use the tokenizer.

```python
def tokenize_text(text):
    response = openai.Completion.create(
        engine="text-davinci-004",
        prompt=text,
        max_tokens=0,
        logprobs=1
    )
    tokens = response.choices[0].logprobs['tokens']
    return tokens

# Example usage
text = "Hello, how are you?"
tokens = tokenize_text(text)
print(tokens)
```

#### Step 7: Image Generation with DALL-E

Show how to use DALL-E for image generation.

```python
def generate_image(prompt):
    response = openai.Image.create(
        prompt=prompt,
        n=1,
        size="512x512"
    )
    return response['data'][0]['url']

# Example usage
prompt = "A futuristic cityscape at sunset."
image_url = generate_image(prompt)
print(image_url)
```

#### Step 8: Function Calling and Limitations

Demonstrate function calling and discuss API limitations.

```python
# Function to get OpenAI API usage
def get_api_usage():
    usage = openai.Usage.retrieve()
    return usage

# Example usage
api_usage = get_api_usage()
print(api_usage)

# Discuss limitations
print("Limitations of OpenAI API:")
print("- Maximum number of tokens per request")
print("- Rate limits on API calls")
print("- Pricing and billing considerations")
```

### Conclusion

By completing these hands-on activities, students will gain practical experience with the OpenAI API, including setting up the environment, generating text, creating a chatbot, using the tokenizer, generating images with DALL-E, and understanding function calling and API limitations. This will reinforce the concepts covered in your session and provide a solid foundation for further exploration of OpenAI's capabilities.
