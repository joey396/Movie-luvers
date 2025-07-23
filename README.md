<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movies Lovers - Movie Database</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

```
    body {
        font-family: 'Arial', sans-serif;
        background: #000000;
        color: white;
        min-height: 100vh;
    }

    .header {
        background: rgba(0, 0, 0, 0.8);
        padding: 1.5rem 2rem;
        backdrop-filter: blur(10px);
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }

    .nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        max-width: 1200px;
        margin: 0 auto;
    }

    .logo {
        font-size: 2rem;
        font-weight: bold;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .search-container {
        display: flex;
        gap: 1rem;
        align-items: center;
    }

    .search-box {
        padding: 0.8rem 1.2rem;
        border: none;
        border-radius: 25px;
        background: rgba(255, 255, 255, 0.1);
        color: white;
        font-size: 1rem;
        backdrop-filter: blur(10px);
        border: 1px solid rgba(255, 255, 255, 0.2);
        width: 300px;
    }

    .search-box::placeholder {
        color: rgba(255, 255, 255, 0.7);
    }

    .search-btn {
        padding: 0.8rem 1.5rem;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        border: none;
        border-radius: 25px;
        color: white;
        font-weight: bold;
        cursor: pointer;
        transition: transform 0.3s ease;
    }

    .search-btn:hover {
        transform: translateY(-2px);
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 2rem;
    }

    .featured {
        margin-bottom: 3rem;
    }

    .section-title {
        font-size: 2rem;
        margin-bottom: 1.5rem;
        text-align: center;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .movie-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 2rem;
        margin-bottom: 3rem;
    }

    .movie-card {
        background: rgba(255, 255, 255, 0.1);
        border-radius: 15px;
        overflow: hidden;
        backdrop-filter: blur(10px);
        border: 1px solid rgba(255, 255, 255, 0.2);
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        cursor: pointer;
        position: relative;
    }

    .movie-card:hover {
        transform: translateY(-10px);
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
    }

    .movie-poster {
        width: 100%;
        height: 350px;
        background: linear-gradient(45deg, #333, #555);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 3rem;
        color: rgba(255, 255, 255, 0.3);
        position: relative;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
    }

    .movie-poster img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 0;
    }

    .poster-placeholder {
        font-size: 3rem;
        color: rgba(255, 255, 255, 0.3);
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        background: linear-gradient(45deg, #333, #555);
    }

    .play-overlay {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        opacity: 0;
        transition: opacity 0.3s ease;
    }

    .movie-card:hover .play-overlay {
        opacity: 1;
    }

    .play-button {
        width: 80px;
        height: 80px;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: transform 0.3s ease;
    }

    .play-button:hover {
        transform: scale(1.1);
    }

    .play-button::before {
        content: '▶';
        font-size: 2rem;
        color: white;
        margin-left: 5px;
    }

    .movie-info {
        padding: 1.5rem;
    }

    .movie-title {
        font-size: 1.2rem;
        font-weight: bold;
        margin-bottom: 0.5rem;
    }

    .movie-year {
        color: rgba(255, 255, 255, 0.7);
        margin-bottom: 0.5rem;
    }

    .movie-rating {
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        padding: 0.3rem 0.8rem;
        border-radius: 15px;
        font-size: 0.9rem;
        font-weight: bold;
        display: inline-block;
    }

    .movie-genre {
        color: rgba(255, 255, 255, 0.8);
        font-size: 0.9rem;
        margin-top: 0.5rem;
    }

    .filters {
        display: flex;
        gap: 1rem;
        margin-bottom: 2rem;
        flex-wrap: wrap;
        justify-content: center;
    }

    .filter-btn {
        padding: 0.8rem 1.5rem;
        background: rgba(255, 255, 255, 0.1);
        border: 1px solid rgba(255, 255, 255, 0.2);
        border-radius: 25px;
        color: white;
        cursor: pointer;
        transition: all 0.3s ease;
        backdrop-filter: blur(10px);
    }

    .filter-btn:hover, .filter-btn.active {
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        transform: translateY(-2px);
    }

    .hero {
        text-align: center;
        padding: 3rem 0;
        background: rgba(0, 0, 0, 0.3);
        border-radius: 20px;
        margin-bottom: 3rem;
        backdrop-filter: blur(10px);
    }

    .hero h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .hero p {
        font-size: 1.2rem;
        color: rgba(255, 255, 255, 0.8);
    }

    /* Modal Styles */
    .modal {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.9);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;
        backdrop-filter: blur(10px);
    }

    .modal-content {
        background: rgba(255,255,255,0.1);
        padding: 2rem;
        border-radius: 20px;
        max-width: 600px;
        width: 90%;
        text-align: center;
        backdrop-filter: blur(10px);
        border: 1px solid rgba(255,255,255,0.2);
        position: relative;
    }

    .modal-buttons {
        display: flex;
        gap: 1rem;
        justify-content: center;
        margin-top: 2rem;
    }

    .btn {
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        border: none;
        padding: 12px 24px;
        border-radius: 25px;
        color: white;
        font-weight: bold;
        cursor: pointer;
        transition: transform 0.3s ease;
    }

    .btn:hover {
        transform: translateY(-2px);
    }

    .btn-secondary {
        background: rgba(255,255,255,0.2);
    }

    /* Video Player Styles */
    .video-modal {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.95);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 2000;
    }

    .video-container {
        width: 90%;
        max-width: 1000px;
        position: relative;
    }

    .video-player {
        width: 100%;
        max-height: 80vh;
        border-radius: 10px;
    }

    .close-video {
        position: absolute;
        top: -50px;
        right: 0;
        background: rgba(255,255,255,0.2);
        border: none;
        color: white;
        font-size: 2rem;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .error-message {
        background: rgba(255, 0, 0, 0.2);
        border: 1px solid rgba(255, 0, 0, 0.5);
        color: #ff6b6b;
        padding: 1rem;
        border-radius: 10px;
        margin-top: 1rem;
    }

    /* Loading Spinner Styles */
    .loading {
        text-align: center;
        padding: 50px;
        font-size: 18px;
        color: #fff;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 20px;
    }

    .loading-spinner {
        width: 50px;
        height: 50px;
        border: 4px solid rgba(255, 255, 255, 0.3);
        border-top: 4px solid #ff6b6b;
        border-radius: 50%;
        animation: spin 1s linear infinite;
    }

    .loading-text {
        background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        font-weight: bold;
        font-size: 1.2rem;
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }

    /* Fade in animation for movies */
    .movie-card {
        opacity: 0;
        animation: fadeIn 0.5s ease forwards;
    }

    .movie-card:nth-child(1) { animation-delay: 0.1s; }
    .movie-card:nth-child(2) { animation-delay: 0.2s; }
    .movie-card:nth-child(3) { animation-delay: 0.3s; }
    .movie-card:nth-child(4) { animation-delay: 0.4s; }
    .movie-card:nth-child(5) { animation-delay: 0.5s; }
    .movie-card:nth-child(6) { animation-delay: 0.6s; }
    .movie-card:nth-child(7) { animation-delay: 0.7s; }
    .movie-card:nth-child(8) { animation-delay: 0.8s; }

    @keyframes fadeIn {
        from {
            opacity: 0;
            transform: translateY(20px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @media (max-width: 768px) {
        .nav {
            flex-direction: column;
            gap: 1rem;
        }
        
        .search-box {
            width: 100%;
        }
        
        .hero h1 {
            font-size: 2rem;
        }
        
        .filters {
            justify-content: flex-start;
        }

        .modal-buttons {
            flex-direction: column;
        }
    }
</style>
```

