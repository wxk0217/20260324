<!DOCTYPE html>
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
            padding: 20px;
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
            gap: 10px;
            align-items: center;
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
            opacity: 0.15;
            pointer-events: none;
            font-size: 100px;
        }

        .hero-decorative.left {
            top: 20px;
            left: 30px;
            animation: rotate 30s linear infinite;
        }

        .hero-decorative.right {
            bottom: 20px;
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
        }

        /* 響應式設計 */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 36px;
            }

            .major-section {
                padding: 40px 20px;
                min-height: 400px;
            }

            .major-section h2 {
                font-size: 32px;
            }

            table {
                font-size: 12px;
            }

            th, td {
                padding: 10px 12px;
            }

            .stats-content {
                grid-template-columns: 1fr;
            }

            .classification-grid {
                grid-template-columns: 1fr;
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
            <div class="device-switcher">
                <button class="device-btn active" onclick="switchDevice('desktop')">💻 電腦</button>
                <button class="device-btn" onclick="switchDevice('tablet')">📱 平板</button>
                <button class="device-btn" onclick="switchDevice('mobile')">📲 手機</button>
            </div>
        </div>
    </header>

    <!-- 主要內容 -->
    <main class="container">
        <!-- 英雄區域 -->
        <section class="hero">
            <div class="hero-decorative left">🌸</div>
            <h1>《佛教小說集》</h1>
            <p>朱橋編著 | 佛教文化出版社，1960年11月</p>

            <div class="hero-decorative right">🌸</div>
        </section>

        <!-- 下拉選單過濾區域 -->
        <section class="filter-section">
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
        </section>

        <!-- 裝飾分隔線 -->
        <div class="decorative-divider">🌸 ❖ 🌸</div>

        <!-- 分類方法標題 -->
        <section style="margin-bottom: 60px; padding: 50px 40px; background: linear-gradient(135deg, rgba(212, 175, 142, 0.12), rgba(168, 197, 192, 0.12)); border-radius: 20px; border: 2px solid var(--border-color); position: relative; overflow: hidden;">
            <div style="position: absolute; top: 20px; right: 30px; font-size: 60px; opacity: 0.15; animation: rotate 30s linear infinite;">☸</div>
            <div style="position: absolute; bottom: 20px; left: 30px; font-size: 60px; opacity: 0.15; animation: rotate 30s linear infinite reverse;">♀</div>
            <div style="position: absolute; top: 50%; right: 10%; font-size: 50px; opacity: 0.1; animation: float 4s ease-in-out infinite;">♕</div>
            <div style="position: absolute; bottom: 30%; left: 10%; font-size: 50px; opacity: 0.1; animation: bounce 2s ease-in-out infinite;">♗</div>
            <h2 style="font-size: 44px; font-weight: 700; color: var(--text-dark); margin: 0; letter-spacing: 3px; position: relative; z-index: 2; text-align: center; padding-bottom: 20px; border-bottom: 4px solid var(--accent-gold);">分類方法</h2>
        </section>

        <!-- 故事性質分類 - 四個粗體字標題 -->

        <!-- 范純武 -->
        <section class="major-section">
            <h2>范純武</h2>
            <div class="major-section-content">
                <ul>
                    <li>新創作題材的小說</li>
                    <li>雜揉個人經驗的小說</li>
                    <li>改編佛教故事的小說</li>
                </ul>
            </div>
        </section>

        <!-- 李玉珍 -->
        <section class="major-section">
            <h2>李玉珍</h2>
            <div class="major-section-content">
                <ul>
                    <li>改寫的佛經故事</li>
                    <li>鄉野傳奇式的勸善小說</li>
                    <li>以家庭情愛印證佛法的小說</li>
                    <li>遊歷寺院和僧尼交遊的記載</li>
                    <li>反共懷鄉的小說創作</li>
                    <li>無法歸類</li>
                </ul>
            </div>
        </section>

        <!-- 丁敏 -->
        <section class="major-section">
            <h2>丁敏</h2>
            <div class="major-section-content">
                <ul>
                    <li>借用佛教題材</li>
                    <li>賦予佛教神佛中國性格</li>
                    <li>以佛教故事和典故為敘述結構</li>
                    <li>以具體事物譬喻佛法</li>
                    <li>以佛教幻設和當下停格的時間為軸</li>
                    <li>因果報應</li>
                </ul>
            </div>
        </section>

        <!-- 吳賢愷 -->
        <section class="major-section">
            <h2>吳賢愷</h2>
            <div class="major-section-content">
                <ul>
                    <li>佛教故事改編</li>
                    <li>佛教哲理和戒律</li>
                    <li>果報思想</li>
                    <li>佛、僧人、寺廟對小說情節有推進作用</li>
                    <li>佛、僧人、寺廟作為背景或敘述填充</li>
                    <li>關係不明</li>
                </ul>
            </div>
        </section>

        <!-- 裝飾分隔線 -->
        <div class="decorative-divider">🌸 ❖ 🌸</div>

        <!-- 完整作品清單表格 -->
        <section class="table-section">
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
        <section class="stats-section">
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
        <section class="classification-section">
            <h2>📖 反共懷鄉 VS 反共愛國</h2>
            <div class="classification-grid">
                <div class="classification-card">
                    <h3>李玉珍十一篇</h3>
                    <ul>
                        <li>〈紅葉〉</li>
                        <li>〈雨〉</li>
                        <li>〈人間的奇蹟〉</li>
                        <li>〈紅塵〉</li>
                        <li>〈三角〉</li>
                        <li>〈喜帖〉</li>
                        <li>〈朝來寒雨晚來風〉</li>
                        <li>〈荒寺的一夜〉</li>
                        <li>〈普陀緣〉</li>
                        <li>〈重生〉</li>
                        <li>〈佈施〉</li>
                    </ul>
                </div>

                <div class="classification-card">
                    <h3>吳賢愷四篇</h3>
                    <ul>
                        <li>〈普陀緣〉</li>
                        <li>〈紅塵〉</li>
                        <li>〈重生〉</li>
                        <li>〈三角〉</li>
                        <li>〈朝來寒雨晚來風〉</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- 核心研究主題 -->
        <section style="margin-bottom: 60px;">
            <h2 style="font-size: 28px; margin-bottom: 40px; color: var(--text-dark); text-align: center; position: relative; padding-bottom: 20px; font-weight: 700;">📖 核心研究主題
                <span style="position: absolute; bottom: 0; left: 50%; transform: translateX(-50%); width: 80px; height: 4px; background: linear-gradient(90deg, var(--accent-purple), var(--accent-teal)); border-radius: 2px; box-shadow: 0 2px 8px rgba(168, 197, 192, 0.3);"></span>
            </h2>
            <div style="display: flex; flex-direction: column; gap: 25px; margin-top: 40px;">
                <section class="major-section" style="margin-bottom: 0; min-height: auto; padding: 40px;">
                    <h2 style="font-size: 22px; margin-bottom: 15px; padding-bottom: 12px; border-bottom: 3px solid var(--accent-gold); display: flex; align-items: center; gap: 12px;">
                        <span style="font-size: 28px; animation: spin-slow 8s linear infinite;">☸</span>
                        反共文學和戰鬥文藝的衰退
                    </h2>
                    <div class="major-section-content" style="padding: 0;">
                        <p style="font-size: 17px; color: var(--text-light); line-height: 2.2; margin: 0;">
                            反共文學和戰鬥文藝的衰退——1956 年《文藝創作》停刊和文獎會解散<br>
                            1955 年戰鬥文藝口號的提出標示著反共文學的挫敗<br>
                            陳明成：美國壓制和張道藩的失勢<br>
                            封德屏：張道藩專心投入公務
                        </p>
                    </div>
                </section>

                <section class="major-section" style="margin-bottom: 0; min-height: auto; padding: 40px;">
                    <h2 style="font-size: 22px; margin-bottom: 15px; padding-bottom: 12px; border-bottom: 3px solid var(--accent-teal); display: flex; align-items: center; gap: 12px;">
                        <span style="font-size: 28px; animation: sway 3s ease-in-out infinite;">✡</span>
                        戰鬥文藝——一種沒有類型的類型
                    </h2>
                    <div class="major-section-content" style="padding: 0;">
                        <p style="font-size: 17px; color: var(--text-light); line-height: 2.2; margin: 0;">
                            戰鬥文藝——一種沒有類型的類型<br>
                            反共文學<br>
                            民族主義<br>
                            健康寫實主義<br>
                            「戰鬥」作為一種人生的精神
                        </p>
                    </div>
                </section>

                <section class="major-section" style="margin-bottom: 0; min-height: auto; padding: 40px;">
                    <h2 style="font-size: 22px; margin-bottom: 15px; padding-bottom: 12px; border-bottom: 3px solid var(--accent-purple); display: flex; align-items: center; gap: 12px;">
                        <span style="font-size: 28px; animation: float 4s ease-in-out infinite;">❊</span>
                        軍中作家不等於軍人作家不等於反共作家
                    </h2>
                    <div class="major-section-content" style="padding: 0;">
                        <p style="font-size: 17px; color: var(--text-light); line-height: 2.2; margin: 0;">
                            軍中作家不等於軍人作家不等於反共作家<br>
                            翁伯川：《「軍中三劍客」的文學創作與活動研究》，臺南：國立成功大學中國文學系博士論文，2017
                        </p>
                    </div>
                </section>
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
