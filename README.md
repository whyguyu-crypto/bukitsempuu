
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bukit Sempu - Wisata Alam</title>
    <!-- Menggunakan Font Google: Poppins -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome untuk Ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* --- VARIABEL CSS & RESET --- */
        :root {
            /* Light Mode Variables */
            --primary-green: #2F7D32;
            --light-green: #66BB6A;
            --primary-blue: #1E88E5;
            --light-blue: #81D4FA;
            --text-dark: #1a1a1a;
            --text-light: #ffffff;
            --glass-bg: rgba(255, 255, 255, 0.15);
            --glass-border: rgba(255, 255, 255, 0.2);
            --card-white: rgba(255, 255, 255, 0.95);
            --shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.15);
            --bg-body: linear-gradient(135deg, #2F7D32 0%, #1E88E5 100%);
            --header-bg: rgba(255, 255, 255, 0.1);
            --input-bg: rgba(255, 255, 255, 1);
            --footer-bg: rgba(0, 0, 0, 0.8);
        }

        /* Dark Mode Variables */
        [data-theme="dark"] {
            --primary-green: #4caf50;
            --light-green: #81c784;
            --primary-blue: #42a5f5;
            --light-blue: #90caf9;
            --text-dark: #e0e0e0; /* Teks utama menjadi terang */
            --text-light: #ffffff;
            --glass-bg: rgba(0, 0, 0, 0.4);
            --glass-border: rgba(255, 255, 255, 0.1);
            --card-white: rgba(30, 30, 30, 0.95); /* Card menjadi gelap */
            --shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.5);
            /* Background gelap dengan gradasi nuansa malam hutan */
            --bg-body: linear-gradient(135deg, #0d2818 0%, #002860 100%);
            --header-bg: rgba(0, 0, 0, 0.6);
            --input-bg: rgba(255, 255, 255, 0.1);
            --footer-bg: rgba(0, 0, 0, 0.95);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease;
        }

        body {
            background: var(--bg-body);
            background-attachment: fixed;
            color: var(--text-dark);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* --- UTILITIES --- */
        .hidden { display: none !important; }
        .fade-in { animation: fadeIn 0.5s ease-in-out; }
        .glass-panel {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: 16px;
        }
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        .btn-primary {
            background: linear-gradient(90deg, var(--primary-green), var(--primary-blue));
            color: white;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }
        .btn-outline {
            background: transparent;
            border: 2px solid white;
            color: white;
        }
        .btn-outline:hover {
            background: white;
            color: var(--primary-green);
        }
        
        /* Tombol Kembali Baru */
        .btn-back {
            background: var(--glass-bg);
            color: var(--text-light);
            border: 1px solid var(--glass-border);
            margin-bottom: 20px;
            padding: 8px 15px;
            border-radius: 12px;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
        }
        .btn-back:hover {
            background: white;
            color: var(--primary-green);
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- TOAST NOTIFICATION (PENGGANTI ALERT) --- */
        .toast-container {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 5000;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .toast {
            background: rgba(0, 0, 0, 0.85);
            color: white;
            padding: 12px 24px;
            border-radius: 50px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 10px;
            animation: slideUp 0.3s ease forwards;
            backdrop-filter: blur(4px);
        }
        
        [data-theme="dark"] .toast {
            background: rgba(255, 255, 255, 0.9);
            color: #333;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeOut {
            to { opacity: 0; transform: translateY(-10px); }
        }

        /* --- HEADER & NAVIGASI --- */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            padding: 15px 5%;
            background: var(--header-bg);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid var(--glass-border);
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom-left-radius: 20px;
            border-bottom-right-radius: 20px;
            margin: 0 10px 10px 10px; 
            width: calc(100% - 20px);
            transition: background 0.3s;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--text-light);
            text-decoration: none;
            font-weight: 700;
            font-size: 1.5rem;
        }

        .logo-img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid white;
            background: white;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 25px;
        }

        nav a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 500;
            font-size: 0.95rem;
            transition: color 0.3s;
            position: relative;
        }

        nav a:hover, nav a.active {
            color: var(--light-blue);
            text-shadow: 0 0 10px rgba(255,255,255,0.5);
        }

        .nav-icons {
            display: flex;
            gap: 20px;
            color: var(--text-light);
            align-items: center;
        }

        .icon-btn {
            background: none;
            border: none;
            color: var(--text-light);
            font-size: 1.2rem;
            cursor: pointer;
            position: relative;
        }

        /* Dropdown Profil */
        .dropdown-menu {
            position: absolute;
            top: 70px;
            right: 5%;
            background: var(--card-white);
            color: var(--text-dark);
            width: 200px;
            border-radius: 16px;
            box-shadow: var(--shadow);
            overflow: hidden;
            transform-origin: top right;
            transition: transform 0.3s ease, opacity 0.3s ease;
            opacity: 0;
            visibility: hidden;
            transform: scale(0.9);
        }

        .dropdown-menu.show {
            opacity: 1;
            visibility: visible;
            transform: scale(1);
        }

        .dropdown-item {
            padding: 12px 20px;
            display: block;
            color: var(--text-dark);
            text-decoration: none;
            border-bottom: 1px solid rgba(0,0,0,0.05);
            font-size: 0.9rem;
            cursor: pointer;
        }

        .dropdown-item:hover {
            background: #f0f8ff;
            color: var(--primary-blue);
        }

        /* --- MODAL PENGATURAN (POP-UP) --- */
        #settings-modal {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.6);
            backdrop-filter: blur(5px);
            z-index: 3000;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: opacity 0.3s;
        }
        
        .modal-content {
            background: var(--card-white);
            color: var(--text-dark);
            width: 300px;
            border-radius: 24px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            position: relative;
        }
        
        .modal-title {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 20px;
            color: var(--primary-green);
        }
        
        .modal-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            width: 100%;
            padding: 12px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 12px;
            background: transparent;
            cursor: pointer;
            font-weight: 500;
            color: var(--text-dark);
            transition: all 0.2s;
        }
        
        .modal-btn:hover {
            background: #f5f5f5;
            border-color: var(--primary-blue);
            color: var(--primary-blue);
        }
        
        .modal-btn.logout {
            color: #c62828;
            border-color: #ffcdd2;
            background: #ffebee;
        }
        .modal-btn.logout:hover {
            background: #ef9a9a;
        }

        /* --- SEARCH OVERLAY --- */
        #search-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: var(--card-white);
            z-index: 2000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: opacity 0.3s;
        }
        
        #search-input {
            width: 80%;
            max-width: 600px;
            padding: 20px;
            font-size: 1.5rem;
            border: none;
            border-bottom: 2px solid var(--primary-green);
            outline: none;
            background: transparent;
            margin-bottom: 20px;
            color: var(--text-dark);
        }

        .close-search {
            position: absolute;
            top: 30px;
            right: 30px;
            font-size: 2rem;
            cursor: pointer;
            color: var(--text-dark);
        }

        /* --- MAIN CONTENT AREA --- */
        main {
            padding-top: 100px;
            min-height: 100vh;
            padding-bottom: 50px;
        }

        section {
            padding: 20px 5%;
        }

        /* --- HOME SECTION --- */
        .hero {
            text-align: center;
            color: var(--text-light);
            padding: 80px 5% 120px;
            position: relative;
            overflow: hidden;
            border-radius: 24px; 
            margin: 20px 5%; 
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
            min-height: 60vh; 
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            /* BACKGROUND DIGANTI SESUAI PERMINTAAN (Gambar Hutan A-Frame) */
            background: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.6)), 
                        url('https://z-cdn-media.chatglm.cn/files/b7183c4b-f986-4f06-9bed-c1ba7faa467d.jpg?auth_key=1868374046-9a18f2c9c7fd4ad09d0766b05f191f13-0-c438a849716cd08e71ce45d83f413d20') center/cover no-repeat;
            opacity: 1;
            z-index: -1;
            filter: brightness(0.9); 
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 15px;
            text-shadow: 0 4px 10px rgba(0,0,0,0.5);
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 40px;
            opacity: 1;
            text-shadow: 0 2px 4px rgba(0,0,0,0.4);
        }

        .search-container {
            max-width: 700px;
            margin: 0 auto;
            position: relative;
        }

        .glass-search {
            display: flex;
            align-items: center;
            padding: 15px 25px;
            background: rgba(255,255,255,0.25);
            backdrop-filter: blur(15px);
            border-radius: 50px;
            border: 1px solid white;
            box-shadow: 0 8px 32px rgba(0,0,0,0.2);
        }

        .glass-search input {
            flex: 1;
            background: transparent;
            border: none;
            outline: none;
            color: white;
            font-size: 1.1rem;
            padding: 0 15px;
        }
        
        .glass-search input::placeholder { color: rgba(255,255,255,0.9); }

        /* Quick Menu Cards */
        .quick-menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            margin-top: -50px;
            margin-bottom: 50px;
            padding: 0 5%;
            position: relative;
            z-index: 10; 
        }

        .menu-card {
            background: var(--card-white);
            color: var(--text-dark);
            padding: 20px;
            border-radius: 24px;
            text-align: center;
            box-shadow: var(--shadow);
            cursor: pointer;
            transition: transform 0.3s;
        }

        .menu-card:hover {
            transform: translateY(-10px);
        }

        .menu-card i {
            font-size: 2rem;
            margin-bottom: 10px;
            background: -webkit-linear-gradient(var(--primary-green), var(--primary-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Promo Section */
        .promo-banner {
            background: linear-gradient(90deg, #ff9800, #ff5722);
            border-radius: 24px;
            padding: 30px;
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 40px;
            box-shadow: var(--shadow);
        }

        /* --- CONTENT GRIDS (Kuliner, Camping, Rental) --- */
        .section-title {
            color: var(--text-light);
            font-size: 2rem;
            margin-bottom: 30px;
            text-align: center;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }
        [data-theme="dark"] .section-title {
            text-shadow: none;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
        }

        .content-card {
            background: var(--card-white);
            color: var(--text-dark);
            border-radius: 24px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s;
        }

        .content-card:hover {
            transform: scale(1.02);
        }

        .card-img {
            width: 100%;
            height: 180px;
            object-fit: cover;
        }

        .card-body {
            padding: 20px;
        }

        .card-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--text-dark);
        }

        .card-price {
            color: var(--primary-green);
            font-weight: 700;
            font-size: 1.1rem;
            margin-bottom: 10px;
        }

        .badge {
            padding: 4px 8px;
            border-radius: 8px;
            font-size: 0.8rem;
            font-weight: 600;
        }
        .badge-stock { background: #e8f5e9; color: #2e7d32; }
        .badge-out { background: #ffebee; color: #c62828; }

        /* --- TICKET & CHECKOUT --- */
        .ticket-container {
            background: var(--card-white);
            color: var(--text-dark);
            max-width: 800px;
            margin: 0 auto;
            border-radius: 30px;
            padding: 30px;
            box-shadow: var(--shadow);
        }

        .form-group {
            margin-bottom: 20px;
        }
        
        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 12px;
            font-size: 1rem;
            background: var(--input-bg);
            color: var(--text-dark);
        }
        
        [data-theme="dark"] .form-control {
            border-color: #444;
        }

        .payment-method {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }

        .payment-option {
            flex: 1;
            border: 2px solid #eee;
            padding: 15px;
            border-radius: 16px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            background: transparent;
            color: var(--text-dark);
        }

        .payment-option.selected {
            border-color: var(--primary-blue);
            background: #e3f2fd;
        }
        [data-theme="dark"] .payment-option.selected {
            background: rgba(66, 165, 245, 0.2);
        }

        /* E-Wallet Options */
        .ewallet-options {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 20px;
        }

        .ewallet-btn {
            padding: 15px 25px;
            border: 1px solid #ddd;
            border-radius: 16px;
            background: white;
            cursor: pointer;
            font-weight: bold;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            min-width: 80px;
        }
        [data-theme="dark"] .ewallet-btn {
            background: #333;
            border-color: #555;
            color: white;
        }
        
        .ewallet-btn:hover { background: #f9f9f9; border-color: var(--primary-blue); }
        .ewallet-btn i { font-size: 1.5rem; }
        .bg-dana { color: #118EEA; }
        .bg-gopay { color: #00AED6; }
        .bg-ovo { color: #4C3494; }

        .qr-placeholder {
            width: 200px;
            height: 200px;
            background: #eee;
            margin: 20px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            border-radius: 20px;
            overflow: hidden;
        }
        
        .qr-placeholder img {
            width: 100%;
            height: 100%;
        }

        .digital-ticket {
            border: 2px dashed var(--primary-green);
            padding: 20px;
            border-radius: 20px;
            text-align: center;
            background: #f1f8e9;
            margin-top: 20px;
        }
        [data-theme="dark"] .digital-ticket {
            background: rgba(76, 175, 80, 0.2);
        }

        /* --- CART (KERANJANG) --- */
        /* Mengaktifkan kembali tombol keranjang */
        .cart-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--primary-green);
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            cursor: pointer;
            z-index: 1100;
            font-size: 1.5rem;
            transition: transform 0.3s;
        }
        .cart-btn:hover { transform: scale(1.1); }
        
        .cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background: #ff5252;
            color: white;
            font-size: 0.8rem;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            border: 2px solid white;
        }

        .cart-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1999;
            display: none;
            backdrop-filter: blur(2px);
        }
        .cart-overlay.open { display: block; }

        .cart-panel {
            position: fixed;
            top: 0; right: -400px;
            width: 350px;
            height: 100%;
            background: var(--card-white);
            box-shadow: -5px 0 15px rgba(0,0,0,0.1);
            z-index: 2000;
            transition: right 0.3s ease;
            display: flex;
            flex-direction: column;
            padding: 20px;
            color: var(--text-dark);
        }
        .cart-panel.open { right: 0; }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
            margin-bottom: 15px;
        }

        .cart-items {
            flex: 1;
            overflow-y: auto;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            border-bottom: 1px solid #f0f0f0;
            padding-bottom: 10px;
        }
        
        .cart-item-info h4 { font-size: 0.95rem; margin-bottom: 4px; }
        .cart-item-info p { font-size: 0.85rem; color: #666; }
        
        .cart-controls {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .qty-btn {
            width: 24px; height: 24px;
            border-radius: 50%;
            border: 1px solid #ccc;
            background: transparent;
            cursor: pointer;
            display: flex; justify-content: center; align-items: center;
            font-size: 0.8rem;
        }
        .qty-btn:hover { background: #eee; }

        .cart-footer {
            margin-top: 15px;
            border-top: 1px solid #eee;
            padding-top: 15px;
        }
        .cart-total {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            font-size: 1.1rem;
            margin-bottom: 15px;
        }

        /* --- FOOTER --- */
        footer {
            background: var(--footer-bg);
            color: white;
            padding: 40px 5% 20px;
            margin-top: 50px;
            border-top-left-radius: 50px;
            border-top-right-radius: 50px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 30px;
        }

        .footer-logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--light-blue);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .footer-logo-img {
            width: 60px;
            height: 60px;
            object-fit: contain;
            border-radius: 16px;
            border: 2px solid rgba(255,255,255,0.2);
            background: white;
        }

        .social-icons a {
            color: white;
            margin-right: 15px;
            font-size: 1.2rem;
            transition: color 0.3s;
        }

        .social-icons a:hover { color: var(--light-green); }

        .copyright {
            text-align: center;
            border-top: 1px solid rgba(255,255,255,0.1);
            padding-top: 20px;
            font-size: 0.9rem;
            color: #aaa;
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 768px) {
            header {
                padding: 15px 20px;
                margin: 0 10px 10px 10px; 
            }
            nav {
                position: fixed;
                bottom: 0;
                left: 0;
                width: 100%;
                background: var(--card-white);
                z-index: 999;
                box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
                padding: 10px 0;
                border-top-left-radius: 20px;
                border-top-right-radius: 20px;
            }
            nav ul {
                justify-content: space-around;
                padding: 0;
                width: 100%;
            }
            nav a {
                color: #555;
                font-size: 0.8rem;
                display: flex;
                flex-direction: column;
                align-items: center;
                gap: 5px;
            }
            nav a i { font-size: 1.2rem; }
            nav a.active { color: var(--primary-green); }
            
            .nav-icons { display: none; } 
            main { padding-bottom: 80px; } 
            .hero { margin: 10px 5%; } 
            .hero h1 { font-size: 2.2rem; }
            .dropdown-menu { top: 60px; right: 20px; }
            
            .footer-logo {
                justify-content: center; 
            }
            .footer-logo-img {
                width: 50px;
                height: 50px;
            }
            .cart-panel { width: 100%; max-width: 300px; }
        }
    </style>
</head>
<body>

    <!-- HEADER -->
    <header>
        <!-- Logo dengan Gambar -->
        <a href="#" class="logo-container" onclick="navigate('home')">
            <img src="https://z-cdn-media.chatglm.cn/files/44d4f9ef-4048-40e9-b1bf-36f92745dc58.jpeg?auth_key=1868288875-c97ebf6fcdbe4fc892fec4fa5de25fc7-0-1fdc5aabbb889423a0324b76c5bc1e1f" alt="Logo Bukit Sempu" class="logo-img">
            <span>Bukit Sempu</span>
        </a>

        <!-- Navigasi Desktop (Hidden on Mobile) -->
        <nav id="desktop-nav">
            <ul>
                <li><a href="#" class="nav-link active" onclick="navigate('home')">Beranda</a></li>
                <li><a href="#" class="nav-link" onclick="navigate('tiket')">Tiket</a></li>
            </ul>
        </nav>

        <div class="nav-icons">
            <button class="icon-btn" onclick="toggleSearch()">
                <i class="fas fa-search"></i>
            </button>
            <button class="icon-btn" onclick="toggleAccount()">
                <i class="fas fa-user-circle"></i>
            </button>
        </div>
    </header>

    <!-- MENU DROPDOWN AKUN -->
    <div id="account-dropdown" class="dropdown-menu">
        <a href="#" class="dropdown-item" onclick="showToast('Membuka Profil Saya...')"><i class="fas fa-user"></i> Profil Saya</a>
        <a href="#" class="dropdown-item" onclick="showToast('Membuka Riwayat Pesanan...')"><i class="fas fa-history"></i> Riwayat Pesanan</a>
        <a href="#" class="dropdown-item" onclick="openSettingsModal()"><i class="fas fa-cog"></i> Pengaturan</a>
        <a href="#" class="dropdown-item" onclick="handleLogout()"><i class="fas fa-sign-out-alt"></i> Logout</a>
    </div>

    <!-- MODAL PENGATURAN (POP-UP) -->
    <div id="settings-modal" class="hidden fade-in">
        <div class="modal-content">
            <div class="modal-title">Pengaturan</div>
            
            <!-- Tombol Mode Gelap/Terang -->
            <button class="modal-btn" onclick="toggleTheme()">
                <i class="fas fa-adjust"></i> Mode Gelap/Terang
            </button>
            
            <!-- Tombol Akun -->
            <button class="modal-btn" onclick="showToast('Menu Edit Akun')">
                <i class="fas fa-user-edit"></i> Akun
            </button>
            
            <!-- Tombol Logout -->
            <button class="modal-btn logout" onclick="handleLogout()">
                <i class="fas fa-sign-out-alt"></i> Logout
            </button>
            
            <button class="btn btn-outline" style="width:100%; margin-top:10px; border-color:#ccc; color: var(--text-dark);" onclick="closeSettingsModal()">Tutup</button>
        </div>
    </div>

    <!-- SEARCH OVERLAY -->
    <div id="search-overlay" class="hidden">
        <span class="close-search" onclick="toggleSearch()">×</span>
        <i class="fas fa-search" style="font-size: 3rem; color: #ccc; margin-bottom: 20px;"></i>
        <input type="text" id="search-input" placeholder="Cari kuliner, tiket, atau paket..." autofocus="">
        <p style="color: #777;">Tekan Enter untuk mencari</p>
    </div>

    <!-- CART OVERLAY & PANEL -->
    <div class="cart-overlay" id="cart-overlay" onclick="toggleCart()"></div>
    <div class="cart-panel" id="cart-panel">
        <div class="cart-header">
            <h3>Keranjang Belanja</h3>
            <i class="fas fa-times" style="cursor:pointer; font-size:1.2rem;" onclick="toggleCart()"></i>
        </div>
        <div class="cart-items" id="cart-items-container">
            <!-- Item keranjang akan muncul disini via JS -->
            <p style="text-align:center; margin-top:20px; color:#888;">Keranjang masih kosong.</p>
        </div>
        <div class="cart-footer">
            <div class="cart-total">
                <span>Total:</span>
                <span id="cart-total-price">Rp 0</span>
            </div>
            <button class="btn btn-primary" style="width:100%;" onclick="processCheckout()">Checkout Sekarang</button>
        </div>
    </div>

    <!-- FLOATING CART BUTTON -->
    <div class="cart-btn" id="floating-cart-btn" onclick="toggleCart()">
        <i class="fas fa-shopping-cart"></i>
        <span class="cart-count" id="cart-count">0</span>
    </div>

    <!-- MAIN CONTENT -->
    <main id="main-content">
        
        <!-- 1. HALAMAN BERANDA -->
        <section id="home" class="fade-in">
            <div class="hero">
                <h1>Nikmati Alam, Ciptakan Kenangan</h1>
                <p>Destinasi wisata paralayang dan camping terbaik dengan pemandangan menakjubkan.</p>
                
                <div class="search-container">
                    <div class="glass-search">
                        <i class="fas fa-search" style="color: white;"></i>
                        <input type="text" placeholder="Mau kemana hari ini?">
                    </div>
                </div>
            </div>

            <div class="quick-menu">
                <div class="menu-card" onclick="navigate('kuliner')">
                    <i class="fas fa-utensils"></i>
                    <h3>Kuliner</h3>
                    <p>Nikmati masakan lokal</p>
                </div>
                <div class="menu-card" onclick="navigate('camping')">
                    <i class="fas fa-campground"></i>
                    <h3>Camping</h3>
                    <p>Paket lengkap keluarga</p>
                </div>
                <div class="menu-card" onclick="navigate('penyewaan')">
                    <i class="fas fa-hiking"></i>
                    <h3>Penyewaan</h3>
                    <p>Perlengkapan terbaik</p>
                </div>
            </div>

            <div class="section-title" style="text-align: left; padding: 0 5%;">Promo Terbaru</div>
            <div class="promo-banner" style="margin: 0 5% 50px;">
                <div>
                    <h2>Diskon 20% Camping Weekday</h2>
                    <p>Nikmati malam dingin Bukit Sempu dengan harga spesial hari Senin - Kamis.</p>
                </div>
                <button class="btn btn-primary" onclick="navigate('camping')">Booking Sekarang</button>
            </div>
        </section>

        <!-- 2. HALAMAN KULINER -->
        <section id="kuliner" class="hidden fade-in">
            <div class="btn-back" onclick="navigate('home')">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </div>
            
            <h2 class="section-title">Kuliner Bukit Sempu</h2>
            <div class="card-grid">
                <!-- Item 1: Nasi Rawon -->
                <div class="content-card">
                    <img src="https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcT9H1WkKcUjxDXAb0b1jgf47bv7D9yxEvJa2XANpvBzlScl2XJlhuOAbQ16n4QX" alt="Nasi Rawon" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Nasi Rawon</h3>
                        <p class="card-price">Rp 30.000</p>
                        <p>Nasi rawon dengan kuah kluwek pilihan, gurih, harum, dan bikin rindu.</p>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Nasi Rawon', 30000)">Tambah ke Keranjang</button>
                    </div>
                </div>
                <!-- Item 2: Kopi -->
                <div class="content-card">
                    <img src="https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?auto=format&fit=crop&w=400&q=80" alt="Kopi Arabika" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Kopi Arabika</h3>
                        <p class="card-price">Rp 15.000</p>
                        <p>Kopi arabika lokal disajikan panas dengan gula aren.</p>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Kopi Arabika', 15000)">Tambah ke Keranjang</button>
                    </div>
                </div>
                <!-- Item 3: Gorengan -->
                <div class="content-card">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQU3z9FLS8VQ3FzzFwV831CF5MS9HbDMUvv7g&s" alt="Pisang Goreng Keju" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Pisang Goreng Keju</h3>
                        <p class="card-price">Rp 2.000/biji</p>
                        <p>Camilan hangat pas untuk udara dingin.</p>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Pisang Goreng Keju', 2000)">Tambah ke Keranjang</button>
                    </div>
                </div>
                
                <!-- ITEM BARU: Indomie -->
                <div class="content-card">
                    <img src="https://images.unsplash.com/photo-1569718212165-3a8278d5f624?auto=format&fit=crop&w=400&q=80" alt="Indomie Special" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Indomie Special</h3>
                        <p class="card-price">Rp 15.000</p>
                        <p>Indomie rebus/goreng dengan telur dan sayur, wajib saat camping.</p>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Indomie Special', 15000)">Tambah ke Keranjang</button>
                    </div>
                </div>
                
                <!-- ITEM BARU: Jagung Bakar -->
                <div class="content-card">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSo2efr5-9UAtL02rrm2IkWU5Gk9qFPnipCagzgqpYSDMk898yKrYxUo0bmOu1N3DiHMLKxWIa4OHqOf2diOwZx8SmypUv_AyEuaUHguTPlyQ&s=10" alt="Jagung Bakar" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Jagung Bakar</h3>
                        <p class="card-price">Rp 10.000</p>
                        <p>Jagung manis bakar dengan bumbu keju atau aneka rasa.</p>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Jagung Bakar', 10000)">Tambah ke Keranjang</button>
                    </div>
                </div>

                <!-- ITEM BARU: Wedang Jahe -->
                <div class="content-card">
                    <img src="data:image/jpeg;base64,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" alt="Wedang Jahe" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Wedang Jahe</h3>
                        <p class="card-price">Rp 5.000</p>
                        <p>Minuman hangat jahe merah asli, sangat menghangatkan badan.</p>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Wedang Jahe', 5000)">Tambah ke Keranjang</button>
                    </div>
                </div>

            </div>
        </section>

        <!-- 3. HALAMAN CAMPING -->
        <section id="camping" class="hidden fade-in">
            <div class="btn-back" onclick="navigate('home')">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </div>

            <h2 class="section-title">Paket Camping</h2>
            <div class="card-grid">
                <div class="content-card">
                    <img src="https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?auto=format&fit=crop&w=400&q=80" alt="Camping" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Paket Bring Your Own Tent</h3>
                        <p class="card-price">Rp 15.000 / orang</p>
                        <ul style="font-size: 0.9rem; list-style: none; margin-bottom: 15px;">
                            <li><i class="fas fa-check text-success"></i> Akses area camping</li>
                            <li><i class="fas fa-check text-success"></i> Toilet bersih</li>
                            <li><i class="fas fa-check text-success"></i> Area api unggun</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;" onclick="addToCart('Paket Camping BYO', 15000)">Booking Sekarang</button>
                    </div>
                </div>
                <div class="content-card">
                    <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?auto=format&fit=crop&w=400&q=80" alt="Glamping" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Paket Glamping (4 Orang)</h3>
                        <p class="card-price">Rp 250.000 / malam</p>
                        <ul style="font-size: 0.9rem; list-style: none; margin-bottom: 15px;">
                            <li><i class="fas fa-check text-success"></i> Tenda sudah berdiri</li>
                            <li><i class="fas fa-check text-success"></i> Kasur & sleeping bag</li>
                            <li><i class="fas fa-check text-success"></i> Teras & lampu</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;" onclick="addToCart('Paket Glamping', 250000)">Booking Sekarang</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- 4. HALAMAN PENYEWAAN -->
        <section id="penyewaan" class="hidden fade-in">
            <div class="btn-back" onclick="navigate('home')">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </div>

            <h2 class="section-title">Penyewaan Alat</h2>
            <div class="card-grid">
                
                <!-- ITEM BARU: Paket Alat Lengkap -->
                <div class="content-card">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcReWACUTToY4cRoFZvDOczns7gYs660ScRTaQ&s" alt="Paket Lengkap" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Paket Alat Lengkap</h3>
                        <p class="card-price">Rp 150.000 / paket</p>
                        <ul style="font-size: 0.9rem; list-style: none; margin-bottom: 15px;">
                            <li><i class="fas fa-check text-success"></i> Tenda Kapasitas 4</li>
                            <li><i class="fas fa-check text-success"></i> Lampu Tenda & Senter</li>
                            <li><i class="fas fa-check text-success"></i> Tikar Matras</li>
                        </ul>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Paket Alat Lengkap', 150000)">Sewa Sekarang</button>
                    </div>
                </div>

                <!-- Item 1: Tenda Dome -->
                <div class="content-card">
                    <img src="data:image/jpeg;base64,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" alt="Tenda" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Tenda Dome Kapasitas 4</h3>
                        <p class="card-price">Rp 50.000 / 24 jam</p>
                        <span class="badge badge-stock">Tersedia 5 Unit</span>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Sewa Tenda Dome', 50000)">Sewa Sekarang</button>
                    </div>
                </div>
                <!-- Item 2: Kompor -->
                <div class="content-card">
                    <img src="data:image/jpeg;base64,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" alt="Kompor" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Kompor Portable & Gas</h3>
                        <p class="card-price">Rp 10.000 / 24 jam</p>
                        <span class="badge badge-out">Stok Habis</span>
                        <button class="btn btn-outline" style="margin-top: 10px; width: 100%; color: #aaa; border-color: #aaa;" disabled="">Habis</button>
                    </div>
                </div>
                <!-- Item 3: Kasur -->
                <div class="content-card">
                    <img src="data:image/jpeg;base64,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" alt="Kasur" class="card-img">
                    <div class="card-body">
                        <h3 class="card-title">Kasur Angin & Pompa</h3>
                        <p class="card-price">Rp 25.000 / 24 jam</p>
                        <span class="badge badge-stock">Tersedia 10 Unit</span>
                        <button class="btn btn-primary" style="margin-top: 10px; width: 100%;" onclick="addToCart('Sewa Kasur Angin', 25000)">Sewa Sekarang</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- 5. HALAMAN TIKET (Direct Buy) -->
        <section id="tiket" class="hidden fade-in">
            <div class="btn-back" onclick="navigate('home')">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </div>

            <h2 class="section-title">Beli Tiket Masuk</h2>
            <div class="ticket-container">
                <div class="form-group">
                    <label class="form-label">Jenis Tiket</label>
                    <select class="form-control" id="ticket-type" onchange="updateTicketPrice()">
                        <option value="15000">Tiket Masuk Weekday - Rp 15.000</option>
                        <option value="20000">Tiket Masuk Weekend - Rp 20.000</option>
                        <option value="300000">Paralayang Single Flight - Rp 300.000</option>
                        <option value="600000">Paralayang Tandem (Video+Foto) - Rp 600.000</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label">Tanggal Kunjungan</label>
                    <input type="date" class="form-control" id="visit-date">
                </div>
                <div class="form-group">
                    <label class="form-label">Jumlah Peserta</label>
                    <input type="number" min="1" value="1" class="form-control" id="ticket-qty" onchange="updateTicketPrice()">
                </div>
                
                <div style="text-align: right; font-size: 1.2rem; font-weight: bold; margin-bottom: 20px;">
                    Total: <span id="total-price">Rp 15.000</span>
                </div>

                <button class="btn btn-primary" style="width: 100%;" onclick="buyTicketNow()">Lanjut Pembayaran</button>
            </div>
        </section>

        <!-- 6. HALAMAN CHECKOUT & PEMBAYARAN -->
        <section id="checkout" class="hidden fade-in">
            <div class="btn-back" onclick="navigate('home')">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </div>

            <h2 class="section-title">Pembayaran</h2>
            <div class="ticket-container">
                <!-- Order Summary -->
                <div style="background: #f9f9f9; padding: 15px; border-radius: 16px; margin-bottom: 20px; color: var(--text-dark);">
                    <h4>Ringkasan Pesanan</h4>
                    <p id="checkout-summary-text">...</p>
                    <h3 id="checkout-total" style="text-align: right; margin-top: 10px;">Rp 0</h3>
                </div>

                <!-- Payment Method -->
                <label class="form-label">Metode Pembayaran</label>
                <div class="payment-method">
                    <!-- QRIS -->
                    <div class="payment-option selected" id="opt-qris" onclick="selectPaymentMethod('qris')">
                        <i class="fas fa-qrcode" style="font-size: 1.5rem;"></i>
                        <p>QRIS</p>
                    </div>
                    <!-- E-Wallet -->
                    <div class="payment-option" id="opt-ewallet" onclick="selectPaymentMethod('ewallet')">
                        <i class="fas fa-wallet" style="font-size: 1.5rem;"></i>
                        <p>E-Wallet</p>
                    </div>
                </div>

                <!-- Area QRIS -->
                <div id="qris-section">
                    <div style="text-align: center;">
                        <p>Scan QRIS di bawah ini:</p>
                        <div class="qr-placeholder">
                            <img src="https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=BukitSempuPaymentExample" alt="QR Code">
                        </div>
                        <p style="font-size: 0.9rem; color: #777;">Menunggu pembayaran...</p>
                    </div>
                </div>

                <!-- Area E-Wallet (Hidden Default) -->
                <div id="ewallet-section" class="hidden">
                    <p style="text-align: center; margin-bottom: 15px;">Pilih E-Wallet Anda:</p>
                    <div class="ewallet-options">
                        <button class="ewallet-btn bg-dana" onclick="showToast('Membuka aplikasi DANA...')">
                            <i class="fas fa-wallet"></i> DANA
                        </button>
                        <button class="ewallet-btn bg-gopay" onclick="showToast('Membuka aplikasi GoPay...')">
                            <i class="fas fa-motorcycle"></i> GoPay
                        </button>
                        <button class="ewallet-btn bg-ovo" onclick="showToast('Membuka aplikasi OVO...')">
                            <i class="fas fa-circle"></i> OVO
                        </button>
                    </div>
                </div>

                <button class="btn btn-primary" id="btn-check-pay" style="width: 100%; margin-top: 15px;" onclick="simulatePaymentSuccess()">Konfirmasi Pembayaran</button>

                <!-- Digital Ticket (Hidden by default) -->
                <div id="digital-ticket" class="hidden digital-ticket">
                    <i class="fas fa-check-circle" style="font-size: 3rem; color: var(--primary-green); margin-bottom: 10px;"></i>
                    <h3>Pembayaran Berhasil!</h3>
                    <p>Tiket Anda telah dikirim ke email.</p>
                    <div style="border-top: 1px dashed #aaa; margin: 15px 0;"></div>
                    <h2 style="letter-spacing: 2px;">BK-SPU-8821</h2>
                    <p id="ticket-valid">Valid: 20 Oktober 2023</p>
                    <button class="btn btn-outline" style="color: var(--primary-green); border-color: var(--primary-green); margin-top: 15px;" onclick="navigate('home')">Kembali ke Beranda</button>
                </div>

            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer>
        <div class="footer-content">
            <div>
                <div class="footer-logo">
                    <img src="https://z-cdn-media.chatglm.cn/files/44d4f9ef-4048-40e9-b1bf-36f92745dc58.jpeg?auth_key=1868288875-c97ebf6fcdbe4fc892fec4fa5de25fc7-0-1fdc5aabbb889423a0324b76c5bc1e1f" alt="Logo Bukit Sempu" class="footer-logo-img">
                    <span>Bukit Sempu</span>
                </div>
                <p>Wisata alam paralayang terbaik di Indonesia. Nikmati keindahan dari ketinggian.</p>
            </div>
            <div>
                <h4>Kontak Kami</h4>
                <p style="margin-top: 10px;"><i class="fas fa-map-marker-alt"></i>&nbsp;&nbsp;Desa Cowek, Kecamatan Purwodadi, Kabupaten Pasuruan, Jawa Timur</p>
                <p><i class="fab fa-whatsapp"></i> +62 813 - 3325 - 6869</p>
                <p><i class="fas fa-envelope"></i> info@bukitsempu.com</p>
            </div>
            <div>
                <h4>Ikuti Kami</h4>
                <div class="social-icons" style="margin-top: 10px;">
                    <a href="https://www.instagram.com/paralayangsempu?igsh=MXo4MnI5eXpvbHNl"><i class="fab fa-instagram"></i></a>
                    <!-- FACEBOOK DIHAPUS, DIGANTI WHATSAPP -->
                    <a href="https://wa.me/6281333256869" target="_blank"><i class="fab fa-whatsapp"></i></a>
                </div>
            </div>
        </div>
        <div class="copyright">
            © 2026 Bukit Sempu. All Rights Reserved.
        </div>
    </footer>

    <!-- TOAST CONTAINER -->
    <div class="toast-container" id="toast-container"></div>

    <!-- JAVASCRIPT -->
    <script>
        // --- VARIABEL GLOBAL ---
        let cart = [];
        let currentTicketOrder = null; // Untuk pembelian tiket langsung

        // --- 1. NAVIGASI HALAMAN (SPA Logic) ---
        function navigate(sectionId) {
            document.querySelectorAll('section').forEach(sec => {
                sec.classList.add('hidden');
            });
            
            document.getElementById(sectionId).classList.remove('hidden');
            
            document.querySelectorAll('.nav-link').forEach(link => {
                link.classList.remove('active');
            });
            
            const activeLink = Array.from(document.querySelectorAll('.nav-link')).find(l => l.getAttribute('onclick').includes(sectionId));
            if(activeLink) activeLink.classList.add('active');

            window.scrollTo(0, 0);
        }

        // --- 2. TOAST NOTIFICATION SYSTEM (PENGGANTI ALERT) ---
        function showToast(message) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.innerHTML = `<i class="fas fa-info-circle"></i> ${message}`;
            
            container.appendChild(toast);
            
            // Hapus toast setelah 3 detik
            setTimeout(() => {
                toast.style.animation = 'fadeOut 0.3s ease forwards';
                toast.addEventListener('animationend', () => {
                    toast.remove();
                });
            }, 3000);
        }

        // --- 3. DARK MODE TOGGLE ---
        function toggleTheme() {
            const body = document.body;
            const currentTheme = body.getAttribute('data-theme');
            
            if (currentTheme === 'dark') {
                body.removeAttribute('data-theme');
                showToast('Mode Terang Diaktifkan');
            } else {
                body.setAttribute('data-theme', 'dark');
                showToast('Mode Gelap Diaktifkan');
            }
        }

        // --- 4. SEARCH TOGGLE ---
        function toggleSearch() {
            const overlay = document.getElementById('search-overlay');
            overlay.classList.toggle('hidden');
            if (!overlay.classList.contains('hidden')) {
                document.getElementById('search-input').focus();
            }
        }

        // --- 5. ACCOUNT DROPDOWN ---
        function toggleAccount() {
            const menu = document.getElementById('account-dropdown');
            menu.classList.toggle('show');
        }

        window.onclick = function(event) {
            if (!event.target.closest('.nav-icons')) {
                const dropdowns = document.getElementsByClassName("dropdown-menu");
                for (let i = 0; i < dropdowns.length; i++) {
                    const openDropdown = dropdowns[i];
                    if (openDropdown.classList.contains('show')) {
                        openDropdown.classList.remove('show');
                    }
                }
            }
        }

        // --- 6. PENGATURAN MODAL ---
        function openSettingsModal() {
            document.getElementById('settings-modal').classList.remove('hidden');
            document.getElementById('account-dropdown').classList.remove('show');
        }

        function closeSettingsModal() {
            document.getElementById('settings-modal').classList.add('hidden');
        }

        // --- 7. LOGOUT HANDLER ---
        function handleLogout() {
            showToast('Anda berhasil logout');
            setTimeout(() => {
                location.reload(); // Reload halaman untuk reset
            }, 1500);
        }

        // --- 8. CART SYSTEM (Untuk Kuliner, Camping, Penyewaan) ---
        
        function toggleCart() {
            document.getElementById('cart-panel').classList.toggle('open');
            document.getElementById('cart-overlay').classList.toggle('open');
            renderCart();
        }

        function addToCart(name, price) {
            // Cek apakah item sudah ada di cart
            const existingItem = cart.find(item => item.name === name);
            
            if (existingItem) {
                existingItem.qty++;
            } else {
                cart.push({ name, price, qty:1 });
            }
            
            showToast(`${name} masuk keranjang`);
            updateCartCount();
        }
        
        function removeFromCart(index) {
            cart.splice(index, 1);
            renderCart();
            updateCartCount();
        }
        
        function updateQty(index, change) {
            cart[index].qty += change;
            if(cart[index].qty < 1) cart[index].qty = 1;
            renderCart();
        }

        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.qty, 0);
            document.getElementById('cart-count').innerText = count;
        }

        function renderCart() {
            const container = document.getElementById('cart-items-container');
            const totalEl = document.getElementById('cart-total-price');
            container.innerHTML = '';
            
            if (cart.length === 0) {
                container.innerHTML = '<p style="text-align:center; margin-top:20px; color:#888;">Keranjang masih kosong.</p>';
                totalEl.innerText = 'Rp 0';
                return;
            }

            let total = 0;
            cart.forEach((item, index) => {
                total += item.price * item.qty;
                const itemHtml = `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <h4>${item.name}</h4>
                            <p>Rp ${item.price.toLocaleString('id-ID')}</p>
                        </div>
                        <div class="cart-controls">
                            <button class="qty-btn" onclick="updateQty(${index}, -1)">-</button>
                            <span>${item.qty}</span>
                            <button class="qty-btn" onclick="updateQty(${index}, 1)">+</button>
                            <i class="fas fa-trash" style="color:red; margin-left:8px; cursor:pointer;" onclick="removeFromCart(${index})"></i>
                        </div>
                    </div>
                `;
                container.innerHTML += itemHtml;
            });

            totalEl.innerText = 'Rp ' + total.toLocaleString('id-ID');
        }
        
        function processCheckout() {
            if(cart.length === 0) {
                showToast("Keranjang kosong!");
                return;
            }
            
            toggleCart(); // Tutup cart panel
            goToCheckoutFromCart();
        }

        // --- 9. TIKET LOGIC (Direct Buy) ---
        
        function updateTicketPrice() {
            const select = document.getElementById('ticket-type');
            const qtyInput = document.getElementById('ticket-qty');
            const priceText = document.getElementById('total-price');
            
            const price = parseInt(select.value);
            const qty = parseInt(qtyInput.value);
            const total = price * qty;
            
            priceText.innerText = 'Rp ' + total.toLocaleString('id-ID');
        }

        function buyTicketNow() {
            const select = document.getElementById('ticket-type');
            const text = select.options[select.selectedIndex].text;
            const price = parseInt(select.value);
            const qty = parseInt(document.getElementById('ticket-qty').value);
            const date = document.getElementById('visit-date').value;
            
            if(!date) {
                showToast("Pilih tanggal kunjungan!");
                return;
            }

            const name = text.split(' - ')[0];
            const total = price * qty;

            // Simpan data pesanan sementara
            currentTicketOrder = {
                name: name,
                date: date,
                price: price,
                qty: qty,
                total: total,
                fullDesc: `${name} (${date}) x${qty}`
            };

            // Masukkan ke UI Checkout
            const summaryEl = document.getElementById('checkout-summary-text');
            const totalEl = document.getElementById('checkout-total');
            
            summaryEl.innerHTML = `<p>${currentTicketOrder.fullDesc}</p><p style="font-size:0.9rem; color:#666;">@ Rp ${price.toLocaleString('id-ID')}</p>`;
            totalEl.innerText = 'Rp ' + total.toLocaleString('id-ID');

            // Reset tampilan pembayaran
            document.getElementById('qris-section').classList.remove('hidden');
            document.getElementById('ewallet-section').classList.add('hidden');
            document.getElementById('digital-ticket').classList.add('hidden');
            document.getElementById('btn-check-pay').style.display = 'block';
            document.getElementById('btn-check-pay').innerText = 'Konfirmasi Pembayaran';
            
            selectPaymentMethod('qris');
            navigate('checkout');
        }

        function goToCheckoutFromCart() {
            const summaryEl = document.getElementById('checkout-summary-text');
            const totalEl = document.getElementById('checkout-total');
            
            let total = 0;
            let summaryHtml = '<ul style="font-size:0.9rem; padding-left:20px; margin-bottom:10px;">';
            
            cart.forEach(item => {
                total += item.price * item.qty;
                summaryHtml += `<li>${item.name} x${item.qty}</li>`;
            });
            summaryHtml += '</ul>';
            
            summaryEl.innerHTML = summaryHtml;
            totalEl.innerText = 'Rp ' + total.toLocaleString('id-ID');

            // Reset tampilan pembayaran
            document.getElementById('qris-section').classList.remove('hidden');
            document.getElementById('ewallet-section').classList.add('hidden');
            document.getElementById('digital-ticket').classList.add('hidden');
            document.getElementById('btn-check-pay').style.display = 'block';
            document.getElementById('btn-check-pay').innerText = 'Konfirmasi Pembayaran';

            selectPaymentMethod('qris');
            navigate('checkout');
        }

        // --- 10. CHECKOUT & PEMBAYARAN ---
        function selectPaymentMethod(method) {
            const optQris = document.getElementById('opt-qris');
            const optEwallet = document.getElementById('opt-ewallet');
            const qrisSection = document.getElementById('qris-section');
            const ewalletSection = document.getElementById('ewallet-section');

            if (method === 'qris') {
                optQris.classList.add('selected');
                optEwallet.classList.remove('selected');
                qrisSection.classList.remove('hidden');
                ewalletSection.classList.add('hidden');
            } else {
                optQris.classList.remove('selected');
                optEwallet.classList.add('selected');
                qrisSection.classList.add('hidden');
                ewalletSection.classList.remove('hidden');
            }
        }

        function simulatePaymentSuccess() {
            const btn = document.getElementById('btn-check-pay');
            const qrSection = document.getElementById('qris-section');
            const ewalletSection = document.getElementById('ewallet-section');
            const ticketSection = document.getElementById('digital-ticket');

            btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Memproses...';
            
            setTimeout(() => {
                qrSection.classList.add('hidden');
                ewalletSection.classList.add('hidden');
                ticketSection.classList.remove('hidden');
                btn.style.display = 'none'; 
                showToast('Pembayaran Berhasil!');
                
                // Jika pembayaran berasal dari cart, kosongkan cart
                if(cart.length > 0) {
                    cart = [];
                    updateCartCount();
                }
                
                // Update detail tiket digital
                if(currentTicketOrder) {
                    document.getElementById('ticket-valid').innerText = 'Valid: ' + currentTicketOrder.date;
                } else {
                    document.getElementById('ticket-valid').innerText = 'Valid: Hari Ini';
                }
                
                currentTicketOrder = null;
            }, 1500);
        }

        document.addEventListener('DOMContentLoaded', () => {
            const today = new Date().toISOString().split('T')[0];
            const dateInput = document.getElementById('visit-date');
            if(dateInput) dateInput.value = today;
            updateTicketPrice();
        });

    </script>

</body></html>
