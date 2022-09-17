<h1 align='center'>🍿 A Scrum Course Project: qBay 🍿</h1>

<p align='center'>CISC 327  -  Fall 2021</p>


## 💺 Project Teams and Process

You have formed a team of four (preferably four) people to design, implement, document, and deliver a two-part software product.  
All phases should follow the scrum software development process as much as it applies with some XP practices - in particular, 

- continuously maintained test suites as requirements and quality control
- pair programming
- code review of all code
- a simplest possible solution to every problem
- continuous redesign and rearchitecting
- automation in testing and integration
- **All the code/documentation contributions will go through the pull-request/review process**

Every 1–2 weeks, you will deliver a sprint of your team’s efforts as required by project assignments.


## 💺 Project Phases

The project will be done in several phases, each of which will be an assignment. 
Phases will cover steps in the process of creating a quality software result in the context of a scrum software development process model.
Each phase of the project corresponds to a single sprint in the Scrum software development process.
Assignments will be on the quality control aspects of requirements, rapid prototyping, design, coding, integration, and analysis of the building's product. 
Your final products will be tested and evaluated by an independent evaluator or an automated system.

## 💺 Getting Start

1. [***Important***] One elected team member, preferably the most experienced one, acts as a Scrum master. 

2. [***Important***] The Scrum master, after negotiating with the team, select a style guide for the programming language in the project. (e.g. PEP 8 for python). If any new languages are added to the project later on, such as HTML later for the front-end, the scrum master has to add a new style guide for that language.  

3. [***Important***] The scrum master follows this [guide](https://docs.github.com/en/free-pro-team@latest/github/building-a-strong-community/creating-a-pull-request-template-for-your-repository) to create a pull request template agreed upon by the team members. 
[Example](https://embeddedartistry.com/blog/2017/08/04/a-github-pull-request-template-for-your-projects/) of a PR template. Starting from this point of the assignments, all the PRs have to follow the agreed template. This template should be used in each PR.
The template must include the selected style guides in the checklist. 


## 💺 Step 1 Project Requirement

The product you are to design and build is qB&B, similar to airB&b, for C2C vacation house/appartment rentals. The instructor and the TAs will be your customers.
The customers have decided that:

- A registered user can create listing and book listing through this online application. Each listing represents a property.
- A transaction represents a successful booking of the property (the listing).
- A verified guest to the listing (the property) can also leave a product review. 
- User payment is directly through their balance on the online application.
- A user can add money to their account through online banking (transfer directly from their own banking account).

For this sprint, the development team (you) decided to first define data models based on the application concept above,
in which the entity types in the system are specified; so the customer (us) can check if these entities have enough attributes to reflect the required information per entity.

- At the moment, the customers do not have any ideas about the constraints (e.g. password complexity, username constraint, possible attributes) of the entities. 
So feel free to include anything. Then, the customer will discuss it and provide you further requirements changes and constraints in the next sprint.

The tasks for this sprint:

- Identify the entities of the application (hint: in total at least 4, can be more depending on your design).
- Create cards (backlog) on your scrum board for this sprint to implement the entities. One card for one feature/part to be implemented by one team member.
- Assign team members and reviewers for each card (task). The assignee then moves them to todo.
- Implement the data models following the python example below. All the code must have detailed comments. All the models can be in a single file.
- PR, Review, and Merge the PR.
- Testing: all the code follow the selected coding guideline. (for example, [pep8 for python](https://flake8.pycqa.org/en/latest/))
- Sprint review: review each card and each PRs, ensuring that they didn't violate any of the rules defined below. Create a tag for A1 and submit through onQ.


```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

// setting up SQLAlchemy and data models so we can map data models into database tables
app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///db.sqlite'
db = SQLAlchemy(app)


class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)

    def __repr__(self):
        return '<User %r>' % self.username

```

If you want to use a different programming language or framework. You have to make sure every one in the team:

 - follow a style guideline for the selected programing language, know how to automatically check if the code follow with the style guide (e.g. eslint for JavaScript)
 - know how to do automated deployment (later on testing will be done in CI rather than running locally; so you will need to automatically deploy a database if you know how to do it with the other language)
 - know how to do automated unit testing and front-end testing in your chosen language (selenium-based web testing or CLI input/output-based testing)

Even though we are using python for the moment. Later for the front end options are CLI, Template-based web, or RESTful+React. Then dockerized everything plus docker-compose.


### ✈️ Step 2 - Planning Meeting

This sprint is then kicked off by a planning meeting, where the scrum master and the team members sit down, 
- Team members are supposed to have read through this document for the assignment before the meeting.
- Create a new scrum board for this sprint (i.e. assignment 1) through the GitHub Projects tab of your repository.
- Create columns (the detailed version but not the simple version).
- Put cards on the backlog, assuming we have at least four entities/models so at least 4 cards.
- Assign members and reviewers to the cards. Each PR requires at least 2 reviewers, and each member has to do at least two reviews.
- Assignees move the cards to the todo column.
- Initial design: team members design the file structure of the project (if you will be following our python-based process, you can put all into a single python file)

### 🚀 Step 3 - Daily-Scrum (Dev+Test)

- The team members start implementing on their own branch.
- Testing: all the code follow the selected coding guideline. (for example, [pep8 for python](https://flake8.pycqa.org/en/latest/))
- Daily standup meeting: skipped for this assignment. 


### ✅ Step 4 - Review/Approve
Once a card is done with the implementation, you can proceed to PR, request review, and seek approval for merge. 


### 📝 Step 5 - Review & Retrospect
Review your PRs again, create tag, and make a submission through onQ.  


## 💺 Rules

All the assignments, starting from this point, will follow these rules:

- No file changes/uploads through the web interface. We can tell.
- No direct change to the master/main branch of your repository. 
- All the changes to the repository have to go through Pull Request (PR).
- All the PRs require reviews and approval before merging. 
- Each PR requires at least 2 reviewers, and each member has to do at least two reviews.
- All the reviews must provide at least one comment (constructive & specific) for improvement. 
- All the team members must have at least a PR for each assignment (sprint).
- All the project activities have to be planned through the scrum board before coding and testing.
- All the cards for each sprint have to go through each column of your team's scrum board (cannot just directly jump from todo to done).
- All the PRs should be associated with at least one card in your scrum board (by mentioning the PR number using `#` in the card)
- All the PRs should follow the agreed PR template.
- All the documentation has to follow the [markdown format](https://guides.github.com/features/mastering-markdown/).
- All the merged code must follow the selected coding style guide. 
- Each of the PR's titles should have emojis. 


Violation of any of the above rules (except the last one about emoji) will result in a grade penalty.
All the team members, through the principle of collective ownership, must ensure other team member's PR/code does not violate any of the rules above.
For any violations that can be tracked down, a penalty will apply for both the reviewers and the related contributors. 

## 💺 Grading:

- Scrum practices (max 2 for the deduction, .25 for each violation, maximum number of violations before deduction 4)
- PR and git practices, including code review (max 3 for the deduction, .25 for each violation, maximum number of violations before deduction 4)
- Code style compliance (max 3 for the deduction, .1 for each style error, maximum number of violations before deduction 2)
- Documentation and comments -** each file/class/method/attribute** should have comments. (max 1 for deduction, .1 for each violation)
- Completeness of the data models covering all the above customer requirements (max 1 for the deduction, missing one required entity minus .25)

