<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movie Collection</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 900px;
            margin: 40px auto;
            padding: 0 20px;
            background-color: #ffffff;
            color: #333;
            line-height: 1.7;
        }

        h1 {
            font-size: 32px;
            border-bottom: 2px solid #ddd;
            padding-bottom: 10px;
        }

        h2 {
            margin-top: 35px;
        }

        h3 {
            margin-bottom: 5px;
        }

        p {
            color: #555;
        }

        hr {
            border: none;
            border-top: 1px solid #ddd;
            margin: 30px 0;
        }

        .search-container {
            display: flex;
            gap: 10px;
            margin: 25px 0;
            flex-wrap: wrap;
        }

        input, select {
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 15px;
        }

        input {
            flex: 1;
            min-width: 180px;
        }

        .movie {
            margin: 25px 0;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }

        .movie h3 {
            font-size: 21px;
        }

        .movie-info {
            color: #777;
            font-size: 14px;
        }

        .rating {
            color: #d69b00;
            font-weight: bold;
        }

        .genre {
            display: inline-block;
            background: #eeeeee;
            padding: 3px 9px;
            border-radius: 4px;
            font-size: 13px;
        }

        footer {
            margin-top: 50px;
            padding-top: 20px;
            border-top: 1px solid #ddd;
            color: #888;
            font-size: 13px;
        }

        @media (max-width: 600px) {
            body {
                margin: 20px auto;
            }

            h1 {
                font-size: 26px;
            }

            .search-container {
                flex-direction: column;
            }

            input, select {
                box-sizing: border-box;
                width: 100%;
            }
        }
    </style>
</head>

<body>

    <h1>My Movie Collection</h1>

    <p>
    </p>

    <hr>

    <h2>Browse Movies</h2>

    <div class="search-container">
        <input
            type="text"
            id="search"
            placeholder="Search for a movie..."
            oninput="filterMovies()"
        >

        <select id="genreFilter" onchange="filterMovies()">
            <option value="all">All Genres</option>
            <option value="Action">Action</option>
            <option value="Adventure">Adventure</option>
            <option value="Drama">Drama</option>
            <option value="Sci-Fi">Sci-Fi</option>
            <option value="Comedy">Comedy</option>
        </select>
    </div>

    <div id="movieList">

        <div class="movie" data-genre="Sci-Fi">
            <h3>Interstellar (2014)</h3>
            <div class="movie-info">
                Genre: <span class="genre">Sci-Fi</span>
                | Rating: <span class="rating">9.0/10</span>
            </div>
            <p>
                A team of explorers travels beyond this galaxy
                to discover whether mankind has a future among
                the stars.
            </p>
        </div>

        <div class="movie" data-genre="Action">
            <h3>The Dark Knight (2008)</h3>
            <div class="movie-info">
                Genre: <span class="genre">Action</span>
                | Rating: <span class="rating">9.0/10</span>
            </div>
            <p>
                Batman faces his greatest challenge when the
                Joker brings chaos and destruction to Gotham City.
            </p>
        </div>

        <div class="movie" data-genre="Adventure">
            <h3>The Lord of the Rings: The Fellowship of the Ring (2001)</h3>
            <div class="movie-info">
                Genre: <span class="genre">Adventure</span>
                | Rating: <span class="rating">8.9/10</span>
            </div>
            <p>
                A young hobbit begins an epic journey to destroy
                a powerful ring and save Middle-earth.
            </p>
        </div>

        <div class="movie" data-genre="Drama">
            <h3>The Shawshank Redemption (1994)</h3>
            <div class="movie-info">
                Genre: <span class="genre">Drama</span>
                | Rating: <span class="rating">9.3/10</span>
            </div>
            <p>
                Two imprisoned men form an unlikely friendship
                while searching for hope and freedom.
            </p>
        </div>

        <div class="movie" data-genre="Comedy">
            <h3>Back to the Future (1985)</h3>
            <div class="movie-info">
                Genre: <span class="genre">Comedy</span>
                | Rating: <span class="rating">8.5/10</span>
            </div>
            <p>
                A teenager accidentally travels back in time
                and must ensure his parents meet in order to
                preserve his own future.
            </p>
        </div>

    </div>

    <p id="noResults" style="display:none;">
        No movies found.
    </p>

    <hr>

    <h2>About This Collection</h2>

    <p>
        This website is a personal movie database.
        More movies and categories can be added at any time.
        Use the search bar to find your favorite movies.
    </p>

    <footer>
        &copy; 2026 My Movie Collection. All rights reserved.
    </footer>

    <script>
        function filterMovies() {
            const search = document
                .getElementById("search")
                .value.toLowerCase();

            const genre = document
                .getElementById("genreFilter")
                .value;

            const movies = document.querySelectorAll(".movie");
            let visibleCount = 0;

            movies.forEach(movie => {
                const title = movie.querySelector("h3")
                    .textContent.toLowerCase();

                const description = movie.querySelector("p")
                    .textContent.toLowerCase();

                const movieGenre = movie.dataset.genre;

                const matchesSearch =
                    title.includes(search) ||
                    description.includes(search);

                const matchesGenre =
                    genre === "all" || movieGenre === genre;

                if (matchesSearch && matchesGenre) {
                    movie.style.display = "block";
                    visibleCount++;
                } else {
                    movie.style.display = "none";
                }
            });

            document.getElementById("noResults").style.display =
                visibleCount === 0 ? "block" : "none";
        }
    </script>

</body>
</html>
