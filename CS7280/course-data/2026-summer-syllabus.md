# CS 7280 — Network Science: Course Policies and Schedule

It is often the case that *complex systems*, both living and man-made, can be represented as static or dynamic *networks* of many interacting components. These components are typically much simpler in terms of behavior or function than the overall system, implying that the additional complexity of the latter is an *emergent network property*.

Network science is a relatively new discipline that investigates the topology and dynamics of such complex networks, aiming to better understand the behavior, function, and properties of the underlying systems.

The applications of network science cover physical, informational, biological, cognitive, and social systems.

In this course, we will study algorithmic, computational, and statistical methods of network science, as well as various applications in social, communication, and biological networks.

A significant component of the course will focus on the overlap between statistics, machine learning and network science, covering methods for network inference, generative network models, embeddings using deep neural networks, and other state of the art topics.

## Learning Objectives

Students will:

- Understand what *"network science"* means, how it relates to other disciplines (graph theory, data mining, machine learning, etc), and how it is useful in practice.
- Learn how to detect, quantify and interpret important properties of real networks, such as power-law degree distribution, "small world" efficiency and clustering, assortativity, hierarchy, modularity, and others.
- Learn how to identify the most important nodes and links in a network through network centrality metrics and core identification algorithms.
- Design and analyze algorithms that compute "communities" of highly clustered nodes, and learn how to compare such algorithms.
- Appreciate the value of network modeling, and learn several approaches to model a static or dynamic network.
- Understand the "network inference" problem and learn statistical and machine learning methods that estimate a network from noisy data.
- Understand how representation learning *(and deep learning in particular)* is applied to network science.
- Learn how to model and predict network epidemics, influence, cascades, and other *"spreading"* phenomena.
- Understand how the structure (topology) of a network affects the function and dynamic activity on that network.
- Become familiar with several state-of-the-art research directions in network science.

## Prerequisites

Some knowledge (at the level of a good undergrad course) of calculus, probability, linear algebra, and Python programming is necessary.

Please take the Prerequisites Quiz to check your background. It is ok if you do not answer all questions correctly — but in that case, do you understand the correct answer?

The course hopes to attract students from different academic backgrounds and research interests (including math, physics, engineering, biology, neuroscience or sociology). Consequently, the instructor tries to keep the course as "self-contained" as possible.

## Assessment

Your understanding of the material for this course will be evaluated via the following assessment instruments, at the specified weighting:

| Assessment Type | Quantity | Final Grade Weight |
| --- | --- | --- |
| Assignments | 5 | 65% |
| Quizzes | 14 | 35% |

The final grade will be determined based on your final weighted grade average (no "curving"), with your lowest quiz and assignment dropped from the calculation, and the percentage being rounded to the nearest integer:

| Final Percentage | Letter Grade |
| --- | --- |
| 90 – 100% | A |
| 80 – 89% | B |
| 70 – 79% | C |
| 60 – 69% | D |
| 0 – 59% | F |

### Quizzes

Quizzes will be released on a weekly cadence, with each quiz corresponding to material in the same lesson (Quiz 1 covers material in Lesson 1, Quiz 2 to Lesson 2, etc.). For the Summer semester there will be one or two quizzes each week. You are free to use your notes and lecture material to help with the quizzes, but you may not share answers with other students, or use other services to solve questions for you. The GT Honor Code fully applies to quizzes. You may start the quiz and return to it at any time until the due date as long as you don't submit the quiz (once submitted there is no going back). Canvas will automatically submit in-progress quizzes for you at the deadline with whatever answers you have most recently saved (there is currently an issue where leaving your quiz in-progress without submitting will flag it on Canvas as "missing"; if this occurs, we will manually clear it within a day or two).

### Projects

Assignments will be released for each course Module. They will be provided as a zip file with a Jupyter Notebook `.ipynb` file, a requirements file listing the packages and their required versions, and any associated data you will need to complete the assignment. Directions for how to load and run the assignment will be provided on the Assignment page on Canvas. You will submit your assignments on Gradescope.

