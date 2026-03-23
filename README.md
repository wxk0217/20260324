<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>《佛教小說集》數位導覽</title>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC:wght@400;600;700&family=Noto+Sans+TC:wght@400;600&display=swap" rel="stylesheet">
    <style>
        @keyframes bg-float {
            0%, 100% { transform: translateY(0px); opacity: 0.8; }
            50% { transform: translateY(-20px); opacity: 0.9; }
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-bg: #F5F3F0;
            --secondary-bg: #FBF9F7;
            --accent-gold: #D4AF8E;
            --accent-teal: #A8C5C0;
            --accent-purple: #C8B8D8;
            --accent-rose: #E8D4C4;
            --text-dark: #3D3D3D;
            --text-light: #6B6B6B;
            --border-color: #E8E4E0;
        }
        /* 解決標題圖案被擠開的問題 */
        .major-section h2 {
            justify-content: center !important;
        }
        .major-section h2 a {
            position: absolute !important;
            opacity: 0 !important;
            pointer-events: none !important;
        }

        body {
            font-family: 'Noto Serif TC', 'Georgia', serif;
            background-color: var(--primary-bg);
            color: var(--text-dark);
            line-height: 1.8;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 20% 50%, rgba(212, 175, 142, 0.03) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(168, 197, 192, 0.03) 0%, transparent 50%);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* 頂部導航欄 */
        header {
            background: linear-gradient(135deg, rgba(244, 241, 237, 0.98), rgba(212, 175, 142, 0.08));
            backdrop-filter: blur(10px);
            border-bottom: 2px solid var(--border-color);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }

        header .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 20px;
            min-height: auto;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--text-dark);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-icon {
            width: 45px;
            height: 45px;
            background: linear-gradient(135deg, var(--accent-gold), var(--accent-teal));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            animation: float 3s ease-in-out infinite;
            box-shadow: 0 4px 12px rgba(212, 175, 142, 0.3);
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-8px) rotate(5deg); }
        }

        .device-switcher {
            display: flex;
            gap: 8px;
            align-items: center;
            flex-wrap: nowrap;
            overflow: hidden;
        }

        .device-btn {
            padding: 8px 14px;
            border: 1px solid var(--border-color);
            background: var(--secondary-bg);
            color: var(--text-dark);
            border-radius: 6px;
            cursor: pointer;
            font-size: 12px;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .device-btn:hover {
            background: var(--accent-gold);
            color: white;
            border-color: var(--accent-gold);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(212, 175, 142, 0.3);
        }

        .device-btn.active {
            background: var(--accent-teal);
            color: white;
            border-color: var(--accent-teal);
            box-shadow: 0 4px 12px rgba(168, 197, 192, 0.4);
        }

        main {
            padding: 60px 0;
        }

        /* 英雄區域 */
        .hero {
            text-align: center;
            margin-bottom: 80px;
            position: relative;
            padding: 80px 40px;
            background: linear-gradient(135deg, rgba(212, 175, 142, 0.08), rgba(168, 197, 192, 0.08));
            border-radius: 20px;
            border: 2px solid var(--border-color);
            animation: fadeInDown 0.8s ease;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(212, 175, 142, 0.05) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: moveBackground 20s linear infinite;
        }

        @keyframes moveBackground {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        .hero > * {
            position: relative;
            z-index: 2;
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: 52px;
            margin-bottom: 20px;
            color: var(--text-dark);
            font-weight: 700;
            letter-spacing: 3px;
        }

        .hero p {
            font-size: 18px;
            color: var(--text-light);
            margin-bottom: 15px;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-decorative {
            position: absolute;
            opacity: 0.08;
            pointer-events: none;
            font-size: 100px;
        }

        .hero-decorative.left {
            top: auto;
            left: 30px;
            animation: rotate 30s linear infinite;
        }

        .hero-decorative.right {
            bottom: auto;
            right: 30px;
            animation: rotate 30s linear infinite reverse;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* 下拉選單區域 */
        .filter-section {
            background: var(--secondary-bg);
            padding: 40px;
            border-radius: 15px;
            margin-bottom: 60px;
            border: 1px solid var(--border-color);
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.04);
            position: relative;
            overflow: hidden;
        }

        .filter-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--accent-gold), var(--accent-teal), var(--accent-purple));
            animation: shimmer 3s ease-in-out infinite;
        }

        @keyframes shimmer {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        .filter-section h2 {
            font-size: 22px;
            margin-bottom: 25px;
            color: var(--text-dark);
            display: flex;
            align-items: center;
            gap: 12px;
            font-weight: 600;
        }

        .filter-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .filter-group {
            display: flex;
            flex-direction: column;
        }

        .filter-group label {
            font-size: 12px;
            font-weight: 600;
            color: var(--text-light);
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 1.5px;
        }

        .filter-group select {
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            background: white;
            color: var(--text-dark);
            font-family: 'Noto Sans TC', sans-serif;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .filter-group select:hover,
        .filter-group select:focus {
            border-color: var(--accent-gold);
            box-shadow: 0 0 12px rgba(212, 175, 142, 0.25);
            outline: none;
        }

        /* 大標題區域 */
        .major-section {
            margin-bottom: 80px;
            padding: 60px 40px;
            background: linear-gradient(135deg, rgba(212, 175, 142, 0.04), rgba(168, 197, 192, 0.04));
            border-radius: 20px;
            min-height: 500px;
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }

        .major-section::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(168, 197, 192, 0.05) 1px, transparent 1px);
            background-size: 60px 60px;
            animation: moveBackground 30s linear infinite;
        }

        .major-section > * {
            position: relative;
            z-index: 2;
        }

        .major-section h2 {
            font-size: 40px;
            font-weight: 700;
            color: var(--text-dark);
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 4px solid var(--accent-gold);
            letter-spacing: 2px;
            position: relative;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .major-section h2::before {
            content: '☸';
            font-size: 32px;
            opacity: 0.7;
            animation: float 3s ease-in-out infinite;
        }

        .major-section h2::after {
            content: '☸';
            font-size: 32px;
            opacity: 0.7;
            animation: float 3s ease-in-out infinite reverse;
        }

        /* 移除特定標題的符號 */
        #section-stats h2::before,
        #section-stats h2::after,
        #section-anti-communist h2::before,
        #section-anti-communist h2::after,
        #section-references h2::before,
        #section-references h2::after {
            content: '';
            display: none;
        }

        .major-section-content {
            flex: 1;
            padding: 20px 0;
            font-size: 16px;
            color: var(--text-light);
            line-height: 1.9;
        }

        .major-section-content ul {
            list-style: none;
            padding-left: 0;
        }

        .major-section-content li {
            padding: 10px 0;
            padding-left: 30px;
            position: relative;
        }

        .major-section-content li::before {
            content: '◆';
            position: absolute;
            left: 0;
            color: var(--accent-gold);
        }

        /* 表格區域 */
        .table-section {
            margin-bottom: 60px;
        }

        .table-section h2 {
            font-size: 28px;
            margin-bottom: 30px;
            color: var(--text-dark);
            text-align: center;
            position: relative;
            padding-bottom: 20px;
            font-weight: 700;
        }

        .table-section h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-purple), var(--accent-teal));
            border-radius: 2px;
            box-shadow: 0 2px 8px rgba(168, 197, 192, 0.3);
        }

        .table-wrapper {
            background: var(--secondary-bg);
            border-radius: 15px;
            border: 1px solid var(--border-color);
            overflow: hidden;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.04);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
        }

        thead {
            background: linear-gradient(135deg, rgba(212, 175, 142, 0.15), rgba(168, 197, 192, 0.15));
            border-bottom: 2px solid var(--border-color);
        }

        th {
            padding: 16px;
            text-align: left;
            font-weight: 600;
            color: var(--text-dark);
            text-transform: uppercase;
            font-size: 12px;
            letter-spacing: 1.5px;
        }

        td {
            padding: 14px 16px;
            border-bottom: 1px solid var(--border-color);
            color: var(--text-light);
        }

        tbody tr:hover {
            background: rgba(212, 175, 142, 0.08);
            transition: all 0.3s ease;
        }

        tbody tr:last-child td {
            border-bottom: none;
        }

        /* 統計區域 */
        .stats-section {
            margin-bottom: 60px;
            background: var(--secondary-bg);
            padding: 40px;
            border-radius: 15px;
            border: 1px solid var(--border-color);
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.04);
        }

        .stats-section h2 {
            font-size: 24px;
            margin-bottom: 30px;
            color: var(--text-dark);
            font-weight: 700;
            border-bottom: 3px solid var(--accent-gold);
            padding-bottom: 15px;
        }

        .stats-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .stat-item {
            padding: 20px;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 10px;
            border-left: 4px solid var(--accent-gold);
        }

        .stat-item h3 {
            font-size: 16px;
            color: var(--text-dark);
            margin-bottom: 15px;
            font-weight: 600;
        }

        .stat-item p {
            font-size: 14px;
            color: var(--text-light);
            line-height: 1.8;
        }

        /* 分類統計卡片 */
        .classification-section {
            margin-bottom: 60px;
        }

        .classification-section h2 {
            font-size: 28px;
            margin-bottom: 40px;
            color: var(--text-dark);
            text-align: center;
            position: relative;
            padding-bottom: 20px;
            font-weight: 700;
        }

        .classification-section h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-teal), var(--accent-purple));
            border-radius: 2px;
            box-shadow: 0 2px 8px rgba(168, 197, 192, 0.3);
        }

        .classification-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .classification-card {
            background: var(--secondary-bg);
            padding: 25px;
            border-radius: 12px;
            border: 1px solid var(--border-color);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.03);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .classification-card::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            background: linear-gradient(180deg, var(--accent-gold), var(--accent-teal), var(--accent-purple));
            transform: scaleY(0);
            transform-origin: top;
            transition: transform 0.3s ease;
        }

        .classification-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
        }

        .classification-card:hover::after {
            transform: scaleY(1);
        }

        .classification-card h3 {
            font-size: 16px;
            margin-bottom: 15px;
            color: var(--text-dark);
            font-weight: 600;
        }

        .classification-card ul {
            list-style: none;
        }

        .classification-card li {
            padding: 8px 0;
            color: var(--text-light);
            font-size: 14px;
            padding-left: 20px;
            position: relative;
        }

        .classification-card li::before {
            content: '◆';
            position: absolute;
            left: 0;
            color: var(--accent-gold);
        }

        /* 裝飾分隔線 */
        .decorative-divider {
            margin: 80px 0;
            text-align: center;
            font-size: 32px;
            animation: bounce 2s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        @keyframes pulse-glow {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        @keyframes spin-slow {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @keyframes sway {
            0%, 100% { transform: rotate(-2deg); }
            50% { transform: rotate(2deg); }
        }

        @keyframes shimmer-glow {
            0%, 100% { text-shadow: 0 0 5px rgba(212, 175, 142, 0.5); }
            50% { text-shadow: 0 0 15px rgba(212, 175, 142, 0.8); }
        }



        /* 漢堡菜單 */
        .hamburger-menu {
            display: flex;
            flex-direction: column;
            background: none;
            border: none;
            cursor: pointer;
            padding: 10px;
            gap: 6px;
        }

        .hamburger-menu span {
            width: 25px;
            height: 3px;
            background-color: var(--accent-gold);
            border-radius: 2px;
            transition: all 0.3s ease;
        }

        .hamburger-menu.active span:nth-child(1) {
            transform: rotate(45deg) translate(8px, 8px);
        }

        .hamburger-menu.active span:nth-child(2) {
            opacity: 0;
        }

        .hamburger-menu.active span:nth-child(3) {
            transform: rotate(-45deg) translate(7px, -7px);
        }

        /* 側邊菜單 */
        .sidebar-menu {
            position: fixed;
            left: 0;
            top: 0;
            width: 280px;
            height: 100vh;
            background: linear-gradient(135deg, rgba(245, 243, 240, 0.98), rgba(251, 249, 247, 0.98));
            backdrop-filter: blur(10px);
            transform: translateX(-100%);
            transition: transform 0.3s ease;
            z-index: 999;
            padding-top: 60px;
            box-shadow: 2px 0 20px rgba(0, 0, 0, 0.1);
            border-right: 2px solid var(--accent-gold);
        }

        .sidebar-menu.active {
            transform: translateX(0);
        }

        .sidebar-menu ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .sidebar-menu li {
            padding: 0;
        }

        .sidebar-menu a {
            display: block;
            padding: 16px 24px;
            color: var(--text-dark);
            text-decoration: none;
            border-left: 4px solid transparent;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .sidebar-menu a:hover {
            background-color: rgba(212, 175, 142, 0.1);
            border-left-color: var(--accent-gold);
            padding-left: 28px;
        }

        .close-menu {
            position: absolute;
            top: 20px;
            right: 20px;
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--text-dark);
            transition: transform 0.2s ease;
        }

        .close-menu:hover {
            transform: scale(1.2);
        }

        .sidebar-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0);
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s ease;
            z-index: 998;
        }

        .sidebar-overlay.active {
            background-color: rgba(0, 0, 0, 0.5);
            opacity: 1;
            pointer-events: auto;
        }

        /* 響應式漢堡菜單 */
        @media (max-width: 768px) {
            .device-switcher {
                display: none;
            }
        }

        /* 頁尾 */
        footer {
            background: transparent;
            border-top: 2px solid rgba(212, 175, 142, 0.3);
            padding: 50px 0;
            margin-top: 80px;
            text-align: center;
            color: var(--text-light);
            font-size: 14px;
            position: relative;
        }

        footer::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-gold), var(--accent-teal), transparent);
        }

        footer p {
            margin: 12px 0;
            text-align: center;
        }

        footer div {
            text-align: center;
        }

        /* 響應式設計 - 平板 */
        @media (max-width: 768px) {
            body {
                font-size: 14px;
            }

            .container {
                padding-left: 12px;
                padding-right: 12px;
            }

            .hero {
                padding: 30px 15px;
                min-height: 250px;
            }

            .hero h1 {
                font-size: 28px;
                margin-bottom: 12px;
            }

            .hero p {
                font-size: 13px;
            }

            .major-section {
                padding: 30px 15px;
                min-height: auto;
                margin-bottom: 40px;
            }

            .major-section h2 {
                font-size: 22px;
                margin-bottom: 15px;
            }

            /* 四個分類並列改為兩列 */
            div[style*="grid-template-columns: repeat(4"] {
                grid-template-columns: repeat(2, 1fr) !important;
                gap: 15px !important;
            }

            /* 表格響應 */
            table {
                font-size: 12px;
                width: 100% !important;
            }

            th, td {
                padding: 8px 6px !important;
            }

            .table-wrapper {
                overflow-x: auto;
                -webkit-overflow-scrolling: touch;
            }

            .filter-section {
                padding: 20px 15px;
                margin-bottom: 20px;
            }

            .filter-section h2 {
                font-size: 16px;
                margin-bottom: 15px;
            }

            .filter-row {
                grid-template-columns: 1fr !important;
                gap: 12px;
            }

            .stats-content {
                grid-template-columns: 1fr;
                gap: 15px;
            }

            .stat-item {
                padding: 15px;
            }

            /* 反共懷鄉網格改為單列 */
            div[style*="grid-template-columns: 1fr 1fr"] {
                grid-template-columns: 1fr !important;
            }
        }

        /* 超小屏幕 */
        @media (max-width: 480px) {
            header .container {
                padding: 12px 10px;
            }

            .logo {
                font-size: 18px;
                gap: 8px;
            }

            .logo-icon {
                width: 36px;
                height: 36px;
                font-size: 18px;
            }

            .device-switcher {
                gap: 4px;
            }

            .device-btn {
                padding: 6px 10px;
                font-size: 10px;
            }

            .container {
                padding-left: 10px;
                padding-right: 10px;
            }

            footer div {
                padding: 0 10px;
            }

            footer p {
                font-size: 12px;
                margin: 10px 0;
            }

            .hero {
                padding: 20px 10px;
                min-height: 200px;
            }

            .hero h1 {
                font-size: 20px;
                margin-bottom: 8px;
            }

            .hero p {
                font-size: 12px;
            }

            .major-section {
                padding: 20px 10px;
                margin-bottom: 30px;
            }

            .major-section h2 {
                font-size: 18px;
            }

            /* 四個分類改為單列 */
            div[style*="grid-template-columns: repeat(4"] {
                grid-template-columns: 1fr !important;
            }

            .filter-section {
                padding: 15px 10px;
            }

            .filter-section h2 {
                font-size: 14px;
            }

            table {
                font-size: 11px;
            }

            th, td {
                padding: 6px 4px !important;
            }

            .decorative-divider {
                font-size: 20px;
                margin: 30px 0;
            }
        }

        /* 平滑過渡 */
        * {
            transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease;
        }
    </style>
