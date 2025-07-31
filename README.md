<!DOCTYPE html>
<html lang="fr">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MBOA Librairie</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap"
        rel="stylesheet">
    <style>
        :root {
            --primary-color: #6366f1;
            --primary-light: #818cf8;
            --primary-dark: #4f46e5;
            --secondary-color: #10b981;
            --secondary-light: #34d399;
            --accent-color: #f59e0b;
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
            --border-radius: 12px;
            --border-radius-lg: 16px;
            --border-radius-xl: 24px;
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            --container-max-width: 1200px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            font-size: 1rem;
            line-height: 1.6;
            color: var(--text-primary);
            background: var(--background-color);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
        }

        /* Container responsive */
        .container {
            max-width: var(--container-max-width, 1200px);
            margin: 0 auto;
            padding: 0 1rem;
            width: 100%;
        }

        /* En-tête principal */
        .entete {
            background: var(--surface-color);
            border-bottom: 1px solid var(--border-color);
            box-shadow: var(--shadow-sm);
            position: sticky;
            top: 0;
            z-index: 1000;
            transition: var(--transition);
            width: 100%;
        }

        /* Contenu de l'en-tête */
        .entete-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 1rem 0;
            gap: 1rem;
            flex-wrap: nowrap;
        }

        /* Logo et menu burger */
        .entete-logo {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            text-decoration: none;
            flex-shrink: 0;
        }

        .entete-logo strong {
            font-size: clamp(1.25rem, 2.5vw, 1.75rem);
            font-weight: 700;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -0.025em;
            white-space: nowrap;
        }

        /* Bouton menu burger (caché par défaut) */
        .btn-menu {
            display: none;
            background: var(--surface-color);
            border: 2px solid var(--border-color);
            color: var(--text-primary);
            width: 44px;
            height: 44px;
            border-radius: var(--border-radius);
            font-size: 1.2rem;
            cursor: pointer;
            transition: var(--transition);
        }

        .btn-menu:hover {
            border-color: var(--primary-color);
            color: var(--primary-color);
        }

        /* Barre de recherche */
        .entete-search {
            flex: 1;
            max-width: 500px;
            position: relative;
            min-width: 0;
        }

        .entete-search input {
            width: 100%;
            height: 48px;
            padding: 0 1rem 0 3rem;
            border: 2px solid var(--border-color);
            border-radius: var(--border-radius-xl, 24px);
            background: var(--surface-color);
            font-size: 1rem;
            transition: var(--transition);
            box-shadow: var(--shadow-sm);
        }

        .entete-search input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
            transform: translateY(-1px);
        }

        .entete-search i {
            position: absolute;
            left: 1rem;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-secondary);
            font-size: 1.1rem;
            z-index: 1;
        }

        /* Liste de suggestions */
        .suggestion-liste {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background: var(--surface-color);
            border: 1px solid var(--border-color);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-lg);
            max-height: 300px;
            overflow-y: auto;
            z-index: 1001;
        }

        /* Actions de l'en-tête */
        .entete-actions {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            flex-shrink: 0;
            flex-wrap: nowrap;
        }

        /* Boutons génériques */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.375rem;
            padding: 0.625rem 1rem;
            border: none;
            border-radius: var(--border-radius, 8px);
            font-size: 0.875rem;
            font-weight: 600;
            text-decoration: none;
            cursor: pointer;
            transition: var(--transition);
            white-space: nowrap;
            position: relative;
            overflow: hidden;
            min-height: 44px;
            box-sizing: border-box;
        }

        /* Variantes de boutons */
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
            background: linear-gradient(135deg, #10b981, #059669);
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        /* Responsive Design */

        /* Tablettes grandes (1024px et moins) */
        @media (max-width: 1024px) {
            .container {
                padding: 0 0.75rem;
            }

            .entete-content {
                gap: 0.75rem;
            }

            .entete-search {
                max-width: 400px;
            }

            .entete-actions {
                gap: 0.375rem;
            }

            .btn {
                padding: 0.5rem 0.875rem;
                font-size: 0.8rem;
            }

            /* Cacher certains textes des boutons */
            .btn span:not(.emoji) {
                display: none;
            }
        }

        /* Tablettes (768px et moins) */
        @media (max-width: 768px) {
            .container {
                padding: 0 0.5rem;
            }

            .entete-content {
                padding: 0.75rem 0;
                gap: 0.5rem;
                flex-wrap: wrap;
            }

            .entete-logo {
                order: 1;
                flex: 0 0 auto;
            }

            .entete-search {
                order: 3;
                flex: 1 1 100%;
                max-width: 100%;
                margin-top: 0.5rem;
            }

            .entete-actions {
                order: 2;
                gap: 0.25rem;
                flex-wrap: wrap;
            }

            .btn {
                padding: 0.5rem 0.75rem;
                font-size: 0.75rem;
                min-width: auto;
            }

            /* Afficher le menu burger */
            .btn-menu {
                display: flex;
            }

            /* Cacher certains boutons sur tablette */
            .entete-actions .btn:nth-child(n+5) {
                display: none;
            }
        }

        /* Mobiles (480px et moins) */
        @media (max-width: 480px) {
            .container {
                padding: 0 0.25rem;
            }

            .entete-content {
                padding: 0.5rem 0;
                gap: 0.25rem;
            }

            .entete-logo {
                gap: 0.5rem;
            }

            .entete-logo strong {
                font-size: 1.25rem;
            }

            .entete-search input {
                height: 44px;
                font-size: 0.9rem;
                padding: 0 0.75rem 0 2.5rem;
            }

            .entete-search i {
                left: 0.75rem;
                font-size: 1rem;
            }

            .entete-actions {
                gap: 0.125rem;
                overflow-x: auto;
                -webkit-overflow-scrolling: touch;
                scrollbar-width: none;
                -ms-overflow-style: none;
            }

            .entete-actions::-webkit-scrollbar {
                display: none;
            }

            .btn {
                padding: 0.375rem 0.5rem;
                font-size: 0.7rem;
                gap: 0.25rem;
                flex-shrink: 0;
            }

            .btn-menu {
                width: 40px;
                height: 40px;
                font-size: 1.1rem;
            }

            /* Ne garder que les boutons essentiels */
            .entete-actions .btn:not(.btn-menu):nth-child(n+4) {
                display: none;
            }
        }

        /* Très petits écrans (360px et moins) */
        @media (max-width: 360px) {
            .entete-logo strong {
                font-size: 1.1rem;
            }

            .entete-search input {
                height: 40px;
                font-size: 0.85rem;
            }

            .btn {
                padding: 0.25rem 0.375rem;
                font-size: 0.65rem;
                min-height: 36px;
            }

            .btn-menu {
                width: 36px;
                height: 36px;
                font-size: 1rem;
            }

            /* Ne garder que 2-3 boutons essentiels */
            .entete-actions .btn:not(.btn-menu):nth-child(n+3) {
                display: none;
            }
        }

        /* Menu mobile (quand activé) */
        .mobile-menu {
            display: none;
            position: fixed;
            top: 100%;
            left: 0;
            right: 0;
            background: var(--surface-color);
            border-top: 1px solid var(--border-color);
            box-shadow: var(--shadow-lg);
            z-index: 999;
            max-height: calc(100vh - 80px);
            overflow-y: auto;
        }

        .mobile-menu.active {
            display: block;
            animation: slideDown 0.3s ease;
        }

        .mobile-menu-content {
            padding: 1rem;
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .mobile-menu-content .btn {
            width: 100%;
            justify-content: flex-start;
            padding: 0.875rem 1rem;
            font-size: 0.9rem;
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Optimisations tactiles */
        @media (hover: none) and (pointer: coarse) {
            .btn:hover {
                transform: none;
            }

            .btn:active {
                transform: scale(0.95);
            }

            .entete-search input:focus {
                transform: none;
            }
        }

        /* Mode paysage mobile */
        @media (max-height: 500px) and (orientation: landscape) {
            .entete-content {
                padding: 0.5rem 0;
            }

            .entete-search {
                margin-top: 0;
            }

            .mobile-menu {
                max-height: calc(100vh - 60px);
            }
        }

        /* Support pour les écrans haute densité */
        @media (-webkit-min-device-pixel-ratio: 2),
        (min-resolution: 192dpi) {
            .entete {
                border-bottom-width: 0.5px;
            }

            .btn-secondary {
                border-width: 1px;
            }
        }

        .btn-success {
            background: linear-gradient(135deg, var(--secondary-color), var(--secondary-light));
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .btn-warning {
            background: linear-gradient(135deg, var(--accent-color), #fbbf24);
            color: white;
            box-shadow: var(--shadow);
        }

        .btn-warning:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .btn-menu {
            width: 48px;
            height: 48px;
            padding: 0;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            font-size: 1.25rem;
            box-shadow: var(--shadow);
        }

        .btn-menu:hover {
            transform: scale(1.1);
            box-shadow: var(--shadow-lg);
        }

        @media (max-width: 768px) {
            .btn {
                padding: 0.625rem 1.25rem;
                font-size: 0.8rem;
            }

            .btn-menu {
                width: 40px;
                height: 40px;
                font-size: 1rem;
            }
        }

        .tous {
            background: linear-gradient(135deg, var(--secondary-color), var(--secondary-light));
            color: white;
            padding: 15px 20px;
            font-size: 1.3rem;
            font-weight: 600;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            margin-bottom: 15px;
        }

        .fournitures {
            padding: 30px;
            width: 90%;
            max-width: 100%;
            background: rgba(255, 255, 255, 0.5);
            backdrop-filter: blur(20px);
            border-radius: var(--border-radius);
            margin: 20px;
            box-shadow: var(--shadow);
        }

        ul {
            list-style: none;
        }

        li {
            padding: 15px 20px;
            background: rgba(255, 255, 255, 0.9);
            margin-bottom: 8px;
            border-radius: var(--border-radius);
            cursor: pointer;
            transition: var(--transition);
            border-left: 4px solid transparent;
            position: relative;
            overflow: hidden;
        }

        li::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 98, 0, 0.1), transparent);
            transition: var(--transition);
        }

        li:hover {
            background: rgba(255, 255, 255, 1);
            transform: translateX(10px);
            border-left-color: var(--primary-color);
            box-shadow: var(--shadow);
        }

        li:hover::before {
            left: 100%;
        }

        .sous-menu {
            display: none;
            margin-left: 20px;
            padding-top: 15px;
        }

        li.active .sous-menu {
            display: block;
            animation: slideDown 0.3s ease;
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .separe {
            color: var(--secondary-color);
            font-size: 1.4rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .avise {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            padding: 40px;
            margin: 40px auto;
            border-radius: 20px;
            max-width: 600px;
            box-shadow: var(--shadow-lg);
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .star {
            font-size: 3rem;
            color: #e0e0e0;
            cursor: pointer;
            transition: var(--transition);
            margin: 0 5px;
            display: inline-block;
        }

        .star:hover,
        .star.active {
            color: #ffc107;
            transform: scale(1.2);
            text-shadow: 0 0 20px rgba(255, 193, 7, 0.5);
        }

        #avi {
            width: 100%;
            max-width: 500px;
            height: 120px;
            border-radius: var(--border-radius);
            border: 2px solid #e2e8f0;
            background: rgba(255, 255, 255, 0.9);
            padding: 15px;
            font-size: 1rem;
            font-family: inherit;
            transition: var(--transition);
            resize: none;
        }

        #avi:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 4px rgba(255, 98, 0, 0.1);
        }

        .soumettre {
            background: linear-gradient(135deg, #28a745, #20c997);
            color: white;
            padding: 15px 30px;
            border-radius: var(--border-radius);
            border: none;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: var(--shadow);
            margin-top: 20px;
        }

        .soumettre:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(40, 167, 69, 0.3);
        }

        .form-container {
            background: var(--surface-color);
            border-radius: var(--border-radius-lg);
            box-shadow: var(--shadow-lg);
            padding: 2rem;
            margin: 2rem auto;
            max-width: 600px;
            border: 1px solid var(--border-color);
        }

        .form-title {
            font-size: 1.75rem;
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
        .form-select {
            width: 100%;
            height: 48px;
            padding: 0 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--border-radius);
            background: var(--surface-color);
            font-size: 1rem;
            font-family: inherit;
            transition: var(--transition);
            color: var(--text-primary);
        }

        .form-input:focus,
        .form-select:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .form-textarea {
            width: 100%;
            min-height: 100px;
            padding: 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--border-radius);
            background: var(--surface-color);
            font-size: 1rem;
            font-family: inherit;
            transition: var(--transition);
            resize: vertical;
            color: var(--text-primary);
        }

        .form-textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .form-actions {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
        }

        .form-actions .btn {
            flex: 1;
        }

        @media (max-width: 768px) {
            .form-container {
                margin: 1rem;
                padding: 1.5rem;
            }

            .form-actions {
                flex-direction: column;
            }
        }

        #confirmer,
        #photoB {
            background: linear-gradient(135deg, var(--secondary-color), var(--secondary-light));
            color: white;
            padding: 15px 30px;
            border-radius: var(--border-radius);
            border: none;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            text-align: center;
            box-shadow: var(--shadow);
        }

        #confirmer:hover,
        #photoB:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 123, 255, 0.3);
        }

        #photoB {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            width: 100%;
            max-width: 300px;
            margin: 0 auto;
        }

        /* Grid responsive pour les annonces */
        .annonces-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
            padding: 2rem 1rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .annonce-card {
            background: var(--surface-color);
            border-radius: var(--border-radius-lg);
            box-shadow: var(--shadow);
            overflow: hidden;
            transition: var(--transition);
            border: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            height: fit-content;
            max-width: 100%;
        }

        .annonce-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-xl);
        }

        .annonce-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            background: linear-gradient(135deg, #f3f4f6, #e5e7eb);
            flex-shrink: 0;
        }

        .annonce-content {
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .annonce-title {
            font-size: clamp(1.1rem, 2.5vw, 1.25rem);
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 0.75rem;
            line-height: 1.3;
            word-wrap: break-word;
            overflow-wrap: break-word;
        }

        /* Prix responsive */
        .annonce-price {
            font-size: clamp(1.25rem, 3vw, 1.5rem);
            font-weight: 800;
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        /* Détails en grid responsive */
        .annonce-details {
            display: grid;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
        }

        .annonce-detail {
            display: flex;
            align-items: flex-start;
            gap: 0.5rem;
            color: var(--text-secondary);
            font-size: 0.875rem;
            line-height: 1.4;
        }

        .annonce-detail strong {
            color: var(--text-primary);
            font-weight: 600;
            min-width: 60px;
            flex-shrink: 0;
        }

        /* Description responsive */
        .annonce-description {
            color: var(--text-secondary);
            font-size: 0.875rem;
            line-height: 1.6;
            margin-bottom: 1.5rem;
            word-wrap: break-word;
            overflow-wrap: break-word;
            flex-grow: 1;
        }

        /* Actions responsive */
        .annonce-actions {
            display: flex;
            gap: 0.75rem;
            margin-top: auto;
        }

        .annonce-actions .btn {
            flex: 1;
            padding: 0.75rem 1rem;
            font-size: 0.875rem;
            font-weight: 600;
            border-radius: var(--border-radius);
            transition: var(--transition);
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            min-height: 44px;
            /* Taille minimum tactile */
        }

        /* Responsive Breakpoints */

        /* Tablettes (768px et moins) */
        @media (max-width: 768px) {
            .annonces-grid {
                grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
                gap: 1.25rem;
                padding: 1.5rem 0.75rem;
            }

            .annonce-content {
                padding: 1.25rem;
            }

            .annonce-image {
                height: 180px;
            }
        }

        /* Mobiles (480px et moins) */
        @media (max-width: 480px) {
            .annonces-grid {
                grid-template-columns: 1fr;
                gap: 1rem;
                padding: 1rem 0.5rem;
            }

            .annonce-card {
                margin: 0 auto;
                width: 100%;
                max-width: 400px;
            }

            .annonce-content {
                padding: 1rem;
            }

            .annonce-image {
                height: 160px;
            }

            .annonce-title {
                font-size: 1.1rem;
                margin-bottom: 0.5rem;
            }

            .annonce-price {
                font-size: 1.25rem;
                margin-bottom: 0.75rem;
            }

            .annonce-details {
                margin-bottom: 1rem;
            }

            .annonce-detail {
                font-size: 0.8rem;
            }

            .annonce-detail strong {
                min-width: 50px;
                font-size: 0.8rem;
            }

            .annonce-description {
                font-size: 0.8rem;
                margin-bottom: 1rem;
            }

            .annonce-actions {
                flex-direction: column;
                gap: 0.5rem;
            }

            .annonce-actions .btn {
                width: 100%;
                padding: 0.875rem 1rem;
                font-size: 0.9rem;
            }
        }

        /* Très petits écrans (360px et moins) */
        @media (max-width: 360px) {
            .annonces-grid {
                padding: 0.75rem 0.25rem;
            }

            .annonce-card {
                max-width: 100%;
            }

            .annonce-content {
                padding: 0.875rem;
            }

            .annonce-image {
                height: 140px;
            }

            .annonce-title {
                font-size: 1rem;
            }

            .annonce-price {
                font-size: 1.15rem;
            }

            .annonce-detail,
            .annonce-description {
                font-size: 0.75rem;
            }

            .annonce-detail strong {
                min-width: 45px;
                font-size: 0.75rem;
            }
        }

        /* Améliorations pour l'accessibilité tactile */
        @media (hover: none) and (pointer: coarse) {
            .annonce-card:hover {
                transform: none;
            }

            .annonce-card:active {
                transform: scale(0.98);
            }

            .annonce-actions .btn {
                min-height: 48px;
                /* Taille recommandée pour le tactile */
            }
        }

        /* Mode sombre responsive */
        @media (prefers-color-scheme: dark) {
            .annonce-image {
                background: linear-gradient(135deg, #374151, #1f2937);
            }
        }

        /* Optimisation pour les écrans haute densité */
        @media (-webkit-min-device-pixel-ratio: 2),
        (min-resolution: 192dpi) {
            .annonce-card {
                border-width: 0.5px;
            }
        }

        .competences {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            padding: 20px;
            border-radius: var(--border-radius);
            font-size: 1.3rem;
            font-weight: 600;
            text-align: center;
            margin: 30px auto;
            max-width: 600px;
            box-shadow: var(--shadow);
        }

        #connexion {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            padding: 40px;
            margin: 50px auto;
            border-radius: 20px;
            max-width: 500px;
            box-shadow: var(--shadow-lg);
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        #connexion input {
            margin-bottom: 20px;
            height: 50px;
            border-radius: var(--border-radius);
            border: 2px solid #e2e8f0;
            background: rgba(255, 255, 255, 0.9);
            padding: 0 15px;
            font-size: 1rem;
            font-family: inherit;
            transition: var(--transition);
            width: 100%;
        }

        #connexion input:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 4px rgba(255, 98, 0, 0.1);
        }

        #connexion button {
            width: 100%;
            padding: 15px;
            border-radius: var(--border-radius);
            background: linear-gradient(135deg, #28a745, #20c997);
            color: white;
            border: none;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            margin-bottom: 15px;
            box-shadow: var(--shadow);
        }

        #connexion button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(40, 167, 69, 0.3);
        }

        footer {
            background: linear-gradient(135deg, #2c3e50, #34495e);
            color: white;
            padding: 3rem 2rem;
            text-align: center;
            margin-top: auto;
            position: relative;
            overflow: hidden;
        }

        footer::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.1) 1px, transparent 1px);
            background-size: 20px 20px;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(0px) rotate(0deg);
            }

            100% {
                transform: translateY(-20px) rotate(360deg);
            }
        }

        footer p {
            font-size: 1.1rem;
            margin-bottom: 1.5rem;
            position: relative;
            z-index: 1;
        }

        .lien {
            position: relative;
            z-index: 1;
        }

        .lien a {
            color: #fff;
            font-size: 1.5rem;
            margin: 0 1rem;
            text-decoration: none;
            transition: var(--transition);
            display: inline-block;
        }

        .lien a:hover {
            color: var(--primary-color);
            transform: translateY(-3px) scale(1.1);
        }

        .listes {
            color: white;
            background: linear-gradient(135deg, #333, #555);
            width: 96%;
            height: 50px;
            padding: 10px 15px;
            border-radius: var(--border-radius);
            text-align: center;
            font-weight: 600;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: var(--shadow);
        }

        .suggestion-liste {
            position: absolute;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(0, 0, 0, 0.1);
            border-radius: var(--border-radius);
            list-style: none;
            padding: 0;
            margin: 0;
            z-index: 1000;
            width: 80%;
            max-height: 300px;
            overflow-y: auto;
            box-shadow: var(--shadow-lg);
            margin-top: 5px;
        }

        .suggestion-liste li {
            padding: 15px 20px;
            cursor: pointer;
            transition: var(--transition);
            border-bottom: 1px solid rgba(0, 0, 0, 0.05);
        }

        .suggestion-liste li:hover {
            background: var(--primary-color);
            color: white;
            transform: none;
        }

        .chat-container {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 90%;
            max-width: 800px;
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
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .chat-actions {
            display: flex;
            gap: 0.75rem;
        }

        .chat-actions .btn {
            flex: 1;
        }

        @media (max-width: 768px) {
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
        }

        #envoyer,
        #conclure,
        #fermerChat {
            width: 100%;
            height: 50px;
            font-size: 1rem;
            font-family: 'Poppins', sans-serif;
            font-weight: 600;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border-radius: var(--border-radius);
            border: none;
            padding: 12px 20px;
            margin-bottom: 15px;
            cursor: pointer;
        }

        #envoyer {
            background: linear-gradient(135deg, #28a745, #20c997);
            color: white;
        }

        #envoyer:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(40, 167, 69, 0.3);
        }

        #conclure {
            background: linear-gradient(135deg, #ffc107, #ffca2c);
            color: #333;
        }

        #conclure:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(255, 193, 7, 0.3);
        }

        #fermerChat {
            background: linear-gradient(135deg, #dc3545, #e74c3c);
            color: white;
        }

        #fermerChat:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(220, 53, 69, 0.3);
        }

        #messageInput {
            margin-bottom: 25px;
            height: 45px;
            width: 90%;
            font-size: 1.1rem;
            border-radius: 25px;
            border: 2px solid #e2e8f0;
            background: rgba(255, 255, 255, 0.9);
            padding: 10px 20px;
            font-family: inherit;
            transition: var(--transition);
        }

        #messageInput:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 4px rgba(255, 98, 0, 0.1);
        }

        @media (max-width: 768px) {
            .entete {
                flex-direction: column;
                gap: 20px;
                padding: 20px;
            }

            .entete input {
                width: 100%;
                max-width: none;
            }

            .avise,
            #formulaire,
            #connexion {
                width: 95%;
                margin: 20px auto;
                padding: 30px 20px;
            }

            #chat {
                position: fixed;
                top: 20px;
                left: 20px;
                right: 20px;
                max-width: none;
                width: calc(100% - 40px);
            }

            .entete strong {
                font-size: 1.8rem;
            }

            .trois {
                font-size: 1.5rem;
                width: 45px;
                height: 45px;
            }
        }

        .entete {
            animation: slideDown 0.6s ease;
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .loading {
            position: relative;
            overflow: hidden;
        }

        .loading::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            animation: loading 1.5s infinite;
        }

        @keyframes loading {
            0% {
                left: -100%;
            }

            100% {
                left: 100%;
            }
        }

        #conteneuravis {
            height: 40%;
            width: 60%;
            border-radius: 20px;
            border: 2px solid lavender;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
            margin: 20px auto;
            color: white;
            font-weight: 600;
        }

        .conteneuravis {
            background: rgba(255, 255, 255, 0.9);
            padding: 15px;
            margin: 10px 0;
            border-radius: 10px;
            color: var(--text-color);
            box-shadow: var(--shadow);
        }

        .content-section {
            padding: 2rem 0;
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            color: var(--text-primary);
            text-align: center;
            margin-bottom: 2rem;
        }

        .suggestion-liste {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background: var(--surface-color);
            border: 1px solid var(--border-color);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-lg);
            z-index: 1000;
            max-height: 300px;
            overflow-y: auto;
        }

        .suggestion-liste li {
            padding: 0.75rem 1rem;
            cursor: pointer;
            transition: var(--transition);
            border-bottom: 1px solid var(--border-color);
        }

        .suggestion-liste li:hover {
            background: var(--primary-color);
            color: white;
        }

        .suggestion-liste li:last-child {
            border-bottom: none;
        }

        .star {
            font-size: 2rem;
            color: #e5e7eb;
            cursor: pointer;
            transition: var(--transition);
            margin: 0 0.25rem;
        }

        .star:hover,
        .star.active {
            color: #fbbf24;
            transform: scale(1.1);
        }

        footer {
            background: linear-gradient(135deg, var(--text-primary), #374151);
            color: white;
            padding: 3rem 0;
            margin-top: auto;
        }

        .lien {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 1.5rem;
        }

        .lien a {
            color: white;
            text-decoration: none;
            font-size: 1.1rem;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .lien a:hover {
            color: var(--primary-light);
            transform: translateY(-2px);
        }

        @media (max-width: 768px) {
            .lien {
                flex-direction: column;
                gap: 1rem;
                align-items: center;
            }
        }

        .advanced {
            display: flex;
            margin: 30px;
            position: relative;
        }

        .croix {
            background: transparent;
            background-color: transparent;
            height: 40px;
            width: 40px;
            border-radius: 25px;
            justify-content: center;
            font-size: 40px;
            align-items: center;
            position: relative;
            left: 17%;
            top: 0;
            border: none;
        }

        .croix:hover {
            background-color: lavender;
        }

        #btnSeConnecter {
            font-size: 10px;
        }

        @media (max-width: 600px) {

            .container,
            .form-container,
            .avise,
            .fournitures {
                width: 100vw !important;
                max-width: 100vw !important;
                margin: 0 !important;
                padding: 8px !important;
                border-radius: 0 !important;
                box-shadow: none !important;
            }

            .entete-content {
                flex-direction: column;
                gap: 0.5rem;
                align-items: stretch;
                padding: 0.5rem 0 !important;
            }

            .entete-actions {
                flex-wrap: nowrap !important;
                overflow-x: auto !important;
                -webkit-overflow-scrolling: touch;
                scrollbar-width: none;
                -ms-overflow-style: none;
            }

            .entete-actions::-webkit-scrollbar {
                display: none;
            }

            .entete-actions .btn {
                flex-shrink: 0;
                min-width: 120px;
                margin-right: 0.5rem;
            }

            .annonces-grid {
                grid-template-columns: 1fr !important;
                gap: 1rem !important;
                padding: 0.5rem !important;
                margin: 0 !important;
            }

            .annonce-card {
                margin: 0 auto !important;
                border-radius: 10px !important;
                box-shadow: var(--shadow-sm) !important;
                max-width: 100vw !important;
            }

            .annonce-image {
                height: 140px !important;
                object-fit: cover !important;
                border-radius: 10px 10px 0 0 !important;
                width: 100% !important;
                max-width: 100vw !important;
            }

            .chat-container {
                width: 100vw !important;
                left: 0 !important;
                transform: none !important;
                border-radius: 0 !important;
                max-width: 100vw !important;
                height: 100vh !important;
                top: 0 !important;
            }

            .chat-messages {
                padding: 0.5rem !important;
                font-size: 0.95rem !important;
            }

            .chat-header,
            .chat-input-container {
                padding: 0.5rem !important;
            }

            .form-actions {
                flex-direction: column !important;
                gap: 0.5rem !important;
            }

            .entete-search input {
                font-size: 1rem !important;
                height: 40px !important;
                padding-left: 2.5rem !important;
            }

            .suggestion-liste {
                width: 100vw !important;
                left: 0 !important;
                border-radius: 0 0 10px 10px !important;
            }

            #conteneuravis {
                width: 100vw !important;
                margin: 0 !important;
                border-radius: 0 !important;
                padding: 10px !important;
            }

            body,
            html {
                overflow-x: hidden !important;
            }
        }

        #temps {
            border: none;
            position: relative;
            left: 50px;
            font-size: 30px;
        }

        #chat {
            position: relative;
            top: 150px;
            left: 100px;
        }
    </style>
