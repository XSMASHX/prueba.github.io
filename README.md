<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Movie Rental</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    .movie-list {
      list-style-type: none;
      padding: 0;
    }
    .movie-item {
      margin-bottom: 20px;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
    .movie-item h3 {
      margin: 0 0 10px 0;
    }
  </style>
</head>
<body>
  <h1>Available Movies for Rent</h1>
  <ul class="movie-list" id="movie-list"></ul>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      fetch('movies.json')
        .then(response => response.json())
        .then(movies => {
          const movieList = document.getElementById('movie-list');
          movies.forEach(movie => {
            const movieItem = document.createElement('li');
            movieItem.classList.add('movie-item');

            movieItem.innerHTML = `
              <h3>${movie.title} (${movie.year})</h3>
              <p><strong>Genre:</strong> ${movie.genre}</p>
              <p>${movie.description}</p>
            `;

            movieList.appendChild(movieItem);
          });
        })
        .catch(error => {
          console.error('Error fetching movie data:', error);
        });
    });
  </script>
</body>
</html>
