# Full Stack Application Development Capstone Project

### Course 11 of the [IBM Full Stack Software Developer](https://www.coursera.org/programs/fresno-county-public-library-c1tox/my-learning?myLearningTab=IN_PROGRESS) Program

#### This project is cloned from 
https://github.com/ibm-developer-skills-network/xrwvm-fullstack_developer_capstone


The final project for this course has several steps that you must complete. The high-level step list given below will help you with an overview of the complete project. The project is divided into smaller labs with detailed instructions for each step. You must complete all labs to complete the project successfully.

### Project breakdown

**Fork the GitHub repo containing the project template. The main web application is a predefined Django application. You will need to add some new features, and then build and run your project implementation.**
 - Fork the repository in your account.
 - Clone the repository in the Cloud IDE environment.
 - Create static pages to finish the user stories.
 - Run the application locally.

**Add user management to the Django application.**

- Implement user management using the Django user authentication system and create a REACT frontend.

**Implement backend services.**
- Create Node.js server to manage dealers and reviews using MongoDB and dockerize it.
- Deploy sentiment analyzer on Code Engine.
- Create Django models and views to manage car model and car make.
- Create Django proxy services and views to integrate dealers and reviews together.

**Add dynamic pages with Django templates.**
- Create a page that displays all the dealers.
- Create a page that displays reviews for a selected dealer.
- Create a page that lets the end user add a review for a selected dealer.

**Implement CI/CD, and then run and test your application**
- Set up continuous integration and delivery for code linting.
- Run your application on Cloud IDE.
- Test the updated application locally.
- Deploy the application on Kubernetes.

### Solution architecture
The solution will consist of multiple technologies

1. The user interacts with the "Dealerships Website", a Django website, through a web browser.

2. The Django application provides the following microservices for the end user:
  - get_cars/ - To get the list of cars from
  - get_dealers/ - To get the list of dealers
  - get_dealers/:state - To get dealers by state
  - dealer/:id - To get dealer by id
  - review/dealer/:id - To get reviews specific to a dealer
  - add_review/ - To post review about a dealer

3. The Django application uses SQLite database to store the Car Make and the Car Model data.

4. The "Dealerships and Reviews Service" is an Express Mongo service running in a Docker container. It provides the following services::
  - /fetchDealers - To fetch the dealers
  - /fetchDealer/:id - To fetch the dealer by id
  - fetchReviews - To fetch all the reviews
  - fetchReview/dealer/:id - To fetch reviews for a dealer by id
  - /insertReview - To insert a review

5. "Dealerships Website" interacts with the "Dealership and Reviews Service" through the "Django Proxy Service" contained within the Django Application.

6. The "Sentiment Analyzer Service" is deployed on IBM Cloud Code Engine, it provides the following service:

  - /analyze/:text - To analyze the sentiment of the text passed. It returns positive, negative or neutral.

7. The "Dealerships Website" consumes the "Sentiment Analyzer Service" to analyze the sentiments of the reviews through the Django Proxy contained within the Django application.


## Running application:
### Setup Virtual Environment
```
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate
```

### Install requirements
```
python3 -m pip install -U -r requirements.txt
```

### Perform Migrations
```
python3 manage.py makemigrations
python3 manage.py migrate
```

### Run Server
```
python3 manage.py runserver
```

#### Additional Setup
- Update `ALLOWED_HOSTS` and `CSRF_TRUSTED_ORIGINS` with the root url `server/djangoproj/settings.py`. (do not include `/` at the end) 



