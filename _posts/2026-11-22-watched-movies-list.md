<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>my watched movies</title>

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
    </p>

    <hr>

    <div id="movieList"></div>

    <script>
        const movies = [
            {
                title: "Trollhunter",
                year: 2010,
                description: "found footage, Norway, Trolls"
            },
            {
                title: "Reign of Fire",
                year: 2002,
                description: "Great Britain, 2020, dragons"
            },
            {
                title: "Blair Witch Project",
                year: 1999,
                description: "found footage, Horror, forest, group"
            },
            {
                title: "A Cure for Wellness",
                year: 2016,
                description: "horror, mystery, eels"
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
