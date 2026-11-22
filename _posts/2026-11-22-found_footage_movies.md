
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Movie List</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 40px auto;
            padding: 0 20px;
            line-height: 1.6;
            color: #333;
        }

        h1 {
            border-bottom: 1px solid #ddd;
            padding-bottom: 10px;
        }

        hr {
            border: none;
            border-top: 1px solid #ddd;
            margin: 25px 0;
        }

        .movie {
            margin: 15px 0;
        }

        .movie-title {
            font-weight: bold;
        }

        .year {
            color: #888;
        }

        .description {
            margin: 2px 0;
            color: #555;
        }
    </style>
</head>

<body>

    <h1>My Movie List</h1>

    <p>
        A collection of movies worth watching.
    </p>

    <hr>

    <h2>Movies</h2>

    <div id="movieList"></div>

    <script>
        const movies = [
            {
                title: "Interstellar",
                year: 2014,
                description: "A group of astronauts travels through a wormhole in search of a new home for humanity."
            },
            {
                title: "The Dark Knight",
                year: 2008,
                description: "Batman faces the Joker, a criminal mastermind threatening Gotham City."
            },
            {
                title: "Inception",
                year: 2010,
                description: "A thief enters people's dreams to steal secrets and attempt an impossible heist."
            },
            {
                title: "Fight Club",
                year: 1999,
                description: "An insomniac and a mysterious stranger create an underground fighting club."
            },
            {
                title: "The Shawshank Redemption",
                year: 1994,
                description: "Two prisoners form a friendship while holding on to hope and freedom."
            },
            {
                title: "Blade Runner 2049",
                year: 2017,
                description: "A blade runner uncovers a secret that could change the future of humanity."
            },
            {
                title: "Goodfellas",
                year: 1990,
                description: "The rise and fall of a man involved in the world of organized crime."
            },
            {
                title: "Back to the Future",
                year: 1985,
                description: "A teenager accidentally travels back in time using a modified DeLorean."
            }
        ];

        // Sort movies alphabetically by title
        movies.sort((a, b) =>
            a.title.localeCompare(b.title)
        );

        // Display movies
        const movieList = document.getElementById("movieList");

        movies.forEach(movie => {
            const entry = document.createElement("div");
            entry.className = "movie";

            const title = document.createElement("div");
            title.className = "movie-title";
            title.textContent = movie.title + " ";

            const year = document.createElement("span");
            year.className = "year";
            year.textContent = "(" + movie.year + ")";

            title.appendChild(year);

            const description = document.createElement("p");
            description.className = "description";
            description.textContent = movie.description;

            entry.appendChild(title);
            entry.appendChild(description);

            movieList.appendChild(entry);
        });
    </script>

</body>
</html>
