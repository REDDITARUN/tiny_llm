# Tiny LLM Performance Analysis

Welcome to the Tiny LLM Performance Analysis repository! This project tests several small-scale language models that you can run locally, analyzing their performance across various tasks. If you're interested in experimenting with local language models and seeing how they handle a range of prompts from simple to complex then you're in the right place!

Check out my blog on this for idepth comparision and analysis:  https://medium.com/@teendifferent/exploring-tiny-llms-as-your-personal-assistant-llama-3-2-codegemma-and-more-679f5455c8c4

## Project Overview

In this project, I tested the following language models:
- **Llama3.2 1B**
- **CodeGemma:2B**
- **Phi3**
- **Llama3.2 3B**

The models were evaluated using 15 prompts categorized into three difficulty levels:
- **Easy Level:** Basic questions like "What is artificial intelligence?"
- **Medium Level:** More involved explanations such as DNA replication or literary summaries.
- **Hard Level:** Advanced topics like reinforcement learning in autonomous vehicles or analyzing existential themes in literature.


## Code Snippets

Here's a quick overview of the functions used to test the models:

- **API Interaction Function:** Sends a request to the Ollama API and retrieves the response.
    ```python
    def run_ollama_api(model, prompt, timeout=60):
        url = "http://localhost:11434/api/generate"
        headers = {"Content-Type": "application/json"}
        data = {"model": model, "prompt": prompt, "stream": False}
        response = requests.post(url, json=data, headers=headers, timeout=timeout)
        return response.json().get('response', ''), time.time() - start_time
    ```

- **Word Count Function:** Counts the number of words in the model's response.
    ```python
    def count_words(text):
        return len(text.split())
    ```

- **Relevance Evaluation Function:** Evaluates the relevance of the model's response based on the prompt.
    ```python
    def evaluate_response(response, prompt):
        relevance_score = 1 if any(word in response.lower() for word in prompt.lower().split()) else 0
        return relevance_score
    ```


## How to Use the Code
- **Modify the Prompts:** You can modify the prompts list in the code to test different questions or tasks.
- **Run the Tests:** Execute the script to see how each model performs with your custom prompts.
- **Visualize the Results:** Use the visualizations to get a better understanding of model performance across different metrics.

## Contributing
Feel free to contribute to the project! If you have ideas for new prompts, models to test, or ways to improve the evaluation, submit a pull request or open an issue.

## Contact
I'd love to hear your thoughts or questions. Drop your ideas in the issues, or let's connect to brainstorm—who knows what we’ll figure out together! Reach out: https://bento.me/tarunreddi

