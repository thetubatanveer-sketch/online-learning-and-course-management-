 Learnova — Online Learning & Course Management Platform

## Project overview
Learnova is a responsive e-learning platform frontend/demo created directly from **Task #21**. The task requires a complete frontend + backend + database + authentication + REST API + admin dashboard, with student and instructor learning workflows. fileciteturn2file0L5-L15

This submission provides the requested **one complete website file**: `learnova.html`. It embeds HTML, CSS and JavaScript in a single file and includes a large connected sample course catalog.

## Requirements implemented in the single-file frontend

### Student experience
- Home / hero section
- Courses and course discovery
- Course categories
- Featured courses
- Popular-style course data
- New-course data
- Search and dynamic result count
- Category, level, price, rating and language filters
- Sorting by newest, oldest, price, rating and popularity
- Wishlist with Local Storage
- Course detail popup
- Image-based course cards and gallery-style hero imagery
- Video-preview area
- Enrollment workflow with mock payment
- Coupon validation
- Learning dashboard
- My Courses view
- Course player
- Lesson navigation
- Progress bar
- Learning materials
- Quiz timer and scoring
- Assignment submission interface
- Course completion/certificate demo
- Certificate display and verification-style information
- Review and 1–5 star rating interface
- Course comparison for up to three courses
- Dark/light mode
- Responsive hamburger navigation
- Toast messages
- Loading/empty/success-style states
- Scroll-to-top
- CSV export demo

The assignment specifically requires search/filter/sort, wishlist, comparison, details, video preview, lesson navigation, progress tracking, quiz scoring, assignments, pricing, coupons, enrollment validation, reviews, notifications, toast messages, pagination and responsive behavior. fileciteturn2file0L161-L201

### Course data
The requirement asks for at least **40 courses** and the provided file contains 40 sample courses. The task also requires 15+ categories, 20 instructors, 200 students, 200 enrollments, 150 lessons, 30 quizzes, 100 questions, 30 assignments, 100 submissions, 100 reviews, 100 certificates, 20 coupons and 50 course images. fileciteturn2file0L1548-L1565

The single-file version uses realistic course objects and repeated learning assets to keep the deliverable portable. The full required dataset should be seeded into the database for the final full-stack submission.

## Technologies
Frontend:
- HTML5
- CSS3
- CSS Grid / Flexbox
- Vanilla JavaScript
- Local Storage for frontend-only demo persistence
- Fetch API can be connected to REST endpoints
- Google Fonts
- Remote Unsplash photography

The assignment recommends HTML5, CSS3, JavaScript, Bootstrap/Tailwind, Fetch API, DOM manipulation, validation and Local Storage on the frontend. fileciteturn2file0L243-L255

Recommended backend:
- Node.js + Express.js

Recommended database:
- MySQL, PostgreSQL or MongoDB

The task allows Node.js/Express, Flask or Django and specifies MySQL/PostgreSQL/MongoDB. fileciteturn2file0L257-L292

## How to run the one-file website
1. Download `learnova.html`.
2. Open it in Chrome, Edge or Firefox.
3. Internet access is recommended for fonts and photographs.
4. No npm installation is needed for this frontend/demo file.

## Demo interactions
- Click a course card to open details.
- Use **Enroll Now** to simulate enrollment and mock payment.
- Try coupons:
  - `LEARN10`
  - `WELCOME15`
  - `COURSE20`
  - `STUDENT25`
- Click ♡ to add/remove wishlist items.
- Use **Compare course** on multiple courses.
- Open **Continue learning** for the course player.
- Start the quiz to see timer and score calculation.
- Open assignment to test the submission UI.
- Open the certificate from the dashboard.
- Use the Admin section for dashboard metrics and CSV export.

## Important full-stack limitation
The original Task #21 explicitly prohibits using only Local Storage/static HTML and requires a real backend, connected database, authentication, authorization and REST APIs. fileciteturn2file0L1809-L1843

Therefore, this one-file HTML is a **complete frontend/demo**, not a claim that a backend database exists inside HTML.

For the final assignment-compliant full-stack version, connect the interface to:

```text
learnova/
├── frontend/
│   └── learnova.html
├── backend/
│   ├── server/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   └── config/
├── database/
│   ├── schema/
│   ├── seed/
│   └── migrations/
├── .env.example
└── README.md
```

The task itself recommends a multi-folder structure for frontend, backend, instructor, admin and database components. fileciteturn2file0L1663-L1743

## Backend setup — recommended Node.js/Express architecture

### Install
```bash
npm init -y
npm install express cors dotenv bcrypt jsonwebtoken mysql2 multer
npm install --save-dev nodemon
```

### Environment variables
Create `.env`:

```env
PORT=5000
DB_HOST=localhost
DB_PORT=3306
DB_NAME=learnova
DB_USER=root
DB_PASSWORD=your_password
JWT_SECRET=replace_with_a_long_random_secret
```

