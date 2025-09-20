<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="src/css/acceuil.css">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>
<link rel="stylesheet" href="src/css/acceuil.css">
<link rel="stylesheet" href="src/css/dahsbord.css">
<style>
    .titre {
        background: linear-gradient(135deg, #0f172a, #1e293b);
        padding: 15px 20px;
        position: fixed;
        width: 100%;
        z-index: 1000;
        box-shadow: 0 4px 20px rgba(15, 23, 42, 0.3);
        border-bottom: 1px solid rgba(59, 130, 246, 0.2);
    }

    .autre {
        display: flex;
        justify-content: space-between;
        align-items: center;
        max-width: 1200px;
        margin: 0 auto;
    }

    .menu-hamburger {
        display: none;
        flex-direction: column;
        cursor: pointer;
        padding: 8px;
        border-radius: 8px;
        background: rgba(59, 130, 246, 0.1);
        transition: all 0.3s ease;
    }

    .menu-hamburger div {
        width: 25px;
        height: 3px;
        background: #3b82f6;
        margin: 3px 0;
        transition: all 0.3s ease;
        border-radius: 2px;
    }

    .menu-hamburger.ouvert div:nth-child(1) {
        transform: rotate(45deg) translate(5px, 5px);
    }

    .menu-hamburger.ouvert div:nth-child(2) {
        opacity: 0;
    }

    .menu-hamburger.ouvert div:nth-child(3) {
        transform: rotate(-45deg) translate(7px, -6px);
    }

    .entete {
        color: #3b82f6 !important;
        font-size: 24px;
        font-weight: 700;
        margin: 0;
        display: flex;
        position: relative;
        left: 5%;
        align-items: center;
        gap: 10px;
    }

    .ceux {
        display: flex;
        gap: 20px;
        align-items: center;
        margin: auto;
        position: relative;
        left: 15%;
    }

    .marcher {
        background: transparent;
        border: 2px solid rgba(59, 130, 246, 0.3);
        color: #e2e8f0;
        padding: 10px 20px;
        border-radius: 25px;
        cursor: pointer;
        transition: all 0.3s ease;
        font-size: 14px;
        font-weight: 600;
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .marcher:hover {
        background: rgba(59, 130, 246, 0.1);
        border-color: #3b82f6;
        color: white;
        transform: translateY(-2px);
    }

    .categorie {
        display: flex;
        gap: 15px;
        align-items: center;
    }

    .notification {
        background: rgba(59, 130, 246, 0.1);
        border: 2px solid rgba(59, 130, 246, 0.3);
        color: #3b82f6;
        padding: 10px;
        border-radius: 50%;
        cursor: pointer;
        transition: all 0.3s ease;
        width: 45px;
        height: 45px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
   .notificatio{
 background: rgba(59, 130, 246, 0.1);
        border: 2px solid rgba(59, 130, 246, 0.3);
        color: #3b82f6;
        padding: 10px;
        border-radius: 50%;
        cursor: pointer;
        transition: all 0.3s ease;
        width: 50px;
        height: 45px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .notification:hover {
        background: rgba(59, 130, 246, 0.2);
        transform: scale(1.1);
    }
    .notificatio:hover {
        background: rgba(59, 130, 246, 0.2);
        transform: scale(1.1);
    }

    body {
        margin: 0;
        padding: 0;
    }

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    body {
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        background: linear-gradient(135deg, #0f172a, #1e293b, #334155);
        min-height: 100vh;
        padding: 20px;
        color: #e2e8f0;
    }

    .commande {
        position: relative;
        left: 9px;
        padding: 25px 30px;
        top: 100px;
        display: flex;
        align-items: center;
        background: linear-gradient(135deg, #1e293b, #334155, #475569);
        border-radius: 20px;
        box-shadow:
            0 10px 30px rgba(15, 23, 42, 0.3),
            0 1px 3px rgba(15, 23, 42, 0.2);
        border: 1px solid rgba(59, 130, 246, 0.2);
        backdrop-filter: blur(10px);
        margin-bottom: 30px;
    }

    .autre-coter {
        position: relative;
        right: -50%;
        display: flex;
        align-items: center;
        gap: 15px;
    }

    .logo {
        background: linear-gradient(135deg, #3b82f6, #2563eb, #1d4ed8);
        padding: 18px;
        border-radius: 15px;
        font-size: 30px;
        height: 60px;
        width: 60px;
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: bold;
        text-transform: uppercase;
        box-shadow:
            0 8px 25px rgba(59, 130, 246, 0.4),
            0 3px 8px rgba(59, 130, 246, 0.3);
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .logo:hover {
        transform: translateY(-2px) scale(1.02);
        box-shadow:
            0 12px 30px rgba(59, 130, 246, 0.5),
            0 5px 12px rgba(59, 130, 246, 0.4);
    }

    .nom {
        margin-left: 20px;
        font-size: 24px;
        font-weight: 700;
        color: #e2e8f0;
        background: linear-gradient(135deg, #e2e8f0, #cbd5e1);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        letter-spacing: 0.5px;
    }

    .autre-coter button:first-child {
        background: linear-gradient(135deg, #475569, #64748b);
        border: none;
        padding: 15px;
        border-radius: 12px;
        color: white;
        cursor: pointer;
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        box-shadow:
            0 4px 15px rgba(71, 85, 105, 0.3),
            0 2px 5px rgba(71, 85, 105, 0.2);
        position: relative;
        overflow: hidden;
    }

    .autre-coter button:first-child::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
        transition: left 0.5s;
    }

    .autre-coter button:first-child:hover::before {
        left: 100%;
    }

    .autre-coter button:first-child:hover {
        transform: translateY(-2px) scale(1.05);
        background: linear-gradient(135deg, #64748b, #475569);
        box-shadow:
            0 8px 25px rgba(100, 116, 139, 0.4),
            0 4px 10px rgba(100, 116, 139, 0.25);
    }

    .voir {
        background: linear-gradient(135deg, #3b82f6, #2563eb, #1d4ed8);
        border-radius: 15px;
        padding: 16px 28px;
        width: 240px;
        text-align: center;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-weight: 700;
        font-size: 16px;
        letter-spacing: 0.8px;
        border: none;
        color: white;
        cursor: pointer;
        box-shadow:
            0 8px 25px rgba(59, 130, 246, 0.4),
            0 4px 10px rgba(59, 130, 246, 0.25);
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        position: relative;
        overflow: hidden;
    }

    .voir::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
        transition: left 0.6s;
    }

    .voir:hover::before {
        left: 100%;
    }

    .notification-badge {
        position: absolute;
        top: 8px;
        right: 85%;
        background: linear-gradient(135deg, #ef4444, #dc2626);
        color: white;
        border-radius: 50%;
        padding: 4px 8px;
        font-size: 12px;
        font-weight: bold;
        min-width: 22px;
        height: 22px;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow:
            0 4px 15px rgba(239, 68, 68, 0.4),
            0 2px 5px rgba(239, 68, 68, 0.3);
        border: 2px solid white;
        animation: pulse-badge 2s infinite;
    }
    .notificatio-badge{
       position: absolute;
        top: 8px;
        right: 85%;
        background: linear-gradient(135deg, #ef4444, #dc2626);
        color: white;
        border-radius: 50%;
        padding: 4px 8px;
        font-size: 12px;
        font-weight: bold;
        min-width: 22px;
        height: 22px;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow:
            0 4px 15px rgba(239, 68, 68, 0.4),
            0 2px 5px rgba(239, 68, 68, 0.3);
        border: 2px solid white;
        animation: pulse-badge 2s infinite;
    }

    @keyframes pulse-badge {
        0% {
            transform: scale(1);
        }

        50% {
            transform: scale(1.1);
            box-shadow: 0 0 20px rgba(239, 68, 68, 0.6);
        }

        100% {
            transform: scale(1);
        }
    }

    .voir:hover {
        transform: translateY(-3px) scale(1.02);
        background: linear-gradient(135deg, #2563eb, #1d4ed8, #1e40af);
        box-shadow:
            0 12px 35px rgba(59, 130, 246, 0.5),
            0 6px 15px rgba(59, 130, 246, 0.3);
    }

    #notif {
        background: transparent !important;
        font-size: 22px;
        transition: all 0.3s ease;
    }

    .autre-coter button:first-child:hover #notif {
        animation: swing 0.6s ease-in-out;
    }

    @keyframes swing {

        0%,
        100% {
            transform: rotate(0deg);
        }

        25% {
            transform: rotate(-10deg);
        }

        75% {
            transform: rotate(10deg);
        }
    }

    .appercu {
        position: relative;
        top: 110px;
        background: linear-gradient(135deg, #1e293b, #334155, #475569);
        border-radius: 20px;
        padding: 30px;
        box-shadow:
            0 10px 30px rgba(15, 23, 42, 0.3),
            0 1px 3px rgba(15, 23, 42, 0.2);
        border: 1px solid rgba(59, 130, 246, 0.2);
        backdrop-filter: blur(10px);
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
        gap: 15px;
    }

    .verbas {
        display: flex;
        align-items: center;
        position: relative;
        top: 130px;
        padding-left: 30px;
        border-radius: 20px;
        color: white;
        background: linear-gradient(135deg, #3b82f6, #2563eb, #1d4ed8);
    }

    .premium {
        background-color: #f1f5f9;
        color: #1e293b;
        font-size: 17px;
        font-weight: bold;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
            Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        gap: 14px;
        padding: 10px;
        width: 200px;
        border-radius: 10px;
        box-shadow: 0px 4px 6px rgba(59, 130, 246, 0.3);
    }

    .premium:hover {
        transition: 1s ease-in-out;
        transform: translateY(-4px);
        transform: translate3d(-2px);
    }

    .cote {
        font-size: 150px;
        position: relative;
        right: -20%;
    }

    .cote {
        position: relative;
        left: 500px;
    }

    .tableau {
        color: #e2e8f0;
        font-size: 16px;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-weight: 600;
        margin-bottom: 0px;
        background: linear-gradient(135deg, #334155, #475569);
        border: 2px solid transparent;
        border-radius: 12px;
        padding: 18px 24px;
        cursor: pointer;
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        position: relative;
        overflow: hidden;
        box-shadow:
            0 4px 15px rgba(15, 23, 42, 0.2),
            0 1px 3px rgba(15, 23, 42, 0.1);
        display: flex;
        align-items: center;
        gap: 12px;
    }

    .tableau::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(230, 57, 70, 0.1), transparent);
        transition: left 0.6s;
    }

    .tableau:hover::before {
        left: 100%;
    }

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    body {
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        background: linear-gradient(135deg, #0f172a, #1e293b, #334155);
        min-height: 100vh;
        padding: 20px;
        color: #e2e8f0;
    }

    .conteneur {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
        gap: 25px;
        position: relative;
        top: 200px;
        max-width: 1400px;
        padding: 30px;
        animation: slideInUp 0.6s ease-out;
    }

    .action {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 25px;
        position: relative;
        top: 230px;
        max-width: 1400px;
        margin: 0 auto;
        padding: 30px;
        animation: slideInUp 0.6s ease-out;
    }

    .contenu:nth-child(1):hover .gestion {
        background-color: rgba(0, 0, 255, 0.726);
        color: white;
        height: 60px;
        width: 250px;
        cursor: pointer;
        font-size: 17px;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
            Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-weight: bold;
        padding: 10px;
        border-radius: 10px;



    }

    .contenu:nth-child(2):hover .gestion {
        background-color: rgba(0, 128, 0, 0.719);
        color: white;
        height: 60px;
        width: 250px;
        cursor: pointer;
        font-size: 17px;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
            Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-weight: bold;
        padding: 10px;
        border-radius: 10px;
    }

    .contenu:nth-child(3):hover .gestion {
        background-color: rgba(255, 255, 0, 0.808);
        color: white;
        height: 60px;
        width: 250px;
        cursor: pointer;
        font-size: 17px;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
            Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-weight: bold;
        padding: 10px;
        border-radius: 10px;
    }

    .contenu:nth-child(4):hover .gestion {
        background-color: rgba(255, 0, 0, 0.795);
        color: white;
        height: 60px;
        width: 250px;
        cursor: pointer;
        font-size: 17px;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
            Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-weight: bold;
        padding: 10px;
        border-radius: 10px;
    }

    .recent {
        position: relative;
        top: 100px;
        height: 500PX;
        width: 100%;
        left: 20px;
        background: linear-gradient(135deg, #1e293b, #334155);
        border-radius: 20px;
        box-shadow: 0px 4px 4px rgba(15, 23, 42, 0.3);
        color: #e2e8f0;
    }

    .contenu {
        background: linear-gradient(135deg, #334155, #475569);
        border: 1px solid rgba(59, 130, 246, 0.2);
        border-radius: 10px;
        padding: 15px;
        text-align: center;
        justify-content: center;
        align-items: center;
        gap: 20px;
        color: #e2e8f0;
    }

    .contenu1 {
        background: linear-gradient(135deg, #1e293b, #334155, #475569);
        border-radius: 20px;
        padding: 30px 25px;
        text-align: center;
        box-shadow:
            0 10px 30px rgba(15, 23, 42, 0.3),
            0 1px 8px rgba(15, 23, 42, 0.2);
        border: 1px solid rgba(59, 130, 246, 0.2);
        backdrop-filter: blur(10px);
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        position: relative;
        overflow: hidden;
    }

    .contenu1::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
        transition: left 0.6s;
    }

    .contenu1:hover::before {
        left: 100%;
    }

    .contenu1:hover {
        transform: translateY(-8px) scale(1.02);
        box-shadow:
            0 20px 40px rgba(0, 0, 0, 0.15),
            0 5px 20px rgba(0, 0, 0, 0.1);
    }

    #vue {
        background: linear-gradient(135deg, #ff9500, #ff7b00);
        color: white;
        border-radius: 50%;
        width: 80px;
        height: 80px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 32px;
        margin: 0 auto 20px;
        box-shadow:
            0 8px 25px rgba(255, 149, 0, 0.4),
            0 4px 10px rgba(255, 149, 0, 0.3);
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        position: relative;
        overflow: hidden;
    }

    #vue::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
        transition: left 0.5s;
    }

    .contenu1:hover #vue::before {
        left: 100%;
    }

    .contenu1:hover #vue {
        transform: scale(1.1) rotate(180deg);
        background: linear-gradient(135deg, #ff7b00, #ff6b00);
        box-shadow:
            0 12px 35px rgba(255, 149, 0, 0.5),
            0 6px 15px rgba(255, 149, 0, 0.4);
        animation: eye-blink 0.8s ease-in-out;
    }

    @keyframes eye-blink {

        0%,
        100% {
            transform: scale(1.1) rotate(5deg);
        }

        50% {
            transform: scale(1.1) rotate(5deg) scaleY(0.1);
        }
    }

    #vues {
        font-size: 36px;
        font-weight: 800;
        color: #e2e8f0;
        margin: 15px 0 10px;
        background: linear-gradient(135deg, #e2e8f0, #cbd5e1);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
    }

    .contenu1:hover #vues {
        transform: scale(1.1);
        filter: drop-shadow(0 3px 6px rgba(0, 0, 0, 0.2));
    }

    .contenu1 p:last-child {
        color: #94a3b8;
        font-size: 16px;
        font-weight: 600;
        letter-spacing: 0.5px;
        text-transform: uppercase;
        margin-top: 5px;
        transition: all 0.3s ease;
    }

    .contenu1:hover p:last-child {
        color: #3b82f6;
        transform: translateY(-2px);
    }

    .contenu1:nth-child(1) #vue {
        background: linear-gradient(135deg, #6366f1, #8b5cf6);
        box-shadow:
            0 8px 25px rgba(99, 102, 241, 0.4),
            0 4px 10px rgba(99, 102, 241, 0.3);
    }

    .contenu1:nth-child(1):hover #vue {
        background: linear-gradient(135deg, #8b5cf6, #a855f7);
        box-shadow:
            0 12px 35px rgba(99, 102, 241, 0.5),
            0 6px 15px rgba(99, 102, 241, 0.4);
    }

    .contenu1:nth-child(1):hover p:last-child {
        color: #6366f1;
    }

    .contenu1:nth-child(2) #vue {
        background: linear-gradient(135deg, #10b981, #059669);
        box-shadow:
            0 8px 25px rgba(16, 185, 129, 0.4),
            0 4px 10px rgba(16, 185, 129, 0.3);
    }

    .contenu1:nth-child(2):hover #vue {
        background: linear-gradient(135deg, #059669, #047857);
        box-shadow:
            0 12px 35px rgba(16, 185, 129, 0.5),
            0 6px 15px rgba(16, 185, 129, 0.4);
    }

    .contenu1:nth-child(2):hover p:last-child {
        color: #10b981;
    }

    .contenu1:nth-child(3) #vue {
        background: linear-gradient(135deg, #f59e0b, #d97706);
        box-shadow:
            0 8px 25px rgba(245, 158, 11, 0.4),
            0 4px 10px rgba(245, 158, 11, 0.3);
    }

    .contenu1:nth-child(3):hover #vue {
        background: linear-gradient(135deg, #d97706, #b45309);
        box-shadow:
            0 12px 35px rgba(245, 158, 11, 0.5),
            0 6px 15px rgba(245, 158, 11, 0.4);
    }

    .contenu1:nth-child(3):hover p:last-child {
        color: #f59e0b;
    }

    .contenu1:nth-child(4) #vue {
        background: linear-gradient(135deg, #ef4444, #dc2626);
        box-shadow:
            0 8px 25px rgba(239, 68, 68, 0.4),
            0 4px 10px rgba(239, 68, 68, 0.3);
    }

    .contenu1:nth-child(4):hover #vue {
        background: linear-gradient(135deg, #dc2626, #b91c1c);
        box-shadow:
            0 12px 35px rgba(239, 68, 68, 0.5),
            0 6px 15px rgba(239, 68, 68, 0.4);
    }

    .contenu1:nth-child(4):hover p:last-child {
        color: #ef4444;
    }

    .contenu1:nth-child(5) #vue {
        background: linear-gradient(135deg, #8b5a2b, #6d4423);
        box-shadow:
            0 8px 25px rgba(139, 90, 43, 0.4),
            0 4px 10px rgba(139, 90, 43, 0.3);
    }

    .contenu1:nth-child(5):hover #vue {
        background: linear-gradient(135deg, #6d4423, #5a361c);
        box-shadow:
            0 12px 35px rgba(139, 90, 43, 0.5),
            0 6px 15px rgba(139, 90, 43, 0.4);
    }

    .contenu1:nth-child(5):hover p:last-child {
        color: #8b5a2b;
    }

    .contenu1:nth-child(1) #vue::after {
        content: '\f06e';
    }

    /* eye */
    .contenu1:nth-child(2) #vue::after {
        content: '\f007';
    }

    /* users */
    .contenu1:nth-child(3) #vue::after {
        content: '\f200';
    }

    /* chart */
    .contenu1:nth-child(4) #vue::after {
        content: '\f004';
    }

    /* heart */
    .contenu1:nth-child(5) #vue::after {
        content: '\f0d6';
    }

    /* money */
    .contenu1:nth-child(1) #vue i::before {
        content: '\f06e';
    }

    /* eye */
    .contenu1:nth-child(2) #vue i::before {
        content: '\f007';
    }

    .contenu1:nth-child(3) #vue i::before {
        content: '\f200';
    }

    .contenu1:nth-child(4) #vue i::before {
        content: '\f004';
    }

    .contenu1:nth-child(5) #vue i::before {
        content: '\f0d6';
    }

    .contenu1:nth-child(1) {
        animation: entrer 0.6s ease-out 0.1s both;
    }

    .contenu1:nth-child(2) {
        animation: entrer 0.6s ease-out 0.2s both;
    }

    .contenu1:nth-child(3) {
        animation: entrer 0.6s ease-out 0.3s both;
    }

    .contenu1:nth-child(4) {
        animation: entrer 0.6s ease-out 0.4s both;
    }

    .contenu1:nth-child(5) {
        animation: entrer 0.6s ease-out 0.5s both;
    }

    @keyframes entrer {
        from {
            opacity: 0;
            transform: rotate(180deg);
        }

        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @media (max-width: 768px) {
        .conteneur {
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            padding: 20px;
            top: 150px;
        }

        .contenu1 {
            padding: 25px 20px;
        }

        #vue {
            width: 70px;
            height: 70px;
            font-size: 28px;
            margin-bottom: 15px;
        }

        #vues {
            font-size: 32px;
        }

        .contenu1 p:last-child {
            font-size: 14px;
        }
        .entete{
          position: relative;
          left: 10%!important;
        }
    }

    @media (max-width: 480px) {
        .conteneur {
            grid-template-columns: 1fr;
            top: 100px;
        }

        #vue {
            width: 60px;
            height: 60px;
            font-size: 24px;
        }

        #vues {
            font-size: 28px;
        }
    }

    @keyframes pulse-glow {

        0%,
        100% {
            box-shadow:
                0 8px 25px rgba(99, 102, 241, 0.4),
                0 4px 10px rgba(99, 102, 241, 0.3);
        }

        50% {
            box-shadow:
                0 12px 35px rgba(99, 102, 241, 0.6),
                0 6px 15px rgba(99, 102, 241, 0.5);
        }
    }

    .contenu1:first-child #vue {
        animation: pulse-glow 3s ease-in-out infinite;
    }

    .tableau:hover {
        color: #e63946;
        transform: translateY(-5px) scale(1.02);
        background: linear-gradient(135deg, #ffffff, #fff5f5);
        border-color: rgba(230, 57, 70, 0.3);
        box-shadow:
            0 12px 35px rgba(109, 57, 230, 0.15),
            0 4px 15px rgba(69, 57, 230, 0.1);
    }

    .tableau:focus {
        outline: none;
        color: #e63946;
        background: linear-gradient(135deg, #fff5f5, #ffffff);
        border-color: rgba(0, 0, 255, 0.637);
        box-shadow:
            0 0 0 3px rgba(109, 57, 230, 0.2),
            0 8px 25px rgba(118, 57, 230, 0.2);
        transform: translateY(-2px);
    }

    .tableau i {
        font-size: 18px;
        transition: all 0.3s ease;
        width: 20px;
        text-align: center;
    }

    .tableau:hover i {
        transform: scale(1.2);
        color: #e63946;
    }

    .tableau:nth-child(1):hover i {
        animation: bounce-bookmark 0.6s ease-in-out;
    }

    .tableau:nth-child(2):hover i {
        animation: shake-cart 0.6s ease-in-out;
    }

    .tableau:nth-child(3):hover i {
        animation: rotate-plus 0.3s ease-in-out;
    }

    .tableau:nth-child(4):hover i {
        animation: wave-user 0.6s ease-in-out;
    }

    .tableau:nth-child(5):hover i {
        animation: pulse-chart 0.6s ease-in-out;
    }

    .tableau:nth-child(6):hover i {
        animation: spin-gear 0.8s ease-in-out;
    }

    @keyframes bounce-bookmark {

        0%,
        100% {
            transform: translateY(0) scale(1.2);
        }

        50% {
            transform: translateY(-5px) scale(1.2);
        }
    }

    @keyframes shake-cart {

        0%,
        100% {
            transform: translateX(0) scale(1.2);
        }

        25% {
            transform: translateX(-3px) scale(1.2);
        }

        75% {
            transform: translateX(3px) scale(1.2);
        }
    }

    @keyframes rotate-plus {
        0% {
            transform: rotate(0deg) scale(1.2);
        }

        100% {
            transform: rotate(180deg) scale(1.2);
        }
    }

    @keyframes wave-user {

        0%,
        100% {
            transform: rotate(0deg) scale(1.2);
        }

        25% {
            transform: rotate(-10deg) scale(1.2);
        }

        75% {
            transform: rotate(10deg) scale(1.2);
        }
    }

    @keyframes pulse-chart {

        0%,
        100% {
            transform: scale(1.2);
        }

        50% {
            transform: scale(1.4);
        }
    }

    @keyframes spin-gear {
        0% {
            transform: rotate(0deg) scale(1.2);
        }

        100% {
            transform: rotate(360deg) scale(1.2);
        }
    }

    .tableau:first-child {
        background: linear-gradient(135deg, #fff5f5, #ffe8e8);
        color: #e63946;
        border-color: rgba(230, 57, 70, 0.3);
    }

    .tableau:first-child i {
        color: #e63946;
    }

    @media (max-width: 768px) {
        .commande {
            flex-direction: column;
            gap: 20px;
            text-align: center;
        }

        .autre-coter {
            right: 0;
            justify-content: center;
            flex-wrap: wrap;
        }

        .voir {
            width: 100%;
            max-width: 280px;
        }

        .appercu {
            grid-template-columns: 1fr;
        }

        .nom {
            margin-left: 0;
            margin-top: 15px;
        }
    }

    .commande:hover {
        transform: translateY(-2px);
        box-shadow:
            0 15px 40px rgba(0, 0, 0, 0.12),
            0 2px 5px rgba(0, 0, 0, 0.1);
    }

    .appercu:hover {
        transform: translateY(-1px);
        box-shadow:
            0 15px 40px rgba(15, 23, 42, 0.4),
            0 2px 5px rgba(15, 23, 42, 0.3);
    }

    @media (max-width: 768px) {
        body {
            padding: 10px;
            padding-top: 80px;
        }
.titre{
  display: flex;
  align-items: center!important;
  justify-content: center;
}

.categorie{
  position: relative !important;
  left:15%!important;
  margin: -5px;
}
.autre{
display: flex;
align-items: center;
}
        .menu-hamburger {
            display: flex;
        }

        .ceux {
            position: fixed;
            top: 70px;
            left: -100%;
            width: 100%;
            height: calc(100vh - 70px);
            background: linear-gradient(135deg, #1e293b, #334155);
            flex-direction: column;
            justify-content: flex-start;
            align-items: center;
            padding: 20px;
            transition: left 0.3s ease;
            z-index: 999;
            gap: 30px;
        }

        .ceux.menu-ouvert {
            left: 0;
        }

        .marcher {
            width: 100%;
            max-width: 300px;
            justify-content: center;
            padding: 15px 20px;
            font-size: 16px;
        }

        .commande {
            flex-direction: column;
            gap: 20px;
            text-align: center;
            padding: 20px;
            left: 0;
            margin: 0 10px 30px 10px;
        }

        .autre-coter {
            right: 0;
            justify-content: center;
            flex-wrap: wrap;
        }

        .voir {
            width: 100%;
            max-width: 280px;
        }

        .appercu {
            grid-template-columns: 1fr;
            padding: 20px;
            margin: 0 10px;
        }

        .nom {
            margin-left: 0;
            margin-top: 15px;
        }

        .verbas {
            flex-direction: column;
            text-align: center;
            padding: 20px;
            margin: 0 10px;
        }

        .cote {
            left: 0;
            font-size: 80px;
            margin-top: 20px;
        }

        .conteneur {
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            padding: 20px 10px;
            top: 150px;
        }

        .action {
            grid-template-columns: 1fr;
            gap: 20px;
            padding: 20px 10px;
            top: 200px;
        }

        .recent {
            left: 0;
            margin: 0 10px;
            height: 400px;
        }

        .tableau {
            padding: 15px 20px;
            font-size: 14px;
        }
    }

    @media (max-width: 480px) {
        .conteneur {
            grid-template-columns: 1fr;
            top: 120px;
        }

        .action {
            top: 180px;
        }

        .commande {
            top: 80px;
            padding: 15px;
        }

        .appercu {
            top: 90px;
        }

        .verbas {
            top: 110px;
        }

        .conteneur {
            top: 140px;
        }

        .action {
            top: 200px;
        }

        .recent {
            top: 80px;
            height: 350px;
        }

        #vue {
            width: 60px;
            height: 60px;
            font-size: 24px;
        }

        #vues {
            font-size: 28px;
        }

        .premium {
            width: 100%;
            max-width: 250px;
        }
    }
</style>

<body>
    <header>
        <div class="titre">
            <div class="autre">
                <div class="menu-hamburger" onclick="toggleMenu()">
                    <div></div>
                    <div></div>
                    <div></div>
                </div>
                <blockquote style="color: blue;" class="entete">
                    <i class="fas fa-envelope" data-lang-en="Creator Market"></i>
                    <span data-lang-en="Creator Market">Creator market</span>
                </blockquote>
                <div class="ceux" id="ceux">
                    <button id="acceuil" class="marcher">
                        <i class="fas fa-envelope"></i>
                        <span data-lang-en="Home">Acceuil</span>
                    </button>
                    <button class="marcher">
                        <i class="fas fa-search"></i>
                        <span data-lang-en="Market Place">Market Place</span>
                    </button>
                    <button onclick="window.location.href='templates.html'" class="marcher">
                        <i class="fas fa-crown"></i>
                        <span data-lang-en="Create">Créer</span>
                    </button>
                    <button class="marcher">
                        <i class="fas fa-arrow-right"></i>
                        <span data-lang-en="Dashboard">Dashboard</span>
                    </button>
                </div>

                <div id="categorie" class="categorie">
                    <button id="notification" class="notification">
                        <i class="fas fa-bell"></i>
                    </button>
                    <button id="langue" class="notificatio">
                        <i class="fas fa-globe"></i>
                        <span data-lang-en="EN">FR</span>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <div class="commande">
        <span class="logo">P</span>
        <span class="nom">Maman Julie</span>
        <div class="autre-coter">
            <button><i id="notif" class="fas fa-bell"></i></button>
            <span class="notification-badge">3</span>
            <button class="voir" id="voir"><i class="fas fa-eye"></i> Voir ma Boutique</button>
        </div>
    </div>

    <div class="appercu">
        <button class="tableau"><i class="fa-solid fa-bookmark active"></i> Aperçu</button>
        <button class="tableau"><i class="fa-solid fa-cart-shopping"></i> Commandes</button>
        <button class="tableau"><i class="fas fa-plus"></i> Produits</button>
        <button class="tableau"><i class="fas fa-user"></i> Clients</button>
        <button class="tableau"><i class="fa-solid fa-chart-line"></i> Analytics</button>
        <button class="tableau"><i class="fa-solid fa-gear"></i> Paramètres</button>
    </div>
    <div class="verbas">
        <div style="display: grid;">
            <h2>Boostez votre visibilité! 🚀</h2>
            <br>
            <p style="color: white;">Passez à Premium pour 2x plus de clients</p>
            <br>
            <button class="premium" id="preminum"> <i class="fas fa-crown"></i> Decouvrir Premium</button>
        </div>
        <div class="cote"><i class="fa-solid fa-chart-line"></i></div>
    </div>

    <div class="conteneur">
        <div class="contenu1">
            <i id="vue" class="fas fa-eye"></i>
            <p class="vues" id="vues">1,234</p>
            <p>Total de Vues</p>
        </div>

        <div class="contenu1">
            <i id="vue" class="fas fa-users"></i>
            <p id="vues">856</p>
            <p>Visiteurs Uniques</p>
        </div>

        <div class="contenu1">
            <i id="vue" class="fas fa-chart-line"></i>
            <p id="vues">94%</p>
            <p>Taux de Conversion</p>
        </div>

        <div class="contenu1">
            <i id="vue" class="fas fa-heart"></i>
            <p id="vues">342</p>
            <p>J'aime Reçus</p>
        </div>

        <div class="contenu1">
            <i id="vue" class="fas fa-dollar-sign"></i>
            <p id="vues">2,458€</p>
            <p>Revenus Générés</p>
        </div>
    </div>
    <div class="action">
        <div class="contenu" style="align-items: center;">
            <i id="jour" style="text-align: center;" class="fas fa-share-alt"></i>
            <button class="gestion">Partager Votre Boutique</button>
        </div>
        <div class="contenu">
            <i id="jour" class="fas fa-plus"></i>
            <button class="gestion">Ajouter un Produit</button>
        </div>
        <div class="contenu">
            <i id="jour" class="fas fa-pencil-alt"></i>
            <button class="gestion">Modifier un Produit</button>
        </div>
        <div class="contenu">
            <i id="jour" class="fas fa-trash-alt"></i>
            <button class="gestion">Supprimer un Produit </button>
        </div>
        <div class="recent">
            <div style="display: flex;align-items: center;">
                <p>Commandes Recentes</p> <span style="left: 500px;">Voir Plus</span>
            </div>
        </div>
    </div>
    <script>
        function toggleMenu() {
            const hamburger = document.querySelector('.menu-hamburger');
            const menu = document.querySelector('.ceux');
            hamburger.classList.toggle('ouvert');
            menu.classList.toggle('menu-ouvert');
        }

    </script>
</body>

</html>
</body>

</html>
