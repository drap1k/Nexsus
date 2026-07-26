<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>NEXUS — AI-Powered Future</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #000000;
            --bg-secondary: #0a0a0a;
            --bg-tertiary: #111111;
            --bg-card: rgba(255,255,255,0.03);
            --bg-card-hover: rgba(255,255,255,0.06);
            --text-primary: #ffffff;
            --text-secondary: rgba(255,255,255,0.6);
            --text-tertiary: rgba(255,255,255,0.35);
            --border: rgba(255,255,255,0.08);
            --border-hover: rgba(255,255,255,0.15);
            --accent: #ffffff;
            --accent-dim: rgba(255,255,255,0.1);
            --gradient-1: linear-gradient(135deg, #ffffff 0%, #888888 50%, #ffffff 100%);
            --gradient-2: linear-gradient(90deg, transparent 0%, rgba(255,255,255,0.08) 50%, transparent 100%);
            --gradient-3: radial-gradient(ellipse at 50% 0%, rgba(255,255,255,0.12) 0%, transparent 60%);
            --shadow-glow: 0 0 60px rgba(255,255,255,0.05);
        }

        html {
            scroll-behavior: smooth;
            -webkit-font-smoothing: antialiased;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* ===== ANIMATED BACKGROUND ===== */
        .bg-aurora {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
            overflow: hidden;
        }

        .aurora-blob {
            position: absolute;
            border-radius: 50%;
            filter: blur(120px);
            opacity: 0.15;
            animation: aurora-float 20s ease-in-out infinite;
        }

        .aurora-blob:nth-child(1) {
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, #ffffff 0%, transparent 70%);
            top: -200px;
            left: -100px;
            animation-delay: 0s;
        }

        .aurora-blob:nth-child(2) {
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, #cccccc 0%, transparent 70%);
            top: 40%;
            right: -150px;
            animation-delay: -7s;
            animation-duration: 25s;
        }

        .aurora-blob:nth-child(3) {
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, #888888 0%, transparent 70%);
            bottom: -100px;
            left: 30%;
            animation-delay: -14s;
            animation-duration: 22s;
        }

        @keyframes aurora-float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            25% { transform: translate(50px, -30px) scale(1.1); }
            50% { transform: translate(-30px, 50px) scale(0.95); }
            75% { transform: translate(20px, 20px) scale(1.05); }
        }

        .bg-grid {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
            background-image: 
                linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
            background-size: 60px 60px;
            mask-image: radial-gradient(ellipse at center, black 30%, transparent 70%);
            -webkit-mask-image: radial-gradient(ellipse at center, black 30%, transparent 70%);
        }

        /* ===== NOISE TEXTURE ===== */
        .noise {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 2;
            pointer-events: none;
            opacity: 0.03;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
        }

        /* ===== SCROLLBAR ===== */
        ::-webkit-scrollbar {
            width: 6px;
        }

        ::-webkit-scrollbar-track {
            background: var(--bg-primary);
        }

        ::-webkit-scrollbar-thumb {
            background: rgba(255,255,255,0.15);
            border-radius: 3px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: rgba(255,255,255,0.3);
        }

        /* ===== NAVIGATION ===== */
        .nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            padding: 16px 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            backdrop-filter: blur(20px) saturate(180%);
            -webkit-backdrop-filter: blur(20px) saturate(180%);
            background: rgba(0,0,0,0.6);
            border-bottom: 1px solid var(--border);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .nav.scrolled {
            padding: 12px 24px;
            background: rgba(0,0,0,0.85);
        }

        .nav-logo {
            font-size: 22px;
            font-weight: 900;
            letter-spacing: -1px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            cursor: pointer;
            transition: opacity 0.3s;
        }

        .nav-logo:hover {
            opacity: 0.7;
        }

        .nav-links {
            display: flex;
            gap: 32px;
            align-items: center;
        }

        .nav-link {
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 14px;
            font-weight: 500;
            transition: color 0.3s;
            position: relative;
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 1px;
            background: var(--text-primary);
            transition: width 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .nav-link:hover {
            color: var(--text-primary);
        }

        .nav-link:hover::after {
            width: 100%;
        }

        .nav-cta {
            padding: 10px 24px;
            background: var(--text-primary);
            color: var(--bg-primary);
            border: none;
            border-radius: 100px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .nav-cta:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(255,255,255,0.2);
        }

        .nav-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--text-primary);
            font-size: 24px;
            cursor: pointer;
        }

        /* ===== HERO SECTION ===== */
        .hero {
            position: relative;
            z-index: 10;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 120px 24px 80px;
            overflow: hidden;
        }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 8px 20px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 100px;
            font-size: 13px;
            font-weight: 500;
            color: var(--text-secondary);
            margin-bottom: 32px;
            animation: fadeInUp 0.8s ease-out 0.2s both;
        }

        .hero-badge-dot {
            width: 8px;
            height: 8px;
            background: #fff;
            border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(0.8); }
        }

        .hero-title {
            font-size: clamp(40px, 8vw, 96px);
            font-weight: 900;
            line-height: 1.05;
            letter-spacing: -3px;
            margin-bottom: 24px;
            animation: fadeInUp 0.8s ease-out 0.4s both;
        }

        .hero-title .gradient-text {
            background: linear-gradient(135deg, #ffffff 0%, #888888 40%, #ffffff 60%, #444444 100%);
            background-size: 200% 200%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradient-shift 8s ease infinite;
        }

        @keyframes gradient-shift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .hero-subtitle {
            font-size: clamp(16px, 2.5vw, 22px);
            color: var(--text-secondary);
            max-width: 600px;
            margin-bottom: 48px;
            font-weight: 400;
            line-height: 1.7;
            animation: fadeInUp 0.8s ease-out 0.6s both;
        }

        .hero-cta-group {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
            justify-content: center;
            animation: fadeInUp 0.8s ease-out 0.8s both;
        }

        .btn-primary {
            padding: 16px 40px;
            background: var(--text-primary);
            color: var(--bg-primary);
            border: none;
            border-radius: 100px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .btn-primary::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.6s;
        }

        .btn-primary:hover::before {
            left: 100%;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 20px 40px rgba(255,255,255,0.15);
        }

        .btn-secondary {
            padding: 16px 40px;
            background: transparent;
            color: var(--text-primary);
            border: 1px solid var(--border);
            border-radius: 100px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .btn-secondary:hover {
            border-color: var(--text-primary);
            background: var(--bg-card-hover);
            transform: translateY(-2px);
        }

        .hero-stats {
            display: flex;
            gap: 48px;
            margin-top: 80px;
            animation: fadeInUp 0.8s ease-out 1s both;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-size: 36px;
            font-weight: 800;
            letter-spacing: -1px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            font-size: 13px;
            color: var(--text-tertiary);
            margin-top: 4px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* ===== SCROLL INDICATOR ===== */
        .scroll-indicator {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            animation: fadeInUp 0.8s ease-out 1.2s both;
        }

        .scroll-text {
            font-size: 11px;
            color: var(--text-tertiary);
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .scroll-line {
            width: 1px;
            height: 40px;
            background: linear-gradient(to bottom, var(--text-tertiary), transparent);
            animation: scroll-bounce 2s ease-in-out infinite;
        }

        @keyframes scroll-bounce {
            0%, 100% { transform: scaleY(1); opacity: 1; }
            50% { transform: scaleY(0.5); opacity: 0.3; }
        }

        /* ===== MARQUEE ===== */
        .marquee-section {
            position: relative;
            z-index: 10;
            padding: 60px 0;
            border-top: 1px solid var(--border);
            border-bottom: 1px solid var(--border);
            overflow: hidden;
            background: var(--bg-secondary);
        }

        .marquee-track {
            display: flex;
            gap: 80px;
            animation: marquee 30s linear infinite;
            width: max-content;
        }

        .marquee-item {
            font-size: 14px;
            font-weight: 600;
            color: var(--text-tertiary);
            text-transform: uppercase;
            letter-spacing: 3px;
            white-space: nowrap;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .marquee-item::before {
            content: '◆';
            font-size: 8px;
            color: var(--text-tertiary);
        }

        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        /* ===== FEATURES SECTION ===== */
        .section {
            position: relative;
            z-index: 10;
            padding: 120px 24px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-header {
            text-align: center;
            margin-bottom: 80px;
        }

        .section-label {
            font-size: 12px;
            font-weight: 600;
            color: var(--text-tertiary);
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 16px;
        }

        .section-title {
            font-size: clamp(32px, 5vw, 56px);
            font-weight: 800;
            letter-spacing: -2px;
            line-height: 1.1;
            margin-bottom: 20px;
        }

        .section-desc {
            font-size: 18px;
            color: var(--text-secondary);
            max-width: 560px;
            margin: 0 auto;
            line-height: 1.7;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 24px;
        }

        .feature-card {
            padding: 40px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 1px;
            background: var(--gradient-2);
            opacity: 0;
            transition: opacity 0.5s;
        }

        .feature-card:hover {
            border-color: var(--border-hover);
            background: var(--bg-card-hover);
            transform: translateY(-4px);
            box-shadow: var(--shadow-glow);
        }

        .feature-card:hover::before {
            opacity: 1;
        }

        .feature-icon {
            width: 48px;
            height: 48px;
            border-radius: 14px;
            background: var(--accent-dim);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            margin-bottom: 24px;
            border: 1px solid var(--border);
        }

        .feature-title {
            font-size: 20px;
            font-weight: 700;
            margin-bottom: 12px;
            letter-spacing: -0.5px;
        }

        .feature-desc {
            font-size: 15px;
            color: var(--text-secondary);
            line-height: 1.7;
        }

        /* ===== SHOWCASE SECTION ===== */
        .showcase {
            position: relative;
            z-index: 10;
            padding: 120px 24px;
            overflow: hidden;
        }

        .showcase-inner {
            max-width: 1200px;
            margin: 0 auto;
        }

        .showcase-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .showcase-content {
            padding-right: 40px;
        }

        .showcase-label {
            font-family: 'JetBrains Mono', monospace;
            font-size: 12px;
            color: var(--text-tertiary);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 20px;
        }

        .showcase-title {
            font-size: clamp(28px, 4vw, 48px);
            font-weight: 800;
            letter-spacing: -2px;
            line-height: 1.1;
            margin-bottom: 24px;
        }

        .showcase-desc {
            font-size: 17px;
            color: var(--text-secondary);
            line-height: 1.8;
            margin-bottom: 32px;
        }

        .showcase-list {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .showcase-list li {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 15px;
            color: var(--text-secondary);
        }

        .showcase-list li::before {
            content: '→';
            color: var(--text-primary);
            font-weight: 700;
        }

        .showcase-visual {
            position: relative;
        }

        .showcase-frame {
            position: relative;
            border-radius: 24px;
            overflow: hidden;
            border: 1px solid var(--border);
            background: var(--bg-tertiary);
            aspect-ratio: 4/3;
        }

        .showcase-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0.9;
            transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.5s;
        }

        .showcase-frame:hover img {
            transform: scale(1.05);
            opacity: 1;
        }

        .showcase-frame::after {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(180deg, transparent 50%, rgba(0,0,0,0.6) 100%);
            pointer-events: none;
        }

        .showcase-glow {
            position: absolute;
            width: 300px;
            height: 300px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(255,255,255,0.08) 0%, transparent 70%);
            filter: blur(60px);
            top: -100px;
            right: -100px;
            pointer-events: none;
        }

        /* ===== PRICING SECTION ===== */
        .pricing {
            position: relative;
            z-index: 10;
            padding: 120px 24px;
            background: var(--bg-secondary);
        }

        .pricing-inner {
            max-width: 1200px;
            margin: 0 auto;
        }

        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 24px;
            margin-top: 60px;
        }

        .pricing-card {
            padding: 40px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
        }

        .pricing-card.popular {
            border-color: rgba(255,255,255,0.2);
            background: linear-gradient(180deg, var(--bg-card) 0%, rgba(255,255,255,0.03) 100%);
        }

        .pricing-card.popular::before {
            content: 'POPULAR';
            position: absolute;
            top: -1px;
            left: 50%;
            transform: translateX(-50%);
            padding: 6px 20px;
            background: var(--text-primary);
            color: var(--bg-primary);
            font-size: 11px;
            font-weight: 700;
            letter-spacing: 2px;
            border-radius: 0 0 12px 12px;
        }

        .pricing-card:hover {
            transform: translateY(-8px);
            border-color: var(--border-hover);
            box-shadow: var(--shadow-glow);
        }

        .pricing-name {
            font-size: 14px;
            font-weight: 600;
            color: var(--text-tertiary);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 16px;
        }

        .pricing-price {
            font-size: 48px;
            font-weight: 900;
            letter-spacing: -2px;
            margin-bottom: 8px;
        }

        .pricing-price span {
            font-size: 16px;
            font-weight: 400;
            color: var(--text-tertiary);
        }

        .pricing-desc {
            font-size: 15px;
            color: var(--text-secondary);
            margin-bottom: 32px;
            line-height: 1.6;
        }

        .pricing-features {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 14px;
            margin-bottom: 32px;
        }

        .pricing-features li {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 14px;
            color: var(--text-secondary);
        }

        .pricing-features li::before {
            content: '✓';
            color: var(--text-primary);
            font-weight: 700;
            font-size: 12px;
        }

        .pricing-btn {
            width: 100%;
            padding: 14px;
            background: transparent;
            color: var(--text-primary);
            border: 1px solid var(--border);
            border-radius: 12px;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .pricing-btn:hover {
            background: var(--text-primary);
            color: var(--bg-primary);
            border-color: var(--text-primary);
        }

        .pricing-card.popular .pricing-btn {
            background: var(--text-primary);
            color: var(--bg-primary);
            border-color: var(--text-primary);
        }

        .pricing-card.popular .pricing-btn:hover {
            background: transparent;
            color: var(--text-primary);
        }

        /* ===== TESTIMONIALS ===== */
        .testimonials {
            position: relative;
            z-index: 10;
            padding: 120px 24px;
        }

        .testimonials-inner {
            max-width: 1200px;
            margin: 0 auto;
        }

        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 24px;
            margin-top: 60px;
        }

        .testimonial-card {
            padding: 36px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            transition: all 0.5s;
        }

        .testimonial-card:hover {
            border-color: var(--border-hover);
            transform: translateY(-4px);
        }

        .testimonial-quote {
            font-size: 15px;
            color: var(--text-secondary);
            line-height: 1.8;
            margin-bottom: 28px;
            font-style: italic;
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            gap: 14px;
        }

        .testimonial-avatar {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            background: linear-gradient(135deg, #333, #666);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            font-weight: 700;
            border: 1px solid var(--border);
        }

        .testimonial-info {
            display: flex;
            flex-direction: column;
        }

        .testimonial-name {
            font-size: 15px;
            font-weight: 600;
        }

        .testimonial-role {
            font-size: 13px;
            color: var(--text-tertiary);
        }

        .testimonial-stars {
            display: flex;
            gap: 4px;
            margin-bottom: 20px;
        }

        .testimonial-stars span {
            color: var(--text-primary);
            font-size: 14px;
        }

        /* ===== CTA SECTION ===== */
        .cta-section {
            position: relative;
            z-index: 10;
            padding: 160px 24px;
            text-align: center;
            overflow: hidden;
        }

        .cta-section::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 800px;
            height: 400px;
            background: radial-gradient(ellipse, rgba(255,255,255,0.06) 0%, transparent 70%);
            pointer-events: none;
        }

        .cta-title {
            font-size: clamp(36px, 6vw, 72px);
            font-weight: 900;
            letter-spacing: -3px;
            line-height: 1.05;
            margin-bottom: 24px;
            position: relative;
        }

        .cta-subtitle {
            font-size: 18px;
            color: var(--text-secondary);
            max-width: 500px;
            margin: 0 auto 48px;
            line-height: 1.7;
            position: relative;
        }

        .cta-btn {
            padding: 18px 48px;
            background: var(--text-primary);
            color: var(--bg-primary);
            border: none;
            border-radius: 100px;
            font-size: 17px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
        }

        .cta-btn:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 30px 60px rgba(255,255,255,0.15);
        }

        /* ===== FOOTER ===== */
        .footer {
            position: relative;
            z-index: 10;
            padding: 80px 24px 40px;
            border-top: 1px solid var(--border);
            background: var(--bg-secondary);
        }

        .footer-inner {
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-top {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 60px;
            margin-bottom: 60px;
        }

        .footer-brand {
            font-size: 24px;
            font-weight: 900;
            letter-spacing: -1px;
            margin-bottom: 16px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .footer-desc {
            font-size: 14px;
            color: var(--text-tertiary);
            line-height: 1.7;
            max-width: 280px;
        }

        .footer-col h4 {
            font-size: 13px;
            font-weight: 600;
            color: var(--text-tertiary);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 20px;
        }

        .footer-col a {
            display: block;
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 14px;
            margin-bottom: 12px;
            transition: color 0.3s;
        }

        .footer-col a:hover {
            color: var(--text-primary);
        }

        .footer-bottom {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 32px;
            border-top: 1px solid var(--border);
        }

        .footer-copy {
            font-size: 13px;
            color: var(--text-tertiary);
        }

        .footer-social {
            display: flex;
            gap: 20px;
        }

        .footer-social a {
            color: var(--text-tertiary);
            text-decoration: none;
            font-size: 14px;
            transition: color 0.3s;
        }

        .footer-social a:hover {
            color: var(--text-primary);
        }

        /* ===== ANIMATIONS ===== */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* ===== MOBILE MENU ===== */
        .mobile-menu {
            position: fixed;
            top: 0;
            right: -100%;
            width: 80%;
            max-width: 360px;
            height: 100vh;
            background: rgba(0,0,0,0.95);
            backdrop-filter: blur(30px);
            z-index: 2000;
            padding: 80px 32px 32px;
            transition: right 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            border-left: 1px solid var(--border);
        }

        .mobile-menu.open {
            right: 0;
        }

        .mobile-menu-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.5);
            z-index: 1999;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s;
        }

        .mobile-menu-overlay.open {
            opacity: 1;
            pointer-events: all;
        }

        .mobile-menu-close {
            position: absolute;
            top: 20px;
            right: 24px;
            background: none;
            border: none;
            color: var(--text-primary);
            font-size: 28px;
            cursor: pointer;
        }

        .mobile-menu a {
            display: block;
            color: var(--text-primary);
            text-decoration: none;
            font-size: 20px;
            font-weight: 600;
            padding: 16px 0;
            border-bottom: 1px solid var(--border);
            transition: color 0.3s;
        }

        .mobile-menu a:hover {
            color: var(--text-secondary);
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 1024px) {
            .features-grid,
            .testimonials-grid,
            .pricing-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .showcase-grid {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .showcase-content {
                padding-right: 0;
            }

            .footer-top {
                grid-template-columns: 1fr 1fr;
                gap: 40px;
            }
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .nav-menu-btn {
                display: block;
            }

            .hero-stats {
                gap: 24px;
            }

            .stat-number {
                font-size: 28px;
            }

            .features-grid,
            .testimonials-grid,
            .pricing-grid {
                grid-template-columns: 1fr;
            }

            .feature-card,
            .testimonial-card,
            .pricing-card {
                padding: 28px;
            }

            .footer-top {
                grid-template-columns: 1fr;
                gap: 32px;
            }

            .footer-bottom {
                flex-direction: column;
                gap: 20px;
                text-align: center;
            }

            .section {
                padding: 80px 24px;
            }

            .showcase,
            .pricing,
            .testimonials,
            .cta-section {
                padding: 80px 24px;
            }

            .marquee-section {
                padding: 40px 0;
            }
        }

        @media (max-width: 480px) {
            .hero-title {
                letter-spacing: -1px;
            }

            .hero-cta-group {
                flex-direction: column;
                width: 100%;
            }

            .btn-primary,
            .btn-secondary {
                width: 100%;
            }

            .hero-stats {
                flex-direction: column;
                gap: 24px;
            }
        }

        /* ===== CURSOR EFFECT ===== */
        .cursor-glow {
            position: fixed;
            width: 300px;
            height: 300px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(255,255,255,0.04) 0%, transparent 70%);
            pointer-events: none;
            z-index: 5;
            transform: translate(-50%, -50%);
            transition: opacity 0.3s;
        }

        @media (pointer: coarse) {
            .cursor-glow {
                display: none;
            }
        }
    </style>
</head>
<body>

    <!-- Background Effects -->
    <div class="bg-aurora">
        <div class="aurora-blob"></div>
        <div class="aurora-blob"></div>
        <div class="aurora-blob"></div>
    </div>
    <div class="bg-grid"></div>
    <div class="noise"></div>
    <div class="cursor-glow" id="cursorGlow"></div>

    <!-- Navigation -->
    <nav class="nav" id="nav">
        <div class="nav-logo">NEXUS</div>
        <div class="nav-links">
            <a href="#features" class="nav-link">Возможности</a>
            <a href="#showcase" class="nav-link">Шоукейс</a>
            <a href="#pricing" class="nav-link">Тарифы</a>
            <a href="#testimonials" class="nav-link">Отзывы</a>
            <button class="nav-cta">Начать</button>
        </div>
        <button class="nav-menu-btn" id="menuBtn">☰</button>
    </nav>

    <!-- Mobile Menu -->
    <div class="mobile-menu-overlay" id="menuOverlay"></div>
    <div class="mobile-menu" id="mobileMenu">
        <button class="mobile-menu-close" id="menuClose">✕</button>
        <a href="#features">Возможности</a>
        <a href="#showcase">Шоукейс</a>
        <a href="#pricing">Тарифы</a>
        <a href="#testimonials">Отзывы</a>
        <a href="#" style="margin-top: 20px; color: var(--text-primary); font-weight: 700;">Начать →</a>
    </div>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-badge">
            <span class="hero-badge-dot"></span>
            Новое поколение AI уже здесь
        </div>
        <h1 class="hero-title">
            Создавай будущее<br>
            с <span class="gradient-text">искусственным<br>интеллектом</span>
        </h1>
        <p class="hero-subtitle">
            NEXUS объединяет мощь нейросетей с интуитивным интерфейсом. 
            Пиши код, генерируй контент, анализируй данные — всё в одном месте.
        </p>
        <div class="hero-cta-group">
            <button class="btn-primary">Попробовать бесплатно</button>
            <button class="btn-secondary">Смотреть демо</button>
        </div>
        <div class="hero-stats">
            <div class="stat-item">
                <div class="stat-number">10M+</div>
                <div class="stat-label">Пользователей</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">99.9%</div>
                <div class="stat-label">Аптайм</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">50ms</div>
                <div class="stat-label">Отклик</div>
            </div>
            <div class="stat-item">
                <div class="stat-number">150+</div>
                <div class="stat-label">Стран</div>
            </div>
        </div>
        <div class="scroll-indicator">
            <span class="scroll-text">Листай вниз</span>
            <div class="scroll-line"></div>
        </div>
    </section>

    <!-- Marquee -->
    <section class="marquee-section">
        <div class="marquee-track" id="marqueeTrack">
            <span class="marquee-item">Машинное обучение</span>
            <span class="marquee-item">Генерация кода</span>
            <span class="marquee-item">Анализ данных</span>
            <span class="marquee-item">NLP</span>
            <span class="marquee-item">Компьютерное зрение</span>
            <span class="marquee-item">Автоматизация</span>
            <span class="marquee-item">Deep Learning</span>
            <span class="marquee-item">Cloud AI</span>
            <span class="marquee-item">Машинное обучение</span>
            <span class="marquee-item">Генерация кода</span>
            <span class="marquee-item">Анализ данных</span>
            <span class="marquee-item">NLP</span>
            <span class="marquee-item">Компьютерное зрение</span>
            <span class="marquee-item">Автоматизация</span>
            <span class="marquee-item">Deep Learning</span>
            <span class="marquee-item">Cloud AI</span>
        </div>
    </section>

    <!-- Features Section -->
    <section class="section" id="features">
        <div class="section-header reveal">
            <div class="section-label">Возможности</div>
            <h2 class="section-title">Всё, что нужно<br>для создания</h2>
            <p class="section-desc">
                От идеи до продакшена — NEXUS покрывает весь цикл разработки 
                с помощью передовых AI-технологий.
            </p>
        </div>
        <div class="features-grid">
            <div class="feature-card reveal">
                <div class="feature-icon">⚡</div>
                <h3 class="feature-title">Молниеносная генерация</h3>
                <p class="feature-desc">
                    Получайте результаты за миллисекунды. Наша оптимизированная 
                    архитектура обеспечивает рекордную скорость обработки запросов.
                </p>
            </div>
            <div class="feature-card reveal">
                <div class="feature-icon">🧠</div>
                <h3 class="feature-title">Продвинутый контекст</h3>
                <p class="feature-desc">
                    Работайте с документами до 2 миллионов токенов. 
                    Понимание контекста на уровне целых книг и кодовых баз.
                </p>
            </div>
            <div class="feature-card reveal">
                <div class="feature-icon">🔒</div>
                <h3 class="feature-title">Enterprise-безопасность</h3>
                <p class="feature-desc">
                    SOC 2 Type II, GDPR, HIPAA. Ваши данные никогда не используются 
                    для обучения моделей. Полный контроль и аудит.
                </p>
            </div>
            <div class="feature-card reveal">
                <div class="feature-icon">🌐</div>
                <h3 class="feature-title">Мультиязычность</h3>
                <p class="feature-desc">
                    Поддержка 100+ языков с нативным качеством. 
                    Переводы, локализация и кросс-культурный анализ текста.
                </p>
            </div>
            <div class="feature-card reveal">
                <div class="feature-icon">🎨</div>
                <h3 class="feature-title">Генерация UI/UX</h3>
                <p class="feature-desc">
                    Создавайте интерфейсы из текстовых описаний. 
                    Автоматическая генерация HTML, CSS, React-компонентов.
                </p>
            </div>
            <div class="feature-card reveal">
                <div class="feature-icon">📊</div>
                <h3 class="feature-title">Аналитика в реальном времени</h3>
                <p class="feature-desc">
                    Визуализация данных, построение графиков и дашбордов 
                    прямо в диалоге. Экспорт в любой формат.
                </p>
            </div>
        </div>
    </section>

    <!-- Showcase Section -->
    <section class="showcase" id="showcase">
        <div class="showcase-inner">
            <div class="showcase-grid">
                <div class="showcase-content reveal">
                    <div class="showcase-label">// Интерфейс</div>
                    <h2 class="showcase-title">
                        Интуитивный дизайн,<br>
                        бесконечные возможности
                    </h2>
                    <p class="showcase-desc">
                        Каждый пиксель продуман. Минималистичный интерфейс 
                        без отвлекающих элементов позволяет сосредоточиться 
                        на главном — вашей работе.
                    </p>
                    <ul class="showcase-list">
                        <li>Адаптивная тёмная тема с OLED-оптимизацией</li>
                        <li>Жесты и горячие клавиши для максимальной скорости</li>
                        <li>Split-view для работы с несколькими задачами</li>
                        <li>История версий и ветвление диалогов</li>
                    </ul>
                </div>
                <div class="showcase-visual reveal">
                    <div class="showcase-glow"></div>
                    <div class="showcase-frame">
                        <img src="https://kimi-web-img.moonshot.cn/img/img.magnific.com/a558bf59a0a00945fe0f1fa5d0be0c1a47f601a0.jpg" alt="Abstract tech visualization">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section class="pricing" id="pricing">
        <div class="pricing-inner">
            <div class="section-header reveal">
                <div class="section-label">Тарифы</div>
                <h2 class="section-title">Простая цена,<br>максимальная ценность</h2>
                <p class="section-desc">
                    Начните бесплатно и масштабируйтесь по мере роста ваших потребностей.
                </p>
            </div>
            <div class="pricing-grid">
                <div class="pricing-card reveal">
                    <div class="pricing-name">Starter</div>
                    <div class="pricing-price">$0<span>/мес</span></div>
                    <p class="pricing-desc">Идеально для знакомства с платформой</p>
                    <ul class="pricing-features">
                        <li>До 100 запросов в день</li>
                        <li>Модель K2.6</li>
                        <li>Контекст 128K токенов</li>
                        <li>Веб-поиск</li>
                        <li>Базовая поддержка</li>
                    </ul>
                    <button class="pricing-btn">Начать бесплатно</button>
                </div>
                <div class="pricing-card popular reveal">
                    <div class="pricing-name">Pro</div>
                    <div class="pricing-price">$19<span>/мес</span></div>
                    <p class="pricing-desc">Для профессионалов и команд</p>
                    <ul class="pricing-features">
                        <li>Безлимитные запросы</li>
                        <li>Модели K2.6 + K3</li>
                        <li>Контекст 2M токенов</li>
                        <li>Agent-режим</li>
                        <li>API доступ</li>
                        <li>Приоритетная поддержка</li>
                    </ul>
                    <button class="pricing-btn">Выбрать Pro</button>
                </div>
                <div class="pricing-card reveal">
                    <div class="pricing-name">Enterprise</div>
                    <div class="pricing-price">$99<span>/мес</span></div>
                    <p class="pricing-desc">Для крупных организаций</p>
                    <ul class="pricing-features">
                        <li>Всё из Pro</li>
                        <li>Выделенная инфраструктура</li>
                        <li>SSO и SAML</li>
                        <li>SLA 99.99%</li>
                        <li>Персональный менеджер</li>
                        <li>Кастомные модели</li>
                    </ul>
                    <button class="pricing-btn">Связаться</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section class="testimonials" id="testimonials">
        <div class="testimonials-inner">
            <div class="section-header reveal">
                <div class="section-label">Отзывы</div>
                <h2 class="section-title">Их доверяют<br>миллионы</h2>
                <p class="section-desc">
                    Присоединяйтесь к сообществу разработчиков, дизайнеров 
                    и исследователей по всему миру.
                </p>
            </div>
            <div class="testimonials-grid">
                <div class="testimonial-card reveal">
                    <div class="testimonial-stars">
                        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                    </div>
                    <p class="testimonial-quote">
                        "NEXUS полностью изменил наш рабочий процесс. 
                        Генерация кода стала в 10 раз быстрее, а качество — выше, 
                        чем у любого другого инструмента, который мы пробовали."
                    </p>
                    <div class="testimonial-author">
                        <div class="testimonial-avatar">AK</div>
                        <div class="testimonial-info">
                            <div class="testimonial-name">Алексей Козлов</div>
                            <div class="testimonial-role">CTO, TechFlow</div>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card reveal">
                    <div class="testimonial-stars">
                        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                    </div>
                    <p class="testimonial-quote">
                        "Контекст в 2 миллиона токенов — это просто безумие. 
                        Я загружаю целую кодовую базу и получаю точные ответы 
                        по архитектуре. Невероятно."
                    </p>
                    <div class="testimonial-author">
                        <div class="testimonial-avatar">MN</div>
                        <div class="testimonial-info">
                            <div class="testimonial-name">Мария Новикова</div>
                            <div class="testimonial-role">Lead Developer, Yandex</div>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card reveal">
                    <div class="testimonial-stars">
                        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                    </div>
                    <p class="testimonial-quote">
                        "Интерфейс — это произведение искусства. Тёмная тема, 
                        плавные анимации, ничего лишнего. Работать — одно удовольствие."
                    </p>
                    <div class="testimonial-author">
                        <div class="testimonial-avatar">DI</div>
                        <div class="testimonial-info">
                            <div class="testimonial-name">Дмитрий Иванов</div>
                            <div class="testimonial-role">Product Designer, VK</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
        <h2 class="cta-title reveal">Готовы к<br>революции?</h2>
        <p class="cta-subtitle reveal">
            Присоединяйтесь к 10 миллионам пользователей, которые уже 
            создают будущее с NEXUS.
        </p>
        <button class="cta-btn reveal">Начать бесплатно →</button>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="footer-inner">
            <div class="footer-top">
                <div>
                    <div class="footer-brand">NEXUS</div>
                    <p class="footer-desc">
                        Создаём будущее искусственного интеллекта. 
                        Каждый день — шаг к совершенству.
                    </p>
                </div>
                <div class="footer-col">
                    <h4>Продукт</h4>
                    <a href="#">Возможности</a>
                    <a href="#">API</a>
                    <a href="#">Документация</a>
                    <a href="#">Обновления</a>
                </div>
                <div class="footer-col">
                    <h4>Компания</h4>
                    <a href="#">О нас</a>
                    <a href="#">Карьера</a>
                    <a href="#">Блог</a>
                    <a href="#">Контакты</a>
                </div>
                <div class="footer-col">
                    <h4>Правовое</h4>
                    <a href="#">Политика конфиденциальности</a>
                    <a href="#">Условия использования</a>
                    <a href="#">Cookie</a>
                    <a href="#">Безопасность</a>
                </div>
            </div>
            <div class="footer-bottom">
                <div class="footer-copy">© 2026 NEXUS AI. Все права защищены.</div>
                <div class="footer-social">
                    <a href="#">Twitter</a>
                    <a href="#">GitHub</a>
                    <a href="#">Discord</a>
                    <a href="#">Telegram</a>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // ===== NAV SCROLL EFFECT =====
        const nav = document.getElementById('nav');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                nav.classList.add('scrolled');
            } else {
                nav.classList.remove('scrolled');
            }
        });

        // ===== MOBILE MENU =====
        const menuBtn = document.getElementById('menuBtn');
        const menuClose = document.getElementById('menuClose');
        const mobileMenu = document.getElementById('mobileMenu');
        const menuOverlay = document.getElementById('menuOverlay');

        function openMenu() {
            mobileMenu.classList.add('open');
            menuOverlay.classList.add('open');
            document.body.style.overflow = 'hidden';
        }

        function closeMenu() {
            mobileMenu.classList.remove('open');
            menuOverlay.classList.remove('open');
            document.body.style.overflow = '';
        }

        menuBtn.addEventListener('click', openMenu);
        menuClose.addEventListener('click', closeMenu);
        menuOverlay.addEventListener('click', closeMenu);

        // Close menu on link click
        mobileMenu.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', closeMenu);
        });

        // ===== SMOOTH SCROLL =====
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });

        // ===== SCROLL REVEAL =====
        const revealElements = document.querySelectorAll('.reveal');
        const revealObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                    revealObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });

        revealElements.forEach(el => revealObserver.observe(el));

        // ===== CURSOR GLOW =====
        const cursorGlow = document.getElementById('cursorGlow');
        let mouseX = 0, mouseY = 0;
        let glowX = 0, glowY = 0;

        document.addEventListener('mousemove', (e) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
        });

        function animateGlow() {
            glowX += (mouseX - glowX) * 0.1;
            glowY += (mouseY - glowY) * 0.1;
            cursorGlow.style.left = glowX + 'px';
            cursorGlow.style.top = glowY + 'px';
            requestAnimationFrame(animateGlow);
        }
        animateGlow();

        // ===== MARQUEE SPEED CONTROL =====
        const marqueeTrack = document.getElementById('marqueeTrack');
        let marqueeSpeed = 1;
        let lastScrollY = window.scrollY;

        window.addEventListener('scroll', () => {
            const scrollDelta = Math.abs(window.scrollY - lastScrollY);
            marqueeSpeed = 1 + scrollDelta * 0.05;
            marqueeTrack.style.animationDuration = (30 / marqueeSpeed) + 's';
            lastScrollY = window.scrollY;
        });

        // ===== BUTTON INTERACTIONS =====
        document.querySelectorAll('.btn-primary, .btn-secondary, .pricing-btn, .cta-btn, .nav-cta').forEach(btn => {
            btn.addEventListener('click', function(e) {
                // Create ripple
                const ripple = document.createElement('span');
                ripple.style.cssText = `
                    position: absolute;
                    border-radius: 50%;
                    background: rgba(255,255,255,0.3);
                    transform: scale(0);
                    animation: ripple 0.6s linear;
                    pointer-events: none;
                `;
                const rect = this.getBoundingClientRect();
                const size = Math.max(rect.width, rect.height);
                ripple.style.width = ripple.style.height = size + 'px';
                ripple.style.left = (e.clientX - rect.left - size/2) + 'px';
                ripple.style.top = (e.clientY - rect.top - size/2) + 'px';
                this.style.position = 'relative';
                this.style.overflow = 'hidden';
                this.appendChild(ripple);
                setTimeout(() => ripple.remove(), 600);
            });
        });

        // Add ripple keyframe
        const style = document.createElement('style');
        style.textContent = `
            @keyframes ripple {
                to {
                    transform: scale(4);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);

        // ===== PARALLAX HERO =====
        const hero = document.querySelector('.hero');
        window.addEventListener('scroll', () => {
            const scrolled = window.scrollY;
            if (scrolled < window.innerHeight) {
                hero.style.transform = `translateY(${scrolled * 0.3}px)`;
                hero.style.opacity = 1 - scrolled / (window.innerHeight * 0.8);
            }
        });

        // ===== STAT COUNTER ANIMATION =====
        const statNumbers = document.querySelectorAll('.stat-number');
        const statObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const el = entry.target;
                    const text = el.textContent;
                    const hasPlus = text.includes('+');
                    const hasPercent = text.includes('%');
                    const hasMs = text.includes('ms');
                    const num = parseFloat(text.replace(/[^0-9.]/g, ''));
                    
                    let current = 0;
                    const increment = num / 60;
                    const timer = setInterval(() => {
                        current += increment;
                        if (current >= num) {
                            current = num;
                            clearInterval(timer);
                        }
                        let display = current < 10 ? current.toFixed(1) : Math.floor(current);
                        if (hasPlus) display += 'M+';
                        if (hasPercent) display += '%';
                        if (hasMs) display += 'ms';
                        el.textContent = display;
                    }, 16);
                    statObserver.unobserve(el);
                }
            });
        }, { threshold: 0.5 });

        statNumbers.forEach(el => statObserver.observe(el));

        // ===== TILT EFFECT ON CARDS =====
        document.querySelectorAll('.feature-card, .pricing-card, .testimonial-card').forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                const rotateX = (y - centerY) / 20;
                const rotateY = (centerX - x) / 20;
                card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateY(-4px)`;
            });

            card.addEventListener('mouseleave', () => {
                card.style.transform = '';
            });
        });

        // ===== TEXT SCRAMBLE EFFECT =====
        class TextScramble {
            constructor(el) {
                this.el = el;
                this.chars = '!<>-_\\/[]{}—=+*^?#________';
                this.update = this.update.bind(this);
            }
            setText(newText) {
                const oldText = this.el.innerText;
                const length = Math.max(oldText.length, newText.length);
                const promise = new Promise((resolve) => this.resolve = resolve);
                this.queue = [];
                for (let i = 0; i < length; i++) {
                    const from = oldText[i] || '';
                    const to = newText[i] || '';
                    const start = Math.floor(Math.random() * 40);
                    const end = start + Math.floor(Math.random() * 40);
                    this.queue.push({ from, to, start, end });
                }
                cancelAnimationFrame(this.frameRequest);
                this.frame = 0;
                this.update();
                return promise;
            }
            update() {
                let output = '';
                let complete = 0;
                for (let i = 0, n = this.queue.length; i < n; i++) {
                    let { from, to, start, end, char } = this.queue[i];
                    if (this.frame >= end) {
                        complete++;
                        output += to;
                    } else if (this.frame >= start) {
                        if (!char || Math.random() < 0.28) {
                            char = this.randomChar();
                            this.queue[i].char = char;
                        }
                        output += `<span style="color: rgba(255,255,255,0.3)">${char}</span>`;
                    } else {
                        output += from;
                    }
                }
                this.el.innerHTML = output;
                if (complete === this.queue.length) {
                    this.resolve();
                } else {
                    this.frameRequest = requestAnimationFrame(this.update);
                    this.frame++;
                }
            }
            randomChar() {
                return this.chars[Math.floor(Math.random() * this.chars.length)];
            }
        }

        // Apply scramble to section labels on hover
        document.querySelectorAll('.section-label').forEach(label => {
            const original = label.textContent;
            const scrambler = new TextScramble(label);
            let isHovering = false;
            
            label.parentElement.addEventListener('mouseenter', () => {
                if (!isHovering) {
                    isHovering = true;
                    scrambler.setText(original).then(() => { isHovering = false; });
                }
            });
        });

        // ===== PARTICLE SYSTEM =====
        const canvas = document.createElement('canvas');
        canvas.style.cssText = 'position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:3;opacity:0.4;';
        document.body.appendChild(canvas);
        const ctx = canvas.getContext('2d');
        let particles = [];
        const particleCount = 50;

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        class Particle {
            constructor() {
                this.reset();
            }
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 0.5;
                this.speedX = (Math.random() - 0.5) * 0.5;
                this.speedY = (Math.random() - 0.5) * 0.5;
                this.opacity = Math.random() * 0.5 + 0.1;
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.x < 0 || this.x > canvas.width || this.y < 0 || this.y > canvas.height) {
                    this.reset();
                }
            }
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = `rgba(255,255,255,${this.opacity})`;
                ctx.fill();
            }
        }

        for (let i = 0; i < particleCount; i++) {
            particles.push(new Particle());
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            
            // Draw connections
            for (let i = 0; i < particles.length; i++) {
                for (let j = i + 1; j < particles.length; j++) {
                    const dx = particles[i].x - particles[j].x;
                    const dy = particles[i].y - particles[j].y;
                    const dist = Math.sqrt(dx * dx + dy * dy);
                    if (dist < 150) {
                        ctx.beginPath();
                        ctx.moveTo(particles[i].x, particles[i].y);
                        ctx.lineTo(particles[j].x, particles[j].y);
                        ctx.strokeStyle = `rgba(255,255,255,${0.05 * (1 - dist / 150)})`;
                        ctx.lineWidth = 0.5;
                        ctx.stroke();
                    }
                }
            }
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        // ===== MAGNETIC BUTTONS =====
        document.querySelectorAll('.btn-primary, .cta-btn').forEach(btn => {
            btn.addEventListener('mousemove', (e) => {
                const rect = btn.getBoundingClientRect();
                const x = e.clientX - rect.left - rect.width / 2;
                const y = e.clientY - rect.top - rect.height / 2;
                btn.style.transform = `translate(${x * 0.2}px, ${y * 0.2}px)`;
            });
            btn.addEventListener('mouseleave', () => {
                btn.style.transform = '';
            });
        });

        // ===== KEYBOARD SHORTCUTS =====
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                closeMenu();
            }
            if (e.key === '/' && !e.ctrlKey && !e.metaKey && document.activeElement.tagName !== 'INPUT') {
                e.preventDefault();
                // Could open search modal here
            }
        });

        // ===== PREFERS REDUCED MOTION =====
        if (window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
            document.querySelectorAll('.aurora-blob, .marquee-track').forEach(el => {
                el.style.animation = 'none';
            });
        }

        // Console easter egg
        console.log('%c NEXUS ', 'background: #fff; color: #000; font-size: 24px; font-weight: 900; padding: 10px 20px; border-radius: 8px;');
        console.log('%c Создано с помощью Kimi AI ', 'color: rgba(255,255,255,0.4); font-size: 12px;');
    </script>
</body>
</html>
