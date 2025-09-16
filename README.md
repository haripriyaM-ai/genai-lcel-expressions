## EXP-2: Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.
<br><br>
### PROBLEM STATEMENT:
To create a system that explains a chosen concept (like Generative AI) in a way that is tailored to a specific type of audience (like beginners), using LangChain’s LCEL pipeline with prompt, model, and output parser.
<br><br>

### DESIGN STEPS:

#### STEP 1: Set up environment 
Load API keys and required libraries.

#### STEP 2: Create a prompt 
Write a template with placeholders {concept} and {audience}.

#### STEP 3: Choose a model 
Use ChatOpenAI() to generate text from the prompt.
#### STEP 4: Add output parser 
Use StrOutputParser() to make the model’s reply a clean string.
#### STEP 5: Run the chain 
Connect everything (prompt | model | output_parser) and give input values to see the explanation.

<br>

### PROGRAM:

```python
import os
import openai

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file
openai.api_key = os.environ['OPENAI_API_KEY']
```

```python
from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser
```
Simple Chain:
```python
prompt = ChatPromptTemplate.from_template(
    "Explain {concept} in a way that a {audience} can understand."
)
model = ChatOpenAI()
output_parser = StrOutputParser()
```

```python
chain = prompt | model | output_parser
```

```python
chain.invoke({"concept": "Generative AI", "audience" : "beginner"})
```



### OUTPUT:
<img width="1000" height="250" alt="Screenshot 2025-09-17 004119" src="https://github.com/user-attachments/assets/b24b91bd-45f5-4feb-be19-222245cffdc8" />


### RESULT:
The LCEL chain was successfully implemented and executed.