</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo">🎬 Movies Lovers</div>
            <div class="search-container">
                <input type="text" class="search-box" placeholder="Search movies..." id="searchInput">
                <button class="search-btn" onclick="searchMovies()">Search</button>
            </div>
        </nav>
    </header>

```
<div class="container">
    <div class="hero">
        <h1>Discover Amazing Movies</h1>
        <p>Your ultimate destination for movie information and reviews</p>
    </div>

    <div class="filters">
        <button class="filter-btn active" onclick="filterMovies('all')">All Movies</button>
        <button class="filter-btn" onclick="filterMovies('action')">Action</button>
        <button class="filter-btn" onclick="filterMovies('drama')">Drama</button>
        <button class="filter-btn" onclick="filterMovies('comedy')">Comedy</button>
        <button class="filter-btn" onclick="filterMovies('sci-fi')">Sci-Fi</button>
        <button class="filter-btn" onclick="filterMovies('thriller')">Thriller</button>
    </div>

    <section class="featured">
        <h2 class="section-title">Featured Movies</h2>
        <div class="movie-grid" id="movieGrid">
            <!-- Movies will be populated by JavaScript -->
        </div>
    </section>
</div>

<script>
    // Sample movie data with video file paths and poster images
    const movies = [
        {
            id: 1,
            title: "The Matrix Resurrections",
            year: 2021,
            rating: 8.2,
            genre: "sci-fi",
            description: "Neo must once again choose between the Matrix and reality.",
            videoPath: "videos/matrix-resurrections.mp4",
            posterPath: "posters/matrix-resurrections.jpg" // Add your poster image path here
        },
        {
            id: 2,
            title: "Dune",
            year: 2021,
            rating: 8.8,
            genre: "sci-fi",
            description: "A mythic journey across a desert planet.",
            videoPath: "videos/dune.mp4",
            posterPath: "posters/dune.jpg"
        },
        {
            id: 3,
            title: "No Time to Die",
            year: 2021,
            rating: 8.1,
            genre: "action",
            description: "James Bond's final mission.",
            videoPath: "videos/no-time-to-die.mp4",
            posterPath: "posters/no-time-to-die.jpg"
        },
        {
            id: 4,
            title: "The Power of the Dog",
            year: 2021,
            rating: 7.8,
            genre: "drama",
            description: "A psychological western drama.",
            videoPath: "videos/power-of-the-dog.mp4",
            posterPath: "posters/power-of-the-dog.jpg"
        },
        {
            id: 5,
            title: "Spider-Man: No Way Home",
            year: 2021,
            rating: 9.1,
            genre: "action",
            description: "Spider-Man faces villains from across the multiverse.",
            videoPath: "videos/spiderman-nwh.mp4",
            posterPath: "posters/spiderman-nwh.jpg"
        },
        {
            id: 6,
            title: "Free Guy",
            year: 2021,
            rating: 7.9,
            genre: "comedy",
            description: "An NPC discovers he's in a video game.",
            videoPath: "videos/free-guy.mp4",
            posterPath: "posters/free-guy.jpg"
        },
        {
            id: 7,
            title: "A Quiet Place Part II",
            year: 2020,
            rating: 8.3,
            genre: "thriller",
            description: "The Abbott family faces new terrors.",
            videoPath: "videos/quiet-place-2.mp4",
            posterPath: "posters/quiet-place-2.jpg"
        },
        {
            id: 8,
            title: "The French Dispatch",
            year: 2021,
            rating: 7.6,
            genre: "comedy",
            description: "An anthology of stories from a French magazine.",
            videoPath: "videos/french-dispatch.mp4",
            posterPath: "posters/french-dispatch.jpg"
        }
    ];

    let currentFilter = 'all';
    let allMovies = [...movies];

    // Show loading spinner
    function showLoading() {
        const grid = document.getElementById('movieGrid');
        grid.innerHTML = `
            <div class="loading">
                <div class="loading-spinner"></div>
                <div class="loading-text">Loading amazing movies...</div>
            </div>
        `;
    }

    // Hide loading spinner
    function hideLoading() {
        const loading = document.querySelector('.loading');
        if (loading) {
            loading.remove();
        }
    }

    // Simulate loading delay for better UX
    function simulateLoading(callback, data) {
        showLoading();
        setTimeout(() => {
            hideLoading();
            callback(data);
        }, 300);
    }

    function displayMovies(moviesToShow) {
        const grid = document.getElementById('movieGrid');
        grid.innerHTML = '';

        if (moviesToShow.length === 0) {
            grid.innerHTML = `
                <div style="grid-column: 1/-1; text-align: center; padding: 50px; color: rgba(255,255,255,0.7);">
                    <h3>No movies found</h3>
                    <p>Try searching for something else or check different genres!</p>
                </div>
            `;
            return;
        }

        moviesToShow.forEach(movie => {
            const movieCard = document.createElement('div');
            movieCard.className = 'movie-card';
            
            movieCard.innerHTML = `
                <div class="movie-poster">
                    <img src="${movie.posterPath}" alt="${movie.title}" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';" style="display: block;">
                    <div class="poster-placeholder" style="display: none;">🎬</div>
                    <div class="play-overlay">
                        <div class="play-button" onclick="playMovie(${movie.id})"></div>
                    </div>
                </div>
                <div class="movie-info">
                    <div class="movie-title">${movie.title}</div>
                    <div class="movie-year">${movie.year}</div>
                    <div class="movie-rating">⭐ ${movie.rating}/10</div>
                    <div class="movie-genre">${movie.genre.toUpperCase()}</div>
                </div>
            `;
            
            // Add click handler for movie info (not the play button)
            movieCard.addEventListener('click', (e) => {
                if (!e.target.closest('.play-button')) {
                    showMovieDetails(movie);
                }
            });
            
            grid.appendChild(movieCard);
        });
    }

    function filterMovies(genre) {
        // Update active filter button
        document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.classList.remove('active');
        });
        event.target.classList.add('active');

        currentFilter = genre;
        let filteredMovies;

        if (genre === 'all') {
            filteredMovies = allMovies;
        } else {
            filteredMovies = allMovies.filter(movie => movie.genre === genre);
        }

        simulateLoading(displayMovies, filteredMovies);
    }

    function searchMovies() {
        const searchTerm = document.getElementById('searchInput').value.toLowerCase();
        
        if (searchTerm === '') {
            filterMovies(currentFilter);
            return;
        }

        const searchResults = allMovies.filter(movie => 
            movie.title.toLowerCase().includes(searchTerm) ||
            movie.genre.toLowerCase().includes(searchTerm) ||
            movie.year.toString().includes(searchTerm)
        );

        simulateLoading(displayMovies, searchResults);
    }

    function showMovieDetails(movie) {
        const modal = document.createElement('div');
        modal.className = 'modal';
        
        modal.innerHTML = `
            <div class="modal-content">
                <h2 style="color: white; margin-bottom: 1rem; font-size: 1.5rem;">${movie.title}</h2>
                <div style="color: rgba(255,255,255,0.8); margin-bottom: 1rem;">
                    📅 Year: ${movie.year}<br>
                    ⭐ Rating: ${movie.rating}/10<br>
                    🎭 Genre: ${movie.genre.toUpperCase()}
                </div>
                <p style="color: rgba(255,255,255,0.9); margin-bottom: 2rem; line-height: 1.5;">
                    ${movie.description}
                </p>
                <div class="modal-buttons">
                    <button class="btn" onclick="playMovie(${movie.id}); closeModal()">▶ Play Movie</button>
                    <button class="btn btn-secondary" onclick="closeModal()">Close</button>
                </div>
            </div>
        `;
        
        modal.onclick = (e) => {
            if (e.target === modal) closeModal();
        };
        
        document.body.appendChild(modal);
    }

    function playMovie(movieId) {
        const movie = movies.find(m => m.id === movieId);
        if (!movie) return;

        // Create video modal
        const videoModal = document.createElement('div');
        videoModal.className = 'video-modal';
        videoModal.id = 'videoModal';
        
        videoModal.innerHTML = `
            <div class="video-container">
                <button class="close-video" onclick="closeVideo()">×</button>
                <video class="video-player" controls autoplay id="videoPlayer">
                    <source src="${movie.videoPath}" type="video/mp4">
                    <p style="color: white;">Your browser doesn't support video playback.</p>
                </video>
                <div id="videoError" style="display: none;">
                    <div class="error-message">
                        <h3>Video not found</h3>
                        <p>The video file "${movie.videoPath}" could not be loaded.</p>
                        <p><strong>To fix this:</strong></p>
                        <ul style="text-align: left; margin-top: 1rem;">
                            <li>Create a "videos" folder in your project directory</li>
                            <li>Add your movie files (MP4 format recommended)</li>
                            <li>Update the videoPath in the movies array to match your file names</li>
                        </ul>
                    </div>
                </div>
            </div>
        `;
        
        document.body.appendChild(videoModal);

        // Handle video loading errors
        const videoPlayer = document.getElementById('videoPlayer');
        const videoError = document.getElementById('videoError');
        
        videoPlayer.addEventListener('error', () => {
            videoPlayer.style.display = 'none';
            videoError.style.display = 'block';
        });

        // Close video when clicking outside
        videoModal.addEventListener('click', (e) => {
            if (e.target === videoModal) {
                closeVideo();
            }
        });

        // Handle ESC key to close video
        document.addEventListener('keydown', handleEscKey);
    }

    function closeVideo() {
        const videoModal = document.getElementById('videoModal');
        const videoPlayer = document.getElementById('videoPlayer');
        
        if (videoPlayer) {
            videoPlayer.pause();
        }
        
        if (videoModal) {
            videoModal.remove();
        }
        
        // Remove ESC key listener
        document.removeEventListener('keydown', handleEscKey);
    }

    function closeModal() {
        const modal = document.querySelector('.modal');
        if (modal) {
            modal.remove();
        }
    }

    function handleEscKey(e) {
        if (e.key === 'Escape') {
            closeVideo();
        }
    }

    // Handle search on Enter key
    document.getElementById('searchInput').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
            searchMovies();
        }
    });

    // Initialize the page
    document.addEventListener('DOMContentLoaded', function() {
        displayMovies(allMovies);
    });
</script>
```

</body>
</html>
