# ALX Project 0x14

## API Overview
The MoviesDatabase API provides developers with a comprehensive way to interact with movie-related data. Key features include:
- Access to detailed information about movies, TV shows, and actors.
- Ability to search for movies or TV shows by title, genre, or release year.
- Support for retrieving popular, trending, and top-rated content.
- Advanced filtering options for sorting search results.
- Endpoints for accessing trailers, reviews, and ratings.

## API Version
Version: v1.0

## Available Endpoints
- **GET /movies**: Retrieves a list of movies with optional filters like genre, release year, and rating.
- **GET /movies/{id}**: Fetches detailed information about a specific movie by its ID.
- **GET /tv-shows**: Returns a list of TV shows with filtering options similar to movies.
- **GET /tv-shows/{id}**: Provides detailed information about a specific TV show by its ID.
- **GET /actors/{id}**: Retrieves details about an actor, including movies or shows they are associated with.
- **GET /search**: Allows searching for movies, TV shows, or actors using a query string.

## Request and Response Format
### Request Format
Requests typically require the following structure:
- **Headers**: Include an API key for authentication (e.g., `Authorization: Bearer YOUR_API_KEY`).
- **Query Parameters**: Use query parameters for filtering and sorting (e.g., `?genre=action&year=2023`).

#### Example Request
```
GET /movies?genre=action HTTP/1.1
Host: api.moviesdatabase.com
Authorization: Bearer YOUR_API_KEY
```

### Response Format
Responses are returned in JSON format. Example:
```
{
  "status": "success",
  "data": [
    {
      "id": "12345",
      "title": "Action Movie",
      "genre": "Action",
      "releaseYear": 2023
    }
  ]
}
```

## Authentication
To authenticate your requests:
1. Obtain an API key by signing up on the MoviesDatabase platform.
2. Include the API key in the request header as `Authorization: Bearer YOUR_API_KEY`.
3. Ensure your API key is kept secure and not exposed in public repositories.

## Error Handling
Common error responses:
- **401 Unauthorized**: Missing or invalid API key.
- **404 Not Found**: The requested resource does not exist.
- **429 Too Many Requests**: You have exceeded the rate limit.
- **500 Internal Server Error**: An error occurred on the server.

### Handling Errors in Code
```javascript
try {
  const response = await fetch('https://api.moviesdatabase.com/movies', {
    headers: { Authorization: 'Bearer YOUR_API_KEY' }
  });
  if (!response.ok) {
    throw new Error(`Error: ${response.status} ${response.statusText}`);
  }
  const data = await response.json();
  console.log(data);
} catch (error) {
  console.error(error.message);
}
```

## Usage Limits and Best Practices
- **Rate Limits**: The API allows up to 1,000 requests per day. Exceeding this will result in a `429 Too Many Requests` error.
- **Caching**: Cache frequent requests to reduce API calls and improve performance.
- **Error Logging**: Implement logging for debugging and monitoring API usage.
- **Efficient Queries**: Use filters and pagination to retrieve only the necessary data.

By adhering to these guidelines, you can effectively utilize the MoviesDatabase API for your project.