</head>
<body style="background-image: url('https://d2xsxph8kpxj0f.cloudfront.net/310519663161794951/aoyupUkZR2DscabuE8zpwF/ink-mountain-bg-green-Ttt9cd4TugRyNciqhiy27i.webp'); background-attachment: fixed; background-size: cover; background-repeat: no-repeat; background-position: center; position: relative;">
    <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: linear-gradient(180deg, rgba(245, 243, 240, 0.85), rgba(245, 243, 240, 0.9)); pointer-events: none; z-index: -1;"></div>
<!-- 頂部導航欄 -->
    <header>
        <div class="container">
            <div class="logo">
                <div class="logo-icon">🏮</div>
                <span>佛教小說集</span>
            </div>
            <button class="hamburger-menu" onclick="toggleMenu()">
                <span></span>
                <span></span>
                <span></span>
            </button>
            <div class="device-switcher">
                <button class="device-btn active" onclick="switchDevice('desktop')">💻 電腦</button>
                <button class="device-btn" onclick="switchDevice('tablet')">📱 平板</button>
                <button class="device-btn" onclick="switchDevice('mobile')">📲 手機</button>
            </div>
        </div>
    </header>

    <!-- 側邊菜單 -->
    <nav class="sidebar-menu" id="sidebarMenu">
        <button class="close-menu" onclick="toggleMenu()">✕</button>
        <ul>
            <li><a href="#section-classification" onclick="toggleMenu()">分類方法</a></li>
            <li><a href="#section-works" onclick="toggleMenu()">作品清單</a></li>
            <li><a href="#section-wu" onclick="toggleMenu()">吳賢愷分類</a></li>
            <li><a href="#section-stats" onclick="toggleMenu()">統計分析</a></li>
            <li><a href="#section-anticommunist" onclick="toggleMenu()">反共文學</a></li>
            <li><a href="#section-research" onclick="toggleMenu()">核心研究主題</a></li>
            <li><a href="#section-references" onclick="toggleMenu()">參考文獻</a></li>
        </ul>
    </nav>
    <div class="sidebar-overlay" id="sidebarOverlay" onclick="toggleMenu()"></div>

    <!-- 主要內容 -->
    <main class="container">
        <!-- 英雄區域 -->
        <section class="hero">
            <div class="hero-decorative left">🌸</div>
            <h1>《佛教小說集》</h1>
            <p>朱橋編著 | 佛教文化出版社，1960年11月</p>

            <div class="hero-decorative right">🌸</div>
        </section>

        <!-- 分類方法標題 -->
        <section id="section-classification" style="margin-bottom: 60px; padding: 50px 40px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.12), rgba(168, 197, 192, 0.12)); border-radius: 20px; border: 2px solid var(--border-color); position: relative; overflow: hidden;">
            <div style="position: absolute; top: 20px; right: 30px; font-size: 60px; opacity: 0.15; animation: rotate 30s linear infinite;">☸</div>
            <div style="position: absolute; bottom: 20px; left: 30px; font-size: 60px; opacity: 0.15; animation: rotate 30s linear infinite reverse;">♀</div>
            <div style="position: absolute; top: 50%; right: 10%; font-size: 50px; opacity: 0.1; animation: float 4s ease-in-out infinite;">♕</div>
            <div style="position: absolute; bottom: 30%; left: 10%; font-size: 50px; opacity: 0.1; animation: bounce 2s ease-in-out infinite;">♗</div>
            <h2 style="font-size: 44px; font-weight: 700; color: var(--text-dark); margin: 0; letter-spacing: 3px; position: relative; z-index: 2; text-align: center; padding-bottom: 20px; border-bottom: 4px solid var(--accent-gold);">分類方法</h2>
        </section>

        <!-- 故事性質分類 - 四個粗體字標題 -->

        <!-- 四個分類並列 -->
        <div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; margin-bottom: 40px;">
            <!-- 范純武 -->
            <div style="padding: 25px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.1), rgba(212, 175, 142, 0.05)); border-left: 4px solid var(--accent-gold); border-radius: 8px;">
                <h3 style="font-size: 20px; font-weight: 700; color: var(--accent-gold); margin-top: 0; margin-bottom: 15px;">范純武</h3>
                <ul style="font-size: 15px; line-height: 2; color: var(--text-light); margin: 0; padding-left: 20px;">
                    <li>新創作題材的小說</li>
                    <li>雜揉個人經驗的小說</li>
                    <li>改編佛教故事的小說</li>
                </ul>
            </div>

            <!-- 李玉珍 -->
            <div style="padding: 25px; background: linear-gradient(135deg, rgba(168, 197, 192, 0.1), rgba(168, 197, 192, 0.05)); border-left: 4px solid var(--accent-teal); border-radius: 8px;">
                <h3 style="font-size: 20px; font-weight: 700; color: var(--accent-teal); margin-top: 0; margin-bottom: 15px;">李玉珍</h3>
                <ul style="font-size: 15px; line-height: 2; color: var(--text-light); margin: 0; padding-left: 20px;">
                    <li>改寫的佛經故事</li>
                    <li>鄉野傳奇式的勸善小說</li>
                    <li>以家庭情愛印證佛法的小說</li>
                    <li>遊歷寺院和僧尼交遊的記載</li>
                    <li>反共懷鄉的小說創作</li>
                    <li>無法歸類</li>
                </ul>
            </div>

            <!-- 丁敏 -->
            <div style="padding: 25px; background: linear-gradient(135deg, rgba(200, 184, 216, 0.1), rgba(200, 184, 216, 0.05)); border-left: 4px solid var(--accent-purple); border-radius: 8px;">
                <h3 style="font-size: 20px; font-weight: 700; color: var(--accent-purple); margin-top: 0; margin-bottom: 15px;">丁敏</h3>
                <ul style="font-size: 15px; line-height: 2; color: var(--text-light); margin: 0; padding-left: 20px;">
                    <li>借用佛教題材</li>
                    <li>賦予佛教神佛中國性格</li>
                    <li>以佛教故事和典故為敘述結構</li>
                    <li>以具體事物譬喻佛法</li>
                    <li>以佛教幻設和當下停格的時間為軸</li>
                    <li>因果報應</li>
                </ul>
            </div>

            <!-- 吳賢愷 -->
            <div style="padding: 25px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.08), rgba(168, 197, 192, 0.08)); border-left: 4px solid var(--accent-gold); border-radius: 8px;">
                <h3 style="font-size: 20px; font-weight: 700; color: var(--text-dark); margin-top: 0; margin-bottom: 15px;">吳賢愷</h3>
                <ul style="font-size: 15px; line-height: 2; color: var(--text-light); margin: 0; padding-left: 20px;">
                    <li>佛教故事改編</li>
                    <li>佛教哲理和戒律</li>
                    <li>果報思想</li>
                    <li>佛、僧人、寺廟對小說情節有推進作用</li>
                    <li>佛、僧人、寺廟作為背景或敘述填充</li>
                    <li>關係不明</li>
                </ul>
            </div>
        </div>

        <!-- 裝飾分隔線 -->
        <div class="decorative-divider">🌸 ❖ 🌸</div>

        <!-- 篩選與查詢 + 作品清單合併 -->
        <section id="section-works" class="table-section">
            <div class="filter-section" id="section-filter" style="margin-bottom: 30px;">
                <h2>🔍 篩選與查詢</h2>
                <div class="filter-row">
                    <div class="filter-group">
                        <label for="filter-author">作者身分</label>
                        <select id="filter-author" onchange="filterData()">
                            <option value="">全部</option>
                            <option value="僧">僧尼</option>
                            <option value="軍">軍職作家</option>
                            <option value="普通">普通作家</option>
                            <option value="虔誠">虔誠信徒</option>
                        </select>
                    </div>
                    <div class="filter-group">
                        <label for="filter-type">佛教性質</label>
                        <select id="filter-type" onchange="filterData()">
                            <option value="">全部</option>
                            <option value="填充">佛、僧人、寺廟作為背景或敘述填充</option>
                            <option value="推進">佛、僧人、寺廟對小說情節有推進作用</option>
                            <option value="哲理">佛教哲理和戒律</option>
                            <option value="未知">關係不明</option>
                            <option value="果報">果報思想</option>
                            <option value="改編">佛教故事改編</option>
                        </select>
                    </div>
                </div>
            </div>
            <h2>📑 作品清單</h2>
            <div class="table-wrapper">
                <table id="worksTable">
                    <thead>
                        <tr>
                            <th>作者</th>
                            <th>篇名</th>
                            <th>作者身分</th>
                            <th>原出處</th>
                            <th>佛教性質</th>
                        </tr>
                    </thead>
                    <tbody id="tableBody">
                        <!-- 動態填充 -->
                    </tbody>
                </table>
            </div>
        </section>

        <!-- 統計數據 -->
        <section id="section-stats" class="stats-section">
            <h2>📊 統計數據</h2>
            <div class="stats-content">
                <div class="stat-item">
                    <h3>作品總數與作者身分</h3>
                    <p>共計：32 篇<br>
                    作者曾任軍職者：13 人<br>
                    作者為僧尼：5 人<br>
                    較虔誠者：5 人（兩人重複為軍職）<br>
                    普通作家：11 人</p>
                </div>

                <div class="stat-item">
                    <h3>佛教性質分類比例</h3>
                    <p>佛教故事改編：1<br>
                    佛教哲理和戒律：7<br>
                    果報思想：1<br>
                    佛、僧人、寺廟對小說情節有推進作用：9<br>
                    佛、僧人、寺廟作為背景或敘述填充：10<br>
                    關係不明：4</p>
                </div>


            </div>
        </section>

        <!-- 身分別統計表 -->
        <section class="major-section">
            <h2>身分別統計表</h2>
            <div class="major-section-content">
                <div style="overflow-x: auto;">
                    <table style="width: 100%; border-collapse: collapse; font-size: 15px;">
                        <thead>
                            <tr style="background: linear-gradient(135deg, rgba(212, 175, 142, 0.15), rgba(168, 197, 192, 0.15)); border-bottom: 2px solid var(--border-color);">
                                <th style="padding: 16px; text-align: left; font-weight: 600; color: var(--text-dark);">身分別</th>
                                <th style="padding: 16px; text-align: center; font-weight: 600; color: var(--text-dark);">人數</th>
                                <th style="padding: 16px; text-align: center; font-weight: 600; color: var(--text-dark);">佛教程度中高</th>
                                <th style="padding: 16px; text-align: center; font-weight: 600; color: var(--text-dark);">佛教程度高</th>
                                <th style="padding: 16px; text-align: center; font-weight: 600; color: var(--text-dark);">反共愛國</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr style="border-bottom: 1px solid var(--border-color);">
                                <td style="padding: 14px 16px; color: var(--text-light);"><strong>軍職</strong></td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">13</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">6 (46%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">1 (8%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">4 (31%)</td>
                            </tr>
                            <tr style="border-bottom: 1px solid var(--border-color);">
                                <td style="padding: 14px 16px; color: var(--text-light);"><strong>僧尼</strong></td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">5</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">5 (100%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">4 (80%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">1 (20%)</td>
                            </tr>
                            <tr style="border-bottom: 1px solid var(--border-color);">
                                <td style="padding: 14px 16px; color: var(--text-light);"><strong>虔誠者</strong></td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">5</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">3 (60%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">1 (20%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">0 (0%)</td>
                            </tr>
                            <tr style="border-bottom: 1px solid var(--border-color);">
                                <td style="padding: 14px 16px; color: var(--text-light);"><strong>普通作家</strong></td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">11</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">5 (45%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">2 (19%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-light);">0 (0%)</td>
                            </tr>
                            <tr style="background: rgba(212, 175, 142, 0.08); border-bottom: 1px solid var(--border-color);">
                                <td style="padding: 14px 16px; color: var(--text-dark); font-weight: 600;"><strong>總計</strong></td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-dark); font-weight: 600;">32</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-dark); font-weight: 600;">19 (60%)</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-dark); font-weight: 600;">8</td>
                                <td style="padding: 14px 16px; text-align: center; color: var(--text-dark); font-weight: 600;">5</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- 反共懷鄉 VS 反共愛國 -->
        <section class="major-section" id="section-anticommunist" style="margin-bottom: 80px; padding: 40px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.04), rgba(168, 197, 192, 0.04));">
            <h2 style="font-size: 40px; font-weight: 700; color: var(--text-dark); margin-bottom: 30px; padding-bottom: 20px; border-bottom: 4px solid var(--accent-gold); letter-spacing: 2px; position: relative; display: flex; align-items: center; gap: 15px;">
                反共懷鄉 VS 反共愛國
            </h2>
            <div class="major-section-content" style="font-size: 17px; line-height: 2.2;">
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 30px; margin-bottom: 40px;">
                    <div style="padding: 30px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.15), rgba(212, 175, 142, 0.05)); border-left: 6px solid var(--accent-gold); border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);">
                        <h3 style="font-size: 22px; font-weight: 700; color: var(--accent-gold); margin-top: 0; margin-bottom: 20px; display: flex; align-items: center; gap: 8px;">
                            <span style="font-size: 20px;">✦</span>
                            李玉珍十一篇
                        </h3>
                        <p style="font-size: 16px; line-height: 2.4; color: var(--text-light); margin: 0;">
                            〈紅葉〉、〈雨〉、〈人間的奇蹟〉、〈紅塵〉、〈三角〉、〈喜帖〉、〈朝來寒雨晚來風〉、〈荒寺的一夜〉、〈普陀緣〉、〈重生〉、〈佈施〉
                        </p>
                    </div>
                    <div style="padding: 30px; background: linear-gradient(135deg, rgba(168, 197, 192, 0.15), rgba(168, 197, 192, 0.05)); border-left: 6px solid var(--accent-teal); border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);">
                        <h3 style="font-size: 22px; font-weight: 700; color: var(--accent-teal); margin-top: 0; margin-bottom: 20px; display: flex; align-items: center; gap: 8px;">
                            <span style="font-size: 20px;">◆</span>
                            吳賢愷五篇
                        </h3>
                        <p style="font-size: 16px; line-height: 2.4; color: var(--text-light); margin: 0;">
                            〈普陀緣〉、〈紅塵〉、〈重生〉、〈三角〉、〈朝來寒雨晚來風〉
                        </p>
                    </div>
                </div>
                <div style="padding: 25px; background: rgba(200, 184, 216, 0.1); border-left: 4px solid var(--accent-purple); border-radius: 6px; margin-top: 30px;">
                    <p style="font-size: 16px; line-height: 2.2; color: var(--text-light); margin: 0; font-style: italic;">
                        反共文學與懷鄉文學是否可以等同？反共文學是否可以稱為一種類型
                    </p>
                </div>
            </div>
        </section>

        <!-- 核心研究主題 -->
        <section id="section-research" style="margin-bottom: 80px;">
            <h2 style="font-size: 40px; font-weight: 700; color: var(--text-dark); margin-bottom: 40px; padding-bottom: 20px; border-bottom: 4px solid var(--accent-gold); text-align: center; letter-spacing: 2px;">📖 核心研究主題</h2>
            <div style="display: flex; flex-direction: column; gap: 25px;">
                <!-- 第一格: 反共文學和戰鬥文藝的衰退 -->
                <div style="padding: 30px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.08), rgba(168, 197, 192, 0.08)); border-left: 6px solid var(--accent-gold); border-radius: 8px;">
                    <h3 style="font-size: 24px; font-weight: 700; color: var(--text-dark); margin-top: 0; margin-bottom: 20px; display: flex; align-items: center; gap: 10px;">
                        <span style="font-size: 20px; animation: float 3s ease-in-out infinite;">☸</span>
                        反共文學和戰鬥文藝的衰退——1956年《文藝創作》停刊和文獎會解散
                    </h3>
                    <p style="font-size: 17px; line-height: 2.2; color: var(--text-light); margin: 0;">
                        1955年戰鬥文藝口號的提出標示著反共文學的挫敗<br>
                        陳明成：美國壓制和張道藩的失勢<br>
                        封德屏：張道藩專心投入公務<br>
                        陳康芬：如抒發個人在經歷大時代動亂之痛的懷鄉思憂之作，有助於國民黨「中國化」政策的各式歷史小說與演義傳奇、女性作家為主的瑣碎的家庭與生活細節的抒情描述、具有正向人性意義的「純文藝」創作……等，仍占有極高的出版比例。這顯示反共文學雖然是戰後台灣五〇年代的主流文學類型，但整體文學發展還並不限於主義政治話語的文學獨白基調。<br>
                        鍾肇政：將日本視為一種經驗
                    </p>
                </div>

                <!-- 第二格: 戰鬥文藝 -->
                <div style="padding: 30px; background: linear-gradient(135deg, rgba(168, 197, 192, 0.08), rgba(200, 184, 216, 0.08)); border-left: 6px solid var(--accent-teal); border-radius: 8px;">
                    <h3 style="font-size: 24px; font-weight: 700; color: var(--text-dark); margin-top: 0; margin-bottom: 20px; display: flex; align-items: center; gap: 10px;">
                        <span style="font-size: 20px; animation: float 3s ease-in-out infinite reverse;">☸</span>
                        戰鬥文藝——一種沒有類型的類型
                    </h3>
                    <p style="font-size: 17px; line-height: 2.2; color: var(--text-light); margin: 0;">
                        反共文學？<br>
                        民族主義？<br>
                        張俐璇：健康寫實主義＝「民生建設的實踐＋大同思想的倡議」<br>
                        <strong style="font-size: 18px; color: var(--accent-gold);">「戰鬥」作為一種人生的精神</strong><br>
                        虞君質：意思是不限於血反共抵俑和爭取民主自由的政治或軍事鬥爭的作品，才算是今日需要的戰鬥文藝；不，除此之外，在面對現實的戰鬥任務的前提之下，凡是表揚人性以否定共匪的發展受性的作品。朝氣蓬勃富戰鬥精神的作品，都是今日需要的戰鬥文藝。
                    </p>
                </div>

                <!-- 第三格: 軍中作家 -->
                <div style="padding: 30px; background: linear-gradient(135deg, rgba(200, 184, 216, 0.08), rgba(212, 175, 142, 0.08)); border-left: 6px solid var(--accent-purple); border-radius: 8px;">
                    <h3 style="font-size: 24px; font-weight: 700; color: var(--text-dark); margin-top: 0; margin-bottom: 20px; display: flex; align-items: center; gap: 10px;">
                        <span style="font-size: 20px; animation: sway 2s ease-in-out infinite;">☸</span>
                        軍中作家不等於軍人作家不等於反共作家
                    </h3>
                    <p style="font-size: 17px; line-height: 2.2; color: var(--text-light); margin: 0;">
                        翁伯川：《「軍中三劍客」的文學創作與活動研究》<br>
                        陳建忠：「和而不同」的書寫策略
                    </p>
                </div>

            </div>
        </section>




        <!-- 參考文獻章節 -->
        <section class="major-section" id="section-references" style="margin-bottom: 0; min-height: auto; padding: 40px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.04), rgba(168, 197, 192, 0.04));">
            <h2 style="font-size: 40px; font-weight: 700; color: var(--text-dark); margin-bottom: 30px; padding-bottom: 20px; border-bottom: 4px solid var(--accent-gold); letter-spacing: 2px; position: relative; display: flex; align-items: center; gap: 15px;">
                參考文獻
            </h2>
            <div class="major-section-content" style="font-size: 17px; line-height: 2.2;">
                <p style="font-weight: 600; color: var(--accent-gold); margin-bottom: 20px;">反共文學和戰鬥文藝的衰退</p>
                <p style="margin-bottom: 20px;">
                    陳明成：〈反攻與反共：關鍵年代的關鍵年份--臺灣文壇「一九五六」的再考察〉，《文學與社會學術研討會：2004年青年文學會議論文集》臺南市：台灣文學館，2005。<br>
                    封德屏：《國民黨文藝政策與實踐（1928-1981）》，臺北市：淡江大學中國文學系博士論文，2009。<br>
                    陳康芬：《政治意識形態、文學歷史與文學敘事——臺灣五○年代反共文學研究》，花蓮縣：國立東華大學中國語文學系博士論文，2007。<br>
                    鍾肇政：《台灣文學十講》，臺北市：前衛出版社，2000。
                </p>

                <p style="font-weight: 600; color: var(--accent-gold); margin-bottom: 20px; margin-top: 30px;">戰鬥文藝——一種沒有類型的類型</p>
                <p style="margin-bottom: 20px;">
                    張俐璇：《建構與流變：「寫實主義」與臺灣小說生產》，臺北市：秀威資訊科技，2016。<br>
                    虞君質：〈建立戰鬥的批評〉，《文藝月報》第2卷第4期（1955年4月）。
                </p>

                <p style="font-weight: 600; color: var(--accent-gold); margin-bottom: 20px; margin-top: 30px;">軍中作家不等於軍人作家不等於反共作家</p>
                <p>
                    翁伯川：《「軍中三劍客」的文學創作與活動研究》，臺南：國立成功大學中國文學系博士論文，2017。<br>
                    陳建忠：〈反共作家？鄉土作家？或現代主義作家？：朱西甯研究史小考〉《記憶流域：臺灣歷史書寫與記憶政治》，新北市：南十字星文化工作室有限公司，2018。
                </p>
            </div>
        </section>
    </main>

    <!-- 頁尾 -->
    <footer>
        <div style="max-width: 1200px; margin: 0 auto; padding: 0 20px;">
            <p>《佛教小說集》數位導覽 | 朱橋編著 | 佛教文化出版社，1960年11月</p>
            <p>本網頁為學術研究用途，展示佛教小說集的內容分析與統計</p>
            <p style="margin-top: 20px; font-size: 14px; font-weight: 600; color: var(--accent-teal);">
                製作者：國立臺灣大學中文系博士班 吳賢愷
            </p>
            <p style="margin-top: 20px; font-size: 12px; opacity: 0.7;">
                🌸 淡雅荘重的佛教美學設計 | 響應式裝置預覽 | 學術內容展示 🌸
            </p>
        </div>
    </footer>

    <script>
        // 完整作品數據
        const worksData = [
            { author: '摩迦（星雲）', title: '不同的愛', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '常覺', title: '一顆沉沒的摩尼珠', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '自立', title: '回頭是岸', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '孟瑤', title: '聲色場', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '郭嗣汾', title: '紅葉', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '周君亮', title: '荒寺之一夜', identity: '普通', source: '《暢流》19卷3期，1959年3月', type: '佛教哲理和戒律' },
            { author: '公孫嬿', title: '普陀緣', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '楚軍', title: '雨', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '魏希文', title: '胡家父子', identity: '軍', source: '《晨光》7卷10期，1959年12月', type: '關係不明' },
            { author: '墨人', title: '馬腳', identity: '軍', source: '未知', type: '關係不明' },
            { author: '劉心皇', title: '幻情錄', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '西帆', title: '人間的奇蹟', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '鄧文來', title: '小蘭', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '鐘雷', title: '紅塵', identity: '軍', source: '《晨光》5卷6-8期，1957年8-10月', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '繁露', title: '髮緣', identity: '普通', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '喬霖（彭樹楷）', title: '重生', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '潘琦君', title: '悟', identity: '虔誠', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '張慈蓮', title: '三角', identity: '僧', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '胡國偉', title: '桃花開九月', identity: '普通', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '絜邨', title: '須大拏太子的故事', identity: '虔誠', source: '未知', type: '佛教故事改編' },
            { author: '杜雲之', title: '大慈悲嶺', identity: '普通', source: '未知', type: '佛教哲理和戒律' },
            { author: '陳劍慧', title: '自殺者的悲歌', identity: '軍、虔誠', source: '未知', type: '佛教哲理和戒律' },
            { author: '宣建人', title: '為善最樂', identity: '軍', source: '未知', type: '果報思想' },
            { author: '志琨', title: '喜帖', identity: '普通', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '鄭心本', title: '皈依', identity: '虔誠', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '觀心', title: '樓上樓下', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '謝冰瑩', title: '永恆的友情', identity: '軍、虔誠', source: '未知', type: '關係不明' },
            { author: '阮囊', title: '朝來寒雨晚來風', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '林海音', title: '母親的祕密', identity: '普通', source: '未知', type: '關係不明' },
            { author: '曼濤', title: '布施', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '蕭傳文', title: '白狐', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '朱橋', title: '畫像', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' }
        ];

        // 吳賢愷分類表數據
        const wuData = [
            { author: '摩迦（星雲）', title: '不同的愛', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '常覺', title: '一顆沉沒的摩尼珠', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '自立', title: '回頭是岸', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '孟瑤', title: '聲色場', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '郭嗣汾', title: '紅葉', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '周君亮', title: '荒寺之一夜', identity: '普通', source: '《暢流》19卷3期，1959年3月', type: '佛教哲理和戒律' },
            { author: '公孫嬿', title: '普陀緣', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '楚軍', title: '雨', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '魏希文', title: '胡家父子', identity: '軍', source: '《晨光》7卷10期，1959年12月', type: '關係不明' },
            { author: '墨人', title: '馬腳', identity: '軍', source: '未知', type: '關係不明' }
        ];

        // 初始化表格
        function initTable() {
            const tbody = document.getElementById('tableBody');
            tbody.innerHTML = '';
            worksData.forEach(work => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${work.author}</td>
                    <td>${work.title}</td>
                    <td>${work.identity}</td>
                    <td>${work.source}</td>
                    <td>${work.type}</td>
                `;
                tbody.appendChild(row);
            });

            // 初始化吳賢愷表
            const wuBody = document.getElementById('wuTableBody');
            wuBody.innerHTML = '';
            wuData.forEach(work => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${work.author}</td>
                    <td>${work.title}</td>
                    <td>${work.identity}</td>
                    <td>${work.source}</td>
                    <td>${work.type}</td>
                `;
                wuBody.appendChild(row);
            });
        }

        // 過濾數據
        // 漢堡菜單切換
        function toggleMenu() {
            const menu = document.getElementById('sidebarMenu');
            const overlay = document.getElementById('sidebarOverlay');
            const hamburger = document.querySelector('.hamburger-menu');
            
            menu.classList.toggle('active');
            overlay.classList.toggle('active');
            hamburger.classList.toggle('active');
        }

        function filterData() {
            const author = document.getElementById('filter-author').value;
            const type = document.getElementById('filter-type').value;

            const tbody = document.getElementById('tableBody');
            tbody.innerHTML = '';

            const filtered = worksData.filter(work => {
                const authorMatch = !author || work.identity.includes(author);
                const typeMatch = !type || work.type.includes(type);
                return authorMatch && typeMatch;
            });

            filtered.forEach(work => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${work.author}</td>
                    <td>${work.title}</td>
                    <td>${work.identity}</td>
                    <td>${work.source}</td>
                    <td>${work.type}</td>
                `;
                tbody.appendChild(row);
            });
        }

        // 裝置切換功能
        function switchDevice(device) {
            document.querySelectorAll('.device-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            console.log('切換到裝置:', device);
        }

        // 頁面加載時初始化
        document.addEventListener('DOMContentLoaded', function() {
            initTable();
        });
    </script>
</body>
</html>

        <!-- 參考文獻章節 -->
        <section class="major-section" id="section-references" style="margin-bottom: 0; min-height: auto; padding: 40px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.04), rgba(168, 197, 192, 0.04));">
            <h2 style="font-size: 40px; font-weight: 700; color: var(--text-dark); margin-bottom: 30px; padding-bottom: 20px; border-bottom: 4px solid var(--accent-gold); letter-spacing: 2px; position: relative; display: flex; align-items: center; gap: 15px;">
                參考文獻
            </h2>
            <div class="major-section-content" style="font-size: 17px; line-height: 2.2;">
                <p style="font-weight: 600; color: var(--accent-gold); margin-bottom: 20px;">反共文學和戰鬥文藝的衰退</p>
                <p style="margin-bottom: 20px;">
                    陳明成：〈反攻與反共：關鍵年代的關鍵年份--臺灣文壇「一九五六」的再考察〉，《文學與社會學術研討會：2004年青年文學會議論文集》臺南市：台灣文學館，2005。<br>
                    封德屏：《國民黨文藝政策與實踐（1928-1981）》，臺北市：淡江大學中國文學系博士論文，2009。<br>
                    陳康芬：《政治意識形態、文學歷史與文學敘事——臺灣五○年代反共文學研究》，花蓮縣：國立東華大學中國語文學系博士論文，2007。<br>
                    鍾肇政：《台灣文學十講》，臺北市：前衛出版社，2000。
                </p>

                <p style="font-weight: 600; color: var(--accent-gold); margin-bottom: 20px; margin-top: 30px;">戰鬥文藝——一種沒有類型的類型</p>
                <p style="margin-bottom: 20px;">
                    張俐璇：《建構與流變：「寫實主義」與臺灣小說生產》，臺北市：秀威資訊科技，2016。<br>
                    虞君質：〈建立戰鬥的批評〉，《文藝月報》第2卷第4期（1955年4月）。
                </p>

                <p style="font-weight: 600; color: var(--accent-gold); margin-bottom: 20px; margin-top: 30px;">軍中作家不等於軍人作家不等於反共作家</p>
                <p>
                    翁伯川：《「軍中三劍客」的文學創作與活動研究》，臺南：國立成功大學中國文學系博士論文，2017。<br>
                    陳建忠：〈反共作家？鄉土作家？或現代主義作家？：朱西甯研究史小考〉《記憶流域：臺灣歷史書寫與記憶政治》，新北市：南十字星文化工作室有限公司，2018。
                </p>
            </div>
        </section>
    </main>

    <!-- 頁尾 -->
    <footer>
        <div style="max-width: 1200px; margin: 0 auto; padding: 0 20px;">
            <p>《佛教小說集》數位導覽 | 朱橋編著 | 佛教文化出版社，1960年11月</p>
            <p>本網頁為學術研究用途，展示佛教小說集的內容分析與統計</p>
            <p style="margin-top: 20px; font-size: 14px; font-weight: 600; color: var(--accent-teal);">
                製作者：國立臺灣大學中文系博士班 吳賢愷
            </p>
            <p style="margin-top: 20px; font-size: 12px; opacity: 0.7;">
                🌸 淡雅荘重的佛教美學設計 | 響應式裝置預覽 | 學術內容展示 🌸
            </p>
        </div>
    </footer>

    <script>
        // 完整作品數據
        const worksData = [
            { author: '摩迦（星雲）', title: '不同的愛', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '常覺', title: '一顆沉沒的摩尼珠', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '自立', title: '回頭是岸', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '孟瑤', title: '聲色場', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '郭嗣汾', title: '紅葉', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '周君亮', title: '荒寺之一夜', identity: '普通', source: '《暢流》19卷3期，1959年3月', type: '佛教哲理和戒律' },
            { author: '公孫嬿', title: '普陀緣', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '楚軍', title: '雨', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '魏希文', title: '胡家父子', identity: '軍', source: '《晨光》7卷10期，1959年12月', type: '關係不明' },
            { author: '墨人', title: '馬腳', identity: '軍', source: '未知', type: '關係不明' },
            { author: '劉心皇', title: '幻情錄', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '西帆', title: '人間的奇蹟', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '鄧文來', title: '小蘭', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '鐘雷', title: '紅塵', identity: '軍', source: '《晨光》5卷6-8期，1957年8-10月', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '繁露', title: '髮緣', identity: '普通', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '喬霖（彭樹楷）', title: '重生', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '潘琦君', title: '悟', identity: '虔誠', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '張慈蓮', title: '三角', identity: '僧', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '胡國偉', title: '桃花開九月', identity: '普通', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '絜邨', title: '須大拏太子的故事', identity: '虔誠', source: '未知', type: '佛教故事改編' },
            { author: '杜雲之', title: '大慈悲嶺', identity: '普通', source: '未知', type: '佛教哲理和戒律' },
            { author: '陳劍慧', title: '自殺者的悲歌', identity: '軍、虔誠', source: '未知', type: '佛教哲理和戒律' },
            { author: '宣建人', title: '為善最樂', identity: '軍', source: '未知', type: '果報思想' },
            { author: '志琨', title: '喜帖', identity: '普通', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '鄭心本', title: '皈依', identity: '虔誠', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '觀心', title: '樓上樓下', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '謝冰瑩', title: '永恆的友情', identity: '軍、虔誠', source: '未知', type: '關係不明' },
            { author: '阮囊', title: '朝來寒雨晚來風', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '林海音', title: '母親的祕密', identity: '普通', source: '未知', type: '關係不明' },
            { author: '曼濤', title: '布施', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '蕭傳文', title: '白狐', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '朱橋', title: '畫像', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' }
        ];

        // 吳賢愷分類表數據
        const wuData = [
            { author: '摩迦（星雲）', title: '不同的愛', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '常覺', title: '一顆沉沒的摩尼珠', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '自立', title: '回頭是岸', identity: '僧', source: '未知', type: '佛教哲理和戒律' },
            { author: '孟瑤', title: '聲色場', identity: '普通', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '郭嗣汾', title: '紅葉', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '周君亮', title: '荒寺之一夜', identity: '普通', source: '《暢流》19卷3期，1959年3月', type: '佛教哲理和戒律' },
            { author: '公孫嬿', title: '普陀緣', identity: '軍', source: '未知', type: '佛、僧人、寺廟對小說情節有推進作用' },
            { author: '楚軍', title: '雨', identity: '軍', source: '未知', type: '佛、僧人、寺廟作為背景或敘述填充' },
            { author: '魏希文', title: '胡家父子', identity: '軍', source: '《晨光》7卷10期，1959年12月', type: '關係不明' },
            { author: '墨人', title: '馬腳', identity: '軍', source: '未知', type: '關係不明' }
        ];

        // 初始化表格
        function initTable() {
            const tbody = document.getElementById('tableBody');
            tbody.innerHTML = '';
            worksData.forEach(work => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${work.author}</td>
                    <td>${work.title}</td>
                    <td>${work.identity}</td>
                    <td>${work.source}</td>
                    <td>${work.type}</td>
                `;
                tbody.appendChild(row);
            });

            // 初始化吳賢愷表
            const wuBody = document.getElementById('wuTableBody');
            wuBody.innerHTML = '';
            wuData.forEach(work => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${work.author}</td>
                    <td>${work.title}</td>
                    <td>${work.identity}</td>
                    <td>${work.source}</td>
                    <td>${work.type}</td>
                `;
                wuBody.appendChild(row);
            });
        }

        // 過濾數據
        // 漢堡菜單切換
        function toggleMenu() {
            const menu = document.getElementById('sidebarMenu');
            const overlay = document.getElementById('sidebarOverlay');
            const hamburger = document.querySelector('.hamburger-menu');
            
            menu.classList.toggle('active');
            overlay.classList.toggle('active');
            hamburger.classList.toggle('active');
        }

        function filterData() {
            const author = document.getElementById('filter-author').value;
            const type = document.getElementById('filter-type').value;

            const tbody = document.getElementById('tableBody');
            tbody.innerHTML = '';

            const filtered = worksData.filter(work => {
                const authorMatch = !author || work.identity.includes(author);
                const typeMatch = !type || work.type.includes(type);
                return authorMatch && typeMatch;
            });

            filtered.forEach(work => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${work.author}</td>
                    <td>${work.title}</td>
                    <td>${work.identity}</td>
                    <td>${work.source}</td>
                    <td>${work.type}</td>
                `;
                tbody.appendChild(row);
            });
        }

        // 裝置切換功能
        function switchDevice(device) {
            document.querySelectorAll('.device-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            console.log('切換到裝置:', device);
        }

        // 頁面加載時初始化
        document.addEventListener('DOMContentLoaded', function() {
            initTable();
        });
    </script>
</body>
</html>
