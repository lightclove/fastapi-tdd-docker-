
# FastAPI app with TDD, DI, and other useful approaches
Asynchronous summarization API with Test-Driven Development:

 - Using test-driven development approach
 - RESTful design principles, using the basic HTTP verbs: GET, POST, PUT, and DELETE according the OAS
 - Tortoise ORM will be used to interact with a Postgres database
 - Pytest instead of unittest for writing unit and integration tests to test the API. 
 - Using a functional approach.
 - Utilize GitHub Actions to run tests before deploying to Heroku
 - Docker to simplifing deploy
 - Using Heroku - abstracted environments where you dont have to manage the underlying infrastructure, 
making it easy to manage, deploy, and scale web applications.

## Setup
Create a new project and install FastAPI along with Uvicorn, an ASGI server used to serve up FastAPI:

    $ mkdir fastapi-tdd-docker && cd fastapi-tdd-docker
    $ mkdir project && cd project
    $ mkdir app
    $ python3.10 -m venv env
    $ source env/bin/activate
    $ pip install poerty
    $ poerty new project
    $ cd project 
    $ mv * to subfolder
    $ rm project
    $ poetry add fastapi 
    $ poetry export -f requirements.txt --output requirements.txt

OUTPUT:

    (env) [ ahost ~/Work/fastapi-tdd-docker/project ]$ poetry add fastapi
    
    $ poetry add uvicorn

Run the server from the "project" directory:
`(env) [ ahost ~/Work/fastapi-tdd-docker/project ]$ uvicorn app.main:appapp.main:app` 
tells Uvicorn where it can find the FastAPI application -- e.g., "within the 'app' module, you'll find the app, `app = FastAPI()`, in the 'main.py' file.

## Auto-reload
Let's run the app again. This time, we'll enable auto-reload mode so that the server will restart after changes are made to the code base:

    (env)$ uvicorn app.main:app --reload

Now when you make changes to the code, the app will automatically reload. 
in app/main.py 
Take note of settings: `Settings = Depends(get_settings)`. 
Here, the Depends function is a dependency that declares another dependency, get_settings. 
Put another way, Depends depends on the result of get_settings. 
The value returned, Settings, is then assigned to the settings parameter.
Rather than having to go through the trouble of spinning up a task queue (like Celery or RQ) or utilizing threads, 
FastAPI makes it easy to deliver routes asynchronously. 
As long as you don't have any blocking I/O calls in the handler, simply declare the handler as asynchronous
