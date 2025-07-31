<!DOCTYPE html>
<html lang="fr">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Saveurs du Cameroun - Restaurant Authentique</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary-color: #2c5530;
            --secondary-color: #d4af37;
            --accent-color: #8b4513;
            --text-light: #ffffff;
            --text-dark: #333333;
            --background-light: #f8f9fa;
            --background-dark: #1a1a1a;
            --success-color: #28a745;
            --warning-color: #ffc107;
            --danger-color: #dc3545;
            --info-color: #17a2b8;
            --border-color: #dee2e6;
            --shadow-light: 0 2px 15px rgba(0, 0, 0, 0.1);
            --shadow-medium: 0 4px 25px rgba(0, 0, 0, 0.15);
            --shadow-heavy: 0 8px 40px rgba(0, 0, 0, 0.2);
            --transition-fast: 0.3s ease;
            --transition-medium: 0.5s ease;
            --transition-slow: 0.8s ease;
            --border-radius-small: 8px;
            --border-radius-medium: 12px;
            --border-radius-large: 20px;
            --gradient-primary: linear-gradient(135deg, var(--primary-color) 0%, #1e3a24 100%);
            --gradient-secondary: linear-gradient(135deg, var(--secondary-color) 0%, #b8941f 100%);
            --gradient-overlay: linear-gradient(45deg, rgba(44, 85, 48, 0.9) 0%, rgba(139, 69, 19, 0.8) 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-dark);
            overflow-x: hidden;
        }

        /* Loading Screen */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--gradient-primary);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            transition: opacity var(--transition-slow);
        }

        .loading-screen.hidden {
            opacity: 0;
            pointer-events: none;
        }

        .loader {
            width: 80px;
            height: 80px;
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top: 4px solid var(--secondary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-bottom: 20px;
        }

        .loading-text {
            color: var(--text-light);
            font-size: 1.2em;
            font-weight: 600;
            letter-spacing: 2px;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }

        @keyframes pulse {

            0%,
            100% {
                opacity: 1;
            }

            50% {
                opacity: 0.6;
            }
        }

        /* Navigation */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(44, 85, 48, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            transition: all var(--transition-fast);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .navbar.scrolled {
            background: rgba(44, 85, 48, 0.98);
            box-shadow: var(--shadow-medium);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--text-light);
            text-decoration: none;
            transition: transform var(--transition-fast);
        }

        .logo:hover {
            transform: scale(1.05);
        }

        .logo i {
            margin-right: 10px;
            color: var(--secondary-color);
            animation: rotate 4s linear infinite;
        }

        @keyframes rotate {
            0% {
                transform: rotate(0deg);
            }

            25% {
                transform: rotate(5deg);
            }

            50% {
                transform: rotate(0deg);
            }

            75% {
                transform: rotate(-5deg);
            }

            100% {
                transform: rotate(0deg);
            }
        }

        .nav-links {
            display: flex;
            list-style: none;
            align-items: center;
            gap: 2rem;
        }

        .nav-links a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 500;
            position: relative;
            transition: color var(--transition-fast);
            padding: 0.5rem 0;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--secondary-color);
            transition: width var(--transition-fast);
        }

        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }

        .nav-links a:hover,
        .nav-links a.active {
            color: var(--secondary-color);
        }

        .reservation-btn {
            background: var(--gradient-secondary);
            color: var(--text-dark) !important;
            padding: 0.7rem 1.5rem;
            border-radius: var(--border-radius-large);
            font-weight: 600;
            transition: all var(--transition-fast);
            box-shadow: var(--shadow-light);
        }

        .reservation-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--text-light);
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(var(--gradient-overlay)), url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 800"><rect fill="%23d4af37" width="1200" height="800"/><rect fill="%232c5530" x="0" y="0" width="400" height="800"/><rect fill="%238b4513" x="800" y="0" width="400" height="800"/><circle fill="%23ffffff" cx="200" cy="200" r="50" opacity="0.1"/><circle fill="%23ffffff" cx="1000" cy="600" r="80" opacity="0.1"/><polygon fill="%23ffffff" points="600,100 650,200 550,200" opacity="0.1"/></svg>');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" patternUnits="userSpaceOnUse" width="100" height="100"><circle fill="%23ffffff" cx="50" cy="50" r="1" opacity="0.05"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
            animation: grain 8s steps(8) infinite;
        }

        @keyframes grain {

            0%,
            100% {
                transform: translate(0, 0);
            }

            10% {
                transform: translate(-5%, -10%);
            }

            30% {
                transform: translate(3%, -15%);
            }

            50% {
                transform: translate(12%, 9%);
            }

            70% {
                transform: translate(9%, 4%);
            }

            90% {
                transform: translate(-1%, 7%);
            }
        }

        .hero-content {
            z-index: 2;
            color: var(--text-light);
            max-width: 800px;
            padding: 2rem;
            animation: fadeInUp 1.2s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 4.5rem);
            margin-bottom: 1rem;
            font-weight: 700;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
            line-height: 1.2;
        }

        .hero-subtitle {
            font-size: clamp(1.2rem, 3vw, 1.6rem);
            margin-bottom: 2rem;
            opacity: 0.9;
            font-weight: 300;
            letter-spacing: 1px;
        }

        .hero-description {
            font-size: 1.1rem;
            margin-bottom: 3rem;
            opacity: 0.8;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-buttons {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 1rem 2rem;
            border: none;
            border-radius: var(--border-radius-large);
            font-size: 1rem;
            font-weight: 600;
            text-decoration: none;
            cursor: pointer;
            transition: all var(--transition-fast);
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.6s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn-primary {
            background: var(--gradient-secondary);
            color: var(--text-dark);
            box-shadow: var(--shadow-medium);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-light);
            border: 2px solid var(--text-light);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-heavy);
        }

        .btn-secondary:hover {
            background: var(--text-light);
            color: var(--text-dark);
        }

        /* Floating Elements */
        .floating-elements {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .floating-element {
            position: absolute;
            opacity: 0.1;
            animation: float 10s ease-in-out infinite;
        }

        .floating-element:nth-child(1) {
            top: 20%;
            left: 10%;
            animation-delay: 0s;
            font-size: 3rem;
        }

        .floating-element:nth-child(2) {
            top: 60%;
            right: 15%;
            animation-delay: 2s;
            font-size: 2.5rem;
        }

        .floating-element:nth-child(3) {
            bottom: 20%;
            left: 20%;
            animation-delay: 4s;
            font-size: 2rem;
        }

        @keyframes float {

            0%,
            100% {
                transform: translateY(0px) rotate(0deg);
            }

            50% {
                transform: translateY(-20px) rotate(5deg);
            }
        }

        /* About Section */
        .about {
            padding: 8rem 0;
            background: var(--background-light);
            position: relative;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-title {
            font-size: clamp(2rem, 4vw, 3rem);
            color: var(--primary-color);
            margin-bottom: 1rem;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: var(--gradient-secondary);
            border-radius: 2px;
        }

        .section-subtitle {
            font-size: 1.2rem;
            color: var(--text-dark);
            opacity: 0.8;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.8;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
            color: var(--text-dark);
        }

        .about-text p {
            margin-bottom: 1.5rem;
        }

        .about-stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat-card {
            text-align: center;
            padding: 2rem;
            background: white;
            border-radius: var(--border-radius-medium);
            box-shadow: var(--shadow-light);
            transition: transform var(--transition-fast);
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-medium);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: var(--text-dark);
            opacity: 0.8;
            font-weight: 500;
        }

        .about-image {
            position: relative;
            border-radius: var(--border-radius-large);
            overflow: hidden;
            box-shadow: var(--shadow-medium);
        }

        .about-image img {
            width: 100%;
            height: 400px;
            object-fit: cover;
            transition: transform var(--transition-slow);
        }

        .about-image:hover img {
            transform: scale(1.05);
        }

        /* Menu Section */
        .menu {
            padding: 8rem 0;
            background: white;
        }

        .menu-categories {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin-bottom: 3rem;
        }

        .category-btn {
            padding: 0.8rem 1.5rem;
            border: 2px solid var(--primary-color);
            background: transparent;
            color: var(--primary-color);
            border-radius: var(--border-radius-large);
            font-weight: 600;
            cursor: pointer;
            transition: all var(--transition-fast);
        }

        .category-btn.active,
        .category-btn:hover {
            background: var(--primary-color);
            color: var(--text-light);
            transform: translateY(-2px);
            box-shadow: var(--shadow-light);
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .menu-item {
            background: white;
            border-radius: var(--border-radius-medium);
            overflow: hidden;
            box-shadow: var(--shadow-light);
            transition: all var(--transition-fast);
            position: relative;
            opacity: 0;
            transform: translateY(30px);
        }

        .menu-item.show {
            opacity: 1;
            transform: translateY(0);
        }

        .menu-item:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: var(--shadow-medium);
        }

        .menu-item-image {
            height: 200px;
            background: var(--gradient-secondary);
            position: relative;
            overflow: hidden;
        }

        .menu-item-image::before {
            content: '🍽️';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3rem;
            opacity: 0.3;
        }

        .price-tag {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: var(--gradient-secondary);
            color: var(--text-dark);
            padding: 0.5rem 1rem;
            border-radius: var(--border-radius-large);
            font-weight: bold;
            box-shadow: var(--shadow-light);
        }

        .menu-item-content {
            padding: 1.5rem;
        }

        .menu-item-title {
            font-size: 1.3rem;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
            font-weight: 700;
        }

        .menu-item-description {
            color: var(--text-dark);
            opacity: 0.8;
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .menu-item-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .spice-level {
            display: flex;
            gap: 0.2rem;
        }

        .spice-icon {
            color: var(--danger-color);
            font-size: 0.9rem;
        }

        .add-to-cart {
            background: var(--gradient-primary);
            color: var(--text-light);
            border: none;
            padding: 0.6rem 1.2rem;
            border-radius: var(--border-radius-small);
            cursor: pointer;
            font-weight: 600;
            transition: all var(--transition-fast);
        }

        .add-to-cart:hover {
            transform: scale(1.05);
            box-shadow: var(--shadow-light);
        }

        /* Reservation Section */
        .reservation {
            padding: 8rem 0;
            background: var(--gradient-primary);
            color: var(--text-light);
        }

        .reservation-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .reservation-info h2 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
        }

        .reservation-info p {
            font-size: 1.1rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            line-height: 1.8;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            font-size: 1.1rem;
        }

        .contact-item i {
            color: var(--secondary-color);
            width: 20px;
        }

        .reservation-form {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 3rem;
            border-radius: var(--border-radius-large);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--text-light);
        }

        .form-control {
            width: 100%;
            padding: 1rem;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: var(--border-radius-small);
            background: rgba(255, 255, 255, 0.1);
            color: var(--text-light);
            font-size: 1rem;
            transition: all var(--transition-fast);
        }

        .form-control::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--secondary-color);
            background: rgba(255, 255, 255, 0.2);
            box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.3);
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }

        textarea.form-control {
            resize: vertical;
            min-height: 120px;
        }

        .submit-btn {
            width: 100%;
            background: var(--gradient-secondary);
            color: var(--text-dark);
            border: none;
            padding: 1.2rem;
            border-radius: var(--border-radius-small);
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all var(--transition-fast);
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }

        .submit-btn:disabled {
            opacity: 0.7;
            cursor: not-allowed;
            transform: none;
        }

        /* Gallery Section */
        .gallery {
            padding: 8rem 0;
            background: var(--background-light);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
            margin-top: 3rem;
        }

        .gallery-item {
            position: relative;
            border-radius: var(--border-radius-medium);
            overflow: hidden;
            aspect-ratio: 1;
            background: var(--gradient-secondary);
            cursor: pointer;
            transition: transform var(--transition-fast);
        }

        .gallery-item:hover {
            transform: scale(1.05);
        }

        .gallery-item::before {
            content: '📸';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3rem;
            opacity: 0.3;
            z-index: 1;
        }

        .gallery-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(44, 85, 48, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity var(--transition-fast);
        }

        .gallery-item:hover .gallery-overlay {
            opacity: 1;
        }

        .gallery-overlay i {
            color: var(--text-light);
            font-size: 2rem;
        }

        /* Reviews Section */
        .reviews {
            padding: 8rem 0;
            background: white;
        }

        .reviews-slider {
            position: relative;
            max-width: 800px;
            margin: 3rem auto 0;
            overflow: hidden;
            border-radius: var(--border-radius-large);
        }

        .review-card {
            background: white;
            padding: 3rem;
            text-align: center;
            box-shadow: var(--shadow-medium);
            border-radius: var(--border-radius-large);
            position: relative;
        }

        .review-card::before {
            content: '"';
            position: absolute;
            top: 1rem;
            left: 2rem;
            font-size: 4rem;
            color: var(--secondary-color);
            opacity: 0.3;
            font-family: serif;
        }

        .review-text {
            font-size: 1.2rem;
            line-height: 1.8;
            margin-bottom: 2rem;
            color: var(--text-dark);
            font-style: italic;
        }

        .review-author {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1rem;
        }

        .review-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--gradient-secondary);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--text-dark);
        }

        .review-info h4 {
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .review-rating {
            color: var(--secondary-color);
            font-size: 1.2rem;
        }

        .review-nav {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 2rem;
        }

        .nav-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(44, 85, 48, 0.3);
            cursor: pointer;
            transition: background var(--transition-fast);
        }

        .nav-dot.active {
            background: var(--primary-color);
        }

        /* Footer */
        .footer {
            background: var(--background-dark);
            color: var(--text-light);
            padding: 4rem 0 2rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            margin-bottom: 3rem;
        }

        .footer-section h3 {
            color: var(--secondary-color);
            margin-bottom: 1.5rem;
            font-size: 1.3rem;
        }

        .footer-section p,
        .footer-section li {
            opacity: 0.8;
            line-height: 1.8;
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 0.5rem;
        }

        .footer-section a {
            color: var(--text-light);
            text-decoration: none;
            transition: color var(--transition-fast);
        }

        .footer-section a:hover {
            color: var(--secondary-color);
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background: var(--primary-color);
            color: var(--text-light);
            border-radius: 50%;
            text-decoration: none;
            transition: all var(--transition-fast);
        }

        .social-link:hover {
            background: var(--secondary-color);
            color: var(--text-dark);
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            opacity: 0.6;
        }

        /* Cart Sidebar */
        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -400px;
            width: 400px;
            height: 100%;
            background: white;
            box-shadow: var(--shadow-heavy);
            z-index: 1001;
            transition: right var(--transition-medium);
            display: flex;
            flex-direction: column;
        }

        .cart-sidebar.open {
            right: 0;
        }

        .cart-header {
            padding: 2rem;
            background: var(--gradient-primary);
            color: var(--text-light);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cart-title {
            font-size: 1.5rem;
            font-weight: bold;
        }

        .cart-close {
            background: none;
            border: none;
            color: var(--text-light);
            font-size: 1.5rem;
            cursor: pointer;
            padding: 0.5rem;
            border-radius: 50%;
            transition: background var(--transition-fast);
        }

        .cart-close:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        .cart-items {
            flex: 1;
            overflow-y: auto;
            padding: 1rem;
        }

        .cart-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            border-bottom: 1px solid var(--border-color);
            transition: background var(--transition-fast);
        }

        .cart-item:hover {
            background: var(--background-light);
        }

        .cart-item-image {
            width: 60px;
            height: 60px;
            background: var(--gradient-secondary);
            border-radius: var(--border-radius-small);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-name {
            font-weight: 600;
            color: var(--primary-color);
            margin-bottom: 0.25rem;
        }

        .cart-item-price {
            color: var(--secondary-color);
            font-weight: bold;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }

        .quantity-btn {
            width: 30px;
            height: 30px;
            border: none;
            background: var(--primary-color);
            color: var(--text-light);
            border-radius: 50%;
            cursor: pointer;
            font-weight: bold;
            transition: all var(--transition-fast);
        }

        .quantity-btn:hover {
            background: var(--secondary-color);
            color: var(--text-dark);
            transform: scale(1.1);
        }

        .quantity {
            font-weight: bold;
            min-width: 30px;
            text-align: center;
        }

        .cart-footer {
            padding: 2rem;
            border-top: 1px solid var(--border-color);
            background: var(--background-light);
        }

        .cart-total {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        .checkout-btn {
            width: 100%;
            background: var(--gradient-secondary);
            color: var(--text-dark);
            border: none;
            padding: 1rem;
            border-radius: var(--border-radius-small);
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all var(--transition-fast);
        }

        .checkout-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-medium);
        }

        /* Modal */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            opacity: 0;
            visibility: hidden;
            transition: all var(--transition-fast);
        }

        .modal.show {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background: white;
            padding: 3rem;
            border-radius: var(--border-radius-large);
            max-width: 500px;
            width: 90%;
            text-align: center;
            transform: scale(0.8);
            transition: transform var(--transition-fast);
        }

        .modal.show .modal-content {
            transform: scale(1);
        }

        .modal-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
        }

        .modal-title {
            font-size: 1.5rem;
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        .modal-text {
            color: var(--text-dark);
            margin-bottom: 2rem;
            line-height: 1.6;
        }

        .modal-btn {
            background: var(--gradient-primary);
            color: var(--text-light);
            border: none;
            padding: 1rem 2rem;
            border-radius: var(--border-radius-small);
            font-weight: bold;
            cursor: pointer;
            transition: all var(--transition-fast);
        }

        .modal-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-light);
        }

        /* Scroll to Top */
        .scroll-top {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            width: 50px;
            height: 50px;
            background: var(--gradient-secondary);
            color: var(--text-dark);
            border: none;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2rem;
            transition: all var(--transition-fast);
            opacity: 0;
            visibility: hidden;
            z-index: 1000;
        }

        .scroll-top.show {
            opacity: 1;
            visibility: visible;
        }

        .scroll-top:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-medium);
        }

        /* Animations */
        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }

            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }

            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }

            to {
                opacity: 1;
            }
        }

        .animate-on-scroll {
            opacity: 0;
            transition: all var(--transition-medium);
        }

        .animate-on-scroll.animated {
            opacity: 1;
        }

        .slide-left {
            transform: translateX(-50px);
        }

        .slide-left.animated {
            transform: translateX(0);
        }

        .slide-right {
            transform: translateX(50px);
        }

        .slide-right.animated {
            transform: translateX(0);
        }

        .slide-up {
            transform: translateY(50px);
        }

        .slide-up.animated {
            transform: translateY(0);
        }

        /* Responsive Design */
        @media (max-width: 1024px) {
            .nav-container {
                padding: 1rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 3rem;
            }

            .reservation-container {
                grid-template-columns: 1fr;
                gap: 3rem;
            }

            .cart-sidebar {
                width: 350px;
            }
        }

        @media (max-width: 768px) {
            .mobile-menu-btn {
                display: block;
            }

            .nav-links {
                position: fixed;
                top: 100%;
                left: 0;
                right: 0;
                background: var(--primary-color);
                flex-direction: column;
                padding: 2rem;
                gap: 1rem;
                transform: translateY(-100%);
                transition: transform var(--transition-fast);
                box-shadow: var(--shadow-medium);
            }

            .nav-links.open {
                transform: translateY(0);
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .btn {
                width: 100%;
                max-width: 250px;
            }

            .menu-grid {
                grid-template-columns: 1fr;
            }

            .about-stats {
                grid-template-columns: 1fr;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .gallery-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .cart-sidebar {
                width: 100%;
                right: -100%;
            }

            .floating-elements {
                display: none;
            }
        }

        @media (max-width: 480px) {
            .nav-container {
                padding: 0.5rem 0.5rem;
                flex-direction: column;
                align-items: stretch;
            }
            .logo {
                font-size: 1.3rem;
                padding: 0.5rem 0;
            }
            .nav-links {
                flex-direction: column;
                gap: 0.7rem;
                padding: 1rem 0.5rem;
                width: 100%;
                align-items: stretch;
            }
            .nav-links a, .reservation-btn, .cart-toggle {
                font-size: 1.1em;
                padding: 0.8em 0.5em;
                border-radius: 16px;
                width: 100%;
                text-align: left;
            }
            .mobile-menu-btn {
                font-size: 2em;
                padding: 0.5em;
            }
            .hero {
                padding: 1.2rem 0.5rem;
                min-height: 70vh;
            }
            .hero-content {
                padding: 1rem 0.5rem;
            }
            .hero-buttons {
                flex-direction: column;
                gap: 0.7rem;
                align-items: stretch;
            }
            .btn {
                width: 100%;
                max-width: none;
                font-size: 1.1em;
                padding: 0.9em 0.5em;
                border-radius: 16px;
            }
            .container {
                padding: 0 0.5rem;
            }
            .section-title {
                font-size: 1.3rem;
            }
            .about-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }
            .about-image img {
                height: 220px;
            }
            .about-stats {
                grid-template-columns: 1fr;
                gap: 1rem;
            }
            .menu-categories {
                flex-direction: row;
                gap: 0.5rem;
                overflow-x: auto;
                padding-bottom: 0.5rem;
                scrollbar-width: none;
                -ms-overflow-style: none;
            }
            .menu-categories::-webkit-scrollbar {
                display: none;
            }
            .category-btn {
                min-width: 120px;
                font-size: 1em;
                padding: 0.7em 0.5em;
                border-radius: 16px;
            }
            .menu-grid {
                grid-template-columns: 1fr;
                gap: 1rem;
            }
            .menu-item-image {
                height: 120px;
            }
            .menu-item-content {
                padding: 1rem;
            }
            .reservation-form {
                padding: 1rem;
            }
            .form-row {
                grid-template-columns: 1fr;
                gap: 0.5rem;
            }
            .gallery-grid {
                grid-template-columns: 1fr;
                gap: 0.5rem;
            }
            .review-card {
                padding: 1rem;
            }
            .reviews-slider {
                max-width: 100%;
                margin: 1rem auto 0;
            }
            .footer-content {
                grid-template-columns: 1fr;
                gap: 1rem;
            }
            .footer {
                padding: 2rem 0 1rem;
            }
            .footer-section h3 {
                font-size: 1.1rem;
            }
            .footer-bottom {
                padding-top: 1rem;
            }
            .cart-sidebar {
                width: 100vw;
                right: -100vw;
                min-width: 0;
            }
            .cart-sidebar.open {
                right: 0;
            }
            .cart-header, .cart-footer {
                padding: 1rem;
            }
            .cart-item {
                padding: 0.7rem;
            }
            .cart-item-image {
                width: 40px;
                height: 40px;
                font-size: 1.1rem;
            }
            .checkout-btn, .submit-btn {
                font-size: 1em;
                padding: 0.8em;
                border-radius: 16px;
            }
            .modal-content {
                padding: 1rem;
                max-width: 95vw;
            }
            .scroll-top {
                width: 40px;
                height: 40px;
                bottom: 1rem;
                right: 1rem;
                font-size: 1em;
            }
        }

        /* Dark mode toggle */
        .theme-toggle {
            position: fixed;
            top: 50%;
            left: 20px;
            transform: translateY(-50%);
            width: 50px;
            height: 50px;
            background: var(--gradient-secondary);
            border: none;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2rem;
            transition: all var(--transition-fast);
            z-index: 1000;
            box-shadow: var(--shadow-light);
        }

        .theme-toggle:hover {
            transform: translateY(-50%) scale(1.1);
            box-shadow: var(--shadow-medium);
        }

        /* Dark theme */
        body.dark-theme {
            --background-light: #2a2a2a;
            --text-dark: #ffffff;
            --border-color: #444444;
        }

        body.dark-theme .menu,
        body.dark-theme .reviews {
            background: #1a1a1a;
        }

        body.dark-theme .menu-item,
        body.dark-theme .review-card,
        body.dark-theme .stat-card {
            background: #2a2a2a;
            border: 1px solid #444444;
        }

        body.dark-theme .form-control {
            background: rgba(255, 255, 255, 0.05);
            border-color: #444444;
            color: var(--text-light);
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--background-light);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--primary-color);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--secondary-color);
        }

        /* Print styles */
        @media print {

            .navbar,
            .cart-sidebar,
            .scroll-top,
            .theme-toggle,
            .floating-elements {
                display: none !important;
            }

            body {
                font-size: 12pt;
                line-height: 1.4;
            }

            .hero {
                height: auto;
                padding: 2rem 0;
            }

            .section {
                padding: 2rem 0;
                page-break-inside: avoid;
            }
        }

        /* Accessibility improvements */
        @media (prefers-reduced-motion: reduce) {
            * {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }
        }

        .sr-only {
            position: absolute;
            width: 1px;
            height: 1px;
            padding: 0;
            margin: -1px;
            overflow: hidden;
            clip: rect(0, 0, 0, 0);
            white-space: nowrap;
            border: 0;
        }

        /* Focus styles */
        *:focus {
            outline: 2px solid var(--secondary-color);
            outline-offset: 2px;
        }

        .btn:focus,
        .form-control:focus {
            box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.3);
        }
        #table{
            background-color: #28a7467c;
        }
         #table:hover{
            background-color: rgba(0, 0, 255, 0.336);
        }
    </style>
