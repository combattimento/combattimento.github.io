
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Movie Collection</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 900px;
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
            display: flex;
            gap: 18px;
            margin: 20px 0;
            align-items: center;
            min-height: 110px;
        }

        .poster {
            width: 75px;
            height: 110px;
            flex-shrink: 0;
            background: #eee;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            color: #888;
            font-size: 12px;
        }

        .poster img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .movie-info {
            min-width: 0;
        }

        .movie-title {
            font-weight: bold;
        }

        .movie-meta {
            color: #888;
            font-size: 14px;
        }

        .description {
            margin: 2px 0;
            color: #555;
        }

        @media (max-width: 500px) {
            body {
                margin: 20px auto;
            }

            .poster {
                width: 65px;
                height: 95px;
            }

            .movie {
                gap: 12px;
            }
        }
    </style>
</head>

<body>

    <h1>My Movie Collection</h1>

    <p>
        A collection of movies worth watching.
        Horror, science fiction, fantasy and everything in between.
    </p>

    <hr>

    <h2>Movies</h2>

    <div id="movieList"></div>

    <script>

        const movies = [

            {
                title: "Trollhunter",
                year: 2010,
                description: "Found footage, Norway, trolls"
            },
            {
                title: "Reign of Fire",
                year: 2002,
                description: "Great Britain, 2020, dragons"
            },
            {
                title: "The Blair Witch Project",
                year: 1999,
                description: "Found footage, horror, forest, group"
            },
            {
                title: "A Cure for Wellness",
                year: 2016,
                description: "Horror, mystery, eels"
            },
            {
                title: "Europa Report",
                year: 2013,
                description: "Found footage, sci-fi, space, alien"
            }

        ];

        // Sort alphabetically by movie title

        movies.sort((a, b) =>
            a.title.localeCompare(b.title)
        );

        const movieList = document.getElementById("movieList");

        movies.forEach(movie => {

            const entry = document.createElement("div");
            entry.className = "movie";

            const poster = document.createElement("div");
            poster.className = "poster";
            poster.textContent = "No poster";

            const info = document.createElement("div");
            info.className = "movie-info";

            const title = document.createElement("div");
            title.className = "movie-title";
            title.textContent = movie.title;

            const year = document.createElement("div");
            year.className = "movie-meta";
            year.textContent = movie.year;

            const description = document.createElement("p");
            description.className = "description";
            description.textContent = movie.description;

            info.appendChild(title);
            info.appendChild(year);
            info.appendChild(description);

            entry.appendChild(poster);
            entry.appendChild(info);

            movieList.appendChild(entry);

            // Search for movie poster using TMDB

            const apiKey = "YOUR_TMDB_API_KEY";

            const searchUrl =
                "https://api.themoviedb.org/3/search/movie?api_key=" +
                apiKey +
                "&query=" +
                encodeURIComponent(movie.title) +
                "&year=" + movie.year;

            fetch(searchUrl)
                .then(response => response.json())
                .then(data => {

                    if (data.results && data.results.length > 0) {

                        const result = data.results[0];

                        if (result.poster_path) {

                            const img = document.createElement("img");

                            img.src =
                                "https://image.tmdb.org/t/p/w342" +
                                result.poster_path;

                            img.alt = movie.title + " poster";

                            poster.textContent = "";
                            poster.appendChild(img);
                        }
                    }

                })
                .catch(error => {
                    console.log("Could not load poster:", movie.title);
                });

        });

    </script>

</body>
</html>
