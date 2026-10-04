<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=200&section=header&text=Eyad%20Amr%20Asaad&fontSize=44&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Computer%20Engineering%20%C2%B7%20AI%20%C2%B7%20Software%20Engineering&descAlignY=58&descSize=16" alt="Eyad Amr Asaad banner" />

<a href="https://github.com/Eydo99">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=20&pause=1200&color=36BCF7&center=true&vCenter=true&width=700&lines=I+train+models+that+predict+football+matches;I+build+real-time+multi-threaded+systems;I+write+shells%2C+schedulers+and+distributed+locks;Computer+Engineering+%40+Alexandria+University" alt="Typing animation" />
</a>

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/eyad-amr-1210ea)
[![Email](https://img.shields.io/badge/Email-eyadamr1644%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:eyadamr1644@gmail.com)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-AI%20Football%20Analyst-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://ai-football-match-analyst.streamlit.app/)

</div>

---

## 👋 About me

I'm a Computer Engineering student at Alexandria University who likes building things that have to actually work: ML pipelines that serves different fields, simulators, and shells and schedulers written in C.

I move between both ends of the stack, from training XGBoost models to hunting race conditions, and the most fun problems are where the two meet.

- 🎓 **B.Sc. Computer Engineering** · Alexandria University · 2023 – 2028
- 🤖 **Built and deployed** an xG model on 1.2M football events, with a [live demo](https://ai-football-match-analyst.streamlit.app/)
- ⚙️ **Wrote from scratch:** a Unix shell, a CPU scheduler, and a Redis-based distributed lock
- 🥉 **3rd place, MATE ROV International:** designed the ROV's power distribution board and the main control board of the team's underwater float (Alexandria University Robotics Club)
- 📫 **Open to internships** in AI/ML and software engineering

---

## 🌟 Featured projects

### ⚽ [AI Football Match Analyst](https://github.com/Eydo99/AI-Football-Match-Analyst) &nbsp;·&nbsp; [**Live demo →**](https://ai-football-match-analyst.streamlit.app/)

An end-to-end **expected goals (xG)** pipeline on StatsBomb open data, served through a live Streamlit app that scores matches the models have never seen.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-EC6B23?style=flat-square)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

| 🎯 xG model | 🧮 Event classifier | 🏟️ Match prediction | 📊 Data |
|:---:|:---:|:---:|:---:|
| **0.920** ROC AUC | **94.0%** accuracy | **70.2%** over 1,003 matches | **1.2M** events |

<details>
<summary><b>How it works (click to expand)</b></summary>

```mermaid
flowchart LR
    A[StatsBomb events] --> B[Cleaning + feature engineering]
    B --> C[XGBoost xG model]
    B --> D[Event-type classifier]
    D -->|finds the shots in unseen matches| C
    C --> E[Sum xG per team]
    E --> F[Win / draw prediction]
    F --> G[Streamlit app]
```

- Modular transformer-based pipeline: location splitting, imputation, distance and angle to goal, nearest defender, defenders within 3 m, ball speed.
- A second classifier recovers which events are shots on new matches, because the real `type` column would leak the answer.
- The app only lists competitions and seasons that were **not** used in training.

</details>

---

### 🏭 [SimBuilder — Real-Time Production Line Simulator](https://github.com/Eydo99/Production-Line-Simulator)

Design a factory out of queues and machines, press Start, and watch products flow through **one Java thread per machine**, live in the browser.

![Java](https://img.shields.io/badge/Java%2017-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket%20%2F%20STOMP-010101?style=flat-square&logo=socketdotio&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![RxJS](https://img.shields.io/badge/RxJS-B7178C?style=flat-square&logo=reactivex&logoColor=white)

<details>
<summary><b>Architecture and highlights (click to expand)</b></summary>

```mermaid
flowchart LR
    UI[Angular canvas] -- REST commands --> API[Spring Boot services]
    API --> T[Machine threads + generator thread]
    T --> Q[(Thread-safe queues)]
    T -- state events --> B[STOMP broker]
    B -- WebSocket --> UI
    API -. snapshot on stop .-> M[Memento: topology + random seed]
    M -. replay identical run .-> T
```

- **Observer pattern** pushes every queue and machine change to the UI over WebSocket/STOMP.
- **Memento pattern** stores the topology and random seed so a run can be replayed exactly.
- **8 pre-flight rules** catch isolated nodes, dead ends and cycles before any thread starts.

</details>

---

### 📬 [Mail Project — Full-Stack Email Client](https://github.com/Eydo99/Mail-Project)

A Gmail-style mail system: **66 Java files**, **22 Angular components**, per-user JSON storage.

![Java](https://img.shields.io/badge/Java%2017-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

Design patterns in action: **Strategy** (8 sort orders), **Chain of Responsibility** (9 combinable filters), **Factory**, and **Command** (undo/redo for profile edits).

---

### 🧠 [Smart Advisor — AI Course Recommender](https://github.com/nelatawy/Course-Recommender)

Two interchangeable engines behind one **Strategy Pattern** interface: a **Prolog** logic engine for hard constraints (prerequisites, eligibility) and a **Google Gemini** engine for preference-based ranking, served through a REST API to a React Native app.

![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![React Native](https://img.shields.io/badge/React%20Native-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Prolog](https://img.shields.io/badge/Prolog-E61B23?style=flat-square)
![Gemini](https://img.shields.io/badge/Gemini%20API-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)

---

### 🔀 [SFGLab — Signal Flow Graph Analyzer](https://github.com/Joo-Ashraf1/Control-Systems-SFG)

Draw a signal flow graph in the browser and get every forward path, loop, non-touching loop combination and the simplified symbolic transfer function using **Mason's gain rule**. **26 pytest cases.**

![Angular](https://img.shields.io/badge/Angular%2021-DD0031?style=flat-square&logo=angular&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![SymPy](https://img.shields.io/badge/SymPy-3B5526?style=flat-square&logo=sympy&logoColor=white)

---

### ⚙️ [OS Labs — Concurrency & Distributed Systems](https://github.com/Eydo99/OS_-Labs)

![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

- A **Unix shell** with background jobs and zombie reaping
- **Multithreaded matrix multiplication** with three threading strategies
- **Caltrain synchronizer** (mutexes + condition variables), stress-tested over 1,000 runs
- **CPU scheduler simulation** (FCFS, Round Robin, HPF) using POSIX message queues and signals
- **Redlock distributed mutex** across 5 Dockerized Redis nodes with quorum and atomic Lua release

---

### 🌳 [Algorithms & Data Structures Benchmarking](https://github.com/Eydo99/DSA-Projects)

Red-Black Tree vs BST, six sorting algorithms (with a JavaFX visualizer), and Prim / Kruskal / Dijkstra / DAG shortest path, all built from scratch with **70 JUnit tests** and seeded, JIT-warmed benchmarks.

> On nearly-sorted input, a plain BST reached a height of **3,145** while the Red-Black Tree stayed at **30**, and inserted up to ~20x faster.

---

<details>
<summary><b>🧰 More projects (click to expand)</b></summary>

<br/>

| Project | Stack | What it is |
|---|---|---|
| [Paint Studio](https://github.com/Eydo99/Paint-Project) | Java · Spring Boot · Angular · Konva | Vector drawing editor with 8 shape types and **server-side undo/redo** using the Command pattern, plus JSON/XML export |
| [OR Projects](https://github.com/Eydo99/OR-Projects) | Python · NumPy · Pandas | Gradient descent and Newton's method **from scratch** on a housing dataset, compared over 1,000+ iterations |
| [Numerical Methods Solver](https://github.com/Eydo99/Numerical-Project) | Python · Flask · Angular 18 | 14 methods for linear systems and root finding, with step-by-step playback, plotting and error analysis |

</details>

---

## 🛠️ Tech stack

<div align="center">

<img src="https://skillicons.dev/icons?i=py,java,c,cpp,ts,js&perline=6" alt="Languages" /><br/>
<img src="https://skillicons.dev/icons?i=spring,angular,flask,django,react,tailwind&perline=6" alt="Frameworks" /><br/>
<img src="https://skillicons.dev/icons?i=pandas,numpy,docker,redis,postgres,sqlite&perline=6" alt="Data and infrastructure" /><br/>
<img src="https://skillicons.dev/icons?i=git,linux,aws,maven,latex,arduino&perline=6" alt="Tools" />

</div>

| | |
|---|---|
| **🤖 AI / ML** | NumPy · Pandas · Matplotlib · Seaborn · scikit-learn · XGBoost · feature engineering · Gemini API · prompt engineering |
| **📚 ML methods** | Linear / logistic regression · decision trees · ensembles · SVM · KNN · Naive Bayes · K-Means · DBSCAN · gradient descent |
| **🌐 Backend & web** | Spring Boot · REST APIs · WebSocket / STOMP · Flask · Django · Angular · RxJS · Streamlit |
| **⚙️ Systems** | POSIX threads · mutexes & condition variables · IPC · signals · Linux · Docker · Redis |
| **🧱 Engineering** | OOP · design patterns (Strategy, Command, Observer, Memento, Factory, Chain of Responsibility) · data structures & algorithms · JUnit · pytest |
| **🔌 Hardware** | PCB design and fabrication · Arduino |

---

## 🎓 Learning & certifications

| | |
|---|---|
| 🤖 [NTI Machine Learning Summer Training](https://drive.google.com/file/d/1Az8QV0r8SDSIXWStuiR2JJ33kCE46yUg/view?usp=sharing) | Python data stack, supervised and unsupervised learning, feature selection and extraction |
| 📘 [Machine Learning — Andrew Ng](https://coursera.org/share/e6f69593c286955a3918a4d81dbb0060) | Coursera / DeepLearning.AI |
| ☁️ [AWS Cloud Foundations](https://www.credly.com/badges/aa234186-426c-400c-a06f-bdcef1134ca1/public_url) | Credly badge |
| ☁️ [AWS Cloud Architecting](https://www.credly.com/badges/3e9231b5-4394-42e8-a4f7-c3086a8611d4/public_url) | Credly badge |
| 🥉 [MATE ROV International — 3rd place](https://drive.google.com/file/d/1Qj9hFOlLR7PCRcQSb9HTkm6BjbOvvveW/view?usp=sharing) | Certificate |

---

## 📈 GitHub stats

<div align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=Eydo99&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" alt="GitHub stats" />
<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Eydo99&layout=compact&theme=tokyonight&hide_border=true" alt="Top languages" />

</div>

---

## 🤝 Let's connect

Got an interesting problem in ML, concurrency, or robotics? Let's talk. I'm open to **internships in AI/ML and software engineering**.

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/eyad-amr-1210ea)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:eyadamr1644@gmail.com)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=100&section=footer" alt="footer" />

</div>
