---------------------------------------------------------------------------------------functionalities:------------------------------------------------------------------------------------------
Admin users can now create courses and manage signups
Both admins and users can register and log in.
Upon successful login, users receive a unique JWT token that acts as their passport to the platform.

Course Management and Access Control:
Built functionality for admins to create and manage courses, including details like title, description, and price.
Users can sign up for courses and view a list of all available courses.
After purchasing a course, users can access exclusive content and track their progress.

JWT-powered Security:
Every interaction with the backend requires the user's JWT token for verification. This ensures only authorized users can access purchased courses and perform actions like updating their profiles.

Next Steps:
Now that the core backend is up and running, I'm excited to move on to building the frontend interface. This will involve creating user dashboards, course pages, and a payment gateway integration.
I'm also looking forward to implementing additional features like user reviews, progress tracking, and personalized recommendations.
--------------------------------------------------------------------------------------------## Routes------------------------------------------------------------------------------------------------------------

### Admin Routes:

- POST /admin/signup
  Description: Creates a new admin account.
  Input Body: { username: 'admin', password: 'pass' }
  Output: { message: 'Admin created successfully' }
- POST /admin/signinImplemented a secure authentication system similar to ChatGPT, using JSON Web Tokens (JWTs) for user authorization.
  Description: Creates a new admin account.
  Input Body: { username: 'admin', password: 'pass' }
  Output: { token: 'your-token' }
- POST /admin/courses
  Description: Creates a new course.
  Input: Headers: { 'Authorization': 'Bearer <your-token>' }, Body: { title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com' }
  Output: { message: 'Course created successfully', courseId: "new course id" }
- GET /admin/courses
  Description: Returns all the courses.
  Input: Headers: { 'Authorization': 'Bearer <your-token>' }
  Output: { courses: [ { id: 1, title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }, ... ] }

### User routes

- POST /users/signup
  Description: Creates a new user account.
  Input: { username: 'user', password: 'pass' }
  Output: { message: 'User created successfully' }
- POST /users/signin
  Description: Creates a new user account.
  Input: { username: 'user', password: 'pass' }
  Output: { token: 'your-token' }
- GET /users/courses
  Description: Lists all the courses.
  Input: Headers: { 'Authorization': 'Bearer <your-token>' }
  Output: { courses: [ { id: 1, title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }, ... ] }
- POST /users/courses/:courseId
  Description: Purchases a course. courseId in the URL path should be replaced with the ID of the course to be purchased.
  Input: Headers: { 'Authorization': 'Bearer <your-token>' }
  Output: { message: 'Course purchased successfully' }
- GET /users/purchasedCourses
  Description: Lists all the courses purchased by the user.
  Input: Headers: { 'Authorization': 'Bearer <your-token>' }
  Output: { purchasedCourses: [ { id: 1, title: 'course title', description: 'course description', price: 100, imageLink: 'https://linktoimage.com', published: true }, ... ] }
