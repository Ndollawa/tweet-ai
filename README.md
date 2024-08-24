Here's a comprehensive `README.md` file to help users set up both the Vue frontend and NestJS backend for your project:

---

# TweetAI Project

Welcome to the TweetAI project! This repository includes a Vue.js frontend and a NestJS backend for managing Autobots, Posts, and Comments. Follow the instructions below to set up and run the project.

## Prerequisites

- **Node.js** (version 18 or later)
- **MySQL** (for the database)
- **npm** (or **yarn** for package management)

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Ndollawa/tweet-ai.git
cd tweetai
```

### 2. Setting Up the Backend (NestJS)

```bash
git clone https://github.com/Ndollawa/tweet-ai-backend.git
cd tweetai
```

#### a. Navigate to the Backend Directory

```bash
cd backend
```

#### b. Install Dependencies

```bash
npm install
```

#### c. Configure Environment Variables

Create a `.env` file in the `backend` directory and add your database credentials and other configuration:

```plaintext
DATABASE_URL=mysql://username:password@localhost:3306/tweetai
```

#### d. Run Migrations

Ensure that Prisma migrations are applied to set up the database schema:

```bash
npx prisma migrate dev
```

#### e. Start the Backend Server

```bash
npm run start:dev
```

The NestJS backend will be available at `http://localhost:3500`.// api/v1

### 3. Setting Up the Frontend (Vue.js)

#### a. Navigate to the Frontend Directory

```bash
cd frontend
```

#### b. Install Dependencies

```bash
npm install
```

#### c. Configure Environment Variables

Create a `.env` file in the `frontend` directory to set the backend API URL:

```plaintext
VITE_API_URL=http://localhost:3000
```

#### d. Start the Frontend Development Server

```bash
npm run dev
```

The Vue.js frontend will be available at `http://localhost:5173`.

## API Endpoints

### Autobots

- **GET** `/autobots` - Retrieve all Autobots
- **GET** `/autobots/:id` - Retrieve a specific Autobot by ID

### Posts

- **GET** `/autobots/:id/posts` - Retrieve all posts for a specific Autobot

### Comments

- **GET** `/posts/:id/comments` - Retrieve all comments for a specific Post

## Throttling Requests

To ensure fair usage, the API is throttled to allow a maximum of 5 requests per minute per IP address, with each request returning up to 10 results.
## Api Endpoints
[https://cloudy-shuttle-5925.postman.co/documentation/10483274-bf578774-34a2-4f20-939b-f0382738aeea/publish?workspaceId=2e25effb-16c9-4db6-82eb-f2b83ccf543a](https://cloudy-shuttle-5925.postman.co/documentation/10483274-bf578774-34a2-4f20-939b-f0382738aeea/publish?workspaceId=2e25effb-16c9-4db6-82eb-f2b83ccf543a);

## Contributing

If you'd like to contribute to this project, please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Make your changes
4. Commit your changes (`git commit -am 'Add new feature'`)
5. Push to the branch (`git push origin feature/your-feature`)
6. Create a new Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or issues, please reach out to [ndollawa@yahoo.com](mailto:ndollawa@yahoo.com).

---

Feel free to adjust the `README.md` to fit your specific project details and repository settings.