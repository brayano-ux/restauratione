<html lang="fr">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Petits Jobs Express</title>
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-firestore.js"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        :root {
            --primary-color: #2563eb;
            --primary-light: #3b82f6;
            --primary-dark: #1d4ed8;
            --secondary-color: #10b981;
            --secondary-light: #34d399;
            --accent-color: #f59e0b;
            --success-color: #059669;
            --danger-color: #dc2626;
            --warning-color: #d97706;
            --background-color: #f8fafc;
            --surface-color: #ffffff;
            --text-primary: #1f2937;
            --text-secondary: #6b7280;
            --text-light: #9ca3af;
            --border-color: #e5e7eb;
            --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            --border-radius: 8px;
            --border-radius-lg: 12px;
            --border-radius-xl: 16px;
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--background-color);
            color: var(--text-primary);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            padding: 1rem 0;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            box-shadow: var(--shadow-lg);
        }

        header h1 {
            text-align: center;
            font-size: 1.75rem;
            font-weight: 700;
            margin: 0;
        }

        /* Container principal */
        .main-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }

        #contenuPrincipal {
            margin-top: 80px;
            padding: 2rem 0;
        }

        /* Boutons */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: var(--border-radius);
            font-size: 0.875rem;
            font-weight: 600;
            text-decoration: none;
            cursor: pointer;
            transition: var(--transition);
            white-space: nowrap;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .btn-secondary {
            background: var(--surface-color);
            color: var(--text-primary);
            border: 2px solid var(--border-color);
        }

        .btn-secondary:hover {
            border-color: var(--primary-color);
            color: var(--primary-color);
            transform: translateY(-2px);
        }

        .btn-success {
            background: linear-gradient(135deg, var(--success-color), var(--secondary-color));
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .btn-warning {
            background: linear-gradient(135deg, var(--warning-color), var(--accent-color));
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-warning:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .btn-danger {
            background: linear-gradient(135deg, var(--danger-color), #ef4444);
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-danger:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        /* Voir Profils button */
        #voirProfils {
            position: fixed;
            top: 90px;
            right: 1rem;
            background: linear-gradient(135deg, var(--accent-color), #fbbf24);
            color: white;
            border: none;
            border-radius: var(--border-radius-lg);
            padding: 0.75rem 1rem;
            font-weight: 600;
            cursor: pointer;
            box-shadow: var(--shadow);
            z-index: 100;
            transition: var(--transition);
        }

        #voirProfils:hover {
            transform: scale(1.05);
            box-shadow: var(--shadow-lg);
        }

        #menuOptions {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: var(--surface-color);
            border-top: 1px solid var(--border-color);
            padding: 1rem;
            display: flex;
            justify-content: space-around;
            box-shadow: 0 -4px 6px -1px rgba(0, 0, 0, 0.1);
            z-index: 999;
        }

        #menuOptions button {
            background: none;
            border: none;
            font-size: 1rem;
            color: var(--text-secondary);
            cursor: pointer;
            padding: 0.5rem;
            border-radius: var(--border-radius);
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.25rem;
        }

        #menuOptions button:hover {
            color: var(--primary-color);
            background: rgba(37, 99, 235, 0.1);
            transform: translateY(-2px);
        }

        /* Cards */
        .card {
            background: var(--surface-color);
            border-radius: var(--border-radius-lg);
            padding: 1.5rem;
            margin-bottom: 1rem;
            box-shadow: var(--shadow);
            border: 1px solid var(--border-color);
            transition: var(--transition);
        }

        .card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-xl);
        }

        .card h4 {
            color: var(--text-primary);
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 0.75rem;
        }

        .card p {
            color: var(--text-secondary);
            margin-bottom: 0.5rem;
            font-size: 0.875rem;
        }

        .card strong {
            color: var(--primary-color);
            font-weight: 600;
        }

        /* Formulaire */
        .form-container {
            background: var(--surface-color);
            border-radius: var(--border-radius-lg);
            padding: 2rem;
            box-shadow: var(--shadow-lg);
            max-width: 500px;
            margin: 2rem auto;
            border: 1px solid var(--border-color);
        }

        .form-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--text-primary);
            text-align: center;
            margin-bottom: 2rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            color: var(--text-primary);
            margin-bottom: 0.5rem;
        }

        .form-input,
        .form-textarea {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--border-radius);
            font-size: 1rem;
            transition: var(--transition);
            background: var(--surface-color);
            color: var(--text-primary);
        }

        .form-input:focus,
        .form-textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .form-textarea {
            min-height: 100px;
            resize: vertical;
        }

        .form-actions {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
        }

        .form-actions .btn {
            flex: 1;
        }

        /* Chat */
        .chat-container {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 90%;
            max-width: 600px;
            height: 80vh;
            background: var(--surface-color);
            border-radius: var(--border-radius-lg);
            box-shadow: var(--shadow-xl);
            display: flex;
            flex-direction: column;
            z-index: 1000;
            border: 1px solid var(--border-color);
        }

        .chat-header {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            padding: 1.5rem;
            border-radius: var(--border-radius-lg) var(--border-radius-lg) 0 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .chat-title {
            font-size: 1.25rem;
            font-weight: 700;
        }

        .chat-close {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.1rem;
            transition: var(--transition);
        }

        .chat-close:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }

        .chat-messages {
            flex: 1;
            padding: 1.5rem;
            overflow-y: auto;
            background: #f8fafc;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .message {
            max-width: 70%;
            padding: 0.75rem 1rem;
            border-radius: var(--border-radius-lg);
            font-size: 0.875rem;
            line-height: 1.4;
            word-wrap: break-word;
        }

        .message-sent {
            align-self: flex-end;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
        }

        .message-received {
            align-self: flex-start;
            background: var(--surface-color);
            color: var(--text-primary);
            border: 1px solid var(--border-color);
        }

        .message-author {
            font-size: 0.75rem;
            font-weight: 600;
            margin-bottom: 0.25rem;
            opacity: 0.8;
        }

        .chat-input-container {
            padding: 1.5rem;
            border-top: 1px solid var(--border-color);
            background: var(--surface-color);
            border-radius: 0 0 var(--border-radius-lg) var(--border-radius-lg);
        }

        .chat-input-group {
            display: flex;
            gap: 0.75rem;
            margin-bottom: 1rem;
        }

        .chat-input {
            flex: 1;
            height: 48px;
            padding: 0 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--border-radius-xl);
            font-size: 1rem;
            transition: var(--transition);
        }

        .chat-input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .chat-actions {
            display: flex;
            gap: 0.75rem;
        }

        .chat-actions .btn {
            flex: 1;
        }

        /* Profil */
        .profile-container {
            background: var(--surface-color);
            border-radius: var(--border-radius-lg);
            padding: 2rem;
            box-shadow: var(--shadow-lg);
            max-width: 600px;
            margin: 2rem auto;
            border: 1px solid var(--border-color);
        }

        .profile-header {
            text-align: center;
            margin-bottom: 2rem;
        }

        .profile-title {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        .photo-upload {
            text-align: center;
            margin-bottom: 2rem;
        }

        .photo-preview {
            width: 150px;
            height: 150px;
            object-fit: cover;
            border-radius: 50%;
            margin: 1rem auto;
            display: block;
            box-shadow: var(--shadow);
            border: 4px solid var(--primary-color);
        }

        .profile-card {
            background: var(--surface-color);
            border: 1px solid var(--border-color);
            border-radius: var(--border-radius-lg);
            padding: 1.5rem;
            margin: 1rem 0;
            box-shadow: var(--shadow);
        }

        .profile-info {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .profile-avatar {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: 50%;
            border: 3px solid var(--primary-color);
        }

        .profile-details h4 {
            color: var(--text-primary);
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 0.25rem;
        }

        .profile-details p {
            color: var(--text-secondary);
            font-size: 0.875rem;
        }

        .contact-btn {
            background: linear-gradient(135deg, var(--success-color), var(--secondary-color));
            color: white;
            border: none;
            border-radius: var(--border-radius);
            padding: 0.75rem 1.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            width: 100%;
            margin-top: 1rem;
        }

        .contact-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .main-container {
                padding: 0 0.5rem;
            }

            #contenuPrincipal {
                margin-top: 70px;
                padding: 1rem 0;
            }

            header h1 {
                font-size: 1.5rem;
            }

            .form-container,
            .profile-container {
                margin: 1rem;
                padding: 1.5rem;
            }

            .chat-container {
                width: 95%;
                height: 90vh;
            }

            .chat-header {
                padding: 1rem;
            }

            .chat-messages {
                padding: 1rem;
            }

            .chat-input-container {
                padding: 1rem;
            }

            .message {
                max-width: 85%;
            }

            .chat-actions {
                flex-direction: column;
            }

            .form-actions {
                flex-direction: column;
            }

            #menuOptions {
                padding: 0.75rem;
            }

            #menuOptions button {
                font-size: 0.875rem;
                padding: 0.5rem;
            }

            .card {
                padding: 1rem;
            }

            #bonus {
                top: 80px;
                right: 0.5rem;
                padding: 0.5rem 0.75rem;
                font-size: 0.875rem;
            }
        }

        @media (max-width: 480px) {
            .profile-info {
                flex-direction: column;
                text-align: center;
            }

            .profile-avatar {
                width: 100px;
                height: 100px;
            }

            .chat-input-group {
                flex-direction: column;
            }

            .chat-input {
                width: 100%;
            }
        }

        /* Utilitaires */
        .hidden {
            display: none !important;
        }

        .text-center {
            text-align: center;
        }

        .mb-2 {
            margin-bottom: 0.5rem;
        }

        .mb-4 {
            margin-bottom: 1rem;
        }

        .mt-4 {
            margin-top: 1rem;
        }
    </style>
