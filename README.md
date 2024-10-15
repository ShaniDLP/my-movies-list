# Top 20 Most Popular Movies Web App

[![Vue.js](https://img.shields.io/badge/Vue.js-2.x-brightgreen.svg)](https://vuejs.org/)
[![Axios](https://img.shields.io/badge/Axios-0.21.x-blue.svg)](https://github.com/axios/axios)

## Description

This project is a web application that displays the top 20 most popular movies using data from [The Movie Database (TMDB)](https://www.themoviedb.org/). The application is built with [Vue.js](https://vuejs.org/) and utilizes [Axios](https://github.com/axios/axios) for fetching movie data.

## Table of Contents

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Potential Features to Add](#potential-features-to-add)

## Getting Started

### Prerequisites

To run this project locally, you need to have the following installed:

- **Node.js** (v14 or higher)
- **npm** or **Yarn**

### Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/top-movies-app.git
   cd top-movies-app

   ```

2. **Install Dependencies**

Using npm:

```bash
npm install
```

Or using Yarn:

```bash
yarn install
```

3. **Create a .env Files**

Create a .env file in the root of the project to store your API key.
Add the following line to the file:

```bash
VUE_APP_API_KEY= your_tmdb_api_key_here
```

Replace your_tmdb_api_key_here with your actual API key from The Movie Database (TMDB).

## Usage

Run the Development Server
Start the development server by running:

Using npm:

```bash
npm run serve
```

Or using Yarn:

```bash
yarn serve
```

The application should now be running on http://localhost:8080.

4. **_Run the Development Server_**

Start the development server by running:

```bash
npm run serve
# or
yarn serve
```

## Features

- Displays the top 20 most popular movies using data from TMDB.

- User-friendly layout with dynamic fetching and error handling.

- Responsive design for both desktop and mobile devices.

## Potential Features to Add

If I had more time, I would add the following features:

- Search Functionality: Allow users to search for their favorite movies directly from the app.
- Sorting: Allow user to sort the list by name, release date, and number of ratings.

- Detailed Movie Pages: Create detailed pages for each movie, showing more information like cast, reviews, trailers, etc.

- Pagination: Add pagination to show more movies beyond the top 20.

- Favorite Movies: Allow users to mark movies as favorites and save them locally.

- Error Handling with Retry: Add a retry button when a request to fetch data fails.

<img width="1780" alt="Screenshot 2024-10-15 at 21 11 07" src="https://github.com/user-attachments/assets/51a05559-840e-4e27-9f69-ffbf5672f08f">
<img width="1785" alt="Screenshot 2024-10-15 at 21 11 39" src="https://github.com/user-attachments/assets/ec22f10f-b3c1-4618-9b08-4b716b451aca">
