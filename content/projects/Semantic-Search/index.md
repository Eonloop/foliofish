---
title: "Semantic Search"
date: 2026-01-27
featured: "featured.png"
draft: false
description: "Project documentation for my MLOps Project"
tags: ["semantic", "search", "docker", "nlp", "linear algebra"]
showAuthor: true
mermaid: true
---

## Purpose Of This Project
This project spawned from my professional experience in documentation, many times finding the most relevant information out of our documentation stores, and a lot of the time they don't even know what's in their own documentation either.

With my interest in Linear Algebra and Natural Language Processing as well as DevOps I figured that a solid project to work on would be to implement a full DevOps pipeline for a dockerized Semantic Search application.

## Tooling Utilized (Subject To Change As The Project Progresses)
- FastAPI - REST API
- Python - Primary Programming Language
- Docker - Containerization
- ChromaDB - Vector database
- VS Code - IDE Utilized
- HTML/CSS/JavaScript - Web Frontend
- GitHub - Version Control
- GitHub Actions - CI/CD
- GitHub Projects - Project Management
- pytest - Unit Testing Framework 
- Mermaid - Diagramming


## Weekly Progress

### 1/29/2026

#### Last Weeks Work

Last Week I spent my time thinking about what project I wanted to work on and making some neural connections between my work and the two other classes I'm taking right now with NLP and Linear Algebra. 

My NLP class went over NLTK and how to process Corpora and this got me thinking about how documentation systems are just large distributed Corpora.

I researched how NLP and Linear Algebra could be applied to documentation and stumbled on this great [Medium Article]() outlining what Semantic Search is and how these concepts might fit together, I also thought about how I'd like to incorporate a little bit of DevOps into this project so I looked into Docker and Github Actions a bit.

I cleaned up my Personal Portfolio Website it was a little neglected so I stood up a page for my project and changed some of the formatting and layout to be a bit more professional with the intent of showing off my portfolio of work.

I researched Vector Databases a bit to understand what I was getting myself into.

#### Work This Week

This week I plan to look a bit more into how to utilize existing Python libraries for handling .docx, .pdf, .txt, and .md files

Research a bit more about FastAPI

Look into the recommendation made to me by Professor Guinn Meta's FAISS library for similarity search and clustering of dense vectors 

Stand up my Github Repo for my project and start building

Pick my Vector Database

#### Impediments

I think the only impediment is that I'll be a traveling a little bit over this next week so making sure that I manage my time properly and find ways to offline some of the research I wanted to do (texts, documentation sites, books, etc.)
I'll be throwing this on my iPad and utilizing that for my offline workflow.


#### Reflections

I think my process can work better if I create an architectural diagram to help me with the big picture, and get this scoped into a project tracker so that I have something to reference broken down into smaller chunks and to keep me focused and on track. 


---

### 2/5/2026

#### Last Weeks Work

