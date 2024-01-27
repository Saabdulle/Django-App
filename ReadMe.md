# Django Rest Framework (DRF) Project

## Overview

In this project, we have built an e-commerce API with functionality to manage items, place orders, and retrieve order information. The project covers various aspects, including models, serializers, viewsets, routers, authentication, and testing.


## Project Structure
The project structure is organised as follows:

```bash
Django DRF App/
    backend/
        core/
        docker/
        drf_app/
        ecommerce/
        utils/
        manage.py
        requirements.txt
    .gitignore
    docker-compose.yml
    env.template
    README.md
    server.py
```
- backend: Contains core, docker, drf_app, eccomerce and utils folders as well as manage.py and requirements.txt.
    -  core: Housing critical components such as data models, administrative interfaces, views, serializers, and tests, serving as the foundation for essential functionalities.
    -  drf_app: Main Django project settings.
    - ecommerce: Django app for the e-commerce functionality.
    - utils: Utility modules.
- docker: Configuration files for Docker.
- .gitignore: Git ignore file.
- docker-compose.yml: Docker Compose configuration.
- env.template: Template for environment variables.
- ReadMe.md: Project documentation.
- server.py: Development server script.

## Achievements

### 1. **Project Setup:**
   - Created a structured Django project with core functionalities.
   - Utilised Docker for containerisation, making the project environment consistent.

### 2. **Token Authentication:**
   - Implemented token authentication for secure API access.
   - Configured DRF settings for token authentication in the `settings.py` file.

### 3. **E-commerce App:**
   - Developed an e-commerce app with models for items and orders.
   - Created serializers to handle data conversion between Python objects and JSON.

### 4. **Viewsets and Routers:**
   - Implemented viewsets for listing, retrieving, updating, and creating items and orders.
   - Configured routers to manage API endpoints and connect them to viewsets.

### 5. **Unit Testing:**
   - Wrote comprehensive unit tests using DRF's APIClient to ensure the functionality of the API.
   - Covered scenarios such as retrieving items, placing orders, and checking stock levels.

### 6. **API Endpoint Documentation:**
   - Provided clear instructions on making requests to various API endpoints.
   - Demonstrated the usage of authentication tokens for secure API interactions.

### 7. **Contact Request Feature:**
   - Added a feature to create contact requests, showcasing versatility in API capabilities.

## Running the Project

### Run Locally
 1. Clone the repository and navigate to the project's root directory.
 2. Create and activate a virtual environment:
 ```bash
    python -m venv venv
 ```
 ```bash
    Mac/Linux: source venv/bin/activate 
    Windows: venv\Scripts\activate
 ```
 3. Install dependencies:
 ```bash
    pip install -r requirements.txt
 ```
 4. Apply migrations while in backend directory:
  ``` bash
    python manage.py makemigrations
    python manage.py migrate
 ```
 5. Run the following command: 
 ``` bash 
 python manage.py runserver
 ```
 4. Access the API at `http://localhost:8000/` in your browser or through API clients like cURL.

 ### Run on Docker
1. Ensure you have Docker installed.
2. Clone the repository and navigate to the project's root directory.
3. Run the following commands:
   ```bash
   docker-compose build
   docker-compose up
   ```
4. Access the API at `http://api:8000/` in your browser or through API clients like cURL or HTTPie.

## Running Tests

Execute the following command to run the unit tests:

```bash
python manage.py test
```
## Endpoint Calls

To create a contact request: 
 - Locally
    ```bash
    Locally: curl -X POST -H "Content-type: application/json" -d '{"name": "John Smith", "message": "Contact Message", "email":"johnsmith@email.com"}' 'http://localhost:8000/contact/'
    ```
 - Docker CLI
    ```bash 
     http http://api:8000/contact/ name="John Smith" message="Contact Message" email="johnsmith@email.com"
    ```
To create a new token ID
- This will be used to login to as Admin at ```http://localhost:8000/```admin. At this endpoint, you have admin control and can make new users, contacts, items, orders and more. 
    - Locally 
        ```bash
        curl -XPOST -F 'username=**your_username**' -F 'password=**your_password**' http://localhost:8000/api-token-auth/
        ```
    - Docker CLI
        ```bash 
        http post http://api:8000/api-token-auth/ username=**your_username** password=**your_password**
        ```
Retrieve user's Auth Token
    - locally:
        ```bash
        curl -X GET -H 'Authorization: Token **your_token**' http://localhost:8000/item/**your_item_uuid**/
        ```
    Docker CLI: 
        ```bash
        http http://api:8000/item/**your_item_uuid**/ 'Authorization: Token **your_token**' 
        ```
Retrieve all items in database
    - Locally
        ```bash
        curl -X GET -H 'Authorization: Token **your_token**' http://localhost:8000/item/
        ```
    - Docker CLI
        ```bash
        http http://api:8000/item/ 'Authorization: Token **your_token**'
        ```
Retrieve a single item
    - Locally
        ```bash
        curl -X GET -H 'Authorization: Token **your_token**' http://localhost:8000/item/**your_item_uuid**/
        ```
    - Docker CLI
        ```bash
        http http://api:8000/item/**your_item_uuid**/ 'Authorization: Token **your_token**' 
        ```
Retrieve all orders
    - Locally
        ```bash
        curl -X GET -H 'Authorization: Token **your_token**' http://localhost:8000/order/
        ```
    - Docker CLI
        ```bash
        http http://api:8000/order/ 'Authorization: Token **your_token**'
        ```
Place an order for specific item ID
    - Locally 
        ```bash
        curl -X GET -H 'Authorization: Token **your_token**' http://localhost:8000/order/**your_order_uuid**/
        ```
    - Docker CLI
        ```bash
        http http://api:8000/order/**your_order_uuid**/ 'Authorization: Token **your_token**'
        ```
## Acknowledgements

Special thanks to the course author at FreeCodeCamp for providing detailed instructions and hands-on exercises to enhance understanding and practical skills in Django Rest Framework.

Feel free to explore, modify, and build upon this project as you continue your journey in DRF development!
