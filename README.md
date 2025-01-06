# mmm

A command-line tool that uses ChatGPT to automatically improve and refine answers and code by continuously requesting improvements.

## Description

`mmm` takes input and uses the OpenAI API to generate an initial answer. It then repeatedly asks ChatGPT to make improvements based on a specified or automatically generated improvement type, ensuring responses become better with each iteration. The tool supports system prompts, custom improvement types, and outputting initial and final responses to markdown files.

## Features

-   **Continuous Improvement**: Makes responses better through multiple iterations by repeatedly asking for improvements.
-   **Customizable Improvement**: Provides options to define specific improvements or auto-generate them.
-   **System Prompts**: Allows setting custom system prompts for specific tasks.
-   **Markdown Output**: Saves initial and final responses to markdown files.
-   **Conversation History**: Maintains a conversation history so follow-up questions can be made.
-   **Clear Output**: Provides informative console output indicating the progress of the requests.

## Usage

```bash
$ mmm <question> [options]
```

-   `<question>`: The question you want to ask ChatGPT.

## Options

-   `--makeIt, -m <string>`: A string describing how to improve the answer. If not specified, the tool will try to determine an improvement type automatically.
-   `--iterations, -i <number>`: The number of times to improve the response. Default is 4.
-   `--systemPrompt, -s <string>`: A system prompt to guide ChatGPT's responses.
-   `--initialOutput, -o <string>`: The file path to write the initial answer to (must be markdown file).
-   `--finalOutput, -f <string>`: The file path to write the final, improved answer to (must be markdown file).

## Setup

1.  **Install Node.js and Bun**: Ensure you have both Node.js and Bun installed on your system. Bun is used as a runtime for this script for performance. You can install Bun via:

    ```bash
    curl -fsSL https://bun.sh/install | bash
    ```
2.  **Install dependencies**:
   ```bash
   bun install meow chalk dotenv
   ```
3.  **Set up your API Key**:  You'll need an API key for the OpenAI API. You can get an API Key here: https://platform.openai.com/api-keys.  Once you have your API key, you need to put this key into your `.env` file in the same directory as this script.  Your `.env` file should look like this:
   ```
    API_KEY=sk-...your-api-key
   ```
4.  **Make the script executable:**  You can use this command to make the script executable: `chmod +x mmm.js`
5.  **Run the script**: You can now run `mmm` by using the command: `./mmm`

## Examples

### Basic Question

```bash
./mmm "Explain the concept of recursion in programming"
```

### Specifying Improvements

```bash
./mmm "Write a Python function to find the factorial of a number" --makeIt "make it more efficient"
```

### Changing Iteration Count

```bash
./mmm "How does the internet work?" -i 2
```

### Using System Prompts

```bash
./mmm "Write a short story" --systemPrompt "You are a creative writer"
```

### Outputting to Markdown

```bash
./mmm "Explain the benefits of using TypeScript" --initialOutput initial.md --finalOutput final.md
```

## Notes

-   Default model is `gpt-4o-mini`
