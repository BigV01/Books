# Books API

## Project Setup

1. Clone the repository:
   ```bash
   git clone <repo-url>
   cd books-api

2. Install dependencies:
   npm install

3. Set up the environment:
Ensure MongoDB is running locally or update the connection string in src/index.ts.

4. Run the application:
 npm run build
npm start

  API Endpoints

  Create a Book
Endpoint: POST /api/books
Request Body: { "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string" }
Response: { "id": "string", "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string" }

  Update Book Cover Picture
Endpoint: PATCH /api/books/cover-image/:id
Request Body: Form-data with key coverImage for file
Response: { "id": "string", "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string", "coverImage": "string" }

  Get All Books
Endpoint: GET /api/books
Response: [{ "id": "string", "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string" }]

  Get a Single Book
Endpoint: GET /api/books/:id
Response: { "id": "string", "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string" }

  Update a Book
Endpoint: PUT /api/books/:id
Request Body: { "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string" }
Response: { "id": "string", "title": "string", "author": "string", "publishedDate": "date", "ISBN": "string" }

  Delete a Book
Endpoint: DELETE /api/books/:id
Response: { "message": "Book deleted successfully" }

Testing

1. Run tests:
  npm test

makefile

### 7. Testing

#### a. Configure Jest for TypeScript
- Update `package.json` to include Jest configuration:
  ```json
  "jest": {
    "preset": "ts-jest",
    "testEnvironment": "node"
  }
  
2. Write Test Cases
   // src/tests/book.test.ts
import request from 'supertest';
import app from '../index'; // Assuming app is exported from index.ts

describe('Books API', () => {
  it('should create a new book', async () => {
    const res = await request(app)
      .post('/api/books')
      .send({
        title: 'Book Title',
        author: 'Author Name',
        publishedDate: '2023-01-01',
        ISBN: '123-456-789'
      });
    expect(res.statusCode).toEqual(201);
    expect(res.body).toHaveProperty('id');
  });

  // Add more test cases for other endpoints
});
