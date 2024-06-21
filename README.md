# Installing-Language-Models-Locally
 Installing and running language model llama3 and moondream locally using Ollama

Download Ollama from [here](https://ollama.com/download/OllamaSetup.exe))
Open the terminal in the folder where the Ollama.exe file is stored

#1 llama3 

To run and chat with Llama 3:
```bash
ollama run llama3
```
Customize a prompt
Models from the Ollama library can be customized with a prompt. For example, to customize the llama3 model:

```bash
ollama pull llama3
```
Create a Modelfile:
```bash
FROM llama3

# set the temperature to 1 [higher is more creative, lower is more coherent]
PARAMETER temperature 1

# set the system message
SYSTEM """
You are Sheldon cooper from Big Bang Theory. Answer as Sheldon, the assistant, only.
"""
```
Next, create and run the model:
```bash
ollama create Sheldon -f ./Modelfile
ollama run Sheldon
>>> hi
>>>Hello! It's your friend Sheldon.
```
Interacting with the model via API through Invoke-WebRequest.
```bash
(Invoke-WebRequest -method POST -Body '{"model":"llama3", "prompt":"When did the roman Empire fall?", "stream": false}' -uri http://localhost:11434/api/generate ).Content | ConvertFrom-json

```

#1 Moondream 

To run and chat with Moondream:
```bash
ollama run Moondream
```
Customize a prompt
Models from the Ollama library can be customized with a prompt. For example, to customize the Moondream model:

```bash
ollama pull Moondream
```
Create a Modelfile1:
```bash
FROM Moondream

# set the temperature to 1 [higher is more creative, lower is more coherent]
PARAMETER temperature 1

# set the system message
SYSTEM """
You are Harvey Specter from Suits. Answer as Harvey, the assistant, only.
"""
```
Next, create and run the model:
```bash
ollama create Harvey -f ./Modelfile1
ollama run Harvey
>>> hi
>>>Hello! It's your friend Harvey.
```
Interacting with the model via API through Invoke-WebRequest.
```bash
(Invoke-WebRequest -method POST -Body '{"model":"Moondream", "prompt":"When did the roman Empire fall?", "stream": false}' -uri http://localhost:11434/api/generate ).Content | ConvertFrom-json

```
Upon installing and running both the models parallely it was noticed that Moondream gave quick and concise responses. While llama3 gave elaborate responses it somehow took more time to generate responses. 
[Link](https://ollama.com/download/OllamaSetup.exe)) to the youtube video demonstrating the above. 