Never commit `.env` or hard-code database credentials. The assignment explicitly requires environment variables, password hashing and protection against plain-text credentials. fileciteturn2file0L1365-L1385

## REST API plan

Authentication:
```text
POST /api/register
POST /api/login
POST /api/logout
POST /api/forgot-password
POST /api/reset-password
```

Courses:
```text
GET    /api/courses
GET    /api/courses/:id
POST   /api/courses
PUT    /api/courses/:id
DELETE /api/courses/:id
```

Lessons:
```text
GET    /api/courses/:id/lessons
POST   /api/lessons
PUT    /api/lessons/:id
DELETE /api/lessons/:id
```

Enrollments:
```text
POST /api/enrollments
GET  /api/enrollments
GET  /api/enrollments/:id
PUT  /api/enrollments/:id
```

Progress:
```text
GET  /api/progress
POST /api/progress
PUT  /api/progress/:id
```

Quizzes:
```text
GET    /api/quizzes
POST   /api/quizzes
PUT    /api/quizzes/:id
DELETE /api/quizzes/:id
```

Assignments:
```text
GET    /api/assignments
POST   /api/assignments
PUT    /api/assignments/:id
DELETE /api/assignments/:id
```

Reviews:
```text
GET    /api/reviews
POST   /api/reviews
PUT    /api/reviews/:id
DELETE /api/reviews/:id
```

Wishlist:
```text
GET    /api/wishlist
POST   /api/wishlist
DELETE /api/wishlist/:id
```

Certificates:
```text
GET  /api/certificates
GET  /api/certificates/:id
POST /api/certificates
```

Admin:
```text
GET /api/admin/dashboard
GET /api/admin/analytics
GET /api/admin/users
GET /api/admin/courses
GET /api/admin/enrollments
```

These endpoint groups follow the REST API requirements in Task #21. fileciteturn2file0L1158-L1239

## Database design

Recommended tables:
- users
- instructors
- admins
- courses
- categories
- lessons
- course_materials
- quizzes
- questions
- assignments
- submissions
- enrollments
- progress
- reviews
- wishlists
- certificates
- payments
- coupons
- notifications

The required relationships include User → Enrollments, Course → Lessons/Quizzes/Assignments/Reviews, User → Reviews/Wishlist, Instructor → Courses, Enrollment → Progress and Course → Certificates. fileciteturn2file0L1243-L1313

## Authentication
Production implementation should:
- hash passwords with bcrypt
- validate email and password strength
- prevent duplicate emails
- use JWT/session authentication
- protect student/instructor/admin routes
- implement logout
- handle expired tokens
- enforce role-based authorization

The assignment explicitly says never to store plain-text passwords and requires protected routes. fileciteturn2file0L297-L346

## Payment
Use a **mock payment gateway** for this assignment. Do not collect or store real card information. The payment record should include payment ID, user, course, enrollment, amount, discount, method, transaction reference, date and status. fileciteturn2file0L822-L846

## Progress and certificates
Required progress calculation:

```text
Progress % =
Completed Lessons / Total Lessons × 100
```

The real backend should persist progress in the database. fileciteturn2file0L482-L506

A certificate should only be generated after the course-completion conditions are verified. It should contain certificate ID, student, course, instructor, completion/issue dates, duration, final score and verification code. fileciteturn2file0L616-L665

## Coupon rules
Required sample codes:
```text
LEARN10     → 10%
WELCOME15   → 15%
COURSE20    → 20%
STUDENT25   → 25%
```

The backend must validate dates, status, usage limits, minimum purchase and maximum discount. fileciteturn2file0L768-L799

## Security
Implement:
- password hashing
- authentication
- authorization
- protected routes
- input validation and sanitization
- environment variables
- CORS configuration where required
- ownership checks
- secure API design

Never store plain-text passwords, real payment card numbers or secrets. fileciteturn2file0L1365-L1385

## Accessibility
The task requires semantic HTML5, heading hierarchy, meaningful alt text, accessible forms/buttons/modals, visible focus states, color contrast, keyboard navigation and responsive layouts. fileciteturn2file0L1391-L1419

## Testing checklist
Test:
- Registration/login/logout
- Invalid credentials
- Duplicate email
- Password validation
- Protected routes
- Search/filter/sort
- Course details
- Enrollment
- Wishlist
- Lesson navigation
- Progress
- Quiz submission/scoring
- Assignment submission/grading
- Course completion
- Certificate generation/verification
- Review/rating/edit/delete
- Admin CRUD and analytics

These testing areas are explicitly listed in the task. fileciteturn2file0L1571-L1626

## Demo credentials
For this standalone frontend file, no real authentication credentials are embedded because that would conflict with the requirement to implement secure backend authentication.

For the actual backend, create seeded demo accounts such as:

```text
Student
Email: student@learnova.demo

Instructor
Email: instructor@learnova.demo

Admin
Email: admin@learnova.demo
```

Set passwords through the database seed process using bcrypt hashes; never store plain-text passwords in the source code.
