# Full Stack API Final Project

## Full Stack Trivia
It is a RESTFUL API application that allow users to do the following:
1) Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer. 
2) Delete questions.
3) Add questions and require that they include question and answer text.
4) Search for questions based on a text query string.
5) Play the quiz game, randomizing either all questions or within a specific category. 

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
Then execute the test suite:
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
Don't use `dropdb` command the first time you run your tests.

## API Reference

### API endpoints  
This part will show the system's endpoints Url including:
- Request parameters
- Response body
---

- GET /categories  

General:   

 * Returns all of the categories in json format and a success flag.  
 
Sample: `curl http://127.0.0.1:5000/categories`
```
  {
      "categories": {
          "1": "Science", 
          "2": "Art", 
          "3": "Geography", 
          "4": "History", 
          "5": "Entertainment", 
          "6": "Sports"
      }, 
      "success": true
  }
```

- GET /questions  

General:  
* Returns a list questions in json format paginated in groups of 10. Also returns the categories, the total number of questions and a success flag.  

Sample: `curl http://127.0.0.1:5000/questions`
```
  {
      "categories": {
          "1": "Science", 
          "2": "Art", 
          "3": "Geography", 
          "4": "History", 
          "5": "Entertainment", 
          "6": "Sports"
      }, 
      "questions": [
          {
              "answer": "Colorado, New Mexico, Arizona, Utah", 
              "category": 3, 
              "difficulty": 3, 
              "id": 164, 
              "question": "Which four states make up the 4 Corners region of the US?"
          }, 
          {
              "answer": "Muhammad Ali", 
              "category": 4, 
              "difficulty": 1, 
              "id": 9, 
              "question": "What boxer's original name is Cassius Clay?"
          }, 
          {
              "answer": "Apollo 13", 
              "category": 5, 
              "difficulty": 4, 
              "id": 2, 
              "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
          }, 
          {
              "answer": "Tom Cruise", 
              "category": 5, 
              "difficulty": 4, 
              "id": 4, 
              "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
          }, 
          {
              "answer": "Edward Scissorhands", 
              "category": 5, 
              "difficulty": 3, 
              "id": 6, 
              "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
          }, 
          {
              "answer": "Brazil", 
              "category": 6, 
              "difficulty": 3, 
              "id": 10, 
              "question": "Which is the only team to play in every soccer World Cup tournament?"
          }, 
          {
              "answer": "Uruguay", 
              "category": 6, 
              "difficulty": 4, 
              "id": 11, 
              "question": "Which country won the first ever soccer World Cup in 1930?"
          }, 
          {
              "answer": "George Washington Carver", 
              "category": 4, 
              "difficulty": 2, 
              "id": 12, 
              "question": "Who invented Peanut Butter?"
          }, 
          {
              "answer": "Lake Victoria", 
              "category": 3, 
              "difficulty": 2, 
              "id": 13, 
              "question": "What is the largest lake in Africa?"
          }, 
          {
              "answer": "The Palace of Versailles", 
              "category": 3, 
              "difficulty": 3, 
              "id": 14, 
              "question": "In which royal palace would you find the Hall of Mirrors?"
          }
      ], 
      "success": true, 
      "total_questions": 19
  }
```

- DELETE /questions/int:id  

General:
* Handles DELETE requests for deleting a question by id coming from URL parameter. It returns a success flag with the deleted question id.
Sample: `curl http://127.0.0.1:5000/questions/6 -X DELETE`
```
        {
          "success": "True",
          "deleted": 6
        }
```
- POST /questions  

General:

* Handles POST requests for creating new questions.

Sample: `curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d 
{ 
"question": "Which country won the first ever soccer World Cup in 1930?",
"answer": "Uruguay", 
"difficulty": 3,
"category": "6" 
}
`

```
{
  "message": "Question successfully created!",
  "success": true
}
```  
- POST /questions/search  

General:

* Handles GET requests for getting questions based on category.
  
Sample: `curl http://127.0.0.1:5000/questions/search -X POST -H "Content-Type: application/json" -d '{"searchTerm": "Anne Rice"}'`
```
{
  "questions": [
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }
  ],
  "success": true,
  "total_questions": 20
}
```
- POST /quizzes  

General:

* Handles POST requests for playing quiz. Also, it returns json object including a new random question.  

Sample: `curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"previous_questions": [20, 21], "quiz_category": {"type": "Science", "id": "1"}}'`
```
  {
      "question": {
          "answer": "Blood", 
          "category": 1, 
          "difficulty": 4, 
          "id": 22, 
          "question": "Hematology is a branch of medicine involving the study of what?"
      }, 
      "success": true
  }
```
### Error handling
Errors are returned in JSON format, using `jsonify()` method, as the following:
```
  @app.errorhandler(404)
    def not_found(error):
        return jsonify({
            "success": False,
            "error": 404,
            "message": "resource not found"
        }), 404
```
#### The API can deal with these types of errors:

- 400 – bad request.
- 404 – resource not found.
- 422 – unprocessable.

## Authors 
Reem Alrashed authored the API which is in `__init__.py` file, test suite `test_flaskr.py`, and this README.md file.
The other project files, were created by [Udacity](https://www.udacity.com/) as a project template for the [Full-Stack Developer Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd0044) API final project.



