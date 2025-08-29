
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lecteur Musique Pro</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: white;
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 0 4px 8px rgba(0,0,0,0.3);
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .controls-panel {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            border: 1px solid rgba(255,255,255,0.2);
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
        }

        .file-input-container {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            align-items: center;
        }

        .file-input-wrapper {
            position: relative;
            overflow: hidden;
            display: inline-block;
        }

        .file-input-wrapper input[type=file] {
            position: absolute;
            left: -9999px;
        }

        .file-input-label {
            background: linear-gradient(45deg, #ff6b6b, #ee5a52);
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            border: none;
            color: white;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255,107,107,0.3);
        }

        .file-input-label:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255,107,107,0.4);
        }

        .search-bar {
            flex: 1;
            min-width: 200px;
        }

        .search-bar input {
            width: 100%;
            padding: 12px 20px;
            border: none;
            border-radius: 25px;
            background: rgba(255,255,255,0.9);
            color: #333;
            font-size: 16px;
            outline: none;
            transition: all 0.3s ease;
        }

        .search-bar input:focus {
            box-shadow: 0 0 20px rgba(78,205,196,0.5);
            transform: scale(1.02);
        }

        .filter-controls {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .filter-btn {
            padding: 8px 16px;
            border: 2px solid rgba(255,255,255,0.3);
            background: transparent;
            color: white;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .filter-btn:hover, .filter-btn.active {
            background: rgba(255,255,255,0.2);
            border-color: #4ecdc4;
            box-shadow: 0 4px 15px rgba(78,205,196,0.3);
        }

        .sort-controls {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .sort-select {
            padding: 8px 15px;
            border: none;
            border-radius: 15px;
            background: rgba(255,255,255,0.9);
            color: #333;
            cursor: pointer;
            outline: none;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 400px;
            gap: 30px;
        }

        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        .playlist-section {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 25px;
            border: 1px solid rgba(255,255,255,0.2);
            max-height: 70vh;
            overflow-y: auto;
        }

        .playlist-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .playlist-header h2 {
            color: #4ecdc4;
        }

        .playlist-counter {
            background: rgba(78,205,196,0.3);
            padding: 5px 15px;
            border-radius: 15px;
            font-size: 14px;
        }

        .song-item {
            display: flex;
            align-items: center;
            padding: 15px;
            margin-bottom: 10px;
            background: rgba(255,255,255,0.05);
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid transparent;
            position: relative;
            overflow: hidden;
        }

        .song-item:hover {
            background: rgba(255,255,255,0.1);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }

        .song-item.playing {
            background: linear-gradient(45deg, rgba(78,205,196,0.3), rgba(255,107,107,0.3));
            border-color: #4ecdc4;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 0 20px rgba(78,205,196,0.3); }
            50% { box-shadow: 0 0 30px rgba(78,205,196,0.6); }
        }

        .song-info {
            flex: 1;
            margin-left: 15px;
            min-width: 0;
        }

        .song-title {
            font-weight: bold;
            font-size: 16px;
            margin-bottom: 5px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .song-duration {
            font-size: 14px;
            color: rgba(255,255,255,0.7);
        }

        .song-actions {
            display: flex;
            gap: 8px;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .song-item:hover .song-actions {
            opacity: 1;
        }

        .action-btn {
            background: none;
            border: none;
            color: white;
            cursor: pointer;
            padding: 8px;
            border-radius: 50%;
            transition: all 0.3s ease;
            font-size: 18px;
        }

        .action-btn:hover {
            background: rgba(255,255,255,0.2);
            transform: scale(1.1);
        }

        .favorite {
            color: #ff6b6b;
        }

        .player-section {
            position: sticky;
            top: 20px;
        }

        .player-card {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255,255,255,0.2);
            text-align: center;
            margin-bottom: 20px;
        }

        .album-art {
            width: 200px;
            height: 200px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 15px;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: rgba(255,255,255,0.3);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            animation: rotate 20s linear infinite;
        }

        .album-art.playing {
            animation: rotate 3s linear infinite;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .current-song-info {
            margin-bottom: 25px;
        }

        .current-title {
            font-size: 1.4rem;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .progress-container {
            margin: 20px 0;
        }

        .progress-bar {
            width: 100%;
            height: 6px;
            background: rgba(255,255,255,0.2);
            border-radius: 3px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .progress {
            height: 100%;
            background: linear-gradient(45deg, #4ecdc4, #44a08d);
            border-radius: 3px;
            transition: width 0.1s ease;
            position: relative;
        }

        .progress::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            animation: shine 2s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .time-info {
            display: flex;
            justify-content: space-between;
            font-size: 14px;
            color: rgba(255,255,255,0.7);
            margin-top: 5px;
        }

        .player-controls {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 25px 0;
        }

        .control-btn {
            background: none;
            border: none;
            color: white;
            cursor: pointer;
            font-size: 1.5rem;
            padding: 15px;
            border-radius: 50%;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .control-btn:hover {
            background: rgba(255,255,255,0.2);
            transform: scale(1.1);
        }

        .play-btn {
            background: linear-gradient(45deg, #4ecdc4, #44a08d);
            font-size: 2rem;
            padding: 20px;
            box-shadow: 0 6px 20px rgba(78,205,196,0.4);
        }

        .play-btn:hover {
            box-shadow: 0 8px 25px rgba(78,205,196,0.6);
        }

        .volume-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .volume-slider {
            width: 100px;
            height: 4px;
            background: rgba(255,255,255,0.3);
            border-radius: 2px;
            outline: none;
            cursor: pointer;
        }

        .volume-slider::-webkit-slider-thumb {
            appearance: none;
            width: 16px;
            height: 16px;
            background: #4ecdc4;
            border-radius: 50%;
            cursor: pointer;
        }

        .equalizer {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 20px;
            border: 1px solid rgba(255,255,255,0.2);
        }

        .equalizer h3 {
            text-align: center;
            margin-bottom: 15px;
            color: #4ecdc4;
        }

        .eq-bars {
            display: flex;
            justify-content: space-around;
            align-items: end;
            height: 60px;
            gap: 5px;
        }

        .eq-bar {
            width: 20px;
            background: linear-gradient(to top, #4ecdc4, #44a08d);
            border-radius: 10px 10px 0 0;
            animation: eq-bounce 1s ease-in-out infinite;
        }

        .eq-bar:nth-child(1) { height: 20px; animation-delay: 0s; }
        .eq-bar:nth-child(2) { height: 35px; animation-delay: 0.1s; }
        .eq-bar:nth-child(3) { height: 45px; animation-delay: 0.2s; }
        .eq-bar:nth-child(4) { height: 25px; animation-delay: 0.3s; }
        .eq-bar:nth-child(5) { height: 40px; animation-delay: 0.4s; }
        .eq-bar:nth-child(6) { height: 30px; animation-delay: 0.5s; }

        @keyframes eq-bounce {
            0%, 100% { transform: scaleY(1); }
            50% { transform: scaleY(0.5); }
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(10px);
        }

        .modal-content {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            margin: 10% auto;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 500px;
            color: white;
            position: relative;
        }

        .close {
            position: absolute;
            right: 20px;
            top: 15px;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
            color: white;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 10px;
            background: rgba(255,255,255,0.9);
            color: #333;
            font-size: 16px;
            outline: none;
        }

        .btn {
            background: linear-gradient(45deg, #4ecdc4, #44a08d);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(78,205,196,0.4);
        }

        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(78,205,196,0.9);
            color: white;
            padding: 15px 25px;
            border-radius: 10px;
            z-index: 1001;
            transform: translateX(300px);
            transition: transform 0.3s ease;
        }

        .toast.show {
            transform: translateX(0);
        }

        .drag-over {
            border: 2px dashed #4ecdc4;
            background: rgba(78,205,196,0.1);
        }

        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(255,255,255,0.1);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb {
            background: #4ecdc4;
            border-radius: 4px;
        }

        .playlist-stats {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            font-size: 14px;
        }

        .stat {
            background: rgba(255,255,255,0.1);
            padding: 8px 12px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1>🎵 Lecteur Musique Pro</h1>
            <p>Votre expérience musicale ultime</p>
        </header>

        <div class="controls-panel">
            <div class="file-input-container">
                <div class="file-input-wrapper">
                    <input type="file" id="fileInput" accept="audio/*" multiple>
                    <label for="fileInput" class="file-input-label">
                        📁 Ajouter des Musiques
                    </label>
                </div>
                <div class="search-bar">
                    <input type="text" id="searchInput" placeholder="🔍 Rechercher une chanson...">
                </div>
            </div>

            <div class="filter-controls">
                <button class="filter-btn active" data-filter="all">Tous</button>
                <button class="filter-btn" data-filter="favorites">❤️ Favoris</button>
                <button class="filter-btn" data-filter="recent">🕒 Récents</button>
                <div class="sort-controls">
                    <label>Trier par:</label>
                    <select id="sortSelect" class="sort-select">
                        <option value="name">Nom</option>
                        <option value="duration">Durée</option>
                        <option value="date">Date d'ajout</option>
                    </select>
                    <button id="shuffleBtn" class="filter-btn">🔀 Aléatoire</button>
                </div>
            </div>
        </div>

        <div class="main-content">
            <div class="playlist-section">
                <div class="playlist-header">
                    <h2>Ma Playlist</h2>
                    <div class="playlist-counter">
                        <span id="songCount">0</span> chansons
                    </div>
                </div>
                <div class="playlist-stats">
                    <div class="stat">Durée totale: <span id="totalDuration">0:00</span></div>
                    <div class="stat">Favoris: <span id="favoriteCount">0</span></div>
                </div>
                <div id="playlist" class="playlist"></div>
            </div>

            <div class="player-section">
                <div class="player-card">
                    <div id="albumArt" class="album-art">🎵</div>
                    <div class="current-song-info">
                        <div id="currentTitle" class="current-title">Sélectionnez une chanson</div>
                        <div id="currentArtist" class="current-artist">Artist</div>
                    </div>
                    
                    <div class="progress-container">
                        <div id="progressBar" class="progress-bar">
                            <div id="progress" class="progress"></div>
                        </div>
                        <div class="time-info">
                            <span id="currentTime">0:00</span>
                            <span id="totalTime">0:00</span>
                        </div>
                    </div>

                    <div class="player-controls">
                        <button id="prevBtn" class="control-btn">⏮️</button>
                        <button id="playPauseBtn" class="control-btn play-btn">▶️</button>
                        <button id="nextBtn" class="control-btn">⏭️</button>
                        <button id="repeatBtn" class="control-btn">🔁</button>
                    </div>

                    <div class="volume-container">
                        <span>🔊</span>
                        <input type="range" id="volumeSlider" class="volume-slider" min="0" max="100" value="50">
                        <span id="volumeValue">50%</span>
                    </div>
                </div>

                <div class="equalizer">
                    <h3>Égaliseur</h3>
                    <div class="eq-bars">
                        <div class="eq-bar"></div>
                        <div class="eq-bar"></div>
                        <div class="eq-bar"></div>
                        <div class="eq-bar"></div>
                        <div class="eq-bar"></div>
                        <div class="eq-bar"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal pour éditer les chansons -->
    <div id="editModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <h2>Éditer la chanson</h2>
            <div class="form-group">
                <label>Titre:</label>
                <input type="text" id="editTitle">
            </div>
            <div class="form-group">
                <label>Artiste:</label>
                <input type="text" id="editArtist">
            </div>
            <button id="saveEdit" class="btn">Sauvegarder</button>
        </div>
    </div>

    <audio id="audioPlayer" preload="metadata"></audio>

    <script>
        class MusicPlayer {
            constructor() {
                this.songs = [];
                this.currentSongIndex = 0;
                this.isPlaying = false;
                this.isShuffled = false;
                this.isRepeating = false;
                this.currentFilter = 'all';
                this.audio = document.getElementById('audioPlayer');
                this.editingSongIndex = -1;
                
                this.initializeElements();
                this.setupEventListeners();
                this.loadFromStorage();
                this.setupDragAndDrop();
                
                // Musiques d'exemple avec sons tendances
                this.addSampleSongs();
            }

            initializeElements() {
                // Elements DOM
                this.fileInput = document.getElementById('fileInput');
                this.playlist = document.getElementById('playlist');
                this.playPauseBtn = document.getElementById('playPauseBtn');
                this.prevBtn = document.getElementById('prevBtn');
                this.nextBtn = document.getElementById('nextBtn');
                this.repeatBtn = document.getElementById('repeatBtn');
                this.shuffleBtn = document.getElementById('shuffleBtn');
                this.progressBar = document.getElementById('progressBar');
                this.progress = document.getElementById('progress');
                this.currentTime = document.getElementById('currentTime');
                this.totalTime = document.getElementById('totalTime');
                this.currentTitle = document.getElementById('currentTitle');
                this.currentArtist = document.getElementById('currentArtist');
                this.volumeSlider = document.getElementById('volumeSlider');
                this.volumeValue = document.getElementById('volumeValue');
                this.searchInput = document.getElementById('searchInput');
                this.sortSelect = document.getElementById('sortSelect');
                this.songCount = document.getElementById('songCount');
                this.totalDuration = document.getElementById('totalDuration');
                this.favoriteCount = document.getElementById('favoriteCount');
                this.albumArt = document.getElementById('albumArt');
                this.editModal = document.getElementById('editModal');
            }

            setupEventListeners() {
                // File input
                this.fileInput.addEventListener('change', (e) => this.handleFiles(e.target.files));
                
                // Player controls
                this.playPauseBtn.addEventListener('click', () => this.togglePlayPause());
                this.prevBtn.addEventListener('click', () => this.previousSong());
                this.nextBtn.addEventListener('click', () => this.nextSong());
                this.repeatBtn.addEventListener('click', () => this.toggleRepeat());
                this.shuffleBtn.addEventListener('click', () => this.toggleShuffle());
                
                // Progress bar
                this.progressBar.addEventListener('click', (e) => this.seek(e));
                
                // Volume
                this.volumeSlider.addEventListener('input', (e) => this.setVolume(e.target.value));
                
                // Search and filter
                this.searchInput.addEventListener('input', (e) => this.searchSongs(e.target.value));
                this.sortSelect.addEventListener('change', (e) => this.sortSongs(e.target.value));
                
                // Filter buttons
                document.querySelectorAll('.filter-btn').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        if (e.target.dataset.filter) {
                            this.setFilter(e.target.dataset.filter);
                        }
                    });
                });
                
                // Audio events
                this.audio.addEventListener('timeupdate', () => this.updateProgress());
                this.audio.addEventListener('ended', () => this.handleSongEnd());
                this.audio.addEventListener('loadedmetadata', () => this.updateDuration());
                
                // Modal events
                document.querySelector('.close').addEventListener('click', () => this.closeModal());
                document.getElementById('saveEdit').addEventListener('click', () => this.saveEdit());
                
                // Keyboard shortcuts
                document.addEventListener('keydown', (e) => this.handleKeyboard(e));
            }

            addSampleSongs() {
                const sampleSongs = [
                    {
                        title: "Blinding Lights",
                        artist: "The Weeknd",
                        duration: "3:20",
                        url: "data:audio/mp3;base64,", // Placeholder
                        favorite: false,
                        dateAdded: new Date()
                    },
                    {
                        title: "As It Was", 
                        artist: "Harry Styles",
                        duration: "2:47",
                        url: "data:audio/mp3;base64,",
                        favorite: true,
                        dateAdded: new Date()
                    },
                    {
                        title: "Heat Waves",
                        artist: "Glass Animals", 
                        duration: "3:58",
                        url: "data:audio/mp3;base64,",
                        favorite: false,
                        dateAdded: new Date()
                    }
                ];

                // Note: Ces sont des exemples sans fichiers audio réels
                // Les utilisateurs devront ajouter leurs propres fichiers
            }

            handleFiles(files) {
                Array.from(files).forEach(file => {
                    if (file.type.startsWith('audio/')) {
                        this.addSong(file);
                    }
                });
            }

            addSong(file) {
                const url = URL.createObjectURL(file);
                const song = {
                    title: file.name.replace(/\.[^/.]+$/, ""),
                    artist: "Artiste Inconnu",
                    duration: "0:00",
                    url: url,
                    file: file,
                    favorite: false,
                    dateAdded: new Date(),
                    id: Date.now() + Math.random()
                };

                // Get duration
                const tempAudio = new Audio(url);
                tempAudio.addEventListener('loadedmetadata', () => {
                    song.duration = this.formatTime(tempAudio.duration);
                    this.updateStats();
                    this.renderPlaylist();
                });

                this.songs.push(song);
                this.renderPlaylist();
                this.updateStats();
                this.saveToStorage();
                this.showToast('Chanson ajoutée avec succès!');
            }

            renderPlaylist() {
                let filteredSongs = this.getFilteredSongs();
                
                this.playlist.innerHTML = '';
                
                filteredSongs.forEach((song, index) => {
                    const songElement = document.createElement('div');
                    songElement.className = `song-item ${this.currentSongIndex === this.songs.indexOf(song) ? 'playing' : ''}`;
                    
                    songElement.innerHTML = `
                        <div class="song-info">
                            <div class="song-title">${song.title}</div>
                            <div class="song-duration">${song.artist} • ${song.duration}</div>
                        </div>
                        <div class="song-actions">
                            <button class="action-btn favorite-btn ${song.favorite ? 'favorite' : ''}" 
                                    onclick="player.toggleFavorite(${this.songs.indexOf(song)})">
                                ${song.favorite ? '❤️' : '🤍'}
                            </button>
                            <button class="action-btn" onclick="player.editSong(${this.songs.indexOf(song)})">✏️</button>
                            <button class="action-btn" onclick="player.deleteSong(${this.songs.indexOf(song)})">🗑️</button>
                            <button class="action-btn" onclick="player.moveSong(${this.songs.indexOf(song)}, 'up')">⬆️</button>
                            <button class="action-btn" onclick="player.moveSong(${this.songs.indexOf(song)}, 'down')">⬇️</button>
                        </div>
                    `;
                    
                    songElement.addEventListener('click', (e) => {
                        if (!e.target.classList.contains('action-btn')) {
                            this.playSong(this.songs.indexOf(song));
                        }
                    });
                    
                    this.playlist.appendChild(songElement);
                });
            }

            getFilteredSongs() {
                let filtered = [...this.songs];
                
                // Apply filter
                switch(this.currentFilter) {
                    case 'favorites':
                        filtered = filtered.filter(song => song.favorite);
                        break;
                    case 'recent':
                        filtered = filtered.filter(song => {
                            const daysDiff = (new Date() - song.dateAdded) / (1000 * 60 * 60 * 24);
                            return daysDiff <= 7;
                        });
                        break;
                }
                
                // Apply search
                const searchTerm = this.searchInput.value.toLowerCase();
                if (searchTerm) {
                    filtered = filtered.filter(song => 
                        song.title.toLowerCase().includes(searchTerm) ||
                        song.artist.toLowerCase().includes(searchTerm)
                    );
                }
                
                // Apply sort
                const sortBy = this.sortSelect.value;
                filtered.sort((a, b) => {
                    switch(sortBy) {
                        case 'name':
                            return a.title.localeCompare(b.title);
                        case 'duration':
                            return this.parseDuration(a.duration) - this.parseDuration(b.duration);
                        case 'date':
                            return b.dateAdded - a.dateAdded;
                        default:
                            return 0;
                    }
                });
                
                return filtered;
            }

            playSong(index) {
                if (index < 0 || index >= this.songs.length) return;
                
                this.currentSongIndex = index;
                const song = this.songs[index];
                
                this.audio.src = song.url;
                this.audio.load();
                
                this.currentTitle.textContent = song.title;
                this.currentArtist.textContent = song.artist;
                
                this.audio.play().then(() => {
                    this.isPlaying = true;
                    this.playPauseBtn.textContent = '⏸️';
                    this.albumArt.classList.add('playing');
                }).catch(e => {
                    console.error('Erreur lors de la lecture:', e);
                    this.showToast('Erreur lors de la lecture du fichier');
                });
                
                this.renderPlaylist();
                this.saveToStorage();
            }

            togglePlayPause() {
                if (!this.songs.length) {
                    this.showToast('Aucune chanson dans la playlist');
                    return;
                }
                
                if (this.isPlaying) {
                    this.audio.pause();
                    this.isPlaying = false;
                    this.playPauseBtn.textContent = '▶️';
                    this.albumArt.classList.remove('playing');
                } else {
                    if (!this.audio.src && this.songs.length > 0) {
                        this.playSong(0);
                    } else {
                        this.audio.play().then(() => {
                            this.isPlaying = true;
                            this.playPauseBtn.textContent = '⏸️';
                            this.albumArt.classList.add('playing');
                        });
                    }
                }
            }

            nextSong() {
                if (!this.songs.length) return;
                
                let nextIndex;
                if (this.isShuffled) {
                    nextIndex = Math.floor(Math.random() * this.songs.length);
                } else {
                    nextIndex = (this.currentSongIndex + 1) % this.songs.length;
                }
                
                this.playSong(nextIndex);
            }

            previousSong() {
                if (!this.songs.length) return;
                
                let prevIndex;
                if (this.isShuffled) {
                    prevIndex = Math.floor(Math.random() * this.songs.length);
                } else {
                    prevIndex = this.currentSongIndex === 0 ? this.songs.length - 1 : this.currentSongIndex - 1;
                }
                
                this.playSong(prevIndex);
            }

            toggleRepeat() {
                this.isRepeating = !this.isRepeating;
                this.repeatBtn.classList.toggle('active');
                this.showToast(this.isRepeating ? 'Répétition activée' : 'Répétition désactivée');
            }

            toggleShuffle() {
                this.isShuffled = !this.isShuffled;
                this.shuffleBtn.classList.toggle('active');
                this.showToast(this.isShuffled ? 'Lecture aléatoire activée' : 'Lecture aléatoire désactivée');
            }

            handleSongEnd() {
                if (this.isRepeating) {
                    this.audio.currentTime = 0;
                    this.audio.play();
                } else {
                    this.nextSong();
                }
            }

            updateProgress() {
                if (this.audio.duration) {
                    const progress = (this.audio.currentTime / this.audio.duration) * 100;
                    this.progress.style.width = progress + '%';
                    this.currentTime.textContent = this.formatTime(this.audio.currentTime);
                }
            }

            updateDuration() {
                this.totalTime.textContent = this.formatTime(this.audio.duration);
            }

            seek(e) {
                if (!this.audio.duration) return;
                
                const rect = this.progressBar.getBoundingClientRect();
                const clickX = e.clientX - rect.left;
                const percentage = clickX / rect.width;
                
                this.audio.currentTime = this.audio.duration * percentage;
            }

            setVolume(value) {
                this.audio.volume = value / 100;
                this.volumeValue.textContent = value + '%';
            }

            toggleFavorite(index) {
                this.songs[index].favorite = !this.songs[index].favorite;
                this.renderPlaylist();
                this.updateStats();
                this.saveToStorage();
                
                const status = this.songs[index].favorite ? 'ajoutée aux' : 'supprimée des';
                this.showToast(`Chanson ${status} favoris`);
            }

            editSong(index) {
                this.editingSongIndex = index;
                const song = this.songs[index];
                
                document.getElementById('editTitle').value = song.title;
                document.getElementById('editArtist').value = song.artist;
                
                this.editModal.style.display = 'block';
            }

            saveEdit() {
                if (this.editingSongIndex === -1) return;
                
                const song = this.songs[this.editingSongIndex];
                song.title = document.getElementById('editTitle').value;
                song.artist = document.getElementById('editArtist').value;
                
                this.renderPlaylist();
                this.saveToStorage();
                this.closeModal();
                this.showToast('Chanson modifiée avec succès');
                
                if (this.currentSongIndex === this.editingSongIndex) {
                    this.currentTitle.textContent = song.title;
                    this.currentArtist.textContent = song.artist;
                }
            }

            closeModal() {
                this.editModal.style.display = 'none';
                this.editingSongIndex = -1;
            }

            deleteSong(index) {
                if (confirm('Êtes-vous sûr de vouloir supprimer cette chanson ?')) {
                    this.songs.splice(index, 1);
                    
                    if (this.currentSongIndex >= index) {
                        this.currentSongIndex = Math.max(0, this.currentSongIndex - 1);
                    }
                    
                    this.renderPlaylist();
                    this.updateStats();
                    this.saveToStorage();
                    this.showToast('Chanson supprimée');
                }
            }

            moveSong(index, direction) {
                if (direction === 'up' && index > 0) {
                    [this.songs[index], this.songs[index - 1]] = [this.songs[index - 1], this.songs[index]];
                    if (this.currentSongIndex === index) this.currentSongIndex--;
                    else if (this.currentSongIndex === index - 1) this.currentSongIndex++;
                } else if (direction === 'down' && index < this.songs.length - 1) {
                    [this.songs[index], this.songs[index + 1]] = [this.songs[index + 1], this.songs[index]];
                    if (this.currentSongIndex === index) this.currentSongIndex++;
                    else if (this.currentSongIndex === index + 1) this.currentSongIndex--;
                }
                
                this.renderPlaylist();
                this.saveToStorage();
            }

            setFilter(filter) {
                this.currentFilter = filter;
                
                document.querySelectorAll('.filter-btn').forEach(btn => {
                    btn.classList.remove('active');
                    if (btn.dataset.filter === filter) {
                        btn.classList.add('active');
                    }
                });
                
                this.renderPlaylist();
            }

            searchSongs(query) {
                this.renderPlaylist();
            }

            sortSongs(sortBy) {
                this.renderPlaylist();
            }

            updateStats() {
                this.songCount.textContent = this.songs.length;
                
                let totalSeconds = 0;
                this.songs.forEach(song => {
                    totalSeconds += this.parseDuration(song.duration);
                });
                this.totalDuration.textContent = this.formatTime(totalSeconds);
                
                const favorites = this.songs.filter(song => song.favorite).length;
                this.favoriteCount.textContent = favorites;
            }

            formatTime(seconds) {
                if (isNaN(seconds)) return '0:00';
                const mins = Math.floor(seconds / 60);
                const secs = Math.floor(seconds % 60);
                return `${mins}:${secs.toString().padStart(2, '0')}`;
            }

            parseDuration(duration) {
                const parts = duration.split(':');
                return parseInt(parts[0]) * 60 + parseInt(parts[1] || 0);
            }

            handleKeyboard(e) {
                switch(e.code) {
                    case 'Space':
                        e.preventDefault();
                        this.togglePlayPause();
                        break;
                    case 'ArrowRight':
                        if (e.ctrlKey) {
                            e.preventDefault();
                            this.nextSong();
                        }
                        break;
                    case 'ArrowLeft':
                        if (e.ctrlKey) {
                            e.preventDefault();
                            this.previousSong();
                        }
                        break;
                    case 'ArrowUp':
                        if (e.ctrlKey) {
                            e.preventDefault();
                            const vol = Math.min(100, parseInt(this.volumeSlider.value) + 10);
                            this.volumeSlider.value = vol;
                            this.setVolume(vol);
                        }
                        break;
                    case 'ArrowDown':
                        if (e.ctrlKey) {
                            e.preventDefault();
                            const vol = Math.max(0, parseInt(this.volumeSlider.value) - 10);
                            this.volumeSlider.value = vol;
                            this.setVolume(vol);
                        }
                        break;
                }
            }

            setupDragAndDrop() {
                const container = document.querySelector('.container');
                
                ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(eventName => {
                    container.addEventListener(eventName, (e) => {
                        e.preventDefault();
                        e.stopPropagation();
                    });
                });

                ['dragenter', 'dragover'].forEach(eventName => {
                    container.addEventListener(eventName, () => {
                        container.classList.add('drag-over');
                    });
                });

                ['dragleave', 'drop'].forEach(eventName => {
                    container.addEventListener(eventName, () => {
                        container.classList.remove('drag-over');
                    });
                });

                container.addEventListener('drop', (e) => {
                    const files = e.dataTransfer.files;
                    this.handleFiles(files);
                });
            }

            showToast(message) {
                const toast = document.createElement('div');
                toast.className = 'toast';
                toast.textContent = message;
                document.body.appendChild(toast);
                
                setTimeout(() => toast.classList.add('show'), 100);
                setTimeout(() => {
                    toast.classList.remove('show');
                    setTimeout(() => document.body.removeChild(toast), 300);
                }, 3000);
            }

            saveToStorage() {
                const data = {
                    songs: this.songs.map(song => ({
                        title: song.title,
                        artist: song.artist,
                        duration: song.duration,
                        favorite: song.favorite,
                        dateAdded: song.dateAdded,
                        id: song.id
                    })),
                    currentSongIndex: this.currentSongIndex,
                    volume: this.volumeSlider.value,
                    isShuffled: this.isShuffled,
                    isRepeating: this.isRepeating
                };
                
                // Note: localStorage n'est pas disponible dans les artifacts Claude
                // Cette fonction est préparée pour un environnement normal
                try {
                    if (typeof Storage !== "undefined") {
                        localStorage.setItem('musicPlayerData', JSON.stringify(data));
                    }
                } catch(e) {
                    console.log('Sauvegarde non disponible dans cet environnement');
                }
            }

            loadFromStorage() {
                try {
                    if (typeof Storage !== "undefined") {
                        const data = localStorage.getItem('musicPlayerData');
                        if (data) {
                            const parsed = JSON.parse(data);
                            this.currentSongIndex = parsed.currentSongIndex || 0;
                            this.volumeSlider.value = parsed.volume || 50;
                            this.setVolume(this.volumeSlider.value);
                            this.isShuffled = parsed.isShuffled || false;
                            this.isRepeating = parsed.isRepeating || false;
                            
                            if (this.isShuffled) this.shuffleBtn.classList.add('active');
                            if (this.isRepeating) this.repeatBtn.classList.add('active');
                        }
                    }
                } catch(e) {
                    console.log('Chargement non disponible dans cet environnement');
                }
            }

            // Export playlist
            exportPlaylist() {
                const playlist = {
                    name: 'Ma Playlist',
                    songs: this.songs.map(song => ({
                        title: song.title,
                        artist: song.artist,
                        duration: song.duration,
                        favorite: song.favorite
                    })),
                    createdAt: new Date().toISOString()
                };
                
                const dataStr = JSON.stringify(playlist, null, 2);
                const dataBlob = new Blob([dataStr], {type: 'application/json'});
                
                const link = document.createElement('a');
                link.href = URL.createObjectURL(dataBlob);
                link.download = 'playlist.json';
                link.click();
                
                this.showToast('Playlist exportée!');
            }

            // Visualizer animation
            startVisualizer() {
                const bars = document.querySelectorAll('.eq-bar');
                
                if (this.isPlaying) {
                    bars.forEach((bar, index) => {
                        const height = Math.random() * 50 + 10;
                        bar.style.height = height + 'px';
                    });
                }
                
                requestAnimationFrame(() => this.startVisualizer());
            }
        }

        // Initialize player
        let player;
        document.addEventListener('DOMContentLoaded', () => {
            player = new MusicPlayer();
            player.startVisualizer();
        });
    </script>
</body>
