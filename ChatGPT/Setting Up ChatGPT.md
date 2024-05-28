## Setting Up ChatGPT

Setting up ChatGPT involves several steps to ensure a smooth installation and
configuration. This section provides a detailed guide to help you set up ChatGPT
efficiently.

### **Prerequisites**

Before you begin, make sure you have the following:

1. **Python:** ChatGPT requires Python 3.7 or later. You can download it from
the [official Python website](https://www.python.org/downloads/).
2. **Pip:** Pip is the package installer for Python. It is usually included
with Python, but you can verify by running `pip --version` in your command line.
3. **OpenAI API Key:** You'll need an API key from OpenAI to access the GPT
models. Sign up at [OpenAI's website](https://www.openai.com/signup) and obtain
your key.

### **Step-by-Step Installation**

#### **1. Install Python and Pip**

Ensure Python and Pip are installed on your system. You can verify the
installation by running the following commands:

```sh
python --version
pip --version
```

If not installed, download Python from the
[official website](https://www.python.org/downloads/) and follow the installation
instructions. Pip is included with Python 3.4 and later versions.

#### **2. Create a Virtual Environment**

Creating a virtual environment is recommended to manage dependencies and avoid
conflicts with other projects. To create a virtual environment, run:

```sh
python -m venv chatgpt_env
```

Activate the virtual environment:

- On Windows:
  ```sh
  .\chatgpt_env\Scripts\activate
  ```

- On macOS/Linux:
  ```sh
  source chatgpt_env/bin/activate
  ```

#### **3. Install Required Packages**

With the virtual environment activated, install the OpenAI package and any other
dependencies:

```sh
pip install openai
```

#### **4. Configure Environment Variables**

Set your OpenAI API key as an environment variable to keep your credentials
secure. Add the following line to your shell configuration file
(`.bashrc`, `.zshrc`, etc.):

```sh
export OPENAI_API_KEY='your-api-key-here'
```

Reload the shell configuration file:

```sh
source ~/.bashrc
```

Or, for the current session:

```sh
export OPENAI_API_KEY='your-api-key-here'
```

#### **5. Verify Installation**

To verify that everything is set up correctly, run a simple script to test the API:

```python
import openai

openai.api_key = os.getenv("OPENAI_API_KEY")

response = openai.Completion.create(
  engine="text-davinci-003",
  prompt="Say hello to the world!",
  max_tokens=5
)

print(response.choices[0].text.strip())
```

You should see a response from the API confirming that it's working.

### **References**

1. Python Software Foundation. (n.d.). "Python Releases for Windows."
Retrieved from [python.org](https://www.python.org/downloads/windows/)
2. OpenAI. (2023). "OpenAI API Documentation." Retrieved from
[OpenAI](https://beta.openai.com/docs/)
3. The Pallets Projects. (n.d.). "Virtual Environments and Packages."
Retrieved from [Python.org](https://docs.python.org/3/tutorial/venv.html)
