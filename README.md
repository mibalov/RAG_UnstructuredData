# RAG: Speak with your Unstructured Data

# Introduction 
This repo constains an E2E Rag application which showcases diferent use and Integrations of Langchain with other technologies to "chat" with your Unstructured Data (audio, video, images, pdf, excel, csv and html).

The main technology we will use will be Langchain, as LLMs we will use Gemini Pro Fast, Microsoft Phi3.5 Mini and LLama 3.2 3B, the last two hosted on Nvidia NIM. 

VectorStores Elastic, Choma, Faiss and Vilmus. 

Embeddings Models: Gemini and Nvidia embeddings

As a UX tool and application server we will use Streamlit

Docker and Docker compose to create containers

![alt text](images/intro.png)

# Getting Started
Documentation Elastic --> https://www.elastic.co/blog/getting-started-with-the-elastic-stack-and-docker-compose

1.	Installation process
    - copy `docker/.env.example` to `docker/.env` and set strong passwords
    - create `keys/.env` using the example [here](docs/env.md)
    - copy your Google Cloud service account `.json` file to the local `keys` folder
    - create the Streamlit user configuration as `keys/config.yaml`
    - build the Docker image: `docker build --pull --rm --build-arg user_app=app -f Dockerfile -t demo-ai-rag:latest .`
    - start the stack: `docker compose -f docker/docker-compose.yml up -d`

   Keep the local `keys` folder and `docker/.env` out of Git. Docker Compose mounts
   `keys` at runtime; credentials are excluded from the image build context.
2.	Software dependencies
    - python 3.11
    - requiremrents file [here](requirements.txt)
3.	Latest releases
4.	API references

# Project Structure

![alt text](images/project.png)

# How to create users and passwords for this app

Create `keys/config.yaml` locally. Do not commit it; the `keys/` directory is ignored.
Use your own usernames, email addresses, bcrypt password hashes, and a random cookie
secret. Do not deploy the placeholders below.
```
credentials:
  usernames:
    your_username:
      email: you@example.com
      name: Your Name
      password: REPLACE_WITH_BCRYPT_HASH
cookie:
  expiry_days: 0
  key: REPLACE_WITH_A_RANDOM_COOKIE_SECRET
  name: rag_app
```


To generate password hashes, edit `hasher/ex.yaml` with your own values, run
`hasher/hasher.py`, and copy the generated hash into `keys/config.yaml`. The example
file contains placeholders only; never reuse its placeholder password or cookie secret.