</head>

<body>
    <header>
        <h1><i class="fas fa-briefcase"></i> Petits Jobs Express</h1>
    </header>

    <div class="main-container">
        <div id="contenuPrincipal">
            <button id="voirProfils" style="display: none;" class="btn btn-warning">
                <i class="fas fa-users"></i> Voir Profils
            </button>

            <!-- Connexion -->
            <div class="form-container" id="connexion" style="display: block;">
                <h3 class="form-title"><i class="fas fa-sign-in-alt"></i> Connexion</h3>
                <div class="form-group">
                    <label class="form-label" for="nom">Nom complet</label>
                    <input class="form-input" type="text" id="nom" placeholder="Entrez votre nom" />
                </div>
                <div class="form-group">
                    <label class="form-label" for="numero">Numéro de téléphone</label>
                    <input class="form-input" type="number" id="numero" placeholder="Ton numéro" />
                </div>
                <div class="form-group">
                    <label class="form-label" for="motdepasse">Mot de passe</label>
                    <input class="form-input" id="motdepasse" placeholder="Mot de passe" type="password" />
                </div>
                <div class="form-actions">
                    <button class="btn btn-primary" id="btnCreerCompte">
                        <i class="fas fa-user-plus"></i> Créer un Compte
                    </button>
                    <button class="btn btn-success" id="btnSeConnecter">
                        <i class="fas fa-sign-in-alt"></i> Se connecter
                    </button>
                </div>
            </div>

            <!-- Menu de navigation -->
            <div id="menuOptions" style="display: none;">
                <button id="btnAcceuil">
                    <i class="fas fa-home"></i>
                    <span>Accueil</span>
                </button>
                <button id="btnPosterJob">
                    <i class="fas fa-plus"></i>
                    <span>Poster un job</span>
                </button>
                <button id="btnConversations">
                    <i class="fas fa-comments"></i>
                    <span>Messagerie</span>
                </button>
                <button id="profil">
                    <i class="fas fa-user"></i>
                    <span>Profil</span>
                </button>
            </div>

            <!-- Profil -->
            <div class="profile-container" id="moi" style="display: none;">
                <div class="profile-header">
                    <h2 class="profile-title"><i class="fas fa-user-circle"></i> Votre profil</h2>
                </div>

                <div class="photo-upload">
                    <img src="" alt="votre photo" id="photos" class="photo-preview" style="display: none;">
                    <button class="btn btn-primary" id="photo">
                        <i class="fas fa-camera"></i> Ajouter une photo
                    </button>
                    <input style="display: none;" type="file" accept="image/*" capture="environnement" id="camera">
                </div>

                <form id="form">
                    <div class="form-group">
                        <label class="form-label">Prénom</label>
                        <input class="form-input" type="text" name="prenom" placeholder="Entrez votre prénom" required>
                    </div>

                    <div class="form-group">
                        <label class="form-label">Ville</label>
                        <input class="form-input" type="text" name="ville" required placeholder="Entrez votre ville">
                    </div>

                    <div class="form-group">
                        <label class="form-label">Expérience</label>
                        <input class="form-input" type="text" name="statut" placeholder="Votre expérience">
                    </div>

                    <div class="form-group">
                        <label class="form-label">Compétences</label>
                        <textarea class="form-textarea" name="competences" required
                            placeholder="Quelles sont vos compétences ?"></textarea>
                    </div>

                    <div class="form-actions">
                        <button type="submit" class="btn btn-success">
                            <i class="fas fa-save"></i> Créer
                        </button>
                        <button type="button" class="btn btn-secondary" id="modifier">
                            <i class="fas fa-edit"></i> Modifier
                        </button>
                    </div>
                </form>
            </div>

            <!-- Section des profils -->
            <section class="offre">
                <div id="profils"></div>
            </section>

            <!-- Formulaire de job -->
            <div class="form-container" id="formulaire" style="display: none;">
                <h3 class="form-title"><i class="fas fa-plus-circle"></i> Poster un job</h3>
                <div class="form-group">
                    <label class="form-label" for="titre">Titre du job</label>
                    <input class="form-input" id="titre" placeholder="Titre du job" />
                </div>
                <div class="form-group">
                    <label class="form-label" for="prix">Prix (FCFA)</label>
                    <input class="form-input" id="prix" placeholder="Prix" />
                </div>
                <div class="form-group">
                    <label class="form-label" for="description">Description</label>
                    <textarea class="form-textarea" id="description" placeholder="Description du job"></textarea>
                </div>
                <div class="form-actions">
                    <button class="btn btn-primary" id="posterBtn">
                        <i class="fas fa-paper-plane"></i> Poster
                    </button>
                    <button class="btn btn-secondary" id="btnAnnuler">
                        <i class="fas fa-times"></i> Annuler
                    </button>
                </div>
            </div>

            <div id="container"></div>

            <div class="chat-container" id="chat" style="display: none;">
                <div class="chat-header">
                    <span class="chat-title"><i class="fas fa-comments"></i> Chat du job</span>
                    <button class="chat-close" onclick="fermerChat()">
                        <i class="fas fa-times"></i>
                    </button>
                </div>

                <div class="chat-messages" id="messages"></div>

                <div class="chat-input-container">
                    <div class="chat-input-group">
                        <input class="chat-input" id="messageInput" placeholder="Écris un message..." />
                        <button class="btn btn-primary" id="envoyer">
                            <i class="fas fa-paper-plane"></i> Envoyer
                        </button>
                    </div>

                    <div class="chat-actions">
                        <button class="btn btn-warning" id="conclure">
                            <i class="fas fa-check"></i> Conclure
                        </button>
                        <button class="btn btn-danger" id="fermerChat">
                            <i class="fas fa-times"></i> Fermer
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
        import {
            getFirestore, collection, addDoc, doc, getDoc, getDocs,
            onSnapshot, query, orderBy, updateDoc, setDoc, limit
        } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";
        import {
            getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword,
            onAuthStateChanged
        } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";

        // 🔐 Config Firebase
        const firebaseConfig = {
            apiKey: "AIzaSyAigx8KtDCEulSWjpu17fnYsrqK7C9o3R8",
            authDomain: "petit-jobs-express.firebaseapp.com",
            projectId: "petit-jobs-express",
            storageBucket: "petit-jobs-express.appspot.com",
            messagingSenderId: "446118780236",
            appId: "1:446118780236:web:08c3a87d56bcd67399c3e9"
        };
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        const auth = getAuth(app);

        // Variables globales
        let utilisateurconnecter = false;
        let utilisateurnom = "";
        let idJobEnCours = null;
        let idConversation = "";

        // Accès DOM simplifié
        const get = id => document.getElementById(id);
        const container = get('container');
        const formulaire = get('formulaire');
        const menuOptions = get('menuOptions');
        const connexionDiv = get('connexion');
        const chatDiv = get('chat');
        const messagesDiv = get('messages');
        const messageInput = get('messageInput');

        // Connexion automatique à chaque ouverture
        onAuthStateChanged(auth, async user => {
            if (user) {
                try {
                    const snapshot = await getDoc(doc(db, "users", user.uid));
                    const data = snapshot.data();

                    // Utiliser le nom s'il existe, sinon utiliser l'email ou un nom par défaut
                    utilisateurnom = data?.nom || data?.prenom || user.email?.split('@')[0] || "Utilisateur";
                    utilisateurconnecter = true;

                    connexionDiv.style.display = "none";
                    menuOptions.style.display = "flex";

                    // Afficher automatiquement les jobs
                    afficheracceuil();
                } catch (e) {
                    console.error("Erreur lors du chargement des infos :", e);
                    // Même en cas d'erreur, on peut continuer avec un nom par défaut
                    utilisateurnom = user.email?.split('@')[0] || "Utilisateur";
                    utilisateurconnecter = true;
                    connexionDiv.style.display = "none";
                    menuOptions.style.display = "flex";
                    afficheracceuil();
                }
            } else {
                // Utilisateur déconnecté
                utilisateurconnecter = false;
                utilisateurnom = "";
                connexionDiv.style.display = "block";
                menuOptions.style.display = "none";
            }
        });

        // 📸 Gestion du bouton photo
        const moi = document.getElementById("moi");
        const form = document.getElementById("form");
        const conteneurProfils = document.getElementById("profils");
        const cameraInput = document.getElementById("camera");
        const photoPreview = document.getElementById("photos");

        // 📸 Affiche les options de photo
        document.getElementById("photo").addEventListener("click", () => {
            cameraInput.style.display = "block";
            photoPreview.style.display = "block";
        });

        // 🎞️ Affiche l'image sélectionnée
        cameraInput.addEventListener("change", function (event) {
            const file = event.target.files[0];
            if (file) {
                const imageUrl = URL.createObjectURL(file);
                photoPreview.src = imageUrl;
                photoPreview.style.display = "block";
            }
        });

        // Création/Mise à jour de profil
        form.addEventListener("submit", async function (e) {
            e.preventDefault();
            const user = auth.currentUser;
            if (!user) return Swal.fire('Attention', 'Connecte-toi d\'abord', 'warning');

            const [prenom, ville, statut, competences] = [...form.querySelectorAll("input[type='text'], textarea")].map(input => input.value);
            let photoURL = "";
            const file = cameraInput.files[0];
            if (file) {
                photoURL = URL.createObjectURL(file);
            }

            await setDoc(doc(db, "users", user.uid), {
                prenom, ville, statut, competences, photoURL
            }, { merge: true });

            Swal.fire('Succès', 'Profil mis à jour !', 'success');
            moi.style.display = "none";
        });

        // Fonction de nettoyage des données
        function sanitizeInput(input) {
            return input
                .replace(/[<>]/g, '') // Supprimer les balises HTML
                .replace(/javascript:/gi, '') // Supprimer les protocoles dangereux
                .trim();
        }

        // Fonction de validation des entrées
        function validateInput(input, type) {
            const value = input.trim();

            switch (type) {
                case 'nom':
                    if (value.length < 2) return 'Le nom doit contenir au moins 2 caractères';
                    if (value.length > 50) return 'Le nom ne peut pas dépasser 50 caractères';
                    if (!/^[a-zA-ZÀ-ÿ\s]+$/.test(value)) return 'Le nom ne peut contenir que des lettres';
                    break;

                case 'numero':
                    if (!/^\d{8,15}$/.test(value)) return 'Le numéro doit contenir entre 8 et 15 chiffres';
                    break;

                case 'password':
                    if (value.length < 6) return 'Le mot de passe doit contenir au moins 6 caractères';
                    if (value.length > 50) return 'Le mot de passe ne peut pas dépasser 50 caractères';
                    break;
            }

            return null;
        }

        // Création de compte 
        async function creerCompte() {
            try {
                const nom = sanitizeInput(get('nom').value);
                const numero = sanitizeInput(get('numero').value);
                const mdp = get('motdepasse').value;

                // Validation des champs
                if (!nom || !numero || !mdp) {
                    return Swal.fire('Attention', 'Remplis tous les champs', 'warning');
                }

                const nomError = validateInput(nom, 'nom');
                if (nomError) return Swal.fire('Attention', nomError, 'warning');

                const numeroError = validateInput(numero, 'numero');
                if (numeroError) return Swal.fire('Attention', numeroError, 'warning');

                const passwordError = validateInput(mdp, 'password');
                if (passwordError) return Swal.fire('Attention', passwordError, 'warning');

                const email = numero + "@momo.cm";
                const cred = await createUserWithEmailAndPassword(auth, email, mdp);
                // Sauvegarde dans Firestore
                await setDoc(doc(db, "users", cred.user.uid), {
                    nom: nom.substring(0, 50),
                    numero: numero.substring(0, 15),
                    premiumExpire: null
                });
                Swal.fire('Succès', 'Compte créé avec succès !', 'success');
                // Afficher automatiquement 
                setTimeout(() => {
                    afficheracceuil();
                }, 1000);

            } catch (error) {
                console.error('Erreur lors de la création du compte:', e);
                if (error.code === "auth/email-already-in-use") {
                    Swal.fire('Attention', 'Ce numéro est déjà utilisé. Essaie sur un autre téléphone.', 'warning');
                } else if (error.code === "auth/weak-password") {
                    Swal.fire('Attention', 'Le mot de passe est trop faible', 'warning');
                } else {
                    Swal.fire('Erreur', 'Erreur lors de la création du compte: ' + e.message, 'error');
                }
            }
        }

        //Connexion
        async function seConnecter() {
            const numero = get('numero').value.trim();
            const mdp = get('motdepasse').value.trim();

            if (!numero || !mdp) return Swal.fire('Attention', 'Remplis tous les champs', 'warning');

            try {
                const email = numero + "@momo.cm";
                await signInWithEmailAndPassword(auth, email, mdp);
                Swal.fire('Succès', 'Connexion réussie !', 'success');
                // Afficher automatiquement les jobs 
                setTimeout(() => {
                    afficheracceuil();
                }, 1000);
            } catch (e) {
                if (e.code === "auth/user-not-found") {
                    Swal.fire('Attention', 'Aucun compte trouvé avec ce numéro. Créez d\'abord un compte.', 'warning');
                } else if (e.code === "auth/wrong-password") {
                    Swal.fire('Attention', 'Mot de passe incorrect', 'warning');
                } else {
                    Swal.fire('Erreur', 'Erreur de connexion: ' + e.message, 'error');
                }
            }
        }

        // Afficher les jobs
        async function afficheracceuil() {
            moi.style.display = "none";
            // Vérifier si l'élément existe avant d'essayer de le modifier
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            formulaire.style.display = "none";
            chatDiv.style.display = "none";
            container.style.display = "block";

            const voirProfils = document.getElementById("voirProfils");
            if (voirProfils) voirProfils.style.display = "block";

            // Afficher un indicateur de chargement
            container.innerHTML = `
                <div class="text-center" style="padding: 2rem;">
                    <div style="display: inline-block; width: 40px; height: 40px; border: 4px solid #e5e7eb; border-top: 4px solid var(--primary-color); border-radius: 50%; animation: spin 1s linear infinite;"></div>
                    <p style="margin-top: 1rem; color: var(--text-secondary);">Chargement des jobs...</p>
                </div>
                <style>
                    @keyframes spin {
                        0% { transform: rotate(0deg); }
                        100% { transform: rotate(360deg); }
                    }
                </style>
            `;

            try {
                const q = query(collection(db, "jobs"), orderBy("timestamp", "desc"));
                const snap = await getDocs(q);

                if (snap.empty) {
                    container.innerHTML = `
                        <h3 class='text-center mb-4'><i class='fas fa-briefcase'></i> Liste des jobs disponibles</h3>
                        <div class="card text-center">
                            <i class="fas fa-inbox" style="font-size: 3rem; color: var(--text-light); margin-bottom: 1rem;"></i>
                            <p>Aucun job disponible pour le moment.</p>
                            <p>Soyez le premier à poster un job !</p>
                        </div>`;
                    return;
                }

                // Réinitialiser le contenu avec le titre
                container.innerHTML = "<h3 class='text-center mb-4'><i class='fas fa-briefcase'></i> Liste des jobs disponibles</h3>";

                // Optimisation : Récupérer tous les UIDs uniques d'abord
                const uids = [...new Set(snap.docs.map(doc => doc.data().posteurUID).filter(Boolean))];
                const usersMap = new Map();

                // Récupérer tous les utilisateurs en parallèle
                if (uids.length > 0) {
                    const userPromises = uids.map(async uid => {
                        try {
                            const userDoc = await getDoc(doc(db, "users", uid));
                            if (userDoc.exists()) {
                                usersMap.set(uid, userDoc.data().nom || "Inconnu");
                            }
                        } catch (error) {
                            console.warn('Erreur lors du chargement de l\'utilisateur:', uid, error);
                            usersMap.set(uid, "Inconnu");
                        }
                    });
                    await Promise.all(userPromises);
                }

                for (const docu of snap.docs) {
                    const job = docu.data();
                    if (job.conclu) continue;

                    const nomPosteur = job.posteurUID ? (usersMap.get(job.posteurUID) || "Inconnu") : "Inconnu";

                    const div = document.createElement("div");
                    div.className = "card";
                    div.innerHTML = `
                        <h4><i class="fas fa-tasks"></i> ${job.titre}</h4>
                        <p><strong><i class="fas fa-coins"></i> Prix:</strong> ${job.prix} FCFA</p>
                        <p><strong><i class="fas fa-user"></i> Posté par:</strong> ${nomPosteur}</p>
                        <p><i class="fas fa-info-circle"></i> ${job.description}</p>
                        <button class="btn btn-primary" data-id="${docu.id}">
                            <i class="fas fa-handshake"></i> Postuler
                        </button>
                    `;
                    container.appendChild(div);
                    div.querySelector("button").addEventListener("click", () => postuler(docu.id));
                }
            } catch (error) {
                console.error("Erreur lors du chargement des jobs:", error);
                container.innerHTML = `
                    <h3 class='text-center mb-4'><i class='fas fa-briefcase'></i> Liste des jobs disponibles</h3>
                    <div class="card text-center">
                        <i class="fas fa-exclamation-triangle" style="font-size: 3rem; color: var(--danger-color); margin-bottom: 1rem;"></i>
                        <p>Erreur lors du chargement des jobs.</p>
                        <button class="btn btn-primary" onclick="afficheracceuil()">
                            <i class="fas fa-refresh"></i> Réessayer
                        </button>
                    </div>`;
            }
        }

        // Formulaire de job
        function afficherformulaire() {
            moi.style.display = "none";
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            formulaire.style.display = "block";
            container.style.display = "none";
            chatDiv.style.display = "none";
        }

        // Envoi d'un job
        async function envoyer() {
            try {
                const profileHeader = document.getElementById("profile-header");
                if (profileHeader) profileHeader.style.display = "none";

                const titre = sanitizeInput(get('titre').value);
                const prix = sanitizeInput(get('prix').value);
                const description = sanitizeInput(get('description').value);

                if (!titre || !prix || !description) {
                    return Swal.fire('Attention', 'Remplis tous les champs', 'warning');
                }

                if (titre.length < 3) {
                    return Swal.fire('Attention', 'Le titre doit contenir au moins 3 caractères', 'warning');
                }

                if (isNaN(prix) || parseInt(prix) <= 0) {
                    return Swal.fire('Attention', 'Le prix doit être un nombre positif', 'warning');
                }

                if (description.length < 10) {
                    return Swal.fire('Attention', 'La description doit contenir au moins 10 caractères', 'warning');
                }

                const user = auth.currentUser;
                if (!user) return Swal.fire('Attention', 'Connecte-toi', 'warning');

                // Obtenir la géolocalisation avec gestion d'erreur
                let coords;
                try {
                    coords = await new Promise((res, rej) => {
                        navigator.geolocation.getCurrentPosition(res, rej, {
                            timeout: 10000,
                            enableHighAccuracy: false
                        });
                    });
                } catch (geoError) {
                    console.warn('Géolocalisation non disponible:', geoError);
                    coords = { coords: { latitude: 0, longitude: 0 } };
                }

                await addDoc(collection(db, "jobs"), {
                    titre: titre.substring(0, 100), 
                    prix: parseInt(prix),
                    description: description.substring(0, 500), 
                    posteur: utilisateurnom,
                    posteurUID: user.uid,
                    latitude: coords.coords.latitude,
                    longitude: coords.coords.longitude,
                    postulantsUid: [],
                    conclu: false,
                    timestamp: Date.now()
                });

                Swal.fire('Succès', 'Job posté avec succès !', 'success');
                afficheracceuil();
            } catch (error) {
                console.error('Erreur lors de la création du job:', error);
                Swal.fire('Erreur', 'Erreur lors de la création du job. Veuillez réessayer.', 'error');
            }
        }

        //  Postuler
        async function postuler(idJob) {
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            const user = auth.currentUser;
            if (!user) return Swal.fire('Attention', 'Connecte-toi d\'abord', 'warning');

            const uid = user.uid;

            const userDoc = await getDoc(doc(db, "users", uid));
            if (!userDoc.exists()) return Swal.fire('Erreur', 'Utilisateur introuvable', 'error');

            const jobRef = doc(db, "jobs", idJob);
            const jobSnap = await getDoc(jobRef);
            if (!jobSnap.exists()) return Swal.fire('Erreur', 'Job introuvable', 'error');

            const job = jobSnap.data();
            let postulants = job.postulants || [];

            if (!postulants.includes(uid)) {
                postulants.push(uid);
                await updateDoc(jobRef, { postulants: postulants });
            }

            //  Création automatique d'une conversation avec message
            const convId = [uid, job.posteurUID].sort().join("_");
            const msgRef = collection(db, "jobs", idJob, "conversations", convId, "messages");

            const messagesSnap = await getDocs(msgRef);
            if (messagesSnap.empty) {
                await addDoc(msgRef, {
                    auteur: uid,
                    text: "Bonjour, je suis intéressé par ce job.",
                    timestamp: Date.now()
                });
            }

            ouvrirChat(idJob, uid, job.posteurUID);
        }

        // Ouvrir le chat
        async function ouvrirChat(idJob, uid1, uid2) {
            console.log("ouvrir chat appeler avec ", { idJob, uid1, uid2 });
            idJobEnCours = idJob;
            idConversation = [uid1, uid2].sort().join("_");

            moi.style.display = "none";
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            container.style.display = "none";
            formulaire.style.display = "none";
            chatDiv.style.display = "block";
            messagesDiv.innerHTML = "";

            const messagesRef = collection(db, "jobs", idJob, "conversations", idConversation, "messages");
            const q = query(messagesRef, orderBy("timestamp", "asc"));

            onSnapshot(q, async (snapshot) => {
                messagesDiv.innerHTML = "";

                // Récupérer en parallèle tous les messages + noms auteurs
                const messagesWithAuthors = await Promise.all(snapshot.docs.map(async docu => {
                    const msg = docu.data();
                    const auteurDoc = await getDoc(doc(db, "users", msg.auteur));
                    const auteurNom = auteurDoc.exists() ? auteurDoc.data().nom : "Inconnu";
                    return { ...msg, auteurNom };
                }));

                messagesWithAuthors.forEach(msg => {
                    const div = document.createElement("div");
                    const isCurrentUser = msg.auteur === auth.currentUser.uid;

                    div.className = `message ${isCurrentUser ? 'message-sent' : 'message-received'}`;
                    div.innerHTML = `
            <div class="message-author">${msg.auteurNom}</div>
            ${msg.text}
          `;

                    messagesDiv.appendChild(div);
                });

                messagesDiv.scrollTop = messagesDiv.scrollHeight;
            });

            const autreDoc = await getDoc(doc(db, "users", uid2));
            const autreNom = autreDoc.exists() ? autreDoc.data().nom : "Inconnu";
            document.querySelector('.chat-title').innerHTML = `<i class="fas fa-comments"></i> Chat avec ${autreNom}`;
            document.getElementById("profile-header").style.display = "none";
        }

        //  Envoyer un message
        async function envoyerMessage() {
            const texte = messageInput.value.trim();
            if (!texte) return Swal.fire("Veuillez entrez un texte");
            const uid = auth.currentUser.uid;
            let msgRef;
            if (idJobEnCours) {
                msgRef = collection(db, "jobs", idJobEnCours, "conversations", idConversation, "messages");
            } else {
                msgRef = collection(db, "conversations", idConversation, "messages");
            }
            await addDoc(msgRef, {
                auteur: uid,
                text: texte,
                timestamp: Date.now()
            });
            if (!idJobEnCours) {
                const otherUid = idConversation.split('_').find(u => u !== uid);
                await setDoc(doc(db, "conversations", idConversation), {
                    participants: [uid, otherUid],
                    lastUpdate: Date.now()
                }, { merge: true });
            }
            messageInput.value = "";
            document.getElementById("profile-header").style.display = "none";
        }

        //  Conclure
        async function conclureJob() {
            const jobRef = doc(db, "jobs", idJobEnCours);
            const snap = await getDoc(jobRef);
            if (!snap.exists()) return;
            const data = snap.data();

            let c = data.conclusionUsers || [];
            if (!c.includes(utilisateurnom)) c.push(utilisateurnom);
            await updateDoc(jobRef, { conclusionUsers: c });
            if (c.length >= 2) await updateDoc(jobRef, { conclu: true });

            Swal.fire('Succès', 'Conclusion enregistrée', 'success');
            fermerChat();
            afficheracceuil();
            document.getElementById("profile-header").style.display = "none";
        }

        // Fermer le chat
        function fermerChat() {
            chatDiv.style.display = "none";
            container.style.display = "block";
            document.getElementById("profile-header").style.display = "none";
            idConversation = "";
        }

        //  Afficher le profil utilisateur
        async function afficherProfil() {
            const user = auth.currentUser;
            if (!user) return Swal.fire('Attention', 'Connecte-toi d\'abord', 'warning');
            const userDoc = await getDoc(doc(db, "users", user.uid));
            let data = userDoc.exists() ? userDoc.data() : {};
            moi.style.display = "block";
            conteneurProfils.innerHTML = "";
            if (userDoc.exists()) {
                moi.innerHTML = `
            <div class="profile-header" id="profile-header">
                <h2 class="profile-title"><i class="fas fa-user-circle"></i> Votre profil</h2>
            </div>
            <div class="profile-info">
                ${data.photoURL ? `<img src="${data.photoURL}" class="profile-avatar">` : ""}
                <div class="profile-details">
                    <h4><i class="fas fa-user"></i> ${data.prenom || data.nom || "Utilisateur"}</h4>
                    <p><i class="fas fa-map-marker-alt"></i> ${data.ville || "Ville non spécifiée"}</p>
                    <p><i class="fas fa-clock"></i> Expérience: ${data.statut || "Non spécifiée"}</p>
                    <p><i class="fas fa-tools"></i> ${data.competences || "Compétences non spécifiées"}</p>
                </div>
            </div>
            <button class="btn btn-secondary" id="modifierProfil"><i class="fas fa-edit"></i> Modifier</button>
        `;
                document.getElementById("modifierProfil").onclick = () => afficherFormulaireProfil(data);
            } else {
                afficherFormulaireProfil();
            }
        }
        function afficherFormulaireProfil(data = {}) {
            moi.innerHTML = `
        <form id="form">
            <div class="form-group">
                <label class="form-label">Prénom</label>
                <input class="form-input" type="text" name="prenom" value="${data.prenom || ""}" placeholder="Entrez votre prénom" required>
            </div>
            <div class="form-group">
                <label class="form-label">Ville</label>
                <input class="form-input" type="text" name="ville" value="${data.ville || ""}" required placeholder="Entrez votre ville">
            </div>
            <div class="form-group">
                <label class="form-label">Expérience</label>
                <input class="form-input" type="text" name="statut" value="${data.statut || ""}" placeholder="Votre expérience">
            </div>
            <div class="form-group">
                <label class="form-label">Compétences</label>
                <textarea class="form-textarea" name="competences" required placeholder="Quelles sont vos compétences ?">${data.competences || ""}</textarea>
            </div>
            <div class="form-actions">
                <button type="submit" class="btn btn-success">
                    <i class="fas fa-save"></i> Enregistrer
                </button>
            </div>
        </form>
    `;
            document.getElementById("form").onsubmit = async function (e) {
                e.preventDefault();
                const user = auth.currentUser;
                if (!user) return Swal.fire('Attention', 'Connecte-toi d\'abord', 'warning');
                const formData = new FormData(this);
                const profil = Object.fromEntries(formData.entries());
                await setDoc(doc(db, "users", user.uid), profil, { merge: true });
                Swal.fire('Succès', 'Profil enregistré !', 'success');
                afficherProfil();
                formulaire.style.display = "none";
                chatDiv.style.display = "none";
                container.style.display = "none";           
            };
        }

        //  Afficher les profils des utilisateurs
        async function afficherProfilsUtilisateurs() {
            moi.style.display = "none";
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            formulaire.style.display = "none";
            chatDiv.style.display = "none";
            container.style.display = "block";
            container.innerHTML = "<h3 class='text-center mb-4'><i class='fas fa-users'></i> Profils des utilisateurs</h3>";
            const usersSnap = await getDocs(collection(db, "users"));
            if (usersSnap.empty) {
                container.innerHTML += `<div class="card text-center"><p>Aucun profil trouvé.</p></div>`;
                return;
            }
            usersSnap.forEach(docu => {
                const data = docu.data();
                const uid = docu.id;
                const isMe = auth.currentUser && auth.currentUser.uid === uid;
                const div = document.createElement("div");
                div.className = "profile-card";
                div.innerHTML = `
            <div class="profile-info">
                ${data.photoURL ? `<img src="${data.photoURL}" class="profile-avatar">` : ""}
                <div class="profile-details">
                    <h4><i class="fas fa-user"></i> ${data.prenom || data.nom || "Utilisateur"}</h4>
                    <p><i class="fas fa-map-marker-alt"></i> ${data.ville || "Ville non spécifiée"}</p>
                    <p><i class="fas fa-clock"></i> Expérience: ${data.statut || "Non spécifiée"}</p>
                    <p><i class="fas fa-tools"></i> ${data.competences || "Compétences non spécifiées"}</p>
                </div>
            </div>
            ${!isMe ? `<button class="contact-btn" data-uid="${uid}"><i class="fas fa-phone"></i> Contacter</button>` : ""}
        `;
                container.appendChild(div);
                if (!isMe) {
                    div.querySelector(".contact-btn").addEventListener("click", function () {
                        window.ouvrirChatPrive(uid);
                    });
                }
            });
        }

        // Lire les conversations
        async function lireConversations() {
            moi.style.display = "none";
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            formulaire.style.display = "none";
            chatDiv.style.display = "none";
            container.style.display = "block";
            container.innerHTML = "<h3 class='text-center mb-4'><i class='fas fa-comments'></i> Mes Conversations</h3>";

            const currentUser = auth.currentUser;
            if (!currentUser) return Swal.fire('Attention', 'Connecte-toi d\'abord', 'warning');

            const uid = currentUser.uid;
            const jobsSnap = await getDocs(collection(db, "jobs"));
            let total = 0;

            for (const doc of jobsSnap.docs) {
                const job = doc.data();
                const jobId = doc.id;
                if (job.conclu) continue;

                const estPosteur = job.posteurUID === uid;
                const estPostulant = (job.postulants || []).includes(uid);

                if (!estPosteur && !estPostulant) continue;

                const div = document.createElement("div");
                div.className = "card";
                div.innerHTML = `
          <h4><i class="fas fa-tasks"></i> ${job.titre}</h4>
          <p><i class="fas fa-coins"></i> Prix: ${job.prix} FCFA</p>
          <p><i class="fas fa-info-circle"></i> ${job.description}</p>
        `;

                if (estPosteur && Array.isArray(job.postulants)) {
                    for (const postulantUID of job.postulants) {
                        let postulantNom = "Utilisateur";
                        try {
                            const postulantDoc = await getDoc(doc(db, "users", postulantUID));
                            if (postulantDoc.exists()) {
                                postulantNom = postulantDoc.data().nom || "Utilisateur";
                            }
                        } catch (e) { }

                        const btnId = `chat_${jobId}_${postulantUID}`;
                        const voirProfilBtnId = `voirProfil_${jobId}_${postulantUID}`;
                        div.innerHTML += `
              <p><strong><i class="fas fa-user"></i> Postulant:</strong> ${postulantNom}</p>
              <div style="display: flex; gap: 0.5rem; margin-top: 0.5rem;">
                <button class="btn btn-primary" id="${btnId}">
                  <i class="fas fa-comments"></i> Ouvrir chat
                </button>
                <button class="btn btn-secondary" id="${voirProfilBtnId}">
                  <i class="fas fa-user"></i> Voir le profil
                </button>
              </div>
            `;
                        setTimeout(() => {
                            const btn = document.getElementById(btnId);
                            if (btn) {
                                btn.addEventListener("click", () => {
                                    ouvrirChat(jobId, uid, postulantUID);
                                });
                            }

                            const voirProfilBtn = document.getElementById(voirProfilBtnId);
                            if (voirProfilBtn) {
                                voirProfilBtn.addEventListener("click", async () => {
                                    try {
                                        const userDoc = await getDoc(doc(db, "users", postulantUID));
                                        if (userDoc.exists()) {
                                            const data = userDoc.data();
                                            Swal.fire('👤 Profil de ' + (data.prenom || data.nom || "Utilisateur"), '\n\n🏙️ Ville: ' + (data.ville || "Non spécifiée") + '\n⏰ Expérience: ' + (data.statut || "Non spécifiée") + '\n🛠️ Compétences: ' + (data.competences || "Non spécifiées"), 'info');
                                        } else {
                                            Swal.fire('Erreur', 'Profil non trouvé', 'error');
                                        }
                                    } catch (error) {
                                        Swal.fire('Erreur', 'Erreur lors du chargement du profil', 'error');
                                    }
                                });
                            }
                        }, 0);
                    }
                }

                if (estPostulant && !estPosteur) {
                    let posteurNom = "Utilisateur";
                    try {
                        const posteurDoc = await getDoc(doc(db, "users", job.posteurUID));
                        if (posteurDoc.exists()) {
                            posteurNom = posteurDoc.data().nom || "Utilisateur";
                        }
                    } catch (e) { }

                    const btnId = `chat_${jobId}_${job.posteurUID}`;
                    div.innerHTML += `
            <p><strong><i class="fas fa-user"></i> Posteur:</strong> ${posteurNom}</p>
            <button class="btn btn-primary" id="${btnId}">
              <i class="fas fa-comments"></i> Ouvrir chat
            </button>
          `;

                    setTimeout(() => {
                        const btn = document.getElementById(btnId);
                        if (btn) {
                            btn.addEventListener("click", () => {
                                ouvrirChat(jobId, uid, job.posteurUID);
                            });
                        }
                    }, 0);
                }

                container.appendChild(div);
                total++;
            }

            if (total === 0) {
                container.innerHTML += `
          <div class="card text-center">
            <i class="fas fa-inbox" style="font-size: 3rem; color: var(--text-light); margin-bottom: 1rem;"></i>
            <p>Tu n'as aucune conversation.</p>
          </div>`;
            }

            const convSnap = await getDocs(collection(db, "conversations"));
            for (const convDoc of convSnap.docs) {
                const convId = convDoc.id;
                if (convId.includes(currentUser.uid)) {
                    const otherUid = convId.split("_").find(uid => uid !== currentUser.uid);
                    // Récupère le dernier message
                    const messagesRef = collection(db, "conversations", convId, "messages");
                    const lastMsgSnap = await getDocs(query(messagesRef, orderBy("timestamp", "desc"), limit(1)));
                    let lastMsg = null;
                    lastMsgSnap.forEach(doc => lastMsg = doc.data());
                    let preview = "";
                    if (lastMsg) {
                        const date = new Date(lastMsg.timestamp).toLocaleString();
                        preview = `<div style="color: #888; font-size: 0.9em; margin-bottom: 0.5em;">
                            <b>${lastMsg.auteur === currentUser.uid ? 'Moi' : 'Lui/Elle'}:</b> ${lastMsg.text} <span style="float:right;">${date}</span>
                        </div>`;
                    }
                    const div = document.createElement("div");
                    div.className = "card";
                    div.innerHTML = `
                        <h4><i class="fas fa-user"></i> Conversation privée</h4>
                        ${preview}
                        <button class="btn btn-primary" onclick="window.ouvrirChatPriveGeneral('${currentUser.uid}', '${otherUid}')">
                            <i class="fas fa-comments"></i> Ouvrir chat
                        </button>
                    `;
                    container.appendChild(div);
                }
            }
        }

        // Liaison des boutons
        window.addEventListener("DOMContentLoaded", () => {
            if (get("btnCreerCompte")) get("btnCreerCompte").addEventListener("click", creerCompte);
            if (get("btnSeConnecter")) get("btnSeConnecter").addEventListener("click", seConnecter);

            if (get("posterBtn")) get("posterBtn").addEventListener("click", envoyer);
            if (get("btnAcceuil")) get("btnAcceuil").addEventListener("click", afficheracceuil);
            if (get("btnPosterJob")) get("btnPosterJob").addEventListener("click", afficherformulaire);
            if (get("btnConversations")) get("btnConversations").addEventListener("click", lireConversations);
            if (get("envoyer")) get("envoyer").addEventListener("click", envoyerMessage);
            if (get("conclure")) get("conclure").addEventListener("click", conclureJob);
            if (get("fermerChat")) get("fermerChat").addEventListener("click", fermerChat);
            if (get("btnAnnuler")) get("btnAnnuler").addEventListener("click", afficheracceuil);
            if (get("voirProfils")) get("voirProfils").addEventListener("click", afficherProfilsUtilisateurs);
            if (get("profil")) get("profil").addEventListener("click", afficherProfil);
        });

        // Rendre les fonctions globales pour les boutons 
        window.postuler = postuler;
        window.ouvrirChat = ouvrirChat;
        window.envoyerMessage = envoyerMessage;
        window.fermerChat = fermerChat;
        window.conclureJob = conclureJob;
        window.afficherProfil = afficherProfil;
        window.afficherProfilsUtilisateurs = afficherProfilsUtilisateurs;

        async function ouvrirChatPriveGeneral(uid1, uid2) {
            console.log('ouvrirChatPriveGeneral appelé avec', uid1, uid2);
            idJobEnCours = null;
            idConversation = [uid1, uid2].sort().join("_");
            moi.style.display = "none";
            const profileHeader = document.getElementById("profile-header");
            if (profileHeader) profileHeader.style.display = "none";

            container.style.display = "none";
            formulaire.style.display = "none";
            chatDiv.style.display = "block";
            messagesDiv.innerHTML = "";
            const messagesRef = collection(db, "conversations", idConversation, "messages");
            const q = query(messagesRef, orderBy("timestamp", "asc"));
            onSnapshot(q, async (snapshot) => {
                messagesDiv.innerHTML = "";
                const messagesWithAuthors = await Promise.all(snapshot.docs.map(async docu => {
                    const msg = docu.data();
                    const auteurDoc = await getDoc(doc(db, "users", msg.auteur));
                    const auteurNom = auteurDoc.exists() ? (auteurDoc.data().prenom || auteurDoc.data().nom) : "Inconnu";
                    return { ...msg, auteurNom };
                }));
                messagesWithAuthors.forEach(msg => {
                    const div = document.createElement("div");
                    const isCurrentUser = msg.auteur === uid1;
                    div.className = `message ${isCurrentUser ? 'message-sent' : 'message-received'}`;
                    div.innerHTML = `<div class=\"message-author\">${msg.auteurNom}</div>${msg.text}`;
                    messagesDiv.appendChild(div);
                });
                messagesDiv.scrollTop = messagesDiv.scrollHeight;
            });
            const autreDoc = await getDoc(doc(db, "users", uid2));
            const autreNom = autreDoc.exists() ? (autreDoc.data().prenom || autreDoc.data().nom) : "Inconnu";
            document.querySelector('.chat-title').innerHTML = `<i class=\"fas fa-comments\"></i> Chat avec ${autreNom}`;
        }
        window.ouvrirChatPriveGeneral = ouvrirChatPriveGeneral;

        async function ouvrirChatPrive(otherUid) {
            const uid1 = auth.currentUser.uid;
            const uid2 = otherUid;
            await window.ouvrirChatPriveGeneral(uid1, uid2);
        }
        window.ouvrirChatPrive = ouvrirChatPrive;

        // Gestion globale des erreurs
        window.addEventListener('error', (event) => {
            console.error('Erreur JavaScript:', event.error);
            Swal.fire('Erreur', 'Une erreur inattendue s\'est produite. Veuillez rafraîchir la page.', 'error');
        });

        window.addEventListener('unhandledrejection', (event) => {
            console.error('Promesse rejetée:', event.reason);
            Swal.fire('Erreur', 'Une erreur réseau s\'est produite. Vérifiez votre connexion.', 'error');
        });
    </script>
</body>
