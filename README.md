# chatgpt-uml 

Large Language Models (LLMs), such as Copilot or ChatGPT, are expected to revolutionize the way in which software is developed nowadays. Many efforts are currently devoted to analyzing the potential advantages and limitations of these generative AI models for writing code. Most studies seem to agree that LLMs do an excellent job in code development: despite some minor syntactical errors, what they produce is essentially correct. However, the analysis of the current state of LLMs with respect to software modeling has received less attention.

We have recently started working on investigating the current capabilities and limitations of ChatGPT for performing modeling tasks and assisting software modelers, in particular in generating UML class diagrams. 

This repository contains all artifacts (such as intent models, prompts, resulting models and logbooks) used for conducting our experiments, as well as their results. It is aimed as serving as companion webpage for a paper in preparation:

> "On the Assessment of Generative AI in Modeling Tasks: An Experience Report with ChatGPT and UML" by [Javier Cámara](mailto:jcamara@uma.es), [Javier Troya](mailto:jtroya@uma.es), [Lola Burgueño](mailto:lolaburgueno@uma.es) and [Antonio Vallecillo](mailto:antoniovallecillomoreno@gmail,com).

## Structure

The contents of this repository as organized as follows:

* [Intent models](https://github.com/atenearesearchgroup/chatgpt-uml/blob/main/IntentModels.md), used as targets to check whether ChatGPT can generate them or not, and how.  
* [Logbooks](https://github.com/atenearesearchgroup/chatgpt-uml/blob/main/LogBooks.zip), recording the conversations we had with ChatGPT in order to generate the intent models. It is a zipped file so that ChatGPT cannot inspect the models.
* Larger examples, to challenge ChatGPT and its future versions. 
* [Images](https://github.com/atenearesearchgroup/chatgpt-uml/tree/main/images) of all models.

---

**Disclaimer**: This repository is currently under development. Please contact any of the authors if you have any specific request. 