</head>

<body>
    <!-- Loading Screen -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loader"></div>
        <div class="loading-text">Saveurs du Cameroun</div>
    </div>

    <!-- Theme Toggle -->
    <button class="theme-toggle" id="themeToggle" aria-label="Toggle dark mode">
        🌙
    </button>

    <!-- Navigation -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <a href="#" class="logo">
                <i class="fas fa-utensils"></i>
                Saveurs du Cameroun
            </a>

            <ul class="nav-links" id="navLinks">
                <li><a href="#home" class="nav-link active">Accueil</a></li>
                <li><a href="#about" class="nav-link">À Propos</a></li>
                <li><a href="#menu" class="nav-link">Menu</a></li>
                <li><a href="#gallery" class="nav-link">Galerie</a></li>
                <li><a href="#reviews" class="nav-link">Avis</a></li>
                <li><a href="#contact" class="nav-link">Contact</a></li>
                <li>
                    <button class="cart-toggle" id="cartToggle" aria-label="Open shopping cart">
                        <i class="fas fa-shopping-cart"></i>
                        <span class="cart-count" id="cartCount">0</span>
                    </button>
                </li>
                <li><a href="#reservation" class="reservation-btn">Réserver</a></li>
            </ul>

            <button class="mobile-menu-btn" id="mobileMenuBtn" aria-label="Toggle navigation menu">
                <i class="fas fa-bars"></i>
            </button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="floating-elements">
            <div class="floating-element">🍛</div>
            <div class="floating-element">🥘</div>
            <div class="floating-element">🌶️</div>
        </div>

        <div class="hero-content">
            <h1 style="color:blue">Saveurs Authentiques du Cameroun</h1>
            <p class="hero-subtitle">Une expérience culinaire unique au cœur de l'Afrique</p>
            <p class="hero-description">
                Découvrez les saveurs authentiques du Cameroun dans un cadre chaleureux et convivial.
                Nos chefs passionnés vous proposent des plats traditionnels préparés avec amour et des ingrédients
                frais.
            </p>
            <div class="hero-buttons">
                <a href="#menu" class="btn btn-primary">
                    <i class="fas fa-utensils"></i>
                    Découvrir le Menu
                </a>
                <a href="#reservation" id="table" class="btn btn-secondary">
                    <i class="fas fa-calendar-alt"></i>
                    Réserver une Table
                </a>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title animate-on-scroll slide-up">À Propos de Nous</h2>
                <p class="section-subtitle animate-on-scroll slide-up">
                    Une passion pour la cuisine camerounaise transmise de génération en génération
                </p>
            </div>

            <div class="about-content">
                <div class="about-text animate-on-scroll slide-left">
                    <p>
                        <strong>Saveurs du Cameroun</strong> est né d'une passion profonde pour la richesse culinaire du
                        Cameroun.
                        Fondé par une famille d'immigrants camerounais, notre restaurant vous invite à découvrir
                        les saveurs authentiques de l'Afrique centrale.
                    </p>
                    <p>
                        Nos chefs expérimentés perpétuent les traditions culinaires ancestrales tout en apportant
                        une touche moderne à nos plats. Chaque recette raconte une histoire, chaque épice a sa
                        signification, et chaque repas est une célébration de notre héritage culturel.
                    </p>
                    <p>
                        De l'emblématique <strong>Ndolé</strong> au savoureux <strong>Poulet DG</strong>, en passant par
                        le traditionnel <strong>Eru</strong>, nous vous promettons un voyage gustatif inoubliable
                        dans un environnement chaleureux et accueillant.
                    </p>

                    <div class="about-stats">
                        <div class="stat-card">
                            <div class="stat-number" data-count="15">0</div>
                            <div class="stat-label">Années d'Expérience</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" data-count="50">0</div>
                            <div class="stat-label">Plats Traditionnels</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" data-count="10000">0</div>
                            <div class="stat-label">Clients Satisfaits</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" data-count="5">0</div>
                            <div class="stat-label">Étoiles Moyennes</div>
                        </div>
                    </div>
                </div>

                <div class="about-image animate-on-scroll slide-right">
                    <img src="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 600 400'><rect fill='%23d4af37' width='600' height='400'/><rect fill='%232c5530' x='0' y='300' width='600' height='100'/><circle fill='%238b4513' cx='300' cy='200' r='80'/><text x='300' y='210' text-anchor='middle' fill='%23ffffff' font-size='20' font-family='Arial'>Chef</text><rect fill='%23ffffff' x='200' y='100' width='200' height='20' rx='10'/><rect fill='%23ffffff' x='220' y='130' width='160' height='15' rx='7'/></svg>"
                        alt="Notre Chef" />
                </div>
            </div>
        </div>
    </section>

    <!-- Menu Section -->
    <section class="menu" id="menu">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title animate-on-scroll slide-up">Notre Menu</h2>
                <p class="section-subtitle animate-on-scroll slide-up">
                    Découvrez nos spécialités camerounaises préparées avec passion
                </p>
            </div>

            <div class="menu-categories">
                <button class="category-btn active" data-category="all">Tous</button>
                <button class="category-btn" data-category="plats-principaux">Plats Principaux</button>
                <button class="category-btn" data-category="soupes">Soupes</button>
                <button class="category-btn" data-category="grillades">Grillades</button>
                <button class="category-btn" data-category="accompagnements">Accompagnements</button>
                <button class="category-btn" data-category="desserts">Desserts</button>
                <button class="category-btn" data-category="boissons">Boissons</button>
            </div>

            <div class="menu-grid" id="menuGrid">
                <!-- Menu items will be populated by JavaScript -->
            </div>
        </div>
    </section>

    <!-- Reservation Section -->
    <section class="reservation" id="reservation">
        <div class="container">
            <div class="reservation-container">
                <div class="reservation-info animate-on-scroll slide-left">
                    <h2>Réservez Votre Table</h2>
                    <p>
                        Rejoignez-nous pour une expérience culinaire authentique dans une ambiance
                        conviviale. Réservez votre table dès maintenant et laissez-vous transporter
                        par les saveurs du Cameroun.
                    </p>

                    <div class="contact-info">
                        <div class="contact-item">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>123 Rue de la Gastronomie, Douala, Cameroun</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-phone"></i>
                            <span>+237 6XX XX XX XX</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-envelope"></i>
                            <span>contact@saveurscameroun.com</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-clock"></i>
                            <span>Lun-Dim: 11h00 - 23h00</span>
                        </div>
                    </div>
                </div>

                <form class="reservation-form animate-on-scroll slide-right" id="reservationForm">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="firstName">Prénom *</label>
                            <input type="text" id="firstName" name="firstName" class="form-control" required
                                placeholder="Votre prénom">
                        </div>
                        <div class="form-group">
                            <label for="lastName">Nom *</label>
                            <input type="text" id="lastName" name="lastName" class="form-control" required
                                placeholder="Votre nom">
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label for="email">Email *</label>
                            <input type="email" id="email" name="email" class="form-control" required
                                placeholder="votre@email.com">
                        </div>
                        <div class="form-group">
                            <label for="phone">Téléphone *</label>
                            <input type="tel" id="phone" name="phone" class="form-control" required
                                placeholder="+237 6XX XX XX XX">
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label for="date">Date *</label>
                            <input type="date" id="date" name="date" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="time">Heure *</label>
                            <input type="time" id="time" name="time" class="form-control" required>
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label for="guests">Nombre de Personnes *</label>
                            <select id="guests" name="guests" class="form-control" required>
                                <option value="">Choisir...</option>
                                <option value="1">1 personne</option>
                                <option value="2">2 personnes</option>
                                <option value="3">3 personnes</option>
                                <option value="4">4 personnes</option>
                                <option value="5">5 personnes</option>
                                <option value="6">6 personnes</option>
                                <option value="7">7 personnes</option>
                                <option value="8">8 personnes</option>
                                <option value="more">Plus de 8</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="occasion">Occasion</label>
                            <select id="occasion" name="occasion" class="form-control">
                                <option value="">Sélectionner...</option>
                                <option value="birthday">Anniversaire</option>
                                <option value="anniversary">Anniversaire de mariage</option>
                                <option value="business">Repas d'affaires</option>
                                <option value="date">Rendez-vous romantique</option>
                                <option value="family">Repas en famille</option>
                                <option value="celebration">Célébration</option>
                                <option value="other">Autre</option>
                            </select>
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="message">Message / Demandes Spéciales</label>
                        <textarea id="message" name="message" class="form-control" rows="4"
                            placeholder="Allergies, préférences alimentaires, demandes spéciales..."></textarea>
                    </div>

                    <button type="submit" class="submit-btn">
                        <i class="fas fa-calendar-check"></i>
                        Confirmer la Réservation
                    </button>
                </form>
            </div>
        </div>
    </section>

    <!-- Gallery Section -->
    <section class="gallery" id="gallery">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title animate-on-scroll slide-up">Galerie</h2>
                <p class="section-subtitle animate-on-scroll slide-up">
                    Découvrez l'ambiance de notre restaurant et nos délicieux plats
                </p>
            </div>

            <div class="gallery-grid" id="galleryGrid">
                <!-- Gallery items will be populated by JavaScript -->
            </div>
        </div>
    </section>

    <!-- Reviews Section -->
    <section class="reviews" id="reviews">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title animate-on-scroll slide-up">Avis de nos Clients</h2>
                <p class="section-subtitle animate-on-scroll slide-up">
                    Ce que disent nos clients sur leur expérience chez nous
                </p>
            </div>

            <div class="reviews-slider" id="reviewsSlider">
                <!-- Reviews will be populated by JavaScript -->
            </div>

            <div class="review-nav" id="reviewNav">
                <!-- Navigation dots will be populated by JavaScript -->
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>Saveurs du Cameroun</h3>
                    <p>
                        Restaurant authentique spécialisé dans la cuisine traditionnelle camerounaise.
                        Venez découvrir les saveurs uniques de l'Afrique centrale dans un cadre chaleureux et convivial.
                    </p>
                    <div class="social-links">
                        <a href="#" class="social-link" aria-label="Facebook">
                            <i class="fab fa-facebook-f"></i>
                        </a>
                        <a href="#" class="social-link" aria-label="Instagram">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="#" class="social-link" aria-label="Twitter">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="social-link" aria-label="TikTok">
                            <i class="fab fa-tiktok"></i>
                        </a>
                    </div>
                </div>

                <div class="footer-section">
                    <h3>Navigation</h3>
                    <ul>
                        <li><a href="#home">Accueil</a></li>
                        <li><a href="#about">À Propos</a></li>
                        <li><a href="#menu">Menu</a></li>
                        <li><a href="#gallery">Galerie</a></li>
                        <li><a href="#reviews">Avis</a></li>
                        <li><a href="#reservation">Réservation</a></li>
                    </ul>
                </div>

                <div class="footer-section">
                    <h3>Contact</h3>
                    <ul>
                        <li><i class="fas fa-map-marker-alt"></i> 123 Rue de la Gastronomie, Douala</li>
                        <li><i class="fas fa-phone"></i> +237 6XX XX XX XX</li>
                        <li><i class="fas fa-envelope"></i> contact@saveurscameroun.com</li>
                        <li><i class="fas fa-clock"></i> Lun-Dim: 11h00 - 23h00</li>
                    </ul>
                </div>

                <div class="footer-section">
                    <h3>Spécialités</h3>
                    <ul>
                        <li>Ndolé traditionnel</li>
                        <li>Poulet DG</li>
                        <li>Eru aux crevettes</li>
                        <li>Poisson braisé</li>
                        <li>Koki de niébé</li>
                        <li>Beignets de plantain</li>
                    </ul>
                </div>
            </div>

            <div class="footer-bottom">
                <p>&copy; 2024 Saveurs du Cameroun. Tous droits réservés. | Conçu avec ❤️ pour la culture camerounaise
                </p>
            </div>
        </div>
    </footer>

    <!-- Cart Sidebar -->
    <div class="cart-sidebar" id="cartSidebar">
        <div class="cart-header">
            <h3 class="cart-title">Mon Panier</h3>
            <button class="cart-close" id="cartClose" aria-label="Close cart">
                <i class="fas fa-times"></i>
            </button>
        </div>

        <div class="cart-items" id="cartItems">
            <!-- Cart items will be populated by JavaScript -->
        </div>

        <div class="cart-footer">
            <div class="cart-total">
                <span>Total:</span>
                <span id="cartTotal">0 FCFA</span>
            </div>
            <button class="checkout-btn" id="checkoutBtn">
                <i class="fas fa-credit-card"></i>
                Passer Commande
            </button>
        </div>
    </div>

    <!-- Modal -->
    <div class="modal" id="modal">
        <div class="modal-content">
            <div class="modal-icon" id="modalIcon">✅</div>
            <h3 class="modal-title" id="modalTitle">Succès!</h3>
            <p class="modal-text" id="modalText">Votre action a été effectuée avec succès.</p>
            <button class="modal-btn" id="modalBtn">OK</button>
        </div>
    </div>

    <!-- Scroll to Top Button -->
    <button class="scroll-top" id="scrollTop" aria-label="Scroll to top">
        <i class="fas fa-arrow-up"></i>
    </button>

    <script>
        // ===== DATA =====
        const menuData = [
            {
                id: 1,
                name: "Ndolé Traditionnel",
                category: "plats-principaux",
                price: 3500,
                description: "Plat emblématique du Cameroun à base de feuilles de ndolé, arachides et viande/poisson",
                spiceLevel: 2,
                image: ""
            },
            {
                id: 2,
                name: "Poulet DG",
                category: "plats-principaux",
                price: 4000,
                description: "Poulet sauté aux légumes (plantains, carottes, haricots verts) dans une sauce savoureuse",
                spiceLevel: 1,
                image: "🍗"
            },
            {
                id: 3,
                name: "Eru aux Crevettes",
                category: "soupes",
                price: 4500,
                description: "Soupe traditionnelle à base de feuilles d'eru, crevettes séchées et viande fumée",
                spiceLevel: 3,
                image: "🍲"
            },
            {
                id: 4,
                name: "Poisson Braisé",
                category: "grillades",
                price: 3000,
                description: "Poisson frais grillé aux épices camerounaises, accompagné d'attiéké ou de plantain",
                spiceLevel: 2,
                image: "🐟"
            },
            {
                id: 5,
                name: "Koki de Niébé",
                category: "accompagnements",
                price: 1500,
                description: "Gâteau de haricots vapeur, spécialité de l'Ouest Cameroun",
                spiceLevel: 1,
                image: "🫘"
            },
            {
                id: 6,
                name: "Beignets de Plantain",
                category: "accompagnements",
                price: 1000,
                description: "Beignets croustillants de plantain mûr, parfaits en accompagnement",
                spiceLevel: 0,
                image: "🍌"
            },
            {
                id: 7,
                name: "Soupe de Pistache",
                category: "soupes",
                price: 3800,
                description: "Soupe riche aux arachides avec du bœuf et des légumes traditionnels",
                spiceLevel: 2,
                image: "🥜"
            },
            {
                id: 8,
                name: "Brochettes de Bœuf",
                category: "grillades",
                price: 3500,
                description: "Brochettes de bœuf marinées aux épices locales, grillées au feu de bois",
                spiceLevel: 2,
                image: "🍢"
            },
            {
                id: 9,
                name: "Fufu de Plantain",
                category: "accompagnements",
                price: 1200,
                description: "Accompagnement traditionnel à base de plantain pilé",
                spiceLevel: 0,
                image: "🥖"
            },
            {
                id: 10,
                name: "Sauce Gombo",
                category: "soupes",
                price: 3200,
                description: "Sauce visqueuse au gombo avec du poisson fumé et de la viande",
                spiceLevel: 2,
                image: "🌶️"
            },
            {
                id: 11,
                name: "Porc au Gingembre",
                category: "plats-principaux",
                price: 4200,
                description: "Porc mijoté dans une sauce au gingembre et aux légumes frais",
                spiceLevel: 1,
                image: "🐷"
            },
            {
                id: 12,
                name: "Mbanga Soup",
                category: "soupes",
                price: 3600,
                description: "Soupe de palme traditionnelle avec du poisson et de la viande",
                spiceLevel: 2,
                image: "🥥"
            },
            {
                id: 13,
                name: "Kwacoco Anglais",
                category: "accompagnements",
                price: 1800,
                description: "Taro vapeur accompagné de sauce tomate épicée",
                spiceLevel: 1,
                image: "🍠"
            },
            {
                id: 14,
                name: "Suya de Chèvre",
                category: "grillades",
                price: 4000,
                description: "Viande de chèvre grillée aux épices suya, spécialité du Nord",
                spiceLevel: 3,
                image: "🐐"
            },
            {
                id: 15,
                name: "Bobolo",
                category: "accompagnements",
                price: 800,
                description: "Manioc fermenté enveloppé dans des feuilles, cuit à la vapeur",
                spiceLevel: 0,
                image: "🌿"
            },
            {
                id: 16,
                name: "Beignet Haricot",
                category: "desserts",
                price: 500,
                description: "Beignets sucrés aux haricots, collation traditionnelle",
                spiceLevel: 0,
                image: "🍩"
            },
            {
                id: 17,
                name: "Piments Verts Farcis",
                category: "plats-principaux",
                price: 2800,
                description: "Piments verts farcis au poisson et aux épices",
                spiceLevel: 3,
                image: "🫑"
            },
            {
                id: 18,
                name: "Kondré de Chèvre",
                category: "plats-principaux",
                price: 4500,
                description: "Ragoût de chèvre aux légumes et épices du Nord Cameroun",
                spiceLevel: 2,
                image: "🍛"
            },
            {
                id: 19,
                name: "Bière Mutzig",
                category: "boissons",
                price: 800,
                description: "Bière locale camerounaise, fraîche et désaltérante",
                spiceLevel: 0,
                image: "🍺"
            },
            {
                id: 20,
                name: "Jus de Bissap",
                category: "boissons",
                price: 1000,
                description: "Boisson rafraîchissante à base de fleurs d'hibiscus",
                spiceLevel: 0,
                image: "🧃"
            },
            {
                id: 21,
                name: "Vin de Palme",
                category: "boissons",
                price: 1500,
                description: "Boisson traditionnelle fermentée à base de sève de palmier",
                spiceLevel: 0,
                image: "🍷"
            },
            {
                id: 22,
                name: "Puff-Puff",
                category: "desserts",
                price: 300,
                description: "Beignets sucrés moelleux, parfaits pour le dessert",
                spiceLevel: 0,
                image: "⚪"
            },
            {
                id: 23,
                name: "Plantain Rôti",
                category: "desserts",
                price: 800,
                description: "Plantain mûr grillé, caramélisé naturellement",
                spiceLevel: 0,
                image: "🍌"
            },
            {
                id: 24,
                name: "Mangue Fraîche",
                category: "desserts",
                price: 600,
                description: "Mangue locale fraîche et juteuse de saison",
                spiceLevel: 0,
                image: "🥭"
            }
        ];

        const reviewsData = [
            {
                id: 1,
                author: "Marie Dubois",
                rating: 5,
                text: "Une expérience culinaire exceptionnelle ! Le ndolé était absolument délicieux et l'ambiance très chaleureuse. Je recommande vivement ce restaurant à tous ceux qui veulent découvrir la vraie cuisine camerounaise.",
                avatar: "MD"
            },
            {
                id: 2,
                author: "Jean-Paul Mvondo",
                rating: 5,
                text: "Enfin un restaurant qui respecte les traditions culinaires camerounaises ! Le poulet DG était parfaitement préparé et le service impeccable. Un vrai régal pour les papilles.",
                avatar: "JM"
            },
            {
                id: 3,
                author: "Sarah Johnson",
                rating: 4,
                text: "Découverte fantastique de la cuisine camerounaise. Les saveurs sont authentiques et les portions généreuses. L'eru aux crevettes était un délice. Seul bémol : l'attente un peu longue.",
                avatar: "SJ"
            },
            {
                id: 4,
                author: "Pierre Nkomo",
                rating: 5,
                text: "Comme à la maison ! Les plats me rappellent ceux de ma grand-mère. L'équipe est accueillante et les prix très raisonnables. Une adresse à retenir absolument.",
                avatar: "PN"
            },
            {
                id: 5,
                author: "Fatima Al-Hassan",
                rating: 5,
                text: "Service exceptionnel et cuisine authentique. Le poisson braisé était cuit à la perfection et les accompagnements parfaitement assaisonnés. Une expérience culinaire inoubliable !",
                avatar: "FA"
            }
        ];

        const galleryData = [
            { id: 1, category: "restaurant", alt: "Intérieur du restaurant" },
            { id: 2, category: "food", alt: "Ndolé traditionnel" },
            { id: 3, category: "food", alt: "Poulet DG" },
            { id: 4, category: "restaurant", alt: "Salle à manger" },
            { id: 5, category: "food", alt: "Eru aux crevettes" },
            { id: 6, category: "food", alt: "Poisson braisé" },
            { id: 7, category: "restaurant", alt: "Cuisine ouverte" },
            { id: 8, category: "food", alt: "Desserts traditionnels" },
            { id: 9, category: "events", alt: "Événement spécial" },
            { id: 10, category: "food", alt: "Brochettes de bœuf" },
            { id: 11, category: "restaurant", alt: "Terrasse extérieure" },
            { id: 12, category: "food", alt: "Boissons traditionnelles" }
        ];

        // ===== STATE MANAGEMENT =====
        let cart = [];
        let currentReviewIndex = 0;
        let isMenuLoaded = false;
        let animationObserver;

        // ===== UTILITY FUNCTIONS =====
        function formatPrice(price) {
            return new Intl.NumberFormat('fr-FR').format(price) + ' FCFA';
        }

        function generateSpiceIcons(level) {
            let icons = '';
            for (let i = 0; i < 3; i++) {
                icons += `<i class="spice-icon ${i < level ? 'fas' : 'far'} fa-pepper-hot"></i>`;
            }
            return icons;
        }

        function showModal(icon, title, text) {
            const modal = document.getElementById('modal');
            const modalIcon = document.getElementById('modalIcon');
            const modalTitle = document.getElementById('modalTitle');
            const modalText = document.getElementById('modalText');

            modalIcon.textContent = icon;
            modalTitle.textContent = title;
            modalText.textContent = text;

            modal.classList.add('show');
        }

        function hideModal() {
            document.getElementById('modal').classList.remove('show');
        }

        function updateCartUI() {
            const cartCount = document.getElementById('cartCount');
            const cartItems = document.getElementById('cartItems');
            const cartTotal = document.getElementById('cartTotal');

            // Update cart count
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;
            cartCount.style.display = totalItems > 0 ? 'inline' : 'none';

            // Update cart items
            if (cart.length === 0) {
                cartItems.innerHTML = `
                    <div style="text-align: center; padding: 3rem; color: #666;">
                        <i class="fas fa-shopping-cart" style="font-size: 3rem; margin-bottom: 1rem; opacity: 0.3;"></i>
                        <p>Votre panier est vide</p>
                        <p style="font-size: 0.9em; opacity: 0.7;">Ajoutez des plats délicieux depuis notre menu</p>
                    </div>
                `;
                cartTotal.textContent = '0 FCFA';
            } else {
                cartItems.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <div class="cart-item-image">${item.image}</div>
                        <div class="cart-item-details">
                            <div class="cart-item-name">${item.name}</div>
                            <div class="cart-item-price">${formatPrice(item.price)}</div>
                            <div class="quantity-controls">
                                <button class="quantity-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                                <span class="quantity">${item.quantity}</span>
                                <button class="quantity-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                            </div>
                        </div>
                    </div>
                `).join('');

                const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                cartTotal.textContent = formatPrice(total);
            }
        }

        function addToCart(menuItem) {
            const existingItem = cart.find(item => item.id === menuItem.id);

            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({ ...menuItem, quantity: 1 });
            }

            updateCartUI();
            showModal('🛒', 'Ajouté au panier!', `${menuItem.name} a été ajouté à votre panier.`);
        }

        function updateQuantity(itemId, change) {
            const item = cart.find(item => item.id === itemId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    cart = cart.filter(item => item.id !== itemId);
                }
                updateCartUI();
            }
        }

        // ===== MENU FUNCTIONS =====
        function renderMenuItems(items = menuData) {
            const menuGrid = document.getElementById('menuGrid');

            menuGrid.innerHTML = items.map(item => `
                <div class="menu-item animate-on-scroll slide-up" data-category="${item.category}">
                    <div class="menu-item-image">
                        <div class="price-tag">${formatPrice(item.price)}</div>
                    </div>
                    <div class="menu-item-content">
                        <h3 class="menu-item-title">${item.name}</h3>
                        <p class="menu-item-description">${item.description}</p>
                        <div class="menu-item-footer">
                            <div class="spice-level" title="Niveau de piment">
                                ${generateSpiceIcons(item.spiceLevel)}
                            </div>
                            <button class="add-to-cart" onclick="addToCart(${JSON.stringify(item).replace(/"/g, '&quot;')})">
                                <i class="fas fa-plus"></i>
                                Ajouter
                            </button>
                        </div>
                    </div>
                </div>
            `).join('');

            // Trigger animation for new items
            setTimeout(() => {
                document.querySelectorAll('.menu-item').forEach((item, index) => {
                    setTimeout(() => {
                        item.classList.add('show');
                    }, index * 100);
                });
            }, 100);
        }

        function filterMenu(category) {
            const filteredItems = category === 'all' ? menuData : menuData.filter(item => item.category === category);
            renderMenuItems(filteredItems);

            // Update active category button
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            document.querySelector(`[data-category="${category}"]`).classList.add('active');
        }

        // ===== GALLERY FUNCTIONS =====
        function renderGallery() {
            const galleryGrid = document.getElementById('galleryGrid');

            galleryGrid.innerHTML = galleryData.map(item => `
                <div class="gallery-item animate-on-scroll slide-up" onclick="openGalleryModal(${item.id})">
                    <div class="gallery-overlay">
                        <i class="fas fa-search-plus"></i>
                    </div>
                </div>
            `).join('');
        }

        function openGalleryModal(itemId) {
            const item = galleryData.find(g => g.id === itemId);
            showModal('📸', 'Galerie', `Affichage de: ${item.alt}`);
        }

        // ===== REVIEWS FUNCTIONS =====
        function renderReviews() {
            const reviewsSlider = document.getElementById('reviewsSlider');
            const reviewNav = document.getElementById('reviewNav');

            // Render current review
            const currentReview = reviewsData[currentReviewIndex];
            reviewsSlider.innerHTML = `
                <div class="review-card">
                    <p class="review-text">${currentReview.text}</p>
                    <div class="review-author">
                        <div class="review-avatar">${currentReview.avatar}</div>
                        <div class="review-info">
                            <h4>${currentReview.author}</h4>
                            <div class="review-rating">
                                ${'★'.repeat(currentReview.rating)}${'☆'.repeat(5 - currentReview.rating)}
                            </div>
                        </div>
                    </div>
                </div>
            `;

            // Render navigation dots
            reviewNav.innerHTML = reviewsData.map((_, index) => `
                <div class="nav-dot ${index === currentReviewIndex ? 'active' : ''}" onclick="goToReview(${index})"></div>
            `).join('');
        }

        function goToReview(index) {
            currentReviewIndex = index;
            renderReviews();
        }

        function nextReview() {
            currentReviewIndex = (currentReviewIndex + 1) % reviewsData.length;
            renderReviews();
        }

        // ===== ANIMATION FUNCTIONS =====
        function initScrollAnimations() {
            animationObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('animated');
                    }
                });
            }, {
                threshold: 0.2,
                rootMargin: '0px 0px -50px 0px'
            });

            document.querySelectorAll('.animate-on-scroll').forEach(el => {
                animationObserver.observe(el);
            });
        }

        function animateCounters() {
            document.querySelectorAll('.stat-number').forEach(counter => {
                const target = parseInt(counter.getAttribute('data-count'));
                const increment = target / 100;
                let current = 0;

                const timer = setInterval(() => {
                    current += increment;
                    if (current >= target) {
                        counter.textContent = target.toLocaleString();
                        clearInterval(timer);
                    } else {
                        counter.textContent = Math.floor(current).toLocaleString();
                    }
                }, 20);
            });
        }

        // ===== FORM HANDLING =====
        function initReservationForm() {
            const form = document.getElementById('reservationForm');
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('date').min = today;

            form.addEventListener('submit', function (e) {
                e.preventDefault();

                // Simulate form submission
                const submitBtn = document.querySelector('.submit-btn');
                const originalText = submitBtn.innerHTML;

                submitBtn.disabled = true;
                submitBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Envoi en cours...';

                setTimeout(() => {
                    showModal('✅', 'Réservation Confirmée!',
                        'Votre demande de réservation a été envoyée avec succès. Nous vous contacterons bientôt pour confirmer.');
                    form.reset();
                    submitBtn.disabled = false;
                    submitBtn.innerHTML = originalText;
                }, 2000);
            });
        }

        // ===== NAVIGATION =====
        function initNavigation() {
            const navbar = document.getElementById('navbar');
            const mobileMenuBtn = document.getElementById('mobileMenuBtn');
            const navLinks = document.getElementById('navLinks');
            const scrollTop = document.getElementById('scrollTop');

            // Navbar scroll effect
            window.addEventListener('scroll', () => {
                if (window.scrollY > 100) {
                    navbar.classList.add('scrolled');
                    scrollTop.classList.add('show');
                } else {
                    navbar.classList.remove('scrolled');
                    scrollTop.classList.remove('show');
                }
            });

            // Mobile menu toggle
            mobileMenuBtn.addEventListener('click', () => {
                navLinks.classList.toggle('open');
                const icon = mobileMenuBtn.querySelector('i');
                icon.classList.toggle('fa-bars');
                icon.classList.toggle('fa-times');
            });

            // Smooth scrolling for navigation links
            document.querySelectorAll('.nav-link, .hero-buttons a, .scroll-top').forEach(link => {
                link.addEventListener('click', function (e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href');
                    if (targetId.startsWith('#')) {
                        const targetElement = document.querySelector(targetId);
                        if (targetElement) {
                            targetElement.scrollIntoView({
                                behavior: 'smooth',
                                block: 'start'
                            });

                            // Close mobile menu if open
                            navLinks.classList.remove('open');
                            mobileMenuBtn.querySelector('i').classList.add('fa-bars');
                            mobileMenuBtn.querySelector('i').classList.remove('fa-times');
                        }
                    }
                });
            });

            // Update active navigation link on scroll
            const sections = document.querySelectorAll('section[id]');
            window.addEventListener('scroll', () => {
                let current = '';
                sections.forEach(section => {
                    const sectionTop = section.offsetTop - 150;
                    if (window.pageYOffset >= sectionTop) {
                        current = section.getAttribute('id');
                    }
                });

                document.querySelectorAll('.nav-link').forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href') === `#${current}`) {
                        link.classList.add('active');
                    }
                });
            });
        }

        // ===== CART FUNCTIONS =====
        function initCart() {
            const cartToggle = document.getElementById('cartToggle');
            const cartSidebar = document.getElementById('cartSidebar');
            const cartClose = document.getElementById('cartClose');
            const checkoutBtn = document.getElementById('checkoutBtn');

            cartToggle.addEventListener('click', () => {
                cartSidebar.classList.add('open');
            });

            cartClose.addEventListener('click', () => {
                cartSidebar.classList.remove('open');
            });

            checkoutBtn.addEventListener('click', () => {
                if (cart.length === 0) {
                    showModal('⚠️', 'Panier Vide', 'Ajoutez des plats à votre panier avant de passer commande.');
                    return;
                }

                const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                showModal('🎉', 'Commande Confirmée!',
                    `Votre commande d'un montant de ${formatPrice(total)} a été confirmée. Merci pour votre confiance!`);
                cart = [];
                updateCartUI();
                cartSidebar.classList.remove('open');
            });

            // Close cart when clicking outside
            document.addEventListener('click', (e) => {
                if (!cartSidebar.contains(e.target) && !cartToggle.contains(e.target)) {
                    cartSidebar.classList.remove('open');
                }
            });
        }

        // ===== THEME TOGGLE =====
        function initThemeToggle() {
            const themeToggle = document.getElementById('themeToggle');
            const body = document.body;

            // Check for saved theme preference
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme === 'dark') {
                body.classList.add('dark-theme');
                themeToggle.textContent = '☀️';
            }

            themeToggle.addEventListener('click', () => {
                body.classList.toggle('dark-theme');
                const isDark = body.classList.contains('dark-theme');
                themeToggle.textContent = isDark ? '☀️' : '🌙';
                localStorage.setItem('theme', isDark ? 'dark' : 'light');
            });
        }

        // ===== INITIALIZATION =====
        function init() {
            // Remove loading screen
            setTimeout(() => {
                document.getElementById('loadingScreen').classList.add('hidden');
            }, 2000);

            // Initialize all components
            initNavigation();
            initCart();
            initThemeToggle();
            initReservationForm();
            renderMenuItems();
            renderGallery();
            renderReviews();
            initScrollAnimations();

            // Set up menu category filters
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.addEventListener('click', () => {
                    const category = btn.getAttribute('data-category');
                    filterMenu(category);
                });
            });

            // Auto-rotate reviews
            setInterval(nextReview, 5000);

            // Initialize modal close
            document.getElementById('modalBtn').addEventListener('click', hideModal);
            document.getElementById('modal').addEventListener('click', (e) => {
                if (e.target.id === 'modal') hideModal();
            });

            // Animate counters when about section is visible
            const aboutSection = document.getElementById('about');
            const aboutObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        animateCounters();
                        aboutObserver.unobserve(entry.target);
                    }
                });
            }, { threshold: 0.5 });

            aboutObserver.observe(aboutSection);

            // Add cart icon style
            const cartToggle = document.getElementById('cartToggle');
            cartToggle.style.cssText = `
                position: relative;
                background: none;
                border: none;
                color: white;
                font-size: 1.2rem;
                cursor: pointer;
                padding: 0.5rem;
                border-radius: 50%;
                transition: all 0.3s ease;
            `;

            const cartCount = document.getElementById('cartCount');
            cartCount.style.cssText = `
                position: absolute;
                top: -5px;
                right: -5px;
                background: #dc3545;
                color: white;
                border-radius: 50%;
                width: 20px;
                height: 20px;
                font-size: 0.8rem;
                display: none;
                align-items: center;
                justify-content: center;
                font-weight: bold;
            `;

            updateCartUI();

            // Add hover effects
            document.addEventListener('mouseover', (e) => {
                if (e.target.matches('.btn, .menu-item, .gallery-item, .review-card')) {
                    e.target.style.transform = 'translateY(-2px)';
                }
            });

            document.addEventListener('mouseout', (e) => {
                if (e.target.matches('.btn, .menu-item, .gallery-item, .review-card')) {
                    e.target.style.transform = 'translateY(0)';
                }
            });

            // Add keyboard navigation
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    hideModal();
                    document.getElementById('cartSidebar').classList.remove('open');
                    document.getElementById('navLinks').classList.remove('open');
                }
            });

            // Add loading states for images
            document.querySelectorAll('.menu-item-image, .gallery-item').forEach(item => {
                item.style.background = 'linear-gradient(45deg, #d4af37, #2c5530)';
                item.style.backgroundSize = '200% 200%';
                item.style.animation = 'gradientShift 3s ease infinite';
            });

            // Add gradient animation
            const style = document.createElement('style');
            style.textContent = `
                @keyframes gradientShift {
                    0% { background-position: 0% 50%; }
                    50% { background-position: 100% 50%; }
                    100% { background-position: 0% 50%; }
                }
                
                .cart-count {
                    animation: pulse 2s infinite;
                }
                
                @keyframes pulse {
                    0% { transform: scale(1); }
                    50% { transform: scale(1.1); }
                    100% { transform: scale(1); }
                }
            `;
            document.head.appendChild(style);

            // Add search functionality (bonus feature)
            const searchInput = document.createElement('input');
            searchInput.type = 'text';
            searchInput.placeholder = 'Rechercher un plat...';
            searchInput.className = 'search-input';
            searchInput.style.cssText = `
                width: 100%;
                max-width: 400px;
                padding: 1rem;
                margin: 2rem auto;
                display: block;
                border: 2px solid #d4af37;
                border-radius: 25px;
                font-size: 1rem;
                text-align: center;
                transition: all 0.3s ease;
            `;

            const menuContainer = document.querySelector('.menu .container');
            const menuHeader = menuContainer.querySelector('.section-header');
            menuHeader.appendChild(searchInput);

            searchInput.addEventListener('input', (e) => {
                const searchTerm = e.target.value.toLowerCase();
                const filteredItems = menuData.filter(item =>
                    item.name.toLowerCase().includes(searchTerm) ||
                    item.description.toLowerCase().includes(searchTerm)
                );
                renderMenuItems(filteredItems);
            });

            // Add nutrition info modal (bonus feature)
            window.showNutritionInfo = function (itemId) {
                const item = menuData.find(m => m.id === itemId);
                if (item) {
                    const nutritionInfo = {
                        calories: Math.floor(Math.random() * 400) + 200,
                        protein: Math.floor(Math.random() * 30) + 10,
                        carbs: Math.floor(Math.random() * 50) + 20,
                        fat: Math.floor(Math.random() * 20) + 5
                    };

                    showModal('📊', 'Informations Nutritionnelles',
                        `${item.name}\n\nCalories: ${nutritionInfo.calories} kcal\nProtéines: ${nutritionInfo.protein}g\nGlucides: ${nutritionInfo.carbs}g\nLipides: ${nutritionInfo.fat}g`);
                }
            };

            // Add social sharing
            window.shareMenu = function () {
                if (navigator.share) {
                    navigator.share({
                        title: 'Saveurs du Cameroun - Menu',
                        text: 'Découvrez notre délicieux menu de cuisine camerounaise authentique!',
                        url: window.location.href
                    });
                } else {
                    navigator.clipboard.writeText(window.location.href).then(() => {
                        showModal('📋', 'Lien Copié!', 'Le lien du menu a été copié dans votre presse-papiers.');
                    });
                }
            };

            // Add contact form validation
            const inputs = document.querySelectorAll('.form-control');
            inputs.forEach(input => {
                input.addEventListener('blur', function () {
                    if (this.hasAttribute('required') && !this.value.trim()) {
                        this.style.borderColor = '#dc3545';
                        this.style.boxShadow = '0 0 0 3px rgba(220, 53, 69, 0.3)';
                    } else {
                        this.style.borderColor = 'rgba(255, 255, 255, 0.3)';
                        this.style.boxShadow = 'none';
                    }
                });

                input.addEventListener('input', function () {
                    if (this.style.borderColor === 'rgb(220, 53, 69)') {
                        this.style.borderColor = 'rgba(255, 255, 255, 0.3)';
                        this.style.boxShadow = 'none';
                    }
                });
            });

            // Add real-time availability checker
            function checkAvailability() {
                const now = new Date();
                const hours = now.getHours();
                const isOpen = hours >= 11 && hours < 23;

                const statusIndicator = document.createElement('div');
                statusIndicator.className = 'status-indicator';
                statusIndicator.innerHTML = `
                    <div style="
                        position: fixed;
                        top: 100px;
                        right: 20px;
                        background: ${isOpen ? '#28a745' : '#dc3545'};
                        color: white;
                        padding: 1rem;
                        border-radius: 10px;
                        box-shadow: 0 4px 15px rgba(0,0,0,0.2);
                        z-index: 1000;
                        font-weight: bold;
                        animation: slideInRight 0.5s ease;
                    ">
                        <i class="fas fa-clock"></i>
                        ${isOpen ? 'Ouvert maintenant!' : 'Fermé actuellement'}
                        <div style="font-size: 0.8em; margin-top: 0.5rem;">
                            ${isOpen ? 'Jusqu\'à 23h00' : 'Ouverture à 11h00'}
                        </div>
                    </div>
                `;

                document.body.appendChild(statusIndicator);

                // Auto-hide after 5 seconds
                setTimeout(() => {
                    statusIndicator.style.animation = 'slideOutRight 0.5s ease';
                    setTimeout(() => statusIndicator.remove(), 500);
                }, 5000);
            }

            checkAvailability();

            // Add slideInRight animation
            const animationStyle = document.createElement('style');
            animationStyle.textContent += `
                @keyframes slideInRight {
                    from {
                        transform: translateX(100%);
                        opacity: 0;
                    }
                    to {
                        transform: translateX(0);
                        opacity: 1;
                    }
                }
                
                @keyframes slideOutRight {
                    from {
                        transform: translateX(0);
                        opacity: 1;
                    }
                    to {
                        transform: translateX(100%);
                        opacity: 0;
                    }
                }
            `;
            document.head.appendChild(animationStyle);

            // Add performance monitoring
            window.addEventListener('load', () => {
                const loadTime = performance.now();
                console.log(`🚀 Site chargé en ${Math.round(loadTime)}ms`);

                if (loadTime > 3000) {
                    console.warn('⚠️ Temps de chargement élevé détecté');
                }
            });

            // Add error handling for failed operations
            window.addEventListener('error', (e) => {
                console.error('❌ Erreur détectée:', e.error);
                showModal('⚠️', 'Erreur', 'Une erreur s\'est produite. Veuillez rafraîchir la page.');
            });

            // Add offline detection
            window.addEventListener('online', () => {
                showModal('✅', 'Connexion Rétablie', 'Vous êtes de nouveau en ligne!');
            });

            window.addEventListener('offline', () => {
                showModal('⚠️', 'Hors Ligne', 'Vous êtes actuellement hors ligne. Certaines fonctionnalités peuvent être limitées.');
            });

            // Add progressive enhancement
            if ('serviceWorker' in navigator) {
                navigator.serviceWorker.register('/sw.js').catch(e => {
                    console.log('Service Worker non disponible');
                });
            }

            // Add final touch - welcome message
            setTimeout(() => {
                if (sessionStorage.getItem('welcomed') !== 'true') {
                    showModal('🎉', 'Bienvenue!', 'Bienvenue chez Saveurs du Cameroun! Découvrez notre cuisine authentique et nos spécialités traditionnelles.');
                    sessionStorage.setItem('welcomed', 'true');
                }
            }, 3000);

            console.log('🍽️ Restaurant website fully loaded and ready!');
        }

        // ===== ADDITIONAL UTILITY FUNCTIONS =====

        // Format currency for different regions
        function formatCurrency(amount, currency = 'FCFA') {
            if (currency === 'FCFA') {
                return new Intl.NumberFormat('fr-FR').format(amount) + ' FCFA';
            }
            return new Intl.NumberFormat('fr-FR', {
                style: 'currency',
                currency: currency
            }).format(amount);
        }

        // Advanced search with filters
        function advancedSearch(term, filters = {}) {
            return menuData.filter(item => {
                const matchesSearch = !term ||
                    item.name.toLowerCase().includes(term.toLowerCase()) ||
                    item.description.toLowerCase().includes(term.toLowerCase());

                const matchesCategory = !filters.category ||
                    filters.category === 'all' ||
                    item.category === filters.category;

                const matchesSpiceLevel = filters.spiceLevel === undefined ||
                    item.spiceLevel <= filters.spiceLevel;

                const matchesPriceRange = (!filters.minPrice || item.price >= filters.minPrice) &&
                    (!filters.maxPrice || item.price <= filters.maxPrice);

                return matchesSearch && matchesCategory && matchesSpiceLevel && matchesPriceRange;
            });
        }

        // Generate receipt
        function generateReceipt() {
            if (cart.length === 0) return null;

            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const tax = subtotal * 0.18; // 18% VAT
            const total = subtotal + tax;

            return {
                items: cart,
                subtotal: subtotal,
                tax: tax,
                total: total,
                date: new Date().toLocaleString('fr-FR'),
                orderNumber: 'CMD' + Date.now().toString().slice(-6)
            };
        }

        // Export cart to different formats
        function exportCart(format = 'json') {
            const receipt = generateReceipt();
            if (!receipt) return;

            let content;
            let filename;
            let mimeType;

            switch (format) {
                case 'json':
                    content = JSON.stringify(receipt, null, 2);
                    filename = `commande_${receipt.orderNumber}.json`;
                    mimeType = 'application/json';
                    break;

                case 'csv':
                    const csvHeaders = 'Plat,Quantité,Prix Unitaire,Total\n';
                    const csvContent = cart.map(item =>
                        `"${item.name}",${item.quantity},${item.price},${item.price * item.quantity}`
                    ).join('\n');
                    content = csvHeaders + csvContent + `\n\nSous-total,,,${receipt.subtotal}\nTVA,,,${receipt.tax}\nTotal,,,${receipt.total}`;
                    filename = `commande_${receipt.orderNumber}.csv`;
                    mimeType = 'text/csv';
                    break;

                case 'txt':
                    content = `SAVEURS DU CAMEROUN\nCommande #${receipt.orderNumber}\nDate: ${receipt.date}\n\n`;
                    content += cart.map(item =>
                        `${item.name} x${item.quantity} - ${formatPrice(item.price * item.quantity)}`
                    ).join('\n');
                    content += `\n\nSous-total: ${formatPrice(receipt.subtotal)}\nTVA (18%): ${formatPrice(receipt.tax)}\nTOTAL: ${formatPrice(receipt.total)}`;
                    filename = `commande_${receipt.orderNumber}.txt`;
                    mimeType = 'text/plain';
                    break;
            }

            const blob = new Blob([content], { type: mimeType });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = filename;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }

        // Initialize everything when DOM is loaded
        if (document.readyState === 'loading') {
            document.addEventListener('DOMContentLoaded', init);
        } else {
            init();
        }

        // Expose useful functions to global scope for debugging
        window.restaurantApp = {
            menuData,
            reviewsData,
            galleryData,
            cart,
            formatPrice,
            addToCart,
            updateQuantity,
            generateReceipt,
            exportCart,
            advancedSearch,
            showModal,
            hideModal
        };

    </script>
</body>

</html>