## Course Policies

**You cannot take this course for *"Audit"*. Doing the assignments is essential.**

**All work for this class is to be done individually. Private study groups (such as those on Discord, Slack, WhatsApp, WeChat, etc) are strictly prohibited.** You are strongly urged to familiarize yourself with the [GT Student Honor Code](https://policylibrary.gatech.edu/student-life/academic-honor-code) rules. Specifically, the following is not allowed:

- Copying, with or without modification, someone else's work when this work is not meant to be publicly accessible *(e.g., a classmate's program or solution.* **This includes copying substantial code or answers from AI tools and software such as LLM's like ChatGPT, Claude, or Gemini***)*.
- Submission of material that is wholly or substantially identical to that created or published by another person or persons, without adequate credit notations indicating authorship *(plagiarism)*.
- Putting your projects on public Github. If a student *(in the future)* copies your codes/projects, the student obviously violates the honor code but you will also be implicated.

You are encouraged to discuss problems and papers with others as long as this does not involve copying of code or solutions. Any public material that you use *(open-source software, help from a text, etc...)* should be acknowledged explicitly in anything you submit to us. If you have any doubt about whether something is legal or not please do check with the class Instructor and the Head TA. We will be monitoring submissions for plagiarism, and will submit suspicious cases to the Office of Student Integrity.

### Discussion Forum

Most communication for this course will take place on the Ed Discussion forum. There will be pinned discussion threads corresponding to the week's material where you can discuss the course material with your fellow students and ask for clarifications and help. Each assignment section has a corresponding discussion thread and assigned TA. The TA team will moderate the discussion forum and will do their best to answer any questions that your fellow students are not able to answer.

Discussion guidelines:

- Never share code, plots, or answers with anyone else.
- General approaches and links to helpful documentation may be shared.
- Ask questions on the official thread so the entire class benefits.
- Private posts (visible only to staff) should be limited to specific questions — not to confirm solutions or review full implementations.
- Plagiarism is reported to the Office of Student Integrity every semester. Do your own work and cite the documentation you use.

### Discussion Conduct

Students are expected to conduct themselves in a professional manner in line with Georgia Tech's Code of Conduct. The staff reserves the right to not engage with students who fail to act in accordance with this conduct by communicating in a manner that is considered rude, hostile, or demeaning, and may forward such communication to the Dean of Students.

## Late Submissions and Extensions

Every project assignment will have a **Due Date** and an **Availability Date/Late Due Date** which are viewable on the Assignments page on Canvas. If for whatever reason you cannot submit the assignment before the Due Date, you will have a period of 3 days where you may still submit the assignment with a deduction for each day. Any assignment submitted after the Due Date will be given a penalty with the following deductions, with the first day starting 1 minute after the Due Date:

- **First day after the Due Date:** 20-point deduction
- **Second day after the Due Date:** 35-point deduction
- **Third day after the Due Date:** 50-point deduction

*These deductions will never bring your assignment below a score of 0.*

After the third day, we will no longer accept your assignment, and you will receive a 0.

If you run into a particular technical issue that blocks you from turning in your assignment within the period of the original Due Date (such as Canvas or Gradescope going down during the submission period) please use the following procedure:

1. Email the Head TA **with the current version of your assignment attached to the email, not in a DropBox or Sharepoint link or any other external platform**.
2. In the email, provide documentation of the error or technical issue you are seeing.
3. If the issue resolves itself, continue to submit as normal up until the Availability Date ends.

After the Availability Date ends, extended deadlines for assignments will only be granted for sudden health issues. To request an extension, follow the below procedure:

1. Email the Head TA as soon as this occurs, with the current version of your completed work attached to the email.
2. Provide a description of the days you were ill and unable to work on the assignment (not prescription lists, hospital bills, or detailed descriptions of your medical procedures).
3. Submit a [Class Absence Verification Form](https://cm.maxient.com/reportingform.php?GeorgiaTech=&layout_id=5) with the Office of Student Life.
4. If any further extension is granted, email the assignment to the Head TA in the same email thread as your request by the agreed upon new deadline.
5. Failure to follow these steps in a timely manner may result in denial of your request.

**Please note that any extension offered is at the discretion of the course staff, and will be dated from the original deadline, not the date at which the staff responds to your request. We reserve the right to deny your request.**

## Regrades

Errors may sometimes occur when your assignments are graded. To request a re-grade on your assignment, we will provide a link to a Microsoft Form on Ed Discussion where you will submit a request on each section that you believe was incorrectly scored.

Note that you may only request a regrade for a specific issue with the grading on your assignment (for example, the deduction suggests that Gradescope ran into a runtime issue). **You may not request a regrade simply because you believe that your score was too low, or that a penalty was too harsh.**

## Topic Outline

**Lesson One: What is Network Science?**

- What is (not) network science?
- The main premise of network science
- History and relation to graph theory, physics, sociology, and other disciplines
- Examples of networks from different application domains

**Lesson Two: Relevant Concepts From Graph Theory**

- Undirected, directed, signed, weighted and spatial networks
- Paths, connected components, random walks, etc
- Directed Acyclic Graphs
- Bipartite graphs
- Max-flow/min-cut

**Lesson Three: Degree Distribution and ER Graphs**

- Degree distribution
- Friendship paradox
- ER graphs and their degree distribution
- Giant component size in ER graphs
- Assortative vs disassortative networks

**Lesson Four: Random vs. Real Graphs and "Scale Free" Networks**

- The degree distribution of real-world networks
- Power-law degree distributions
- Preferential attachment model
- How to detect a power-law and estimate the exponent
- Configuration model and degree-preserving randomization

**Lesson Five: Network Paths, Clustering and The "Small World" Property**

- Clustering and transitivity in networks
- Diameter and characteristic path length
- Small-world networks and the Watts-Strogatz model
- Network motifs

**Lesson Six: Centrality and Network-core Metrics and Algorithms**

- Link-based centrality metrics
- Path-based centrality metrics
- k-core decomposition
- Core-periphery structure
- Rich-club set of nodes

**Lesson Seven: Community Detection and Hierarchical Modularity**

- Hierarchical clustering in networks
- Modularity metric
- Algorithms for modularity maximization
- Limitations of modularity
- Hierarchical modularity

**Lesson Eight: Advanced Topics in Community Detection**

- Overlapping communities
- Dynamic communities
- Comparing community structures
- The role of nodes within and between communities
- Applications of community detection

**Lesson Nine: Network Contagion and Epidemics**

- Epidemics on networks
- Epidemic modeling (SI, SIS, SIR, etc) under homogeneous mixing
- Epidemic modeling under arbitrary degree distributions
- Basic reproductive number and superspreaders

**Lesson Ten: Influence Phenomena On Networks**

- The linear threshold model and the Independent cascades model
- Empirical studies in information and behavior spreading
- Seeding strategies on how to maximize influence
- Cascades and community structure

**Lesson Eleven: Other Dynamic Processes Of/On Networks**

- Percolation, random failures, and targeted attacks on networks
- Search on networks
- Synchronization on networks
- Coevolutionary networks

**Lesson Twelve: Models of Static and Dynamic Networks**

- Stochastic network models that generate power-law degree distributions
- Optimization-based network models
- Stochastic block models
- Hierarchical Random Graphs

**Lesson Thirteen: Statistical Analysis of Network Data**

- Network sampling methods
- Estimation of network metrics
- Association networks
- Network tomography

**Lesson Fourteen: Machine Learning meets Network Science**

- Node embeddings
- Graph neural networks
- Deep generative network models
- Limitations and applications of graph neural networks

## Course Schedule (Summer 2026)

Deliverable due dates (all times Eastern; quizzes and assignments are due by 7:00 AM on the listed date):

| Due Date | Deliverable |
| --- | --- |
| Wed, 27 May 2026 | Quiz 1 (Lesson 1) |
| Mon, 1 Jun 2026 | Quiz 2 (Lesson 2) |
| Mon, 8 Jun 2026 | Assignment 1 · Quiz 3 (Lesson 3) |
| Mon, 15 Jun 2026 | Quiz 4 (Lesson 4) · Quiz 5 (Lesson 5) |
| Mon, 22 Jun 2026 | Assignment 2 · Quiz 6 (Lesson 6) |
| Mon, 29 Jun 2026 | Quiz 7 (Lesson 7) · Quiz 8 (Lesson 8) |
| Mon, 6 Jul 2026 | Assignment 3 · Quiz 9 (Lesson 9) |
| Mon, 13 Jul 2026 | Quiz 10 (Lesson 10) · Quiz 11 (Lesson 11) |
| Mon, 20 Jul 2026 | Assignment 4 · Quiz 12 (Lesson 12) |
| Mon, 27 Jul 2026 | Quiz 13 (Lesson 13) · Quiz 14 (Lesson 14) |
| Mon, 3 Aug 2026 | Assignment 5 |

Onboarding items (no fixed weekly slot): Step 5 — ID Verification Onboarding Quiz; Step 6 — Prerequisites Quiz. Per-lesson Knowledge Checks (L1–L14) are also available on Canvas.

### Recurring Office Hours

| Day | Time (Eastern) | Host |
| --- | --- | --- |
| Monday | 7:00 – 8:00 | Sravani |
| Tuesday | 18:00 – 19:00 | Kirill |
| Wednesday | 8:00 – 9:00 | Vivian |
| Wednesday | 13:00 – 14:00 | Aayush |
| Thursday | 21:00 – 22:00 | Jason |

*Office hours run weekly through the semester (late May through late August 2026); confirm exact dates and any cancellations on the Canvas calendar.*

## Course FAQ

*Source: Ed Discussion post by Jason Cox (Head TA), pinned in General. These items supplement the official policies above.*

### Administrative Questions and Extensions

Email the Head TA, Jason Cox, at jcox90@gatech.edu (verify the recipient — multiple people share the name at Georgia Tech). Course content questions should go to the discussion threads.

### Grade Curving

The decision is made by Professor Dovrolis at the end of the semester. All grade calculations should assume strict adherence to the grading scheme listed above (no curving).

### Assignment Answer Keys

Detailed answers to assignments are not released. Questions about deductions not explained by grading comments may be directed to the TA for that section via office hours or email.

### Early Access to Quizzes/Assignments

No special exemptions are made outside what is usually covered by the university. Quizzes and assignments are released on the cadence listed on Canvas.

### Autograder / Gradescope

The course uses Gradescope. Unlimited submissions are allowed before the deadline, but detailed scores are not released until after grading.

### Code Reuse and Citation

Code from previous work (academic or non-academic) may be reused — check with the Instructor and/or Head TA if uncertain. Over-attribute rather than under-attribute to protect against plagiarism flagging.

### Google Colab

Google Colab may be used for assignments. Ensure Jupyter notebooks are formatted so they can be run locally by the grading team.

### Graph Neural Networks (GNNs)

GNNs are covered in Module 14 and appear on quiz material, but are not the primary focus of the course. Assignment 5 (which includes Module 14 content) may or may not include limited GNN material.

### Downloading Lectures

No known method for downloading lectures from Canvas. Unofficial external resources hosting lecture material are not monitored by staff and their accuracy cannot be verified.

### Textbook

Primary textbook: Barabási, *Network Science* — available free online at [networksciencebook.com](http://networksciencebook.com/). Check the [errata page](http://networksciencebook.com/translations/en/resources/NetworkScienceErrata.pdf) before reading each chapter.
