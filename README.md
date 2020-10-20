# Full Stack API Final Project

## Full Stack Trivia

Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a  webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out. 

That's where you come in! Help them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application must:

1) Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer. 
2) Delete questions.
3) Add questions and require that they include question and answer text.
4) Search for questions based on a text query string.
5) Play the quiz game, randomizing either all questions or within a specific category. 

Completing this trivia app will give you the ability to structure plan, implement, and test an API - skills essential for enabling your future applications to communicate with others. 

## Getting Started

### Installing Dependencies

Python3, pip (Package installer for Python) , node.js, and npm (Node Package Manager) should be installed before running the project.

#### Frontend Dependencies

Inside the project's terminal run the following command:
```
npm install
```
### Backend Dependencies

You need to open the /backend directory and run the following command:
```
pip install -r requirements.txt
```
Run this command to start the front-end:
```
npm start
```

Open the browser and open the website using a localhost with the port 3000,  http://localhost:3000.

To run the server, execute:
```
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
Testing
```
Then execute the tests:
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
Don't use `dropdb` command the first time you run your tests.
