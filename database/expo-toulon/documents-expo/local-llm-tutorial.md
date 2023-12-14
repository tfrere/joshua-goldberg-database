# Local LLM - tutorial

### Ressources

Twitter : 

[https://twitter.com/GregKamradt](https://twitter.com/GregKamradt)

[https://twitter.com/engineerrprompt](https://twitter.com/engineerrprompt)

[https://x.com/aidfulai?s=21&t=CCpJOf7uAsWtzEff8nKqRA](https://x.com/aidfulai?s=21&t=CCpJOf7uAsWtzEff8nKqRA)

[https://x.com/emollick?s=21&t=CCpJOf7uAsWtzEff8nKqRA](https://x.com/emollick?s=21&t=CCpJOf7uAsWtzEff8nKqRA)

Ismael YouTube playlist : [https://youtube.com/playlist?list=PLIf46k6Q6GjS5qK6O3xSrj9BUL8eYO6HD&si=uoagNRUx_E7FCt9_](https://youtube.com/playlist?list=PLIf46k6Q6GjS5qK6O3xSrj9BUL8eYO6HD&si=uoagNRUx_E7FCt9_)

Assistant prompt : [http://promptperfect.xyz/](http://promptperfect.xyz/)

Hugginface : 

[https://huggingface.co/TheBloke](https://huggingface.co/TheBloke)

[https://huggingface.co/ehartford](https://huggingface.co/ehartford)

### 🔗 Uncensored models

Uncensored models Guide : [https://erichartford.com/uncensored-models](https://erichartford.com/uncensored-models)

Twitter thread : 

[https://x.com/aidfulai/status/1734132170619551882?s=46&t=CCpJOf7uAsWtzEff8nKqRA](https://x.com/aidfulai/status/1734132170619551882?s=46&t=CCpJOf7uAsWtzEff8nKqRA)

The Bloke : 

[https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML)

### **What's a model?**

When I talk about a model, I'm talking about a huggingface transformer model, that is instruct trained, so that you can ask it questions and get a response. What we are all accustomed to, using ChatGPT. Not all models are for chatting. But the ones I work with are.

First we have to understand technically why the models are aligned.

Open source AI models are trained from a base model such as LLaMA, GPT-Neo-X, MPT-7b, Pythia. The base model is then finetuned with an instruction dataset, and the purpose of this is to teach it to be helpful, to obey the user, answer questions, and engage in conversation.

The reason is that the instruction dataset is composed of questions and answers, and when the dataset contains answers where the AI is being coy or outright refusing (called Refusals) then the bot learns how to refuse, and under what circumstances to refuse, and how to word the refusals. In other words, it learns alignment.

Enjoy responsibly. You are responsible for whatever you do with the output of these models, just like you are responsible for whatever you do with a knife, a car, or a lighter.

### Fine-tuning services

- Runpod
- 

Roleplay : 

Modele ? 

Dataset fine tuning : peut aussi mettre des exemples

Exemple de quelqu’un qui a fait fine tuning character 

Invocation / preprompt 

Instruction + exemple 

Sandbox // 

30k/50k/100k 

Thibaud : prompt engineering // 

Preprompt invocation 

Mistral7b 

### Custom GPTs (Open AI)

[https://open.substack.com/pub/oneusefulthing/p/almost-an-agent-what-gpts-can-do?r=mpyl7&utm_medium=ios&utm_campaign=post](https://open.substack.com/pub/oneusefulthing/p/almost-an-agent-what-gpts-can-do?r=mpyl7&utm_medium=ios&utm_campaign=post)

### Tools

- LM studio
- Hugginface
- Mistral 7b
- Yi 200k
- Langchain
- Gpt4all
- Ollama
- Oogabooga webui
- Prompt perfect
- Llama index
- Unsloth (30x speed fine tuning)
- Silly tavern

### Customizing LLM

1. **Bots GPT** : Ce sont des applications ou des services qui utilisent un modèle GPT pour interagir avec les utilisateurs, souvent dans un cadre spécifique (comme un assistant client ou un chatbot de divertissement). Ils sont généralement configurés pour répondre de manière appropriée dans leur domaine d'application.
2. **Custom Instructions dans ChatGPT** : Cela fait référence à la possibilité de donner des directives spécifiques à ChatGPT pour qu'il réponde d'une certaine manière. Par exemple, vous pouvez demander à ChatGPT de répondre comme s'il était un personnage de fiction ou de se conformer à un certain style ou ton.
3. **Prompt Templates** : Ce sont des modèles ou des structures de prompts préconçus que vous utilisez pour obtenir des réponses cohérentes et ciblées d'un modèle GPT. Ils aident à formuler des requêtes de manière à guider le modèle vers le type de réponse souhaité.
4. **Fine Tuning** : C'est un processus où vous entraînez davantage un modèle GPT sur un ensemble de données spécifique pour qu'il soit plus performant dans un domaine particulier. Par exemple, affiner GPT pour qu'il soit plus compétent en médecine ou en droit.
5. **RAGs (Rules as Graphs) dans Langchain** : Les RAGs sont des structures de règles sous forme de graphes qui sont utilisées pour contrôler et guider la manière dont un modèle de langage génère des réponses. C'est une façon de structurer des règles complexes pour des cas d'utilisation spécifiques.
6. **Langchain** : C'est une bibliothèque qui permet d'intégrer des modèles de langage dans des applications. Elle offre des outils comme les RAGs pour personnaliser et contrôler le comportement du modèle de langage.
7. **Agents** : les agents sont des entités programmables qui utilisent des modèles de langage et des structures comme les RAGs pour interagir de manière intelligente et contextuelle. Ils représentent une couche d’abstraction au-dessus des modèles de langage, fournissant autonomie et spécialisation dans leur comportement.

En résumé :

- Les bots GPT, les prompt templates et les custom instructions dans ChatGPT sont des méthodes pour interagir avec ou guider les modèles GPT dans des contextes spécifiques.
- Le fine tuning est une technique d'entraînement pour spécialiser un modèle GPT dans un domaine.
- Les RAGs et Langchain fournissent des cadres pour structurer et imposer des règles plus complexes sur les réponses des modèles de langage.
- Agents : Des programmes ou modules qui utilisent des modèles de langage pour effectuer des tâches spécifiques, souvent guidés par des règles ou des logiques complexes comme les RAGs.

Fine tune pour les documents : éviter la baisse de pertinence dans les requêtes d’info du milieu de doc (de it/fin ok) 

Uncensored question 

Sexbot : fine tune to trove censor and fine tune for own data 

[https://www.reddit.com/r/LocalLLaMA/s/tB4DDGXniQ](https://www.reddit.com/r/LocalLLaMA/s/tB4DDGXniQ)

[https://www.reddit.com/r/LocalLLaMA/comments/15b7x1l/what_is_the_best_uncensored_llm_model_for_erp/](https://www.reddit.com/r/LocalLLaMA/comments/15b7x1l/what_is_the_best_uncensored_llm_model_for_erp/)

### Large context

Chat gpt : most important instruction in the end.

![IMG_5441.jpeg](Local%20LLM%20-%20tutorial%20ac430bcb878c4d2ba0fdad574e4b4a2f/IMG_5441.jpeg)

![IMG_5440.jpeg](Local%20LLM%20-%20tutorial%20ac430bcb878c4d2ba0fdad574e4b4a2f/IMG_5440.jpeg)

Fine tuning pourrait être bon pour le bot Joshua. Il faudrait s’arrêter sur une version et refaire plus tard 

### Comme samantha d’Éric hartford

Samantha est un modèle de langage développé par Eric Hartford. Ce modèle semble être une version avancée et personnalisée d'un modèle de langage à grande échelle, similaire aux modèles GPT d'OpenAI, avec des améliorations spécifiques en termes de quantification et d'utilisation de la mémoire. Samantha est disponible en plusieurs versions, avec des tailles variables en termes de paramètres, et semble être optimisée pour différentes utilisations en fonction de ses versions. Les détails techniques incluent des informations sur la quantification des bits et les exigences de mémoire, ce qui indique une attention particulière à l'efficacité du modèle et à sa capacité à être déployé dans différents environnements informatiques [oai_citation:1,TheBloke/Samantha-1.1-70B-GGML · Hugging Face](https://huggingface.co/TheBloke/Samantha-1.1-70B-GGML) [oai_citation:2,TheBloke/Samantha-1.1-70B-GPTQ · Hugging Face](https://huggingface.co/TheBloke/Samantha-1.1-70B-GPTQ).

Ces modèles sont disponibles sur Hugging Face, une plateforme populaire pour les modèles de machine learning, et semblent être conçus pour être intégrés et utilisés dans diverses applications de génération de texte, offrant ainsi un degré de flexibilité et de personnalisation pour des cas d'utilisation spécifiques.

Wizard_vicuna_70k_unfiltered 

⇒ model llama 2 fine tuned avec vicuña pour Le uncensored. Mais on fine tune ça ou on template prompt ? 

Claude 2 sera toujours au dessus de tout sur l’analyse de doc 

Se Focus sur de la matière censurée à analyser ou bien pour role play et ligne de dialogues 

Chatbot + rag

Story idea 

feeding the program a prompt, such as a genre or a character, and then letting it generate a plot or story based on that prompt. 

for [dialogue](https://aicontentfy.com/en/blog/chatgpt-and-future-of-dialogue-generation), character development and scene changes.

editing process by providing alternative lines of dialogue or suggesting ways to improve pacing, ensuring a smooth flow in the script.

### Creative screenwriting assistant

[https://github.com/daveshap/ChatGPT_Custom_Instructions/blob/main/creative_writing_partner.md](https://github.com/daveshap/ChatGPT_Custom_Instructions/blob/main/creative_writing_partner.md)

### Clone writing

0/ Tutoriel

[https://x.com/rowancheung/status/1720797318209831034?s=46&t=CCpJOf7uAsWtzEff8nKqRA](https://x.com/rowancheung/status/1720797318209831034?s=46&t=CCpJOf7uAsWtzEff8nKqRA)

1/ Collect and copy writing sample

2/ prepare : 

You are an expert screenwriter. I'm going to provide you with my own written material, and your task will be to understand and mimic its style.
You'll start this exercise by saying "BEGIN." After, I'll present an example text, to which you'll respond, "CONTINUE". The process will continue similarly with another piece of writing and then with further examples. I'll give you unlimited examples. Your response will only be
"CONTINUE. You're only permitted to change your response when I tell you "FINISHED".
After this, you'll explore and understand the tone, style, and characteristics of my writing based on the samples I've given. Finally, I'll prompt you to craft a new piece of writing on a specified topic, emulating my distinctive writing style.

3/ the more you provide, the better it is

4/ BEGIN, FINISHED // 4 pieces Min.

5/ name the style : Joshua’s style

6/ 80% style precision with gtp3.5 // but gpt4 any%?

7/ needs big context window (gpt4 128k, Claude 2 200k, llama 100k?)

8/ split files into chunks 

### Chat with document

Framework (langchainetc.) + pypdf2 

⇒ allows the model to interact with API

1 click Packages (gpt4all)

- Read pdf
- Derermine chunk_size
- Determine chunk_overlap
- Embeddings = (OpenAIEmbeddings)
- Query?

Tools 

Super dupera DB

Oogabooga local GPT

Chat with PDF files ⇒ extract data/context ⇒ split in chunks (1,2,3,4) ⇒ embedding (1,2,3,4) ⇒ semantic index 

![IMG_5427.png](Local%20LLM%20-%20tutorial%20ac430bcb878c4d2ba0fdad574e4b4a2f/IMG_5427.png)