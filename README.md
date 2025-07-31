<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ShopExpress Beauté INNOVA - Version Pro</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --primary-color: #ff6b9d;
      --primary-dark: #e55a8a;
      --secondary-color: #4ecdc4;
      --accent-color: #ffe66d;
      --success-color: #25d366;
      --danger-color: #ff4757;
      --warning-color: #ffa726;
      --info-color: #42a5f5;
      --dark-color: #2f3542;
      --light-color: #f1f2f6;
      --white: #ffffff;
      --shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      --shadow-hover: 0 20px 40px rgba(0, 0, 0, 0.15);
      --border-radius: 20px;
      --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: var(--dark-color);
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* Nouveauté: Notification Bar */
    .notification-bar {
      background: linear-gradient(90deg, var(--success-color), var(--secondary-color));
      color: white;
      text-align: center;
      padding: 10px;
      font-weight: 500;
      animation: slideDown 0.5s ease-out;
      position: relative;
      overflow: hidden;
    }

    .notification-bar::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
      animation: shimmer 2s infinite;
    }

    @keyframes shimmer {
      0% { left: -100%; }
      100% { left: 100%; }
    }

    @keyframes slideDown {
      from { transform: translateY(-100%); }
      to { transform: translateY(0); }
    }

    /* Navigation améliorée */
    .nav-menu {
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(10px);
      padding: 1rem 2rem;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: var(--shadow);
    }

    .nav-content {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    .nav-links a {
      text-decoration: none;
      color: var(--dark-color);
      font-weight: 500;
      transition: var(--transition);
      position: relative;
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -5px;
      left: 0;
      width: 0;
      height: 2px;
      background: var(--primary-color);
      transition: var(--transition);
    }

    .nav-links a:hover::after {
      width: 100%;
    }

    /* Animation d'arrière-plan améliorée */
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="20" cy="20" r="1" fill="%23ffffff" opacity="0.1"/><circle cx="80" cy="80" r="1" fill="%23ffffff" opacity="0.1"/><circle cx="40" cy="60" r="1" fill="%23ffffff" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
      z-index: -1;
      animation: float 20s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-20px); }
    }

    header {
      background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
      color: var(--white);
      text-align: center;
      padding: 4rem 2rem;
      position: relative;
      overflow: hidden;
      box-shadow: var(--shadow);
    }

    header::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="2" fill="%23ffffff" opacity="0.1"/></svg>');
      animation: rotate 30s linear infinite;
    }

    @keyframes rotate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    header h1 {
      font-size: clamp(2rem, 5vw, 3.5rem);
      font-weight: 700;
      margin-bottom: 1rem;
      position: relative;
      z-index: 1;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    }

    header p {
      font-size: clamp(1rem, 3vw, 1.4rem);
      font-weight: 300;
      position: relative;
      z-index: 1;
      opacity: 0.9;
    }

    /* Nouveauté: Badge de promotions */
    .promo-badge {
      position: absolute;
      top: 15px;
      right: 15px;
      background: linear-gradient(45deg, var(--warning-color), #ff9800);
      color: white;
      padding: 5px 10px;
      border-radius: 15px;
      font-size: 0.8rem;
      font-weight: 600;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }

    /* Nouveauté: Section statistiques */
    .stats-section {
      background: var(--white);
      padding: 3rem 2rem;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 2rem;
      max-width: 1200px;
      margin: -2rem auto 0;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
      position: relative;
      z-index: 10;
    }

    .stat-item {
      text-align: center;
      padding: 1.5rem;
      border-radius: 15px;
      background: linear-gradient(135deg, var(--light-color), #e8eaf6);
      transition: var(--transition);
    }

    .stat-item:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow);
    }

    .stat-number {
      font-size: 2.5rem;
      font-weight: 700;
      color: var(--primary-color);
      display: block;
    }

    .stat-label {
      color: #666;
      font-weight: 500;
      margin-top: 0.5rem;
    }

    .main-container {
      background: var(--white);
      margin: 2rem 1rem;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
      overflow: hidden;
      position: relative;
    }

    /* Nouveauté: Système de filtres */
    .filter-section {
      padding: 2rem;
      background: var(--light-color);
      border-bottom: 1px solid #e0e0e0;
    }

    .filter-buttons {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
    }

    .filter-btn {
      padding: 0.8rem 1.5rem;
      border: 2px solid var(--primary-color);
      background: transparent;
      color: var(--primary-color);
      border-radius: 25px;
      cursor: pointer;
      transition: var(--transition);
      font-weight: 500;
    }

    .filter-btn.active,
    .filter-btn:hover {
      background: var(--primary-color);
      color: white;
      transform: translateY(-2px);
    }

    .services {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      padding: 3rem 2rem;
      max-width: 1400px;
      margin: 0 auto;
    }

    .service {
      background: var(--white);
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
      overflow: hidden;
      transition: var(--transition);
      position: relative;
      transform: translateY(0);
    }

    .service::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 4px;
      background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
      transform: scaleX(0);
      transform-origin: left;
      transition: var(--transition);
    }

    .service:hover {
      transform: translateY(-10px) scale(1.02);
      box-shadow: var(--shadow-hover);
    }

    .service:hover::before {
      transform: scaleX(1);
    }

    .service img {
      width: 100%;
      height: 250px;
      object-fit: cover;
      display: block;
      transition: var(--transition);
    }

    .service:hover img {
      transform: scale(1.1);
    }

    .service-content {
      padding: 2rem;
      text-align: center;
      position: relative;
    }

    .service-content h3 {
      font-size: 1.5rem;
      font-weight: 600;
      color: var(--primary-color);
      margin-bottom: 1rem;
    }

    .service-content p {
      font-size: 1rem;
      color: #666;
      margin: 0.5rem 0;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .service-content p i {
      color: var(--secondary-color);
    }

    /* Nouveauté: Système de notation */
    .rating {
      display: flex;
      justify-content: center;
      gap: 0.2rem;
      margin: 1rem 0;
    }

    .star {
      color: #ffc107;
      font-size: 1.2rem;
    }

    .rating-text {
      margin-left: 0.5rem;
      color: #666;
      font-size: 0.9rem;
    }

    /* Nouveauté: Disponibilité en temps réel */
    .availability {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      margin: 1rem 0;
      padding: 0.5rem;
      border-radius: 25px;
      font-size: 0.9rem;
      font-weight: 500;
    }

    .availability.available {
      background: rgba(76, 175, 80, 0.1);
      color: var(--success-color);
    }

    .availability.busy {
      background: rgba(255, 167, 38, 0.1);
      color: var(--warning-color);
    }

    .availability.unavailable {
      background: rgba(244, 67, 54, 0.1);
      color: var(--danger-color);
    }

    .whatsapp-btn {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: linear-gradient(135deg, var(--success-color), #20b058);
      color: var(--white);
      padding: 1rem 2rem;
      border: none;
      border-radius: 50px;
      text-decoration: none;
      font-weight: 500;
      font-size: 1rem;
      margin-top: 1.5rem;
      transition: var(--transition);
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }

    .whatsapp-btn::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
      transition: var(--transition);
    }

    .whatsapp-btn:hover::before {
      left: 100%;
    }

    .whatsapp-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 20px rgba(37, 211, 102, 0.3);
    }

    /* Nouveauté: Section témoignages */
    .testimonials-section {
      background: linear-gradient(135deg, var(--light-color), #e8eaf6);
      padding: 4rem 2rem;
      margin: 2rem;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
    }

    .testimonials-title {
      text-align: center;
      font-size: 2rem;
      color: var(--dark-color);
      margin-bottom: 3rem;
    }

    .testimonials-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .testimonial {
      background: var(--white);
      padding: 2rem;
      border-radius: 15px;
      box-shadow: var(--shadow);
      text-align: center;
      transition: var(--transition);
    }

    .testimonial:hover {
      transform: translateY(-5px);
    }

    .testimonial-avatar {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      margin: 0 auto 1rem;
      background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.5rem;
      font-weight: bold;
    }

    .testimonial-text {
      font-style: italic;
      color: #666;
      margin-bottom: 1rem;
      line-height: 1.6;
    }

    .testimonial-author {
      font-weight: 600;
      color: var(--primary-color);
    }

    /* Nouveauté: Calendrier de disponibilité */
    .calendar-section {
      background: var(--white);
      margin: 2rem;
      padding: 3rem 2rem;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
    }

    .calendar-title {
      text-align: center;
      font-size: 1.8rem;
      color: var(--dark-color);
      margin-bottom: 2rem;
    }

    .calendar-grid {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 0.5rem;
      max-width: 600px;
      margin: 0 auto;
    }

    .calendar-day {
      aspect-ratio: 1;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 10px;
      cursor: pointer;
      transition: var(--transition);
      position: relative;
    }

    .calendar-day.available {
      background: rgba(76, 175, 80, 0.1);
      color: var(--success-color);
    }

    .calendar-day.busy {
      background: rgba(255, 167, 38, 0.1);
      color: var(--warning-color);
    }

    .calendar-day.unavailable {
      background: rgba(244, 67, 54, 0.1);
      color: var(--danger-color);
    }

    .calendar-day:hover {
      transform: scale(1.1);
    }

    /* Status Check Section améliorée */
    .status-section {
      background: linear-gradient(135deg, var(--light-color), #e8eaf6);
      padding: 3rem 2rem;
      margin: 2rem;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
      text-align: center;
    }

    .status-section h3 {
      font-size: 1.8rem;
      color: var(--dark-color);
      margin-bottom: 2rem;
      position: relative;
    }

    .status-section h3::after {
      content: '';
      position: absolute;
      bottom: -0.5rem;
      left: 50%;
      transform: translateX(-50%);
      width: 60px;
      height: 3px;
      background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
      border-radius: 2px;
    }

    .input-group {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      max-width: 400px;
      margin: 0 auto;
    }

    .input-group input {
      padding: 1rem 1.5rem;
      border: 2px solid #e0e0e0;
      border-radius: 50px;
      font-size: 1rem;
      transition: var(--transition);
      outline: none;
    }

    .input-group input:focus {
      border-color: var(--primary-color);
      box-shadow: 0 0 0 3px rgba(255, 107, 157, 0.1);
    }

    /* Nouveauté: Chat en ligne */
    .chat-widget {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 1000;
    }

    .chat-toggle {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
      color: white;
      border: none;
      cursor: pointer;
      font-size: 1.5rem;
      box-shadow: var(--shadow);
      transition: var(--transition);
      animation: bounce 2s infinite;
    }

    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
      40% { transform: translateY(-10px); }
      60% { transform: translateY(-5px); }
    }

    .chat-toggle:hover {
      transform: scale(1.1);
    }

    .chat-window {
      position: absolute;
      bottom: 70px;
      right: 0;
      width: 300px;
      height: 400px;
      background: var(--white);
      border-radius: 15px;
      box-shadow: var(--shadow-hover);
      display: none;
      flex-direction: column;
      overflow: hidden;
    }

    .chat-header {
      background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
      color: white;
      padding: 1rem;
      text-align: center;
      font-weight: 600;
    }

    .chat-messages {
      flex: 1;
      padding: 1rem;
      overflow-y: auto;
    }

    .chat-input {
      padding: 1rem;
      border-top: 1px solid #e0e0e0;
      display: flex;
      gap: 0.5rem;
    }

    .chat-input input {
      flex: 1;
      padding: 0.5rem;
      border: 1px solid #e0e0e0;
      border-radius: 20px;
      outline: none;
    }

    .chat-send {
      background: var(--primary-color);
      color: white;
      border: none;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      cursor: pointer;
    }

    .verify-btn {
      background: linear-gradient(135deg, var(--secondary-color), #3db8b0);
      color: var(--white);
      border: none;
      padding: 1rem 3rem;
      border-radius: 50px;
      font-size: 1.1rem;
      font-weight: 500;
      cursor: pointer;
      transition: var(--transition);
      box-shadow: var(--shadow);
    }

    .verify-btn:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-hover);
    }

    #statusResult {
      margin-top: 2rem;
      padding: 1rem;
      border-radius: var(--border-radius);
      font-weight: 500;
      min-height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* Form Styles améliorés */
    .form-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.8);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      padding: 1rem;
    }

    .form-content {
      background: var(--white);
      padding: 3rem;
      border-radius: var(--border-radius);
      width: 100%;
      max-width: 500px;
      max-height: 90vh;
      overflow-y: auto;
      position: relative;
      animation: slideIn 0.3s ease-out;
    }

    @keyframes slideIn {
      from {
        opacity: 0;
        transform: translateY(-50px) scale(0.9);
      }
      to {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .form-content h3 {
      text-align: center;
      color: var(--primary-color);
      font-size: 2rem;
      margin-bottom: 2rem;
    }

    .form-group {
      margin-bottom: 1.5rem;
    }

    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: 500;
      color: var(--dark-color);
    }

    .form-group input,
    .form-group select {
      width: 100%;
      padding: 1rem;
      border: 2px solid #e0e0e0;
      border-radius: 12px;
      font-size: 1rem;
      transition: var(--transition);
      outline: none;
    }

    .form-group input:focus,
    .form-group select:focus {
      border-color: var(--primary-color);
      box-shadow: 0 0 0 3px rgba(255, 107, 157, 0.1);
    }

    .form-buttons {
      display: flex;
      gap: 1rem;
      justify-content: center;
      margin-top: 2rem;
    }

    .btn {
      padding: 1rem 2rem;
      border: none;
      border-radius: 50px;
      font-size: 1rem;
      font-weight: 500;
      cursor: pointer;
      transition: var(--transition);
      min-width: 120px;
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--success-color), #20b058);
      color: var(--white);
    }

    .btn-secondary {
      background: linear-gradient(135deg, var(--danger-color), #e74c3c);
      color: var(--white);
    }

    .btn:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow);
    }

    /* Admin Dashboard amélioré */
    .admin-controls {
      text-align: center;
      padding: 2rem;
    }

    .admin-btn {
      background: linear-gradient(135deg, var(--dark-color), #57606f);
      color: var(--white);
      border: none;
      padding: 1rem 2rem;
      border-radius: 50px;
      font-size: 1rem;
      cursor: pointer;
      transition: var(--transition);
    }

    .admin-btn:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow);
    }

    .dashboard {
      background: var(--white);
      margin: 2rem;
      padding: 3rem 2rem;
      border-radius: var(--border-radius);
      box-shadow: var(--shadow);
      display: none;
    }

    .dashboard h2 {
      text-align: center;
      color: var(--dark-color);
      margin-bottom: 2rem;
      font-size: 2rem;
    }

    .booking-item {
      background: var(--light-color);
      padding: 2rem;
      margin: 1rem 0;
      border-radius: 15px;
      border-left: 4px solid var(--primary-color);
      transition: var(--transition);
    }

    .booking-item:hover {
      transform: translateX(5px);
      box-shadow: var(--shadow);
    }

    .booking-info {
      display: grid;
      grid-template-columns: 1fr auto;
      gap: 1rem;
      align-items: center;
    }

    .booking-details h4 {
      color: var(--primary-color);
      font-size: 1.2rem;
      margin-bottom: 0.5rem;
    }

    .booking-details p {
      color: #666;
      margin: 0.25rem 0;
    }

    .cancel-btn {
      background: var(--danger-color);
      color: var(--white);
      border: none;
      padding: 0.8rem 1.5rem;
      border-radius: 25px;
      cursor: pointer;
      transition: var(--transition);
    }

    .cancel-btn:hover {
      background: #e74c3c;
      transform: scale(1.05);
    }

    /* Footer amélioré */
    footer {
      background: var(--dark-color);
      color: var(--white);
      text-align: center;
      padding: 3rem 2rem;
      margin-top: 3rem;
    }

    .social-links {
      margin-top: 2rem;
      display: flex;
      justify-content: center;
      gap: 1rem;
    }

    .social-links a {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      width: 50px;
      height: 50px;
      background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
      color: var(--white);
      border-radius: 50%;
      text-decoration: none;
      font-size: 1.2rem;
      transition: var(--transition);
    }

    .social-links a:hover {
      transform: translateY(-3px) scale(1.1);
      box-shadow: var(--shadow);
    }

    /* Mobile Responsiveness */
    @media (max-width: 768px) {
      .notification-bar {
        font-size: 0.9rem;
        padding: 8px;
      }

      .nav-content {
        flex-direction: column;
        gap: 1rem;
      }

      .nav-links {
        gap: 1rem;
      }

      .stats-section {
        grid-template-columns: repeat(2, 1fr);
        margin: -1rem 0.5rem 0;
      }

      .main-container {
        margin: 1rem 0.5rem;
        border-radius: 15px;
      }

      .services {
        grid-template-columns: 1fr;
        gap: 1.5rem;
        padding: 2rem 1rem;
      }

      .service img {
        height: 200px;
      }

      .testimonials-section,
      .calendar-section,
      .status-section {
        margin: 1rem 0.5rem;
        padding: 2rem 1rem;
      }

      .testimonials-grid {
        grid-template-columns: 1fr;
      }

      .calendar-grid {
        grid-template-columns: repeat(7, 1fr);
        gap: 0.3rem;
      }

      .filter-buttons {
        gap: 0.5rem;
      }

      .filter-btn {
        padding: 0.6rem 1rem;
        font-size: 0.9rem;
      }

      .input-group {
        max-width: 100%;
      }

      .form-buttons {
        flex-direction: column;
      }

      .btn {
        width: 100%;
      }

      .booking-info {
        grid-template-columns: 1fr;
        text-align: center;
      }

      .dashboard {
        margin: 1rem 0.5rem;
        padding: 2rem 1rem;
      }

      .chat-window {
        width: 280px;
        height: 350px;
      }

      header {
        padding: 3rem 1rem;
      }

      .social-links a {
        width: 45px;
        height: 45px;
        font-size: 1.1rem;
      }
    }

    @media (max-width: 480px) {
      .stats-section {
        grid-template-columns: 1fr;
        gap: 1rem;
      }

      .services {
        padding: 1.5rem 0.8rem;
      }

      .service-content {
        padding: 1.5rem;
      }

      .form-content {
        padding: 2rem 1.5rem;
      }

      .status-section {
        padding: 1.5rem 1rem;
      }

      .dashboard {
        padding: 1.5rem 1rem;
      }

      .chat-window {
        width: 260px;
        height: 320px;
      }
    }

    /* Animations supplémentaires */
    .fade-in {
      animation: fadeIn 0.6s ease-out;
    }

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

    /* Loading spinner */
    .spinner {
      border: 3px solid #f3f3f3;
      border-top: 3px solid var(--primary-color);
      border-radius: 50%;
      width: 30px;
      height: 30px;
      animation: spin 1s linear infinite;
      margin: 0 auto;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* Nouveauté: Boutons d'action client */
    .client-actions {
      display: flex;
      gap: 0.5rem;
      margin-top: 1rem;
      justify-content: center;
      flex-wrap: wrap;
    }

    .client-btn {
      padding: 0.6rem 1.2rem;
      border: none;
      border-radius: 25px;
      font-size: 0.9rem;
      font-weight: 500;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .client-btn.cancel {
      background: linear-gradient(135deg, var(--danger-color), #e74c3c);
      color: white;
    }

    .client-btn.modify {
      background: linear-gradient(135deg, var(--warning-color), #ff9800);
      color: white;
    }

    .client-btn.whatsapp {
      background: linear-gradient(135deg, var(--success-color), #20b058);
      color: white;
    }

    .client-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    }

    .client-btn:disabled {
      opacity: 0.6;
      cursor: not-allowed;
      transform: none !important;
    }

    /* Modal de confirmation */
    .confirm-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.8);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1001;
    }

    .confirm-content {
      background: var(--white);
      padding: 2rem;
      border-radius: var(--border-radius);
      max-width: 400px;
      width: 90%;
      text-align: center;
      animation: slideIn 0.3s ease-out;
    }

    .confirm-content h4 {
      color: var(--danger-color);
      margin-bottom: 1rem;
      font-size: 1.3rem;
    }

    .confirm-content p {
      color: #666;
      margin-bottom: 2rem;
      line-height: 1.5;
    }

    .confirm-buttons {
      display: flex;
      gap: 1rem;
      justify-content: center;
    }

    /* Nouveauté: Politique d'annulation */
    .cancellation-policy {
      background: rgba(255, 193, 7, 0.1);
      border: 1px solid #ffc107;
      border-radius: 10px;
      padding: 1rem;
      margin: 1rem 0;
      font-size: 0.9rem;
      color: #856404;
    }

    .policy-title {
      font-weight: 600;
      margin-bottom: 0.5rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }
    .theme-toggle {
      position: fixed;
      top: 20px;
      right: 20px;
      background: var(--white);
      border: 2px solid var(--primary-color);
      border-radius: 50%;
      width: 50px;
      height: 50px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      color: var(--primary-color);
      transition: var(--transition);
      z-index: 1000;
      box-shadow: var(--shadow);
    }

    .theme-toggle:hover {
      transform: scale(1.1);
    }

    /* Toast notifications */
    .toast {
      position: fixed;
      top: 20px;
      right: 20px;
      padding: 1rem 2rem;
      border-radius: 25px;
      color: white;
      font-weight: 500;
      z-index: 10000;
      animation: slideInRight 0.3s ease-out;
      box-shadow: var(--shadow);
      max-width: 350px;
    }

    .toast.success { background: var(--success-color); }
    .toast.error { background: var(--danger-color); }
    .toast.warning { background: var(--warning-color); }
    .toast.info { background: var(--info-color); }

    @keyframes slideInRight {
      from { transform: translateX(100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }

    @keyframes slideOutRight {
      from { transform: translateX(0); opacity: 1; }
      to { transform: translateX(100%); opacity: 0; }
    }

    /* Nouveauté: Progress bar pour les réservations */
    .booking-progress {
      width: 100%;
      height: 6px;
      background: #e0e0e0;
      border-radius: 3px;
      overflow: hidden;
      margin: 1rem 0;
    }

    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--success-color), var(--secondary-color));
      border-radius: 3px;
      transition: width 0.3s ease;
      animation: shimmer 2s infinite;
    }

    /* Nouveauté: Weather widget */
    .weather-widget {
      background: linear-gradient(135deg, #87CEEB, #4682B4);
      color: white;
      padding: 1rem;
      border-radius: 15px;
      text-align: center;
      margin: 1rem 0;
      box-shadow: var(--shadow);
    }

    .weather-icon {
      font-size: 2rem;
      margin-bottom: 0.5rem;
    }

    .weather-temp {
      font-size: 1.5rem;
      font-weight: bold;
    }

    .weather-desc {
      font-size: 0.9rem;
      opacity: 0.9;
    }
  </style>
</head>
<body>
  <!-- Nouveauté: Barre de notification -->
  <div class="notification-bar">
    <i class="fas fa-gift"></i> 
    Promotion spéciale : -20% sur tous les services jusqu'au 31 août ! 
    <i class="fas fa-sparkles"></i>
  </div>

  <!-- Nouveauté: Toggle thème -->
  <button class="theme-toggle" onclick="toggleTheme()">
    <i class="fas fa-moon" id="theme-icon"></i>
  </button>

  <!-- Nouveauté: Navigation améliorée -->
  <nav class="nav-menu">
    <div class="nav-content">
      <div class="logo">
        <i class="fas fa-sparkles"></i> ShopExpress
      </div>
      <ul class="nav-links">
        <li><a href="#services" onclick="showSection('services')">Services</a></li>
        <li><a href="#testimonials" onclick="showSection('testimonials')">Avis</a></li>
        <li><a href="#calendar" onclick="showSection('calendar')">Disponibilités</a></li>
        <li><a href="#contact" onclick="showSection('contact')">Contact</a></li>
      </ul>
    </div>
  </nav>

  <header>
    <h1><i class="fas fa-sparkles"></i> ShopExpress Beauté INNOVA</h1>
    <p>Réservez votre look en un clic ✨</p>
  </header>

  <!-- Nouveauté: Section statistiques -->
  <section class="stats-section">
    <div class="stat-item">
      <span class="stat-number" id="clientsCount">250+</span>
      <div class="stat-label">Clients satisfaits</div>
    </div>
    <div class="stat-item">
      <span class="stat-number" id="servicesCount">500+</span>
      <div class="stat-label">Services réalisés</div>
    </div>
    <div class="stat-item">
      <span class="stat-number">4.9</span>
      <div class="stat-label">Note moyenne</div>
    </div>
    <div class="stat-item">
      <span class="stat-number">24h</span>
      <div class="stat-label">Réponse rapide</div>
    </div>
  </section>

  <div class="main-container">
    <!-- Nouveauté: Section de filtres -->
    <section class="filter-section">
      <div class="filter-buttons">
        <button class="filter-btn active" onclick="filterServices('tous')">Tous les services</button>
        <button class="filter-btn" onclick="filterServices('coiffure')">Coiffure</button>
        <button class="filter-btn" onclick="filterServices('maquillage')">Maquillage</button>
        <button class="filter-btn" onclick="filterServices('soins')">Soins</button>
      </div>
    </section>

    <section class="services" id="services">
      <div class="service fade-in" data-category="coiffure">
        <div class="promo-badge">-20%</div>
        <img src="https://i.postimg.cc/02V0vj1q/Screenshot-20250703-215049.jpg" alt="Nattes africaines">
        <div class="service-content">
          <h3><i class="fas fa-cut"></i> Nattes africaines</h3>
          <div class="rating">
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <span class="rating-text">(128 avis)</span>
          </div>
          <p><i class="fas fa-euro-sign"></i> Prix : <span class="old-price" style="text-decoration: line-through; opacity: 0.6;">5 000</span> 4 000 FCFA</p>
          <p><i class="fas fa-clock"></i> Durée : ~1h30</p>
          <div class="availability available">
            <i class="fas fa-circle"></i> Disponible aujourd'hui
          </div>
          <button class="whatsapp-btn">
            <i class="fab fa-whatsapp"></i>
            Réserver
          </button>
        </div>
      </div>

      <div class="service fade-in" data-category="maquillage">
        <img src="https://i.postimg.cc/nh5KsWLR/Screenshot-20250703-215157.jpg" alt="Maquillage professionnel">
        <div class="service-content">
          <h3><i class="fas fa-paint-brush"></i> Maquillage professionnel</h3>
          <div class="rating">
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <span class="rating-text">(95 avis)</span>
          </div>
          <p><i class="fas fa-euro-sign"></i> Prix : 7 000 FCFA</p>
          <p><i class="fas fa-clock"></i> Durée : ~45 min</p>
          <div class="availability busy">
            <i class="fas fa-circle"></i> Peu de créneaux
          </div>
          <button class="whatsapp-btn">
            <i class="fab fa-whatsapp"></i>
            Réserver
          </button>
        </div>
      </div>

      <div class="service fade-in" data-category="coiffure">
        <img src="https://i.postimg.cc/tJtDWNc1/Screenshot-20250703-215113-2.jpg" alt="Pose de perruque">
        <div class="service-content">
          <h3><i class="fas fa-user-crown"></i> Pose de perruque</h3>
          <div class="rating">
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="far fa-star star"></i>
            <span class="rating-text">(73 avis)</span>
          </div>
          <p><i class="fas fa-euro-sign"></i> Prix : 5 500 FCFA</p>
          <p><i class="fas fa-clock"></i> Durée : ~1h</p>
          <div class="availability available">
            <i class="fas fa-circle"></i> Disponible
          </div>
          <button class="whatsapp-btn">
            <i class="fab fa-whatsapp"></i>
            Réserver
          </button>
        </div>
      </div>

      <!-- Nouveaux services ajoutés -->
      <div class="service fade-in" data-category="soins">
        <img src="https://via.placeholder.com/400x250/FF69B4/FFFFFF?text=Soin+Visage" alt="Soin du visage">
        <div class="service-content">
          <h3><i class="fas fa-spa"></i> Soin du visage</h3>
          <div class="rating">
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <span class="rating-text">(156 avis)</span>
          </div>
          <p><i class="fas fa-euro-sign"></i> Prix : 8 500 FCFA</p>
          <p><i class="fas fa-clock"></i> Durée : ~1h15</p>
          <div class="availability available">
            <i class="fas fa-circle"></i> Disponible
          </div>
          <button class="whatsapp-btn">
            <i class="fab fa-whatsapp"></i>
            Réserver
          </button>
        </div>
      </div>

      <div class="service fade-in" data-category="coiffure">
        <div class="promo-badge">Nouveau!</div>
        <img src="https://via.placeholder.com/400x250/4ECDC4/FFFFFF?text=Coiffure+Mariée" alt="Coiffure de mariée">
        <div class="service-content">
          <h3><i class="fas fa-crown"></i> Coiffure de mariée</h3>
          <div class="rating">
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <span class="rating-text">(42 avis)</span>
          </div>
          <p><i class="fas fa-euro-sign"></i> Prix : 15 000 FCFA</p>
          <p><i class="fas fa-clock"></i> Durée : ~2h30</p>
          <div class="availability busy">
            <i class="fas fa-circle"></i> Sur réservation
          </div>
          <button class="whatsapp-btn">
            <i class="fab fa-whatsapp"></i>
            Réserver
          </button>
        </div>
      </div>

      <div class="service fade-in" data-category="soins">
        <img src="https://via.placeholder.com/400x250/FFE66D/333333?text=Manucure+Pédicure" alt="Manucure Pédicure">
        <div class="service-content">
          <h3><i class="fas fa-hand-sparkles"></i> Manucure & Pédicure</h3>
          <div class="rating">
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="fas fa-star star"></i>
            <i class="far fa-star star"></i>
            <span class="rating-text">(89 avis)</span>
          </div>
          <p><i class="fas fa-euro-sign"></i> Prix : 6 500 FCFA</p>
          <p><i class="fas fa-clock"></i> Durée : ~1h45</p>
          <div class="availability available">
            <i class="fas fa-circle"></i> Disponible
          </div>
          <button class="whatsapp-btn">
            <i class="fab fa-whatsapp"></i>
            Réserver
          </button>
        </div>
      </div>
    </section>

    <!-- Nouveauté: Section météo -->
    <div class="weather-widget" id="weather">
      <div class="weather-icon">
        <i class="fas fa-sun"></i>
      </div>
      <div class="weather-temp">28°C</div>
      <div class="weather-desc">Parfait pour une sortie beauté!</div>
    </div>

    <div class="status-section">
      <h3><i class="fas fa-search"></i> Gérer vos réservations</h3>
      <div class="input-group">
        <input type="number" id="checkNumber" placeholder="Entrez votre numéro WhatsApp" required>
        <button onclick="checkStatus()" class="verify-btn">
          <i class="fas fa-check-circle"></i> Vérifier
        </button>
      </div>
      <div id="statusResult"></div>
    </div>

    <div class="admin-controls">
      <button onclick="showDashboard()" class="admin-btn">
        <i class="fas fa-cogs"></i> Tableau de bord (Admin)
      </button>
    </div>
  </div>

  <!-- Nouveauté: Section témoignages -->
  <section class="testimonials-section" id="testimonials">
    <h2 class="testimonials-title">
      <i class="fas fa-quote-left"></i> Ce que disent nos clientes
    </h2>
    <div class="testimonials-grid">
      <div class="testimonial">
        <div class="testimonial-avatar">M</div>
        <div class="testimonial-text">
          "Service exceptionnel! Ma coiffure de mariage était absolument parfaite. L'équipe est très professionnelle et à l'écoute."
        </div>
        <div class="testimonial-author">- Marie K.</div>
      </div>
      <div class="testimonial">
        <div class="testimonial-avatar">S</div>
        <div class="testimonial-text">
          "Le maquillage était magnifique et a tenu toute la journée. Je recommande vivement ShopExpress Beauté!"
        </div>
        <div class="testimonial-author">- Sarah D.</div>
      </div>
      <div class="testimonial">
        <div class="testimonial-avatar">A</div>
        <div class="testimonial-text">
          "Toujours satisfaite de mes nattes! Un travail soigné et un accueil chaleureux. Mon salon de beauté préféré."
        </div>
        <div class="testimonial-author">- Aminata B.</div>
      </div>
    </div>
  </section>

  <!-- Nouveauté: Calendrier de disponibilité -->
  <section class="calendar-section" id="calendar">
    <h2 class="calendar-title">
      <i class="fas fa-calendar-alt"></i> Disponibilités de la semaine
    </h2>
    <div class="calendar-grid" id="calendarGrid">
      <!-- Généré dynamiquement par JavaScript -->
    </div>
    <div style="margin-top: 2rem; text-align: center;">
      <div style="display: inline-flex; gap: 2rem; flex-wrap: wrap;">
        <div><i class="fas fa-circle" style="color: var(--success-color);"></i> Disponible</div>
        <div><i class="fas fa-circle" style="color: var(--warning-color);"></i> Peu de créneaux</div>
        <div><i class="fas fa-circle" style="color: var(--danger-color);"></i> Complet</div>
      </div>
    </div>
  </section>

  <!-- Nouveauté: Widget de chat -->
  <div class="chat-widget">
    <button class="chat-toggle" onclick="toggleChat()">
      <i class="fas fa-comments"></i>
    </button>
    <div class="chat-window" id="chatWindow">
      <div class="chat-header">
        <i class="fas fa-headset"></i> Assistance en ligne
      </div>
      <div class="chat-messages" id="chatMessages">
        <div style="padding: 1rem; background: #f0f0f0; border-radius: 10px; margin-bottom: 1rem;">
          Bonjour! Comment puis-je vous aider aujourd'hui? 😊
        </div>
      </div>
      <div class="chat-input">
        <input type="text" id="chatInput" placeholder="Tapez votre message...">
        <button class="chat-send" onclick="sendMessage()">
          <i class="fas fa-paper-plane"></i>
        </button>
      </div>
    </div>
  </div>

  <!-- Formulaire de réservation (Modal amélioré) -->
  <div id="formulaire" class="form-container">
    <div class="form-content">
      <h3><i class="fas fa-calendar-plus"></i> Réservation en ligne</h3>
      <div class="booking-progress">
        <div class="progress-fill" style="width: 0%" id="bookingProgress"></div>
      </div>
      <form id="formule">
        <div class="form-group">
          <label><i class="fas fa-concierge-bell"></i> Service sélectionné :</label>
          <input type="text" id="service" readonly>
        </div>

        <div class="form-group">
          <label><i class="fas fa-calendar-day"></i> Jour de rendez-vous :</label>
          <input type="date" id="date" required>
        </div>

        <div class="form-group">
          <label><i class="fas fa-clock"></i> Heure de rendez-vous :</label>
          <select id="time" required>
            <option value="">Choisir une heure</option>
            <option value="08:00">08:00</option>
            <option value="09:00">09:00</option>
            <option value="10:00">10:00</option>
            <option value="11:00">11:00</option>
            <option value="12:00">12:00</option>
            <option value="13:00">13:00</option>
            <option value="14:00">14:00</option>
            <option value="15:00">15:00</option>
            <option value="16:00">16:00</option>
            <option value="17:00">17:00</option>
            <option value="18:00">18:00</option>
          </select>
        </div>

        <div class="form-group">
          <label><i class="fab fa-whatsapp"></i> Numéro WhatsApp :</label>
          <input type="number" id="numero" placeholder="Ex: 237670000000" required>
        </div>

        <!-- Nouveauté: Options supplémentaires -->
        <div class="form-group">
          <label><i class="fas fa-comment"></i> Commentaires particuliers :</label>
          <textarea id="comments" placeholder="Demandes spéciales, allergies, etc." rows="3" style="width: 100%; padding: 1rem; border: 2px solid #e0e0e0; border-radius: 12px; resize: vertical;"></textarea>
        </div>

        <div class="form-buttons">
          <button type="submit" class="btn btn-primary">
            <i class="fas fa-check"></i> Confirmer
          </button>
          <button type="button" onclick="fermer()" class="btn btn-secondary">
            <i class="fas fa-times"></i> Annuler
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- Dashboard Admin amélioré -->
  <div id="dashboard" class="dashboard">
    <h2><i class="fas fa-chart-line"></i> Tableau de bord - Gestion des réservations</h2>
    
    <!-- Nouveauté: Statistiques du dashboard -->
    <div class="dashboard-stats" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; margin-bottom: 2rem;">
      <div class="stat-item">
        <span class="stat-number" id="todayBookings">0</span>
        <div class="stat-label">Réservations aujourd'hui</div>
      </div>
      <div class="stat-item">
        <span class="stat-number" id="weekBookings">0</span>
        <div class="stat-label">Cette semaine</div>
      </div>
      <div class="stat-item">
        <span class="stat-number" id="monthRevenue">0</span>
        <div class="stat-label">Revenus du mois (FCFA)</div>
      </div>
    </div>

    <div style="text-align: center; margin-bottom: 2rem;">
      <button onclick="toggleDashboard()" class="btn btn-secondary">
        <i class="fas fa-arrow-left"></i> Retour
      </button>
      <button onclick="exportBookings()" class="btn" style="background: var(--info-color); color: white; margin-left: 1rem;">
        <i class="fas fa-download"></i> Exporter
      </button>
    </div>
    <div id="bookingList"></div>
  </div>

  <footer>
    <p>© 2025 ShopExpress Beauté INNOVA - Votre beauté, notre priorité</p>
    <div class="social-links">
      <a href="#" title="Instagram"><i class="fab fa-instagram"></i></a>
      <a href="#" title="Facebook"><i class="fab fa-facebook"></i></a>
      <a href="#" title="WhatsApp"><i class="fab fa-whatsapp"></i></a>
      <a href="#" title="TikTok"><i class="fab fa-tiktok"></i></a>
    </div>
  </footer>

  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.0.0/firebase-app.js";
    import { getFirestore, collection, addDoc, query, where, getDocs, onSnapshot, doc, updateDoc, orderBy } from "https://www.gstatic.com/firebasejs/10.0.0/firebase-firestore.js";

    const firebaseConfig = {
      apiKey: "AIzaSyA6rq0a6kG0bf7ChXEZyarDPWh4ougVofQ",
      authDomain: "gere-b2d31.firebaseapp.com",
      projectId: "gere-b2d31",
      storageBucket: "gere-b2d31.appspot.com",
      messagingSenderId: "166834348126",
      appId: "1:166834348126:web:cffe60797ac377fb4a14cf",
      measurementId: "G-YK8Y0Z7F2L"
    };

    const app = initializeApp(firebaseConfig);
    const db = getFirestore(app);

    // Variables globales
    let isDarkMode = false;
    let chatOpen = false;

    // Nouvelles fonctions

    // Gestion du thème sombre
    window.toggleTheme = function() {
      isDarkMode = !isDarkMode;
      const body = document.body;
      const icon = document.getElementById('theme-icon');
      
      if (isDarkMode) {
        body.style.filter = 'invert(1) hue-rotate(180deg)';
        icon.className = 'fas fa-sun';
        showToast('Mode sombre activé', 'info');
      } else {
        body.style.filter = 'none';
        icon.className = 'fas fa-moon';
        showToast('Mode clair activé', 'info');
      }
    };

    // Système de filtrage des services
    window.filterServices = function(category) {
      const services = document.querySelectorAll('.service');
      const buttons = document.querySelectorAll('.filter-btn');
      
      // Mise à jour des boutons
      buttons.forEach(btn => btn.classList.remove('active'));
      event.target.classList.add('active');
      
      // Filtrage des services
      services.forEach(service => {
        if (category === 'tous' || service.dataset.category === category) {
          service.style.display = 'block';
          service.style.animation = 'fadeIn 0.5s ease-out';
        } else {
          service.style.display = 'none';
        }
      });
      
      showToast(`Filtrage: ${category}`, 'info');
    };

    // Navigation fluide
    window.showSection = function(sectionId) {
      const element = document.getElementById(sectionId) || document.querySelector(`.${sectionId}-section`);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    };

    // Gestion du chat
    window.toggleChat = function() {
      const chatWindow = document.getElementById('chatWindow');
      chatOpen = !chatOpen;
      chatWindow.style.display = chatOpen ? 'flex' : 'none';
      
      if (chatOpen) {
        document.getElementById('chatInput').focus();
      }
    };

    window.sendMessage = function() {
      const input = document.getElementById('chatInput');
      const message = input.value.trim();
      
      if (message) {
        const chatMessages = document.getElementById('chatMessages');
        
        // Message utilisateur
        const userMsg = document.createElement('div');
        userMsg.style.cssText = `
          text-align: right; 
          margin-bottom: 1rem; 
          padding: 0.5rem 1rem; 
          background: var(--primary-color); 
          color: white; 
          border-radius: 15px 15px 5px 15px; 
          max-width: 80%; 
          margin-left: auto;
        `;
        userMsg.textContent = message;
        chatMessages.appendChild(userMsg);
        
        // Réponse automatique
        setTimeout(() => {
          const botMsg = document.createElement('div');
          botMsg.style.cssText = `
            text-align: left; 
            margin-bottom: 1rem; 
            padding: 0.5rem 1rem; 
            background: #f0f0f0; 
            border-radius: 15px 15px 15px 5px; 
            max-width: 80%;
          `;
          
          const responses = [
            "Merci pour votre message! Un conseiller vous répondra rapidement.",
            "Pour une réservation rapide, utilisez le bouton WhatsApp sur nos services.",
            "Avez-vous consulté nos disponibilités dans le calendrier?",
            "Notre équipe est disponible de 8h à 18h pour vous servir!"
          ];
          
          botMsg.textContent = responses[Math.floor(Math.random() * responses.length)];
          chatMessages.appendChild(botMsg);
          chatMessages.scrollTop = chatMessages.scrollHeight;
        }, 1000);
        
        input.value = '';
        chatMessages.scrollTop = chatMessages.scrollHeight;
      }
    };

    // Gestion des notifications toast
    window.showToast = function(message, type = 'success') {
      const toast = document.createElement('div');
      toast.className = `toast ${type}`;
      toast.textContent = message;
      document.body.appendChild(toast);

      setTimeout(() => {
        toast.style.animation = 'slideOutRight 0.3s ease-out';
        setTimeout(() => {
          if (document.body.contains(toast)) {
            document.body.removeChild(toast);
          }
        }, 300);
      }, 3000);
    };

    // Génération du calendrier
    function generateCalendar() {
      const calendarGrid = document.getElementById('calendarGrid');
      const days = ['Lun', 'Mar', 'Mer', 'Jeu', 'Ven', 'Sam', 'Dim'];
      const availabilityStates = ['available', 'busy', 'unavailable'];
      
      // En-têtes des jours
      days.forEach(day => {
        const header = document.createElement('div');
        header.style.cssText = 'font-weight: bold; text-align: center; padding: 0.5rem; color: var(--dark-color);';
        header.textContent = day;
        calendarGrid.appendChild(header);
      });
      
      // Jours du mois (exemple pour 7 jours)
      for (let i = 1; i <= 7; i++) {
        const dayElement = document.createElement('div');
        const randomState = availabilityStates[Math.floor(Math.random() * availabilityStates.length)];
        dayElement.className = `calendar-day ${randomState}`;
        dayElement.textContent = i + 30; // Exemple: fin juillet/début août
        dayElement.onclick = () => {
          showToast(`Jour ${i + 30}: ${randomState}`, 'info');
        };
        calendarGrid.appendChild(dayElement);
      }
    }

    // Mise à jour des statistiques
    function updateStats() {
      const stats = {
        clients: Math.floor(Math.random() * 50) + 250,
        services: Math.floor(Math.random() * 100) + 500,
        todayBookings: Math.floor(Math.random() * 10) + 1,
        weekBookings: Math.floor(Math.random() * 50) + 20,
        monthRevenue: Math.floor(Math.random() * 500000) + 2000000
      };
      
      document.getElementById('clientsCount').textContent = stats.clients + '+';
      document.getElementById('servicesCount').textContent = stats.services + '+';
      document.getElementById('todayBookings').textContent = stats.todayBookings;
      document.getElementById('weekBookings').textContent = stats.weekBookings;
      document.getElementById('monthRevenue').textContent = stats.monthRevenue.toLocaleString();
    }

    // Fonction d'export des réservations
    window.exportBookings = function() {
      showToast('Export en cours...', 'info');
      
      setTimeout(() => {
        const csvContent = "data:text/csv;charset=utf-8,Date,Service,Client,Statut\n" +
          "01/08/2025,Nattes africaines,237670000000,confirmé\n" +
          "02/08/2025,Maquillage,237671111111,confirmé\n" +
          "03/08/2025,Pose perruque,237672222222,annulé\n";
        
        const encodedUri = encodeURI(csvContent);
        const link = document.createElement("a");
        link.setAttribute("href", encodedUri);
        link.setAttribute("download", "reservations_" + new Date().toISOString().split('T')[0] + ".csv");
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        
        showToast('Export terminé!', 'success');
      }, 1500);
    };

    // Mise à jour de la barre de progression de réservation
    function updateBookingProgress() {
      const inputs = document.querySelectorAll('#formule input, #formule select');
      let filledInputs = 0;
      
      inputs.forEach(input => {
        if (input.value.trim() !== '') {
          filledInputs++;
        }
      });
      
      const progress = (filledInputs / inputs.length) * 100;
      document.getElementById('bookingProgress').style.width = progress + '%';
    }

    // Fonctions existantes améliorées
    window.fermer = function () {
      document.getElementById('formulaire').style.display = 'none';
      document.body.style.overflow = 'auto';
      document.getElementById('bookingProgress').style.width = '0%';
    };

    // Gestion des boutons de réservation
    document.querySelectorAll('.whatsapp-btn').forEach(btn => {
      btn.addEventListener("click", () => {
        const titre = btn.parentElement.querySelector("h3").textContent;
        document.getElementById('service').value = titre.replace(/.*\s/, '');
        document.getElementById('formulaire').style.display = 'flex';
        document.body.style.overflow = 'hidden';
        
        // Animation d'entrée
        setTimeout(() => {
          document.querySelector('.form-content').style.animation = 'slideIn 0.3s ease-out';
        }, 10);
      });
    });

    // Fermer le modal en cliquant à l'extérieur
    document.getElementById('formulaire').addEventListener('click', (e) => {
      if (e.target.id === 'formulaire') {
        fermer();
      }
    });

    // Mise à jour de la barre de progression en temps réel
    document.querySelectorAll('#formule input, #formule select').forEach(input => {
      input.addEventListener('input', updateBookingProgress);
    });

    // Soumission du formulaire améliorée
    document.getElementById('formule').addEventListener('submit', async (e) => {
      e.preventDefault();
      
      const submitBtn = e.target.querySelector('button[type="submit"]');
      const originalText = submitBtn.innerHTML;
      submitBtn.innerHTML = '<div class="spinner"></div>';
      submitBtn.disabled = true;

      const service = document.getElementById('service').value;
      const date = document.getElementById('date').value;
      const heure = document.getElementById('time').value;
      const numero = document.getElementById('numero').value;
      const comments = document.getElementById('comments').value;

      if (!service || !date || !heure || !numero) {
        showToast("Veuillez remplir tous les champs obligatoires.", 'error');
        submitBtn.innerHTML = originalText;
        submitBtn.disabled = false;
        return;
      }

      const form = {
        service,
        date,
        heure,
        numero,
        comments,
        status: 'confirmé',
        createdAt: new Date().toISOString()
      };

      try {
        await addDoc(collection(db, "bookings"), form);
        showToast(`✅ Réservation confirmée pour ${form.service} le ${form.date} à ${form.heure}`, 'success');
        fermer();
        document.getElementById('formule').reset();
        updateStats(); // Mise à jour des stats
      } catch (error) {
        console.error("❌ Erreur Firebase :", error);
        showToast("Erreur lors de la réservation!", 'error');
      } finally {
        submitBtn.innerHTML = originalText;
        submitBtn.disabled = false;
      }
    });

    // Vérification du statut en temps réel (améliorée)
    document.addEventListener("DOMContentLoaded", () => {
      const unsubscribe = {};

      document.getElementById('checkNumber').addEventListener('input', async (e) => {
        const phone = e.target.value;
        if (unsubscribe[phone]) unsubscribe[phone]();
        
        if (phone) {
          const q = query(collection(db, 'bookings'), where('numero', '==', phone));
          unsubscribe[phone] = onSnapshot(q, (snapshot) => {
            snapshot.docChanges().forEach((change) => {
              if (change.type === 'modified') {
                const data = change.doc.data();
                if (data.status === 'annulé') {
                  showToast(`❌ Votre réservation pour ${data.service} a été annulée.`, 'error');
                  document.getElementById('statusResult').innerHTML = `
                    <div style="background: #ffebee; color: #c62828; border: 1px solid #ffcdd2; padding: 1rem; border-radius: 10px;">
                      <i class="fas fa-times-circle"></i> <strong>Statut : ${data.status}</strong>
                    </div>`;
                }
              }
            });
          });
        } else {
          document.getElementById('statusResult').innerHTML = '';
        }
      });

      window.checkStatus = async function () {
        const phone = document.getElementById('checkNumber').value;
        const statusResult = document.getElementById('statusResult');
        
        if (!phone) {
          showToast('Veuillez entrer votre numéro WhatsApp', 'warning');
          return;
        }

        statusResult.innerHTML = '<div class="spinner"></div>';

        try {
          const q = query(collection(db, 'bookings'), where('numero', '==', phone));
          const snapshot = await getDocs(q);
          
          if (!snapshot.empty) {
            let resultHTML = '';
            const bookings = [];
            
            // Collecter toutes les réservations et les trier
            snapshot.forEach((docSnap) => {
              const data = docSnap.data();
              bookings.push({ id: docSnap.id, ...data });
            });
            
            // Trier par date de création (plus récent en premier)
            bookings.sort((a, b) => new Date(b.createdAt || 0) - new Date(a.createdAt || 0));
            
            bookings.forEach((data) => {
              const docId = data.id;
              const statusColor = data.status === 'confirmé' ? '#e8f5e8' : '#ffebee';
              const textColor = data.status === 'confirmé' ? '#2e7d32' : '#c62828';
              const icon = data.status === 'confirmé' ? 'check-circle' : 'times-circle';
              
              // Calculer si l'annulation est possible (24h avant le RDV)
              let canCancel = false;
              let canModify = false;
              
              try {
                if (data.date && data.heure && data.status === 'confirmé') {
                  const bookingDate = new Date(data.date + 'T' + data.heure);
                  const now = new Date();
                  const timeDiff = bookingDate.getTime() - now.getTime();
                  const hoursDiff = timeDiff / (1000 * 3600);
                  canCancel = hoursDiff > 24;
                  canModify = hoursDiff > 12;
                }
              } catch (error) {
                console.log('Erreur calcul date:', error);
                // En cas d'erreur, permettre le contact
              }
              
              resultHTML += `
                <div style="background: ${statusColor}; color: ${textColor}; border: 1px solid ${data.status === 'confirmé' ? '#c8e6c9' : '#ffcdd2'}; padding: 1.5rem; border-radius: 15px; margin-bottom: 1rem; box-shadow: var(--shadow);">
                  <div style="text-align: center;">
                    <i class="fas fa-${icon}" style="font-size: 1.5rem; margin-bottom: 0.5rem;"></i>
                    <h4 style="margin-bottom: 1rem; color: ${textColor};">${data.service || 'Service non spécifié'}</h4>
                  </div>
                  
                  <div style="display: grid; gap: 0.5rem; margin-bottom: 1rem; text-align: left;">
                    <p><i class="fas fa-calendar-day"></i> <strong>Date:</strong> ${data.date || 'Non spécifiée'} à ${data.heure || 'Non spécifiée'}</p>
                    <p><i class="fas fa-info-circle"></i> <strong>Statut:</strong> ${data.status || 'confirmé'}</p>
                    ${data.comments ? `<p><i class="fas fa-comment"></i> <strong>Commentaires:</strong> ${data.comments}</p>` : ''}
                    <p><i class="fas fa-clock"></i> <strong>Réservé le:</strong> ${data.createdAt ? new Date(data.createdAt).toLocaleDateString('fr-FR') : 'Date inconnue'}</p>
                  </div>

                  ${data.status === 'confirmé' || !data.status ? `
                    <div class="client-actions">
                      ${canCancel ? `
                        <button class="client-btn cancel" onclick="requestCancellation('${docId}', '${data.service || 'ce service'}', '${data.date || ''}', '${data.heure || ''}')">
                          <i class="fas fa-times"></i> Annuler
                        </button>
                      ` : `
                        <button class="client-btn cancel" disabled title="Annulation possible jusqu'à 24h avant le RDV">
                          <i class="fas fa-lock"></i> Trop tard
                        </button>
                      `}
                      
                      ${canModify ? `
                        <button class="client-btn modify" onclick="requestModification('${docId}', '${phone}')">
                          <i class="fas fa-edit"></i> Modifier
                        </button>
                      ` : ''}
                      
                      <button class="client-btn whatsapp" onclick="contactSalon('${phone}', '${data.service || ''}', '${data.date || ''}')">
                        <i class="fab fa-whatsapp"></i> Contacter
                      </button>
                    </div>
                    
                    ${canCancel ? `
                      <div class="cancellation-policy">
                        <div class="policy-title">
                          <i class="fas fa-exclamation-triangle"></i> Politique d'annulation
                        </div>
                        <p>• Annulation gratuite jusqu'à 24h avant le RDV<br>
                        • Modification possible jusqu'à 12h avant<br>
                        • Annulation tardive: 50% du montant retenu</p>
                      </div>
                    ` : ''}
                  ` : (data.status && data.status.includes('annulé')) ? `
                    <div style="text-align: center; margin-top: 1rem;">
                      <p style="font-weight: 600;"><i class="fas fa-ban"></i> Réservation annulée</p>
                      <button class="client-btn whatsapp" onclick="contactSalon('${phone}', '${data.service || ''}', '${data.date || ''}')">
                        <i class="fab fa-whatsapp"></i> Nouvelle réservation
                      </button>
                    </div>
                  ` : ''}
                </div>`;
            });
            statusResult.innerHTML = resultHTML;
          } else {
            statusResult.innerHTML = `
              <div style="background: #fff3e0; color: #ef6c00; border: 1px solid #ffe0b2; padding: 1rem; border-radius: 10px;">
                <i class="fas fa-exclamation-triangle"></i>
                Aucune réservation trouvée avec ce numéro.
              </div>`;
          }
        } catch (error) {
          console.error('Erreur lors de la vérification:', error);
          statusResult.innerHTML = `
            <div style="background: #ffebee; color: #c62828; border: 1px solid #ffcdd2; padding: 1.5rem; border-radius: 15px; text-align: center;">
              <i class="fas fa-exclamation-circle" style="font-size: 2rem; margin-bottom: 1rem;"></i>
              <h4>Erreur de connexion</h4>
              <p>Vérifiez votre connexion internet et réessayez.</p>
              <button onclick="checkStatus()" style="margin-top: 1rem; padding: 0.5rem 1rem; background: var(--primary-color); color: white; border: none; border-radius: 20px; cursor: pointer;">
                <i class="fas fa-refresh"></i> Réessayer
              </button>
            </div>`;
          showToast('❌ Erreur lors de la vérification. Vérifiez votre connexion.', 'error');
        }
      };
    });

    // Gestion de l'admin (améliorée)
    const ADMIN_PASSWORD = "admin123";
    
    window.showDashboard = async function () {
      const password = prompt("Entrez le mot de passe admin :");
      if (password === ADMIN_PASSWORD) {
        document.getElementById('dashboard').style.display = 'block';
        document.getElementById('services').style.display = 'none';
        document.querySelector('.status-section').style.display = 'none';
        document.querySelector('.admin-controls').style.display = 'none';
        document.querySelector('.testimonials-section').style.display = 'none';
        document.querySelector('.calendar-section').style.display = 'none';
        await loadBookings();
        updateStats();
        showToast('Dashboard admin ouvert', 'success');
      } else if (password !== null) {
        showToast("❌ Mot de passe incorrect!", 'error');
      }
    };

    window.toggleDashboard = function () {
      document.getElementById('dashboard').style.display = 'none';
      document.getElementById('services').style.display = 'grid';
      document.querySelector('.status-section').style.display = 'block';
      document.querySelector('.admin-controls').style.display = 'block';
      document.querySelector('.testimonials-section').style.display = 'block';
      document.querySelector('.calendar-section').style.display = 'block';
    };

    async function loadBookings() {
      const bookingList = document.getElementById('bookingList');
      bookingList.innerHTML = '<div class="spinner" style="margin: 2rem auto;"></div>';

      try {
        const q = query(collection(db, "bookings"));
        const querySnapshot = await getDocs(q);
        bookingList.innerHTML = '';

        if (querySnapshot.empty) {
          bookingList.innerHTML = `
            <div style="text-align: center; padding: 2rem; color: #666;">
              <i class="fas fa-inbox" style="font-size: 3rem; margin-bottom: 1rem; opacity: 0.5;"></i>
              <p>Aucune réservation pour le moment</p>
            </div>`;
          return;
        }

        // Collecter et trier les réservations
        const bookings = [];
        querySnapshot.forEach((docSnap) => {
          const data = docSnap.data();
          bookings.push({ id: docSnap.id, ...data });
        });
        
        // Trier par date de création (plus récent en premier)
        bookings.sort((a, b) => new Date(b.createdAt || 0) - new Date(a.createdAt || 0));

        bookings.forEach((data) => {
          const statusColor = data.status === 'confirmé' || !data.status ? '#e8f5e8' : '#ffebee';
          const statusIcon = data.status === 'confirmé' || !data.status ? 'check-circle' : 'times-circle';
          
          const bookingItem = document.createElement("div");
          bookingItem.className = "booking-item";
          bookingItem.style.background = statusColor;
          
          bookingItem.innerHTML = `
            <div class="booking-info">
              <div class="booking-details">
                <h4><i class="fas fa-calendar"></i> ${data.service || 'Service non spécifié'}</h4>
                <p><i class="fas fa-calendar-day"></i> <strong>Date:</strong> ${data.date || 'Non spécifiée'} à ${data.heure || 'Non spécifiée'}</p>
                <p><i class="fab fa-whatsapp"></i> <strong>Contact:</strong> ${data.numero || 'Non spécifié'}</p>
                <p><i class="fas fa-${statusIcon}"></i> <strong>Statut:</strong> ${data.status || "confirmé"}</p>
                ${data.comments ? `<p><i class="fas fa-comment"></i> <strong>Commentaires:</strong> ${data.comments}</p>` : ''}
                ${data.cancelReason ? `<p><i class="fas fa-info-circle"></i> <strong>Raison:</strong> ${data.cancelReason}</p>` : ''}
                <p><i class="fas fa-clock"></i> <strong>Créé le:</strong> ${data.createdAt ? new Date(data.createdAt).toLocaleDateString('fr-FR') : 'Date inconnue'}</p>
                ${data.cancelledAt ? `<p><i class="fas fa-ban"></i> <strong>Annulé le:</strong> ${new Date(data.cancelledAt).toLocaleDateString('fr-FR')}</p>` : ''}
              </div>
              ${!data.status || data.status === 'confirmé' ? `
                <div style="display: flex; flex-direction: column; gap: 0.5rem;">
                  <button class="cancel-btn" onclick="cancelBooking('${data.id}', '${data.numero || ''}')">
                    <i class="fas fa-ban"></i> Annuler
                  </button>
                  <button class="btn" style="background: var(--info-color); color: white; padding: 0.5rem 1rem; border-radius: 20px;" onclick="contactClient('${data.numero || ''}')">
                    <i class="fas fa-phone"></i> Contacter
                  </button>
                </div>
              ` : `
                <div style="text-align: center;">
                  <span style="color: #c62828; font-weight: bold; display: block; margin-bottom: 0.5rem;">
                    <i class="fas fa-times-circle"></i> ${data.status}
                  </span>
                  ${data.status && data.status.includes('client') ? `
                    <span style="color: #666; font-size: 0.8rem;">
                      <i class="fas fa-user"></i> Annulation client
                    </span>
                  ` : ''}
                </div>
              `}
            </div>
          `;
          
          bookingList.appendChild(bookingItem);
        });
      } catch (error) {
        console.error('Erreur lors du chargement:', error);
        bookingList.innerHTML = `
          <div style="text-align: center; padding: 2rem; color: #c62828;">
            <i class="fas fa-exclamation-triangle" style="font-size: 2rem; margin-bottom: 1rem;"></i>
            <p>Erreur lors du chargement des réservations</p>
          </div>`;
      }
    }

    window.cancelBooking = async function (id, phone) {
      if (!confirm('Êtes-vous sûr de vouloir annuler cette réservation ?')) {
        return;
      }

      try {
        await updateDoc(doc(db, 'bookings', id), { 
          status: "annulé par salon",
          cancelledAt: new Date().toISOString(),
          cancelReason: "Annulation salon"
        });
        await loadBookings();
        showToast(`✅ Réservation annulée. Le client au ${phone} sera informé.`, 'success');
      } catch (error) {
        console.error('Erreur Firebase :', error);
        showToast("❌ Erreur lors de l'annulation!", 'error');
      }
    };

    // Nouvelle fonction: demande d'annulation par le client
    window.requestCancellation = function(bookingId, service, date, heure) {
      const modal = document.createElement('div');
      modal.className = 'confirm-modal';
      modal.innerHTML = `
        <div class="confirm-content">
          <h4><i class="fas fa-exclamation-triangle"></i> Confirmer l'annulation</h4>
          <p>Êtes-vous sûr de vouloir annuler votre réservation pour :</p>
          <p style="font-weight: 600; color: var(--primary-color);">${service}<br>Le ${date} à ${heure}</p>
          <p style="font-size: 0.9rem; color: #666;">Cette action est irréversible.</p>
          
          <div class="confirm-buttons">
            <button class="btn btn-secondary" onclick="closeCancelModal()">
              <i class="fas fa-arrow-left"></i> Retour
            </button>
            <button class="btn" style="background: var(--danger-color); color: white;" onclick="confirmCancellation('${bookingId}')">
              <i class="fas fa-check"></i> Confirmer l'annulation
            </button>
          </div>
        </div>
      `;
      
      document.body.appendChild(modal);
      modal.style.display = 'flex';
      document.body.style.overflow = 'hidden';
    };

    window.closeCancelModal = function() {
      const modal = document.querySelector('.confirm-modal');
      if (modal) {
        document.body.removeChild(modal);
        document.body.style.overflow = 'auto';
      }
    };

    window.confirmCancellation = async function(bookingId) {
      try {
        // Mettre à jour le statut de la réservation
        await updateDoc(doc(db, 'bookings', bookingId), { 
          status: "annulé par client",
          cancelledAt: new Date().toISOString(),
          cancelReason: "Demande client"
        });
        
        closeCancelModal();
        showToast('✅ Réservation annulée avec succès!', 'success');
        
        // Rafraîchir l'affichage
        setTimeout(() => {
          const phone = document.getElementById('checkNumber').value;
          if (phone) {
            checkStatus();
          }
        }, 1000);
        
      } catch (error) {
        console.error('Erreur lors de l\'annulation:', error);
        showToast('❌ Erreur lors de l\'annulation. Veuillez réessayer.', 'error');
      }
    };

    // Nouvelle fonction: demande de modification
    window.requestModification = function(bookingId, phone) {
      const message = encodeURIComponent(`Bonjour! Je souhaite modifier ma réservation (ID: ${bookingId}). Pouvez-vous m'aider?`);
      window.open(`https://wa.me/237696020536?text=${message}`, '_blank');
      showToast('Redirection vers WhatsApp pour modification...', 'info');
    };

    // Nouvelle fonction: contacter le salon
    window.contactSalon = function(clientPhone, service, date) {
      const message = encodeURIComponent(`Bonjour! Je vous contacte concernant ${service ? 'ma réservation pour ' + service + (date ? ' du ' + date : '') : 'une réservation'}. Mon numéro: ${clientPhone}`);
      window.open(`https://wa.me/237696020536?text=${message}`, '_blank');
      showToast('Redirection vers WhatsApp...', 'info');
    };
    window.contactClient = function(phone) {
      const message = encodeURIComponent("Bonjour! Concernant votre réservation chez ShopExpress Beauté INNOVA...");
      window.open(`https://wa.me/${phone}?text=${message}`, '_blank');
      showToast('Redirection vers WhatsApp...', 'info');
    };

    // Animation au scroll améliorée
    const observerOptions = {
      threshold: 0.1,
      rootMargin: '0px 0px -50px 0px'
    };

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.style.opacity = '1';
          entry.target.style.transform = 'translateY(0)';
        }
      });
    }, observerOptions);

    // Observer tous les services et sections
    document.querySelectorAll('.service, .testimonial, .stat-item').forEach(element => {
      element.style.opacity = '0';
      element.style.transform = 'translateY(30px)';
      element.style.transition = 'all 0.6s ease-out';
      observer.observe(element);
    });

    // Effet de parallaxe pour l'en-tête
    window.addEventListener('scroll', () => {
      const scrolled = window.pageYOffset;
      const parallax = document.querySelector('header');
      const speed = scrolled * 0.5;
      parallax.style.transform = `translateY(${speed}px)`;
    });

    // Validation du formulaire en temps réel
    const inputs = document.querySelectorAll('#formule input, #formule select');
    inputs.forEach(input => {
      input.addEventListener('input', function() {
        if (this.checkValidity()) {
          this.style.borderColor = '#4caf50';
        } else {
          this.style.borderColor = '#f44336';
        }
      });
    });

    // Gestion des touches du clavier
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') {
        fermer();
        if (chatOpen) {
          toggleChat();
        }
      }
      if (e.key === 'Enter' && chatOpen && document.activeElement.id === 'chatInput') {
        sendMessage();
      }
    });

    // Initialisation au chargement
    window.addEventListener('load', () => {
      // Animation des services au chargement
      const services = document.querySelectorAll('.service');
      services.forEach((service, index) => {
        setTimeout(() => {
          service.classList.add('fade-in');
        }, index * 200);
      });

      // Génération du calendrier
      generateCalendar();
      
      // Mise à jour des statistiques
      updateStats();
      
      // Mise à jour périodique des stats
      setInterval(updateStats, 30000); // Toutes les 30 secondes
      
      // Message de bienvenue
      setTimeout(() => {
        showToast('Bienvenue chez ShopExpress Beauté INNOVA! 💄✨', 'success');
      }, 1000);
    });

    // Gestion de la météo (simulation)
    function updateWeather() {
      const weatherWidget = document.getElementById('weather');
      const weather = [
        { icon: 'fas fa-sun', temp: '28°C', desc: 'Parfait pour une sortie beauté!' },
        { icon: 'fas fa-cloud-sun', temp: '26°C', desc: 'Temps idéal pour se faire belle!' },
        { icon: 'fas fa-cloud-rain', temp: '24°C', desc: 'Journée cocooning beauté!' }
      ];
      
      const current = weather[Math.floor(Math.random() * weather.length)];
      weatherWidget.innerHTML = `
        <div class="weather-icon">
          <i class="${current.icon}"></i>
        </div>
        <div class="weather-temp">${current.temp}</div>
        <div class="weather-desc">${current.desc}</div>
      `;
    }

    // Mise à jour de la météo
    updateWeather();
    setInterval(updateWeather, 300000); // Toutes les 5 minutes

    // Gestion des animations d'hover personnalisées
    document.querySelectorAll('.service').forEach(service => {
      service.addEventListener('mouseenter', function() {
        this.style.transform = 'translateY(-10px) scale(1.02)';
      });
      
      service.addEventListener('mouseleave', function() {
        this.style.transform = 'translateY(0) scale(1)';
      });
    });

    // Système de notification push (simulation)
    function simulateNotifications() {
      const notifications = [
        "Nouvelle réservation reçue!",
        "Rappel: RDV dans 30 minutes",
        "Client satisfait - 5 étoiles reçues!",
        "Promotion: -20% jusqu'à demain!"
      ];
      
      setInterval(() => {
        if (Math.random() > 0.7) { // 30% de chance
          const notification = notifications[Math.floor(Math.random() * notifications.length)];
          showToast(notification, 'info');
        }
      }, 60000); // Toutes les minutes
    }
    // Démarrer les notifications
    simulateNotifications();

    console.log("🎨 ShopExpress Beauté INNOVA - Version Pro chargée avec succès!");
  </script>
</body>
</html>