</head>

<body id="bod" data-aos="fade-down-right">
    <div class="entete" id="entete">
        <div class="container">
            <div class="entete-content">
                <div class="entete-logo">
                    <button class="btn btn-menu" id="trois">☰</button>
                    <strong>MBOA Librairie</strong>
                    <button class="btn btn-secondary" id="temps">🌞</button>
                </div>

                <div class="entete-search">
                    <i class="fas fa-search"></i>
                    <input type="search" id="searchBar" placeholder="Rechercher un produit..." autocomplete="off" />
                    <ul id="suggestions" class="suggestion-liste" style="display:none;"></ul>
                </div>

                <div class="entete-actions">
                    <button class="btn btn-secondary" id="accueilBtn">
                        <i class="fas fa-home"></i> Accueil
                    </button>
                    <button class="btn btn-secondary" id="avis">🌟 Avis</button>
                    <button onclick="lireConversations()" class="btn btn-secondary" id="mess"
                        aria-label="Voir mes conversations">
                        <i class="fas fa-comments"></i> Messages
                    </button>
                    <a href="https://wa.me/237657300644" class="btn btn-secondary" id="question">❓ Question</a>
                    <button class="btn btn-primary" id="vendre">💼 Vendre</button>
                    <button class="btn btn-success" id="connexionn">🔐 Connexion</button>
                </div>
            </div>
        </div>
    </div>

    <div class="fournitures" id="fourniture" style="display: none;">
        <p class="listes">❤️ Mes listes</p>
        <br>
        <p class="tous">📋 Tous les rayons</p>
        <ul>
            <li onclick="afficherFournituresCategorie('livres')" id="livre">
                <p class="separe">📚 Livres</p>
                <ul class="sous-menu">
                    <li>🎓 Terminale</li>
                    <li>📖 Première</li>
                    <li>📝 Seconde</li>
                    <li>✏️ Troisième</li>
                    <li>📄 Quatrième</li>
                    <li>📑 Cinquième</li>
                    <li>📋 Sixième</li>
                    <li>📊 CM2</li>
                    <li>📈 CM1</li>
                    <li>📉 CE2</li>
                    <li>📌 CE1</li>
                    <li>📍 CP</li>
                    <li>🔤 SIL</li>
                </ul>
            </li>
            <li onclick="afficherFournituresCategorie('produits')" id="produit">
                <p class="separe">🛍️ Produits</p>
                <ul class="sous-menu">
                    <li>📔 Cahiers</li>
                    <li>📐 Boîte académique</li>
                    <li>🎒 Sacs</li>
                    <li>🧮 Calculatrice</li>
                </ul>
            </li>
        </ul>
    </div>

    <div id="connexion" style="display: none;">
        <div class="advanced">
            <h3 style="margin-bottom: 30px; color: var(--primary-color); font-size: 2rem;">🔐 Connexion</h3><button
                class="croixe"
                onclick="document.getElementById('connexion').style.display='none'; document.getElementById('conteneurProfils').style.display='block';">×</button>
        </div>
        <input type="text" class="nom" id="nom" placeholder="👤 Entrez votre nom" />
        <input type="number" class="nom" id="numero" placeholder="📱 Votre numéro" />
        <input type="email" class="nom" id="email" placeholder="📧 Entrez votre adresse email" />
        <input type="password" class="nom" id="motdepasse" placeholder="🔒 Mot de passe" />
        <button id="btnCreerCompte">✨ Créer un Compte</button>
        <button id="btnSeConnecter" class="fas fa-sign-in-alt"> Se connecter</button>
    </div>

    <div class="chat-container" id="chat" style="display: none;">
        <div class="chat-header">
            <span class="chat-title" id="chatTitre">💬 Chat de la vente</span>
            <button class="chat-close"
                onclick="document.getElementById('chat').style.display='none'; document.getElementById('conteneurProfils').style.display='block';">✖</button>
        </div>

        <div class="chat-messages" id="messages"></div>

        <div class="chat-input-container">
            <div class="chat-input-group">
                <input class="chat-input" id="messageInput" placeholder="💭 Écris un message..." />
                <button class="btn btn-primary" onclick="envoyerMessage()">📤 Envoyer</button>
            </div>

            <div class="chat-actions">
                <button class="btn btn-warning" onclick="conclureJob()">✅ Conclure</button>
                <button class="btn btn-secondary"
                    onclick="document.getElementById('chat').style.display='none'; document.getElementById('conteneurProfils').style.display='block';">❌
                    Fermer</button>
            </div>
        </div>
    </div>
    <div id="conteneuravis"></div>

    <div class="avise" id="avise" style="display: none;">
        <div class="advanced">
            <h4 style="margin-bottom: 30px; color: var(--primary-color); font-size: 1.8rem;">⭐ Donnez votre avis</h4>
            <button class="croix"
                onclick="document.getElementById('avise').style.display='none'; document.getElementById('conteneurProfils').style.display='block';">×</button>
        </div>
        <div id="stars" style="margin-bottom: 25px;">
            <span class="star" onclick="rate(1)">★</span>
            <span class="star" onclick="rate(2)">★</span>
            <span class="star" onclick="rate(3)">★</span>
            <span class="star" onclick="rate(4)">★</span>
            <span class="star" onclick="rate(5)">★</span>
        </div>
        <textarea id="avi" placeholder="💭 Votre commentaire..."></textarea>
        <button class="soumettre" id="soumettre">🚀 Soumettre</button>
    </div>

    <div class="form-container" id="formulaire" data-aos="fade-up" style="display: none;">
        <div class="advanced">
            <h3 class="form-title">📦 Vendre une fourniture</h3><button class="croix"
                onclick="document.getElementById('formulaire').style.display='none'; document.getElementById('conteneurProfils').style.display='block';">×</button>
        </div>
        <form id="form">
            <div class="form-group">
                <label class="form-label" for="item">🏷️ Que vendez-vous ?</label>
                <select class="form-select" id="item">
                    <option value="Livres">📚 Livres</option>
                    <option value="Bords">📝 Bords</option>
                    <option value="Cahiers">📔 Cahiers</option>
                    <option value="Calculatrice">🧮 Calculatrice</option>
                    <option value="Sacs">🎒 Sacs</option>
                </select>
            </div>

            <div class="form-group">
                <label class="form-label" for="categorie">📂 Catégorie :</label>
                <select class="form-select" id="categorie" required>
                    <option value="livres">📚 Livres</option>
                    <option value="produits">🛍️ Produits</option>
                </select>
            </div>

            <div class="form-group">
                <label class="form-label" for="price">💰 Prix (en FCFA) :</label>
                <input class="form-input" type="number" id="price" min="0" required placeholder="Ex: 5000" />
            </div>

            <div class="form-group">
                <label class="form-label" for="classe">🎓 Classe :</label>
                <select class="form-select" id="classe" required>
                    <option value="terminale">🎓 Terminale</option>
                    <option value="premiere">📖 Première</option>
                    <option value="seconde">📝 Seconde</option>
                    <option value="troisieme">✏️ Troisième</option>
                    <option value="quatrieme">📄 Quatrième</option>
                    <option value="cinquieme">📑 Cinquième</option>
                    <option value="sixieme">📋 Sixième</option>
                    <option value="cm2">📊 CM2</option>
                    <option value="cm1">📈 CM1</option>
                    <option value="ce2">📉 CE2</option>
                    <option value="ce1">📌 CE1</option>
                    <option value="cp">📍 CP</option>
                    <option value="sil">🔤 SIL</option>
                </select>
            </div>

            <div class="form-group">
                <label class="form-label" for="location">📍 Lieu (quartier) :</label>
                <select class="form-select" id="location">
                    <option value="Douala">🏙️ Douala</option>
                    <option value="Yaounde">🏛️ Yaoundé</option>
                    <option value="Bafoussam">🏔️ Bafoussam</option>
                    <option value="Limbe">🌊 Limbe</option>
                    <option value="Kribi">🏖️ Kribi</option>
                    <option value="Garoua">🌆 Garoua</option>
                    <option value="Melong">🏘️ Melong</option>
                    <option value="Nkongsamba">🏞️ Nkongsamba</option>
                    <option value="Autre">🌍 Autre</option>
                </select>
            </div>

            <div class="form-group">
                <label class="form-label" for="description">📝 Description :</label>
                <input class="form-input" type="text" id="description" required
                    placeholder="Décrivez votre article..." />
            </div>

            <div class="form-actions">
                <button type="button" class="btn btn-secondary" id="photoB">📸 Ajouter une photo</button>
                <button class="btn btn-primary" id="confirmer" type="submit">🚀 Publier</button>
            </div>

            <input type="file" accept="image/*" id="camer" style="display: none;" />

            <div id="maphoto">
                <img src="" alt="Aperçu" id="photoPreview"
                    style="display: none; max-width: 100%; border-radius: 12px; box-shadow: var(--shadow); margin-top: 15px;" />
            </div>
        </form>
    </div>

    <div class="profile" id="conteneurProfils" style="display: none;"></div>
    <script src="https://api-checkout.cinetpay.com/v2/checkout.js"></script>
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
        import { getFirestore, collection, addDoc, getDocs, doc, onSnapshot, query, where, orderBy, setDoc, getDoc, updateDoc, increment } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";
        import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";
        import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-analytics.js";
        import { getStorage, ref, uploadBytes, getDownloadURL } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-storage.js";

        // 🔧 Configuration Firebase
        const firebaseConfig = {
            apiKey: "AIzaSyCwYVursGqdwA47BgpjxFx-UuPOooorqcU",
            authDomain: "mboa-librerie.firebaseapp.com",
            projectId: "mboa-librerie",
            storageBucket: "mboa-librerie.appspot.com",
            messagingSenderId: "323486943031",
            appId: "1:323486943031:web:a536c81bfc61517eddfcb2",
            measurementId: "G-X514RE9V3G"
        };

        const app = initializeApp(firebaseConfig);
        const analytics = getAnalytics(app);
        const db = getFirestore(app);
        const storage = getStorage(app);
        const auth = getAuth(app);

        // 🔎 Sélecteurs
        const form = document.getElementById("form");
        const camer = document.getElementById("camer");
        const photoB = document.getElementById("photoB");
        const photoPreview = document.getElementById("photoPreview");
        const conteneurProfils = document.getElementById("conteneurProfils");
        const formulaire = document.getElementById("formulaire");
        const confirmerBtn = document.getElementById("confirmer");

        // --- Variables globales pour annonces ---
        let allAnnonces = [];
        let imageFile = null;
        let utilisateurNom = localStorage.getItem('utilisateurNom') || null;
        if (!utilisateurNom) {
            utilisateurNom = prompt("Entrez votre nom pour le chat :") || "Utilisateur";
            localStorage.setItem('utilisateurNom', utilisateurNom);
        }
        let annonceActuelle = null;

        // Variables globales pour le chat privé par annonce
        let idAnnonceEnCours = null;
        let idConversation = null;

        // --- Sélecteurs supplémentaires pour l'auth ---
        const btnCreerCompte = document.getElementById("btnCreerCompte");
        const btnSeConnecter = document.getElementById("btnSeConnecter");
        const btnDeconnexion = document.createElement("button");
        btnDeconnexion.textContent = "Déconnexion";
        btnDeconnexion.className = "fourniture";
        btnDeconnexion.style.display = "none";
        document.getElementById("entete").appendChild(btnDeconnexion);
        const userDisplay = document.createElement("span");
        userDisplay.style.marginLeft = "15px";
        document.getElementById("entete").appendChild(userDisplay);

        // --- Gestion de l'état de connexion ---
        function majEtatConnexion(user) {
            if (user) {
                btnDeconnexion.style.display = "inline-block";
                userDisplay.textContent = `Connecté : ${user.email}`;
                document.getElementById("connexion").style.display = "none";
                btnConnexion.style.display = "none";
                btnVendre.style.display = "inline-block";
                document.getElementById("question").style.display = "inline-block";
            } else {
                btnDeconnexion.style.display = "none";
                userDisplay.textContent = "";
                btnConnexion.style.display = "inline-block";
                btnVendre.style.display = "none";
                document.getElementById("question").style.display = "inline-block";
            }
        }
        onAuthStateChanged(auth, majEtatConnexion);

        // Bouton pour une photo
        photoB.addEventListener("click", () => {
            camer.click();
        });
        camer.addEventListener("change", (e) => {
            imageFile = e.target.files[0];
            if (imageFile) {
                const imageUrl = URL.createObjectURL(imageFile);
                photoPreview.src = imageUrl;
                photoPreview.style.display = "block";
            }
        });

        // formulaire
        form.addEventListener("submit", async (e) => {
            e.preventDefault();
            document.getElementById("conteneurProfils").style.display = "none";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "none";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
            if (!utilisateurConnecte()) {
                alert("Vous devez être connecté pour publier une annonce.");
                return;
            }
            //  le blocage
            const stats = await getUserStats(auth.currentUser.email);
            if (stats.ventes >= 2) {
                alert("Vous avez atteint la limite de 2 ventes.");
                return;
            }
            if (!imageFile) {
                alert("Merci de sélectionner une image !");
                return;
            }
            const nomProduit = document.getElementById("item").value;
            const prix = document.getElementById("price").value;
            const classe = document.getElementById("classe").value;
            const lieu = document.getElementById("location").value;
            const description = document.getElementById("description").value;
            const categorie = document.getElementById("categorie").value;
            let imageUrl = "";
            try {
                imageUrl = await uploadImage(imageFile);
                // Ajoute l'annonce dans Firestore et récupère son id
                const docRef = await addDoc(collection(db, "annonces"), {
                    nomProduit,
                    prix,
                    classe,
                    lieu,
                    description,
                    categorie,
                    imageUrl,
                    auteur: auth.currentUser.email
                });
                // Ajoute l'annonce dans le tableau local avec son id
                allAnnonces.push({
                    id: docRef.id,
                    nomProduit,
                    prix,
                    classe,
                    lieu,
                    description,
                    categorie,
                    imageUrl,
                    auteur: auth.currentUser.email
                });
                await incrementUserStat(auth.currentUser.email, "ventes");
                alert("Annonces poster avec succes");
                afficherAnnonces(allAnnonces);
                formulaire.style.display = "none";
                form.reset();
                photoPreview.style.display = "none";
                imageFile = null;
                checkBlockPublier();
            } catch (err) {
                alert("Erreur lors de la publication ou de l'upload de l'image : " + err.message);

                return;
            }
        });

        // --- Création de compte ---
        btnCreerCompte.addEventListener("click", async () => {
            document.getElementById("connexion").style.display = "block";
            const email = document.getElementById("email").value;
            const password = document.getElementById("motdepasse").value;
            try {
                await createUserWithEmailAndPassword(auth, email, password);
                alert("Compte créé et connecté !");
                document.getElementById("conteneurProfils").style.display = "block";
                document.getElementById("connexion").style.display = "none";
            } catch (e) {
                alert("Erreur création de compte : " + e.message);
            }
        });

        // --- Connexion ---
        btnSeConnecter.addEventListener("click", async () => {

            document.getElementById("connexion").style.display = "block";
            const email = document.getElementById("email").value;
            const password = document.getElementById("motdepasse").value;
            try {
                await signInWithEmailAndPassword(auth, email, password);
                alert("Connecté !");
                document.getElementById("conteneurProfils").style.display = "block";
                document.getElementById("connexion").style.display = "none";
            } catch (e) {
                alert("Erreur connexion : " + e.message);
            }
        });

        // --- Déconnexion ---
        btnDeconnexion.addEventListener("click", async () => {
            await signOut(auth);
            alert("Déconnecté !");
            document.getElementById("conteneurProfils").style.display = "block";
        });

        // --- Empêche publication/chat si non connecté ---
        function utilisateurConnecte() {
            return auth.currentUser;
        }

        // --- Recherche dynamique ---
        const searchBar = document.getElementById("searchBar");
        const suggestions = document.getElementById("suggestions");

        // --- Recherche dynamique optimisée (filtrage côté client) ---
        searchBar.addEventListener("input", function () {
            document.getElementById("conteneurProfils").style.display = "block";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "none";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
            const searchTerm = searchBar.value.trim().toLowerCase();
            suggestions.innerHTML = "";
            if (!searchTerm) {
                suggestions.style.display = "none";
                afficherAnnonces(allAnnonces);
                return;
            }
            let found = false;
            const filtered = allAnnonces.filter((annonce) =>
                (annonce.nomProduit && annonce.nomProduit.toLowerCase().includes(searchTerm)) ||
                (annonce.description && annonce.description.toLowerCase().includes(searchTerm))
            );
            filtered.forEach((annonce) => {
                const li = document.createElement("li");
                li.textContent = annonce.nomProduit + " - " + annonce.description;
                li.onclick = () => {
                    afficherAnnonces([annonce]);
                    suggestions.style.display = "none";
                    searchBar.value = li.textContent;
                };
                suggestions.appendChild(li);
                found = true;
            });
            suggestions.style.display = found ? "block" : "none";
            if (!found) {
                const li = document.createElement("li");
                li.textContent = "Aucun résultat trouvé";
                suggestions.appendChild(li);
            }
            afficherAnnonces(filtered);
        });
        // Autres boutons et interactions
        const btnConnexion = document.getElementById("connexionn");
        const btnVendre = document.getElementById("vendre");
        const btnAvis = document.getElementById("avis");
        const btnJourNuit = document.getElementById("temps");
        const conn = document.getElementById("connexion");
        const fournitureMenu = document.getElementById("fourniture");
        const avisZone = document.getElementById("avise");
        const body = document.getElementById("bod");

        btnConnexion.addEventListener("click", () => {
            conn.style.display = "block";
            fournitureMenu.style.display = "none";
            btnVendre.style.display = "none";
            avisZone.style.display = "none";
            document.getElementById("question").style.display = "none";
        });

        btnVendre.addEventListener("click", () => {
            formulaire.style.display = "block";
            document.getElementById("conteneurProfils").style.display = "block";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "none";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
        });

        btnAvis.addEventListener("click", () => {
            avisZone.style.display = "block";
            formulaire.style.display = "none";
            document.getElementById("conteneurProfils").style.display = "block";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "block";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
        });

        btnJourNuit.addEventListener("click", () => {
            if (body.style.backgroundColor === "black") {
                body.style.backgroundColor = "white";
                btnJourNuit.innerText = "🌞";
            } else {
                body.style.backgroundColor = "black";
                btnJourNuit.innerText = "🌑";
            }
        });

        document.getElementById("livre").addEventListener("click", () => {
            document.getElementById("produit").style.display = "block";
        });

        document.getElementById("produit").addEventListener("click", () => {
            document.getElementById("livre").style.display = "block";
        });

        document.getElementById("trois").addEventListener("click", () => {
            fournitureMenu.style.display = "block";
            formulaire.style.display = "none";
            document.getElementById("conteneurProfils").style.display = "block";
            document.getElementById("fourniture").style.display = "block";
            document.getElementById("avise").style.display = "none";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
        });

        // Système d'étoiles pour les avis
        window.rate = function (n) {
            const stars = document.querySelectorAll('.star');
            stars.forEach((star, index) => {
                star.classList.toggle('active', index < n);
            });
        };
        //avis
        async function afficheravis(avisList) {
            const container = document.getElementById("conteneuravis");
            container.innerHTML = "";
            if (!avisList || avisList.length === 0) {
                container.innerHTML = "<p>Aucun avis trouvé.</p>";
                container.style.display = "block";
                return;
            }
            avisList.forEach(async (avis) => {
                const bloc = document.createElement("div");
                bloc.className = "conteneuravis";
                bloc.innerHTML = `<p><strong>Note: ${avis.rating} étoiles<br>
                    Commentaire: ${avis.comment}</strong></p>`;
                container.appendChild(bloc);
            });
        }

        // --- Fonction pour afficher les annonces ---
        function escapeHTML(str) {
            if (!str) return "";
            return str.replace(/&/g, "&amp;")
                .replace(/</g, "&lt;")
                .replace(/>/g, "&gt;")
                .replace(/"/g, "&quot;")
                .replace(/'/g, "&#039;");
        }
        async function afficherAnnonces(annonces) {
            const container = conteneurProfils;
            container.innerHTML = "";

            if (!annonces || annonces.length === 0) {
                container.innerHTML = `
                    <div class="container">
                        <div style="text-align: center; padding: 3rem; color: var(--text-secondary);">
                            <h3>Aucune annonce trouvée</h3>
                            <p>Soyez le premier à publier une annonce !</p>
                        </div>
                    </div>`;
                container.style.display = "block";
                return;
            }

            const annoncesHTML = annonces.map(async (annonce) => {
                // Bloque le bouton si plus de 2 achats
                let achatBloque = false;
                if (utilisateurConnecte()) {
                    const stats = await getUserStats(auth.currentUser.email);
                    if (stats.achats >= 2) {
                        achatBloque = true;
                        alert("Vous avez atteint la limite de vos achats cliquez sur payer pour continuer(200 fcfa) ");
                        document.getElementById("payer").style.display = "block";

                    }
                }

                return `
                    <div class="annonce-card">
                        ${annonce.imageUrl ? `<img src="${escapeHTML(annonce.imageUrl)}" alt="${escapeHTML(annonce.nomProduit)}" class="annonce-image" />` : ''}
                        <div class="annonce-content">
                            <h3 class="annonce-title">${escapeHTML(annonce.nomProduit) || ""}</h3>
                            <div class="annonce-price">${escapeHTML(annonce.prix ? annonce.prix + ' FCFA' : '')}</div>
                            
                            <div class="annonce-details">
                                <div class="annonce-detail">
                                    <strong>Classe:</strong> ${escapeHTML(annonce.classe) || ''}
                                </div>
                                <div class="annonce-detail">
                                    <strong>Lieu:</strong> ${escapeHTML(annonce.lieu) || ''}
                                </div>
                                <div class="annonce-detail">
                                    <strong>Vendeur:</strong> ${escapeHTML(annonce.auteur) || ''}
                                </div>
                            </div>
                            
                            <p class="annonce-description">${escapeHTML(annonce.description)}</p>
                            
                            <div class="annonce-actions">
                                <button class="btn btn-primary" onclick="postuler('${annonce.id}', '${annonce.auteur}')" ${achatBloque ? 'disabled' : ''}>
                                    💬 Contacter
                                </button>
                                <button class="btn btn-success" id="payer" style="display:none;" onclick="startPayment(${annonce.prix}, async (success) => { if (success) { await incrementUserStat(auth.currentUser.email, 'achats'); alert('Paiement réussi !'); afficherAnnonces(allAnnonces); } })" ${achatBloque ? 'disabled' : ''}>
                                    💳 Payer
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            });

            const annoncesContent = await Promise.all(annoncesHTML);

            container.innerHTML = `
                <div class="container">
                    <div class="annonces-grid">
                        ${annoncesContent.join('')}
                    </div>
                </div>`;
            container.style.display = "block";
        }
        //FONCTION POUR LE PAYEMENT
        async function startPayment(amount, callback) {
            CinetPay.setConfig({
                apikey: '61737472068756e2b167aa8.58285306',
                site_id: '105901967',
                notify_url: '',
                mode: 'PRODUCTION'
            });
            let transaction_id = 'TXN_' + Math.floor(Math.random() * 1000000000);
            CinetPay.getCheckout({
                transaction_id: transaction_id,
                amount: 200,
                currency: 'XAF',
                channels: 'ALL',
                description: 'Paiement fournitures scolaires'
            });
            CinetPay.waitResponse(async function (data) {
                if (data.status === "REFUSED") {
                    alert("Paiement échoué ❌");
                    if (callback) callback(false);
                } else if (data.status === "ACCEPTED") {
                    alert("Paiement réussi ✅");
                    if (callback) callback(true);
                }
            });
            CinetPay.onError(function (data) {
                console.error(data);
                alert("Erreur lors du paiement ⚠");
                if (callback) callback(false);
            });
        }
        // --- Fonction pour charger toutes les annonces au démarrage ---
        async function chargerToutesLesAnnonces() {
            try {
                const querySnapshot = await getDocs(collection(db, "annonces"));
                const annonces = [];
                querySnapshot.forEach((doc) => {
                    annonces.push({ id: doc.id, ...doc.data() }); // Ajoute l'id Firestore à chaque annonce
                });
                allAnnonces = annonces;
                afficherAnnonces(allAnnonces);
            } catch (error) {
                conteneurProfils.innerHTML = "<p>Erreur de chargement des annonces.</p>";
                conteneurProfils.style.display = "block";
            }
        }

        // --- Fonction pour filtrer les annonces par catégorie ---
        window.afficherFournituresCategorie = async function (categorie) {
            conteneurProfils.innerHTML = "<p>Chargement...</p>";
            conteneurProfils.style.display = "block";
            fournitureMenu.style.display = "none";
            avisZone.style.display = "block";
            formulaire.style.display = "none";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "block";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
            try {
                const filtered = allAnnonces.filter((data) => data.categorie === categorie);
                afficherAnnonces(filtered);
            } catch (error) {
                conteneurProfils.innerHTML = "<p>Erreur de chargement.</p>";
            }
        };

        // --- Chargement initial des annonces ---
        chargerToutesLesAnnonces();

        // --- Fonction d'upload Base64 (Gratuit et permanent) ---
        async function uploadImage(file) {
            // Validation de la taille (1MB max pour Firestore)
            if (file.size > 1024 * 1024) {
                throw new Error("L'image doit faire moins de 1MB");
            }

            // Conversion en Base64
            return await fileToBase64(file);
        }

        function fileToBase64(file) {
            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.readAsDataURL(file);
                reader.onload = () => resolve(reader.result);
                reader.onerror = error => reject(error);
            });
        }

        // --- Messagerie adaptée à l'utilisateur connecté ---
        window.envoyerMessage = async function () {
            const input = document.getElementById('messageInput');
            const message = input.value.trim();
            if (!message)
                alert("Veuillez entrez un message");
            return;
            if (!utilisateurConnecte()) {
                alert("Vous devez être connecté pour envoyer un message.");
                return;
            }
            if (!idAnnonceEnCours || !idConversation) {
                alert("Aucune conversation active.");
                return;
            }

            try {
                const msgRef = collection(db, "annonces", idAnnonceEnCours, "conversations", idConversation, "messages");
                await addDoc(msgRef, {
                    auteur: auth.currentUser.email,
                    text: message,
                    timestamp: Date.now()
                });

                input.value = '';
            } catch (error) {
                console.error("Erreur envoi message:", error);
                alert("Erreur lors de l'envoi du message.");
            }
        }

        // Cette fonction n'est plus nécessaire car les messages sont chargés dans ouvrirChat
        window.chargerMessages = function () {
            console.log("chargerMessages appelé mais non utilisé");
        }

        // --- Compteurs d'achats/ventes utilisateur ---
        async function getUserStats(email) {
            const userRef = doc(db, "users", email);
            const snap = await getDoc(userRef);
            if (snap.exists()) {
                return snap.data();
            } else {
                return { ventes: 0, achats: 0 };
            }
        }
        async function incrementUserStat(email, champ) {
            const userRef = doc(db, "users", email);
            await setDoc(userRef, { ventes: 0, achats: 0 }, { merge: true });
            await updateDoc(userRef, { [champ]: increment(1) });
        }

        // --- Bloque le bouton publier si plus de 2 ventes ---
        async function checkBlockPublier() {
            if (!utilisateurConnecte())
                alert("Vous deverez etre connecter");
            return;
            const stats = await getUserStats(auth.currentUser.email);
            if (stats.ventes >= 2) {
                confirmerBtn.disabled = true;
                confirmerBtn.title = "Vous avez atteint la limite de 2 ventes.";
                alert("Vous avez atteint la limite de 2 ventes.payer 200fcfa pour continuer")
                document.getElementById("payer").style.display = "block";
            } else {
                confirmerBtn.disabled = false;
                confirmerBtn.title = "";
            }
        }
        onAuthStateChanged(auth, checkBlockPublier);

        // Fonction pour ouvrir le chat privé pour une annonce
        async function ouvrirChat(idAnnonce, emailAcheteur, emailVendeur) {
            console.log('ouvrirChat appelé avec:', idAnnonce, emailAcheteur, emailVendeur);

            if (!idAnnonce || !emailAcheteur || !emailVendeur) {
                alert("Erreur : paramètres du chat manquants !");
                return;
            }

            idAnnonceEnCours = idAnnonce;
            idConversation = [emailAcheteur, emailVendeur].sort().join("_");

            // Affiche le chat et masque les autres sections
            conteneurProfils.style.display = "none";
            fournitureMenu.style.display = "none";
            avisZone.style.display = "none";
            formulaire.style.display = "none";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "none";
            document.getElementById("chat").style.display = "block";
            document.getElementById("connexion").style.display = "none";
            document.getElementById("conteneurProfils").style.display = "block";
            document.getElementById("formulaire").style.display = "none";
            document.getElementById("chat").style.display = "block";
            document.getElementById("messages").innerHTML = "";

            // Affiche le titre du chat
            document.getElementById("chatTitre").innerText = `Chat entre ${emailAcheteur} et ${emailVendeur}`;

            try {
                // Récupère les messages de la conversation
                const messagesRef = collection(db, "annonces", idAnnonce, "conversations", idConversation, "messages");
                const q = query(messagesRef, orderBy("timestamp", "asc"));

                onSnapshot(q, (snapshot) => {
                    const messagesDiv = document.getElementById("messages");
                    messagesDiv.innerHTML = "";
                    snapshot.forEach(docu => {
                        const msg = docu.data();
                        const div = document.createElement("div");
                        const isCurrentUser = msg.auteur === auth.currentUser.email;

                        div.className = `message ${isCurrentUser ? 'message-sent' : 'message-received'}`;
                        div.innerHTML = `
                            <div class="message-author">${isCurrentUser ? 'Moi' : msg.auteur}</div>
                            <div>${msg.text}</div>
                        `;
                        messagesDiv.appendChild(div);
                    });
                    messagesDiv.scrollTop = messagesDiv.scrollHeight;
                });
            } catch (error) {
                console.error("Erreur ouverture chat:", error);
                alert("Erreur lors de l'ouverture du chat.");
            }
        }

        // Fonction pour envoyer un message dans le chat
        async function envoyerMessage() {
            const messageInput = document.getElementById("messageInput");
            const texte = messageInput.value.trim();

            if (!texte) {
                alert('Veuillez remplir le champ');
                return;
            }

            if (!idAnnonceEnCours || !idConversation) {
                alert("Aucune conversation sélectionnée.");
                return;
            }

            if (!utilisateurConnecte()) {
                alert("Vous devez être connecté pour envoyer un message.");
                return;
            }

            try {
                const email = auth.currentUser.email;
                const msgRef = collection(db, "annonces", idAnnonceEnCours, "conversations", idConversation, "messages");
                await addDoc(msgRef, {
                    auteur: email,
                    text: texte,
                    timestamp: Date.now()
                });

                messageInput.value = "";
            } catch (error) {
                console.error("Erreur envoi message:", error);
                alert("Erreur lors de l'envoi du message.");
            }
        }

        // conclure la transaction
        async function conclureJob() {
            if (!idAnnonceEnCours) {
                alert("Aucune annonce active.");
                return;
            }

            if (!utilisateurConnecte()) {
                alert("Vous devez être connecté pour conclure.");
                return;
            }

            try {
                const annonceRef = doc(db, "annonces", idAnnonceEnCours);
                const snap = await getDoc(annonceRef);
                if (!snap.exists()) {
                    alert("Annonce introuvable.");
                    return;
                }

                const data = snap.data();
                let c = data.conclusionUsers || [];
                if (!c.includes(auth.currentUser.email)) c.push(auth.currentUser.email);
                await updateDoc(annonceRef, { conclusionUsers: c });
                if (c.length >= 2) await updateDoc(annonceRef, { conclu: true });

                alert("Conclusion enregistrée");
                document.getElementById("chat").style.display = "none";
                document.getElementById("conteneurProfils").style.display = "block";
            } catch (error) {
                console.error("Erreur conclusion:", error);
                alert("Erreur lors de la conclusion.");
            }
        }

        //  pour postuler 
        window.postuler = async function (idAnnonce, emailVendeur) {
            document.getElementById("chat").style.display = "block";
            console.log('postuler appelé avec:', idAnnonce, emailVendeur);

            if (!idAnnonce) {
                alert("Erreur : id de l'annonce manquant !");
                return;
            }
            if (!emailVendeur) {
                alert("Erreur : email du vendeur manquant !");
                return;
            }

            const user = auth.currentUser;
            if (!user) {
                alert("Connecte-toi d'abord");
                return;
            }

            const emailAcheteur = user.email;

            try {
                // Crée la conversation si elle n'existe pas
                const convId = [emailAcheteur, emailVendeur].sort().join("_");
                const msgRef = collection(db, "annonces", idAnnonce, "conversations", convId, "messages");
                const messagesSnap = await getDocs(msgRef);

                if (messagesSnap.empty) {
                    await addDoc(msgRef, {
                        auteur: emailAcheteur,
                        text: "Bonjour, je suis intéressé par cette annonce.",
                        timestamp: Date.now()
                    });
                }

                ouvrirChat(idAnnonce, emailAcheteur, emailVendeur);
            } catch (error) {
                console.error("Erreur postuler:", error);
                alert("Erreur lors de la création du chat.");
            }
        }

        // Fermer le chat
        document.getElementById("fermerChat").addEventListener("click", function () {
            document.getElementById("conteneurProfils").style.display = "block";
            document.getElementById("chat").style.display = "none";
            conn.style.display = "block";
            fournitureMenu.style.display = "none";
            btnVendre.style.display = "none";
            avisZone.style.display = "none";
            document.getElementById("question").style.display = "none";
        });
        async function lireConversations() {
            const container = document.getElementById("conteneurProfils");
            container.innerHTML = "<h3 class='section-title'>💬 Mes Conversations</h3>";
            container.style.display = "block";
            document.getElementById("fourniture").style.display = "none";
            document.getElementById("avise").style.display = "none";
            document.getElementById("chat").style.display = "none";
            document.getElementById("connexion").style.display = "none";
            document.getElementById("formulaire").style.display = "none";

            const user = auth.currentUser;
            if (!user) {
                alert("Connecte-toi d'abord");
                return;
            }
            const email = user.email;

            // Récupère toutes les annonces où l'utilisateur est vendeur ou a déjà postulé (a discuté)
            const annoncesSnap = await getDocs(collection(db, "annonces"));
            let conversations = [];

            annoncesSnap.forEach(docu => {
                const annonce = { id: docu.id, ...docu.data() };
                // Conversation si je suis vendeur
                if (annonce.auteur === email) {
                    conversations.push({ annonce, role: "vendeur" });
                }
            });

            // Ajoute les conversations où je suis acheteur
            for (const docu of annoncesSnap.docs) {
                const annonce = { id: docu.id, ...docu.data() };
                const convsSnap = await getDocs(collection(db, "annonces", annonce.id, "conversations"));
                convsSnap.forEach(convDoc => {
                    const convId = convDoc.id;
                    if (convId.includes(email) && annonce.auteur !== email) {
                        conversations.push({ annonce, role: "acheteur", convId });
                    }
                });
            }

            if (conversations.length === 0) {
                container.innerHTML += `<div style="text-align:center; color:var(--text-secondary); margin-top:2rem;">Aucune conversation trouvée.</div>`;
                return;
            }

            // Affichage des conversations
            conversations.forEach(({ annonce, role, convId }) => {
                const card = document.createElement("div");
                card.className = "annonce-card";
                card.innerHTML = `
            ${annonce.imageUrl ? `<img src="${annonce.imageUrl}" alt="${annonce.nomProduit}" class="annonce-image" />` : ""}
            <div class="annonce-content">
                <h3 class="annonce-title">${annonce.nomProduit || ""}</h3>
                <div class="annonce-price">${annonce.prix ? annonce.prix + " FCFA" : ""}</div>
                <div class="annonce-details">
                    <div class="annonce-detail"><strong>Classe:</strong> ${annonce.classe || ""}</div>
                    <div class="annonce-detail"><strong>Lieu:</strong> ${annonce.lieu || ""}</div>
                    <div class="annonce-detail"><strong>Vendeur:</strong> ${annonce.auteur || ""}</div>
                </div>
                <p class="annonce-description">${annonce.description || ""}</p>
                <div class="annonce-actions">
                    <button class="btn btn-primary">💬 Ouvrir le chat</button>
                </div>
            </div>
        `;
                card.querySelector(".btn-primary").addEventListener("click", () => {
                    // On déduit l'autre participant
                    let emailVendeur = annonce.auteur;
                    let emailAcheteur = (role === "vendeur")
                        ? convId ? convId.replace(emailVendeur, "").replace("_", "") : null
                        : email;
                    if (role === "vendeur" && !convId) {
                        // Si vendeur, on doit choisir un acheteur (on peut lister les conversations)
                        getDocs(collection(db, "annonces", annonce.id, "conversations")).then(convsSnap => {
                            if (convsSnap.empty) {
                                alert("Aucun acheteur pour cette annonce.");
                                return;
                            }
                            // On propose de choisir un acheteur
                            let acheteurs = [];
                            convsSnap.forEach(convDoc => {
                                const emails = convDoc.id.split("_");
                                const acheteur = emails.find(e => e !== emailVendeur);
                                if (acheteur) acheteurs.push(acheteur);
                            });
                            const choix = prompt("Avec quel acheteur discuter ?\n" + acheteurs.join("\n"));
                            if (choix && acheteurs.includes(choix)) {
                                ouvrirChat(annonce.id, choix, emailVendeur);
                            }
                        });
                    } else {
                        ouvrirChat(annonce.id, emailAcheteur, emailVendeur);
                    }
                });
                container.appendChild(card);
            });
        }
        setTimeout(() => {
            showNotification('🎉 Bienvenue sur MBOA Librairie !', 'success');
        }, 3000);
        window.lireConversations = lireConversations;

        window.addEventListener("DOMContentLoaded", function () {
            // Fonction utilitaire pour afficher une seule section à la fois
            function afficherSection(idSection) {
                const sections = [
                    "conteneurProfils",
                    "fourniture",
                    "avise",
                    "chat",
                    "connexion",
                    "formulaire"
                ];
                sections.forEach(id => {
                    const el = document.getElementById(id);
                    if (el) el.style.display = "none";
                });
                const toShow = document.getElementById(idSection);
                if (toShow) toShow.style.display = "block";
            }

            // Handler du bouton Accueil
            const accueilBtn = document.getElementById("accueilBtn");
            if (accueilBtn) {
                accueilBtn.addEventListener("click", () => {
                    afficherSection("conteneurProfils");
                    if (typeof afficherAnnonces === "function") afficherAnnonces(allAnnonces);
                });
            }

            // Handler du bouton Vendre
            const btnVendre = document.getElementById("vendre");
            if (btnVendre) {
                btnVendre.addEventListener("click", () => {
                    afficherSection("formulaire");
                });
            }

            // Handler du bouton Avis
            const btnAvis = document.getElementById("avis");
            if (btnAvis) {
                btnAvis.addEventListener("click", () => {
                    afficherSection("avise");
                });
            }

            // Handler du bouton Menu
            const menuBtn = document.getElementById("trois");
            if (menuBtn) {
                menuBtn.addEventListener("click", () => {
                    afficherSection("fourniture");
                });
            }

            // Handler du bouton Connexion
            const btnConnexion = document.getElementById("connexionn");
            if (btnConnexion) {
                btnConnexion.addEventListener("click", () => {
                    afficherSection("connexion");
                    btnVendre.style.display = "none";
                    document.getElementById("question").style.display = "none";
                });
            }

            // Handler du bouton Jour/Nuit
            const btnJourNuit = document.getElementById("temps");
            const body = document.getElementById("bod");
            if (btnJourNuit) {
                btnJourNuit.addEventListener("click", () => {
                    if (body.style.backgroundColor === "black") {
                        body.style.backgroundColor = "white";
                        btnJourNuit.innerText = "☀️Jour";
                    } else {
                        body.style.backgroundColor = "black";
                        btnJourNuit.innerText = "Nuit";
                    }
                    // NE PAS masquer conteneurProfils ici !
                });
            }

            // Handler du bouton Fermer Chat
            const fermerChatBtn = document.getElementById("fermerChat");
            if (fermerChatBtn) {
                fermerChatBtn.addEventListener("click", function () {
                    afficherSection("conteneurProfils");
                    if (typeof afficherAnnonces === "function") afficherAnnonces(allAnnonces);
                });
            }

            // Handler pour la recherche dynamique (affiche toujours la liste)
            const searchBar = document.getElementById("searchBar");
            if (searchBar) {
                searchBar.addEventListener("input", function () {
                    afficherSection("conteneurProfils");
                });
            }

            // Corrige ouvrirChat pour utiliser afficherSection
            window.ouvrirChat = async function ouvrirChat(idAnnonce, emailAcheteur, emailVendeur) {
                idAnnonceEnCours = idAnnonce;
                idConversation = [emailAcheteur, emailVendeur].sort().join("_");
                afficherSection("chat");
                document.getElementById("messages").innerHTML = "";
                document.getElementById("chatTitre").innerText = `Chat entre ${emailAcheteur} et ${emailVendeur}`;
                try {
                    const messagesRef = collection(db, "annonces", idAnnonce, "conversations", idConversation, "messages");
                    const q = query(messagesRef, orderBy("timestamp", "asc"));
                    onSnapshot(q, (snapshot) => {
                        const messagesDiv = document.getElementById("messages");
                        messagesDiv.innerHTML = "";
                        snapshot.forEach(docu => {
                            const msg = docu.data();
                            const div = document.createElement("div");
                            const isCurrentUser = msg.auteur === auth.currentUser.email;
                            div.className = `message ${isCurrentUser ? 'message-sent' : 'message-received'}`;
                            div.innerHTML = `
                                <div class="message-author">${isCurrentUser ? 'Moi' : msg.auteur}</div>
                                <div>${msg.text}</div>
                            `;
                            messagesDiv.appendChild(div);
                        });
                        messagesDiv.scrollTop = messagesDiv.scrollHeight;
                    });
                } catch (error) {
                    alert("Erreur lors de l'ouverture du chat.");
                }
            }

            // Corrige postuler pour ouvrir le chat proprement
            window.postuler = async function (idAnnonce, emailVendeur) {
                const user = auth.currentUser;
                if (!user) {
                    alert("Connecte-toi d'abord");
                    return;
                }
                const emailAcheteur = user.email;
                try {
                    const convId = [emailAcheteur, emailVendeur].sort().join("_");
                    const msgRef = collection(db, "annonces", idAnnonce, "conversations", convId, "messages");
                    const messagesSnap = await getDocs(msgRef);
                    if (messagesSnap.empty) {
                        await addDoc(msgRef, {
                            auteur: emailAcheteur,
                            text: "Bonjour, je suis intéressé par cette annonce.",
                            timestamp: Date.now()
                        });
                    }
                    ouvrirChat(idAnnonce, emailAcheteur, emailVendeur);
                } catch (error) {
                    alert("Erreur lors de la création du chat.");
                }
            }

            // Rends lireConversations global
            window.lireConversations = lireConversations;
        });
    </script>

</body>

</html>