Last week I spent some time standing up my [GitHub Repo](https://github.com/Eonloop/semantix), and setting up the inital structure with the FastAPI Boilerplate, as well as the Dockerfile boilerplate and researching [ChromaDB](https://docs.trychroma.com/docs/overview/getting-started) vs. [Pinecone](https://www.pinecone.io/) vs. Meta's [FAISS](https://ai.meta.com/tools/faiss/) 

I decided to go with ChromaDB as my Vector Database, this decision was based on their simple integration with FastAPI and their "batteries included" style. Reading more into these tools was intriguing however, it seems like if I wanted a faster solution for simliarity search I would want to go with Meta's FAISS, but it seems a bit too low level for the scope I'm trying to maintain for this project, it seems like I'd need to build some supporting pieces to implement this properly for the task of text embedding comparisons.

Pinecone also presented an attractive solution, but with the cloud dependencies and more enterprise focus I figured I'd just go with ChromaDB for a purely local, fast and effective experience. That being said I'm now curious and will probably be poking at Pinecone and FAISS outside of this project as well.

I did some reading on [FastAPI](https://fastapi.tiangolo.com/tutorial/first-steps/) and it's accompanying web-server tools uvicorn which seems to be included if you `pip install fastapi[standard]` this getting started article was helpful. It reminded me of [Flask](https://flask.palletsprojects.com/en/stable/) a similar framework that I worked with in a previous class for assignments, as well as with an AI Technical interview application our team built. I got a boilerplate template stood up to familiarize myself with the tool so that I can eventually plug in my python scripting for text processing as well as the ChromaDB connection, and (hopefully) eventually a front-end user interface.

Finally I made sure to also take a look at Docker's documentation on containerizing this application so that I can make it portable, so that when someone wants to use or demo the tool they can do it from any machine they'd like. This [Writing a Dockerfile](https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/) guide really helped me start a basic boilerplate to start the containerization process.

#### Next Weeks Work

Now that I'm back in the swing of things and have a little less travel time, this week will be more about the nuts and bolts. Some of my plans include:

- Standing up the scripts to ingest .pdf, .docx, and .md documentation, there are some python libraries that should help me out here.
- Create or pull some test documentation for ChromaDB to ingest, it seems to have an embedding pipeline already built in so that's cool and I'll see what I can do with that!
- Research more about Cosine Similarity Comparisons, this is already starting to pop-up in my NLP and Linear Algebra courses and it seems like it will be a better method than pure Euclidean distance (more to come on this)
- Stand up a diagram of what this flow will look like with Mermaid.js. Usually this is my first step, but I dove right into the research and boilerplates this time instead, I want to contextualize visually the flow I'm trying to achieve for this application, and the digramming stage is always one of the most helpful for me.

#### Impediments

- Context Switching: I think switching between work, the classes I'm taking, and everyday life can be tricky sometimes and it takes me a while to get into a solid flow. I think that scheduling some time for "Deep Work" this week may help me. I'm going to time block my calendar so that I carve out time appropriately.
- Fine tuning my strategy for how I'm approaching this project, making sure that I'm listing out the process via my diagram, and utilizing Github Projects more. I started with that a little bit this past week, but project management is it's own discipline that takes effort.

#### Reflections

Selecting a Vector Database and understanding the tooling that I'll be using and how I need to connect it has been a huge relief. I think trying to build the perfect architecture leads me into decision fatigue. That can be debilitating, I'm getting better about how I make my technical decisions. Which is helpful to actual moving forward on a project. It's all about iterations, getting the basic understanding and working prototype and building from there. I think I'm becoming a lot more realistic (while also maintaining a healthy level of curiosity) with how I handle projects. 


--- 
### 2/12/2026

#### Last Weeks Work

This week I focused first on understanding the flow of data through this application. I think that my previous efforts were a little fragmented so I mapped out the flow of what will be happening through some research of a how traditional semantic search application would be handled.

I came to this diagram

{{< mermaid >}}
graph TD
subgraph Client_Side [User Interface Container]
UI[HTML/JS Frontend]
end

subgraph Backend_API [FastAPI Container]
API[FastAPI Router]
Ingestor["Ingestion Logic: PyMuPDF/Docx"]
Splitter[LangChain Splitter]
Embedder[Sentence-Transformers Model]
end

subgraph Storage_Layer [Vector Database Container]
DB[(ChromaDB)]
end

UI -->|"1. Upload File (POST /ingest)"| API
API --> Ingestor --> Splitter --> Embedder
Embedder -->|"2. Store Vectors and Metadata"| DB

UI -->|"3. Search Query (GET /search)"| API
API -->|"4. Embed Query"| Embedder
Embedder -->|"5. Semantic Comparison"| DB
DB -->|"6. Return Top-K Results"| API
API -->|"7. JSON Response"| UI
{{< /mermaid >}}

I utilized [Mermaid.js](https://mermaid.js.org/syntax/flowchart.html) which was extremely useful in constructing a graph inside of my Github documentation, I really enjoyed all the possible visualizations that you can create with this tool and I'll probably be utilizing it going forward.

Next what I tried to get working was my initial ingestion script. I found out that LangChain has a lot of interesting modules that help standardize the document ingestion process. So after reading the [PyMuPDF Documentation](https://pymupdf.readthedocs.io/en/latest/rag.html) that mentions their integration with LangChain I started to do a little bit more research. The Python libraries for docx and pymupdf are of course faster and native but I'm trying to create a portable application which it seems like LangChain is perfect for (I may learn a lesson here to the contrary but if that happens I will refactor my code after running some tests).

So then after realizing I wanted to utilize LangChain for ingestion, I then started reading about chunking and a solid strategy for that. I found this [phenomenal article](https://www.pinecone.io/learn/chunking-strategies/#:~:text=Recursive%20Character%20Level,sizes%20when%20possible.) on Pinecone's website describing different chunking strategies and why it's important for context windows. This helped me realize that the strategy that I probably wanted to go with is RecursiveCharacterTextSplitter, this method prioritizes first paragraphs, then sentences, then characters, it actually reminds me very much of the backoff algorithm for handling n-grams.

Additionally I found a solid sentence-transformer model that I wanted to utilize
[all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) the documentation is clear and straight-forward and it seems to be a model that could run on MOST machines without issue. So I prioritized this model.

Overall this was a bit more involved than I was expecting getting this ingestion script stood up, but I learned a TON about the process.

#### Next Weeks Work

Next week I really plan to fine tune this ingest.py script that I've stood up because nothing else matters if this doesn't work well. I think I realized that with this weeks work that I should first focus on the basic functionality of the application before jumping into how I'd like to connect it to a front-end and package it for portability. 

So I think I want to spend some more time working on the Ingest -> Chunk -> Embed -> Index workflow. 

Something that I really want to get locked down is the categorization of the ingested documentation in the vector database with the appropriate metadata.

So overall I think I'm going to shift towards focusing a bit more on the core app logic and understanding the flow of the data and it's performance before I start running tests and setting up the FastAPI routes fully. 

#### Impediments

I think the only impediments that I've been running into are not tracking the work I'm doing as closely as I'd like. It's very easy to get off track without a focused plan in place and I've neglected the Project Management side of the work a bit. So now that I have the diagram I'm probably going to setup some more issues to tackle in Github Projects so that I have a more defined path. I realized that at some point I got lost in the documentation between LangChain, Pinecone, and HuggingFace and I realized I was getting a bit overwhelmed.

So in short I'm going to scope out my tasks for the week more clearly in my Github Repo through Github Projects.

#### Reflections

This week was incredible in just how much I learned about all of the tooling and methods there are for Semantic Search, it was very cool to get to think about what I'm trying to build at a basic level and how to make that work locally on my computer before getting it ready to be pushed out to others. 

I think that this well is extremely deep and I even took a look at training my own classifier for text in the documentation on [Pytorch](https://docs.pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html) but that's a rabbit hole I may not fall into for the purpose of this project scope.

I've been getting more and more excited about this project as I've worked on it, I feel like I'm just scraping the surface. 


--- 
### 02/19/2026

#### Last Weeks Work
Last week I didn't get as much traction on this project because I got an ear infection (fun) but I tried to center around following course content around word embeddings in my NLP course it was helpful to learn some more content about cosine similarity comparisons for vector embeddings as that's going to be the primary method that I'm going to utilize with my ChromaDB implementation.

I did get a chance this week to get a working document ingestion -> chunking -> embedding -> indexing script working where it's able to take a local document path and embed that into a ChromaDB .sqlite3 file, it was interesting to learn that ChromaDB is using sqlite3 behind the scenes so I spent some time exploring how the data is stored in the ChromaDB tables. 

#### Next Weeks Work
Now that I've got the ingestion script working, the next step will be to write a query script to be able to ask natural language questions of the database. Once I'm able to get top-k results back in a query I think I'll be able to start fine tuning the ingestion and query script so that I can start working on the front-end and FastAPI connectors. 

#### Impediments
Getting over being sick! Seriously though I think the only impediment will be ensuring that I continue along the path, I front-loaded a lot of the research so I think that I know where I'm going with this, the only tricky part may be measuring the results, I'll have to see how I can measure the effectiveness of the ingestion and search.

#### Reflections
Weirdly being sick actually helped me focus on what was important, I asked myself what I wanted the end of the week to look like and to get a working ingestion flow where I was able to verify that a simple .md file was embedded into my chroma.sqlite3 was a huge win for me because now I've got a large part of the main functionality down, which is a huge relief for me. I think that getting the query script up now sounds exciting because it will snowball from there (not to jinx myself). Sometimes I can really get overwhelmed with what I think I should get done in a week, but with being sick and referencing my roadmap I think that really centered me this week.


---
### 02/26/2026

### Last Weeks Work
Last week I had a better time working forward with my project, I started to think about what the query script might look like. Before I could test out a query script I decided to start pulling in documentation in .docx, .pdf and .md format.

I was thinking about where I could find some solid documentation that was decently related so I decided to start pulling terms and conditions pages from different technology companies. I've heard many jokes that no one reads those anyway so I figured hey why not have a language model read them instead. So I found 6 different terms and conditions documents from apple, microsoft, google, github, meta, and proton and split them evenly between .docx, .pdf, and .md formatting.

After I had my documents, I realized how annoying it was to ingest them one by one so I altered my ingestion script to handle directories with an ingest_directory function in my ingest class.

Great! So ease-of-use improved and then I could start working on the query script, this was a little tricky because I didn't quite understand the [.query method](https://docs.trychroma.com/docs/querying-collections/query-and-get) of ChromaDB at first so I did some reading of documentation again this week, because ChromaDB has become the heart and soul of this project essentially. Go figure I could ask AI about what I was looking for in their documentation. Incredible! So after figuring out how to pass in query strings to ChromaDB I was able to test out the cosine simliarity results of a query looking for "Refunds" and I was able to get the top 2 results. It wasn't formatted, so it's not beautiful but check it out: 

```bash
((venv312) ) ianj in ~/Code/semantix/app on main ● λ python3 query.py
Enter your query: Refund policy 
Document: ['B. PAYMENTS, TAXES, AND REFUNDS', 'days old. We reserve the right to issue refunds or credits at our sole discretion. If we issue a refund or credit, we are under no obligation to issue\nthe same or similar refund in the future. This refund policy does not affect any statutory rights that may apply. For more refund information,\nplease visit our help topic (https://go.microsoft.com/fwlink/p/?linkid=618283).\ng. Canceling the Services. You may cancel a Service at any time, with or without cause. Cancelling paid Services stops future charges to continue\nthe Service. To cancel a Service and request a refund, if you are entitled to one, visit the Microsoft account management website. You can request\na refund from Skype using the Cancellation and Refund form (https://go.microsoft.com/fwlink/p/?linkid=618286). You should refer back to the\noffer describing the Services as (i) you may not receive a refund at the time of cancellation; (ii) you may be obligated to pay cancellation charges;']
Metadata: [{'chunk_index': 2, 'source': '/Users/ianj/Code/semantix/data/policies/Apple_Media_Services_Terms_and_Conditions.docx'}, {'source': '/Users/ianj/Code/semantix/data/policies/Microsoft_Services_Agreement.pdf', 'chunk_index': 46}]
```

SO wow voila we now have a working Semantic Search Engine, I'm so excited and happy to see that I was able to get this up and running. 


### This Weeks Work
This week it's going to be testing, and building out the end user interface. I'll be going through and writing some unit tests using pytest to try and measure expected outputs, once I've got some solid unit tests in place I'm going to start working on the user frontend, some basic html, css, and javascript should be easy enough to stand up for a small search bar and document upload button. I don't want to aim for more than that because I'm aiming at basic functionality currently. Once I've got those both working I think I'll be able to start moving on to connecting everything with FastAPI! I'm very excited I feel like my workflow has become a lot more clear.

### Impediments

I think my biggest impediment will be understanding how to measure the results that I'm getting returned, I want to measure precision and recall so I'll be working on how to measure those effictively from my queries, the unit test methods will probably just be for the code function and I'll have to come up with a more creative solution for measuring the model itself, as I think about this it starts to become one of the harder portions of this in my mind!

### Reflections

Getting the basic functionality working is a huge relief, but now comes the cleaning, tuning, connecting and measuring, which may actually be just as important as the functionality itself, because I want a consistent tool that doesn't produce unexpected behaviors. I'm starting to reflect on how I can now answer the question; so what? So what you can return results, how accurate and precise are they? How many errors does your code produce? I think I'm starting to really see the systems thinking for these models and it's reframing my general thought around natural language models in general.


---
### 03/12/2026

### Last Weeks Work
Last week I spent a considerable amount of time looking through [Pytest](docs.pytest.org) documentation. I had never used this tool before but everything that I read pointed me towards this for Python unit testing. After utilizing it, it makes perfect sense, but I spent a considerable amount of time wrapping my head around some of it's conventions.

conftest.py and fixtures for example. [This page](https://docs.pytest.org/en/stable/reference/fixtures.html#fixtures) was invaluable in the pytest documentation, it covered what fixtures are and what conftest files are useful for. In short conftest.py is a convention that pytest utilizes to make functions, class calls and fixtures avaiable across tests. This is super useful because it keeps everything very modular and you don't have to repeat yourself in every unit test file. 

Fixtures on the other hand were useful to me due to the fact that they create a temporary environment for each test. It's basically a way to stand up and tear down structures and memory without having to do that every single time by running your entire program. For me this was particularly useful because to actually test the functionality of my ingest.py and query.py scripts I would have had to create a new chromadb instance every single time, and to honest that can get messy. So instead the @pytest.fixture convention just basically calls those functions every time and cleans them up afterwards, very much reminiscient of memory managment in C++ but for folders, so that was a fun parallel!

Specifically the tests I wrote cover things like verifying that unsupported file types are rejected, that ingesting the same file twice doesn't create duplicates in ChromaDB, that metadata like the source file and chunk index are stored correctly, and that querying for something like "refund policy" actually returns text chunks containing information about refunds. Nothing too crazy but it gives me confidence that the core plumbing is working the way I expect it to.

I think another challenging piece this week was ensuring that I focused on getting the unit tests running and having an honest conversation with myself about the initial scope of the project. In my NLP class I've been really enjoying measuring the precision, recall and f-scores of models, but that's a way to measure the effectiveness of the model I'm utilizing and while that may be exciting I think to make sure that I've got a finished product I needed to focus on the unit tests first. The model that I'm utilizing from Hugging Face (sentence-transformers/all-MiniLM-L6-v2) can be something that I measure after I've got everything working, because right now I'm building the harness and functionality. I can assess effectiveness once I've accomplished all my goals. So I went with some basic unit tests to ensure that I'm getting expected return text chunks that I know are in the test data and not necessarily measuring against other documentation just yet. 

Overall I'm really happy with how much I learned about the pytest unit testing framework this week, and pending model performance I have a working prototype at the very least.

### This Weeks Work

This week I'll be really focused on building the UI for the Semantic Search Engine and wiring everything together with FastAPI. Once that's complete I'll be ready to build some more tests for model performance and to dockerize the application. I feel like I'm nearing the point where I can focus more on fine tuning than on learning the stack that will go into the application. I feel like I'm in a relatively decent place. 

### Impediments
This is the first week that I don't forsee any major impediments I don't know if I should be worried about that or not, but I feel pretty confident about the UI and FastAPI, probably because I'm more familiar with those than other tools I've worked with this semester for this project.

### Reflections
I think it was really interseting going through the pytest documentation and learning all of the different conventions utilized for this unit testing framework, I think I also didn't realize how involved the whole process would be to test the application, so that lead me to stopping a little short of everything I actually wanted to measure, I guess that's the beauty of the process of a project like this, I'm thinking of all of the ways that I could improve this past this class, because it really has become something I've loved to work on, especially with everything that I've learned!

