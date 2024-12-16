
# Project Name

This project is an online platform that provides tourist guide and booking services. Our goal is to meet the needs of tourists and create a space where guides can offer their services.

## Table of Contents
- [Project Purpose](#project-purpose)
- [Goals and Benefits](#goals-and-benefits)
- [User Types and Registration Processes](#user-types-and-registration-processes)
- [Profile Management](#profile-management)
- [Guide List and Booking](#guide-list-and-booking)
- [Booking Management](#booking-management)
- [Technologies Used](#technologies-used)
- [Project Requirements](#project-requirements)
- [Class Diagrams](#class-diagrams)
- [Application Layers](#application-layers)
- [Key Features and Functions](#key-features-and-functions)
- [Testing and Debugging Process](#testing-and-debugging-process)
- [Example Test Scenario: User Login](#example-test-scenario-user-login)
- [Conclusion and Future Plans](#conclusion-and-future-plans)
- [Installation and Setup](#installation-and-setup)
- [Running Tests](#running-tests)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)
- [Contact](#contact)

## Project Purpose

The main purpose of the project is to offer special guidance services to tourists coming from abroad and make these services accessible through an online platform. This way, tourists can plan their trips more safely and easily, while guides can reach a wider audience with their services.

## Goals and Benefits

- **For Tourists**: Easy access, reliable guides, fast booking, and cancellation processes.
- **For Guides**: A wider customer base, the opportunity to promote themselves, and regular booking tracking.
- **General Benefits of the Platform**: User-friendly interface, secure payment options, continuous improvement through customer and guide feedback.

## User Types and Registration Processes

There are two main user types in our project: Tour Guides and Travelers.

- **Tour Guides**: They can create their profiles, specify their languages and experiences, and promote their services.
- **Travelers**: They can search for guides, review profiles, and make bookings.

## Profile Management

Users can update their profiles whenever they want. Tour guides can specify their languages and experiences to better promote themselves. This feature ensures that users are more active and interactive on the platform.

## Guide List and Booking

- **Guide List**: Travelers can view the guide list and reserve guides. Guides can improve themselves with user comments and ratings.
- **Booking**: Travelers can reserve guides and track their booking status. Guides can view and manage their booking status.

## Booking Management

- **Booking Cancellation**: Travelers can cancel their bookings. Guides can also update their booking status.
- **Booking Tracking**: Both user types can track their bookings and view their past bookings.

## Technologies Used

- **Backend**: Django (Python)
- **Frontend**: HTML, CSS, Bootstrap
- **Database**: SQLite (During development)
- **Testing**: Django Test Framework
- **Version Control**: Git

## Project Requirements

- **Functional Requirements**: User registration and login processes, profile creation and updating, guide listing and searching, guide booking and cancellation, booking management and viewing.
- **Non-Functional Requirements**: Performance, security, usability, scalability, and ease of maintenance.

## Class Diagrams

The class diagrams created within the scope of the project show the structure of the system and the relationships between the classes.

## Application Layers

1. **Business Logic Layer**:
   - Contains the core business rules and logic of the application.
   - Coordinates user operations and data management.
2. **Presentation Layer**:
   - Manages the user interface and user interactions.
   - Designed with HTML, CSS, and Bootstrap.
3. **Database Layer**:
   - Handles the storage, retrieval, and management of data.
   - Works on the SQLite database using Django ORM.

## Key Features and Functions

- **Registration and Login**: Allows users to create accounts and log into the system.
- **Profile Management**: Allows users to update their profile information.
- **Guide List**: Allows travelers to view and reserve guides.
- **Booking Management**: Allows guides and travelers to manage bookings.
- **Pagination**: Allows the guide list to be displayed page by page.
- **User-Friendly Interface**: Designed with Bootstrap, a modern and user-friendly interface.

## Testing and Debugging Process

- **Test Scenarios**: User Registration, Login Processes, Guide Booking, and Booking Cancellation.
- **Test Results**: All tests have been successfully passed. The detected errors during the tests have been resolved, ensuring the stability of the system.

## Example Test Scenario: User Login

**guides/tests.py**:

```python
from django.test import TestCase
from django.urls import reverse
from django.contrib.auth import get_user_model
from .models import Profile

User = get_user_model()

class UserLoginTest(TestCase):

    def setUp(self):
        self.user = User.objects.create_user(username='testuser', password='password', is_traveler=True)
        self.profile = Profile.objects.create(user=self.user)
        
    def test_user_login(self):
        response = self.client.post(reverse('login'), {
            'username': 'testuser',
            'password': 'password'
        })
        self.assertEqual(response.status_code, 302)  # If login is successful, a redirect (302) is expected

    def test_invalid_login(self):
        response = self.client.post(reverse('login'), {
            'username': 'testuser',
            'password': 'wrongpassword'
        })
        self.assertEqual(response.status_code, 200)  # If login fails, the form is shown again
        self.assertContains(response, "Please enter a correct username and password")  # Error message check
```

## Conclusion and Future Plans

- **Conclusion**: The project has been developed as a successful platform that offers tourist guide and booking services online.
- **Future Plans**:
  - Adding more features (e.g., user reviews and ratings).
  - Adding different payment methods.
  - Developing a mobile-friendly interface.
  - Marketing and promotional efforts to reach a broader user base.

## Installation and Setup

To set up the project locally, follow these steps:

### Prerequisites
- Python 3.x
- Django
- Git

### Clone the Repository
```sh
git clone https://github.com/yourusername/yourproject.git
cd yourproject
```

### Install Dependencies
Create a virtual environment and activate it:
```sh
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scriptsctivate`
```

Install the required packages:
```sh
pip install -r requirements.txt
```

### Database Migration
Run the following commands to apply migrations:
```sh
python manage.py makemigrations
python manage.py migrate
```

### Create a Superuser
Create a superuser to access the Django admin panel:
```sh
python manage.py createsuperuser
```

### Run the Development Server
Start the Django development server:
```sh
python manage.py runserver
```
Access the project in your web browser at `http://127.0.0.1:8000/`.

## Running Tests

To run the tests, use the following command:
```sh
python manage.py test
```

## Contributing

If you would like to contribute to this project, please follow these guidelines:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Create a new Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Django Documentation](https://docs.djangoproject.com/en/3.2/)
- [Bootstrap Documentation](https://getbootstrap.com/docs/4.3/getting-started/introduction/)
- [GitHub Guides](https://guides.github.com/)

## Contact

If you have any questions or feedback, feel free to reach out:

- Email: your.email@example.com
- GitHub: [yourusername](https://github.com/yourusername)

Thank you for checking out this project!
