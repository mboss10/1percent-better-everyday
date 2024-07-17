# Configuring a .env File for Python and Jupyter Notebook to Save API Keys 

Environment variables are an excellent way to store sensitive information like API keys, ensuring they're not exposed in your code. This guide will walk you through the process of setting up and using a .env file for both Python scripts and Jupyter Notebooks.

## What is a .env File?

A .env file is a simple text file that stores key-value pairs of environment variables. It's commonly used to keep configuration settings and sensitive information separate from your code.

## Setting Up a .env File

1. Create a new file in your project's root directory and name it `.env`.
2. Add your environment variables in the following format:
   ```
   API_KEY=your_api_key_here
   SECRET_TOKEN=your_secret_token_here
   ```
3. Make sure to add `.env` to your `.gitignore` file to prevent it from being tracked by Git.

## Using .env in Python Scripts

To use the .env file in your Python scripts, follow these steps:

1. Install the `python-dotenv` library:
   ```
   pip install python-dotenv
   ```

2. In your Python script, import and load the .env file:
   ```python
   from dotenv import load_dotenv
   import os

   load_dotenv()
   ```

3. Access your environment variables using `os.getenv()`:
   ```python
   api_key = os.getenv('API_KEY')
   secret_token = os.getenv('SECRET_TOKEN')
   ```

## Using .env in Jupyter Notebooks

For Jupyter Notebooks, the process is similar:

1. Install `python-dotenv` if you haven't already.

2. In your notebook, load the .env file:
   ```python
   %run -m dotenv
   ```

3. Access your environment variables using `os.getenv()`:
   ```python
   import os

   api_key = os.getenv('API_KEY')
   secret_token = os.getenv('SECRET_TOKEN')
   ```

Alternatively, you can use Jupyter's magic commands to set environment variables directly in the notebook:

```python
%env API_KEY=your_api_key_here
%env SECRET_TOKEN=your_secret_token_here
```

## Best Practices

1. **Never commit your .env file to version control.** Always add it to your `.gitignore` file.

2. **Use descriptive variable names.** For example, use `OPENAI_API_KEY` instead of just `API_KEY`.

3. **Provide a sample .env file.** Create a `.env.example` file with placeholder values to show other developers what environment variables are needed.

4. **Validate required environment variables.** At the start of your script or notebook, check if all required variables are set.

5. **Use different .env files for different environments.** For example, `.env.development`, `.env.production`, etc.

## Troubleshooting

If you're having trouble accessing your environment variables:

- Ensure your .env file is in the correct directory (usually the project root).
- Double-check that you've installed `python-dotenv` and imported it correctly.
- Verify that your .env file is formatted correctly with no spaces around the `=` sign.
- Restart your Jupyter kernel or Python environment after making changes to the .env file.
