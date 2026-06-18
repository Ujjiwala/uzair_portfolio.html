<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Uzair Salman | Portfolio</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        :root {
            --primary: #6366f1;
            --primary-light: #818cf8;
            --secondary: #ec4899;
            --accent: #06b6d4;
            --bg: #0a0a0f;
            --bg-card: rgba(255, 255, 255, 0.03);
            --bg-card-hover: rgba(255, 255, 255, 0.06);
            --text: #f1f5f9;
            --text-muted: #94a3b8;
            --border: rgba(255, 255, 255, 0.08);
            --gradient-1: linear-gradient(135deg, #6366f1 0%, #ec4899 50%, #06b6d4 100%);
            --gradient-2: linear-gradient(135deg, #06b6d4 0%, #6366f1 100%);
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
            font-family: 'Inter', sans-serif;
            background: var(--bg);
            color: var(--text);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Animated Background */
        .bg-mesh {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .bg-mesh::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: 
                radial-gradient(circle at 20% 80%, rgba(99, 102, 241, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(236, 72, 153, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 50% 50%, rgba(6, 182, 212, 0.08) 0%, transparent 50%);
            animation: meshMove 20s ease-in-out infinite;
        }

        @keyframes meshMove {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(30px, -30px) rotate(2deg); }
            66% { transform: translate(-20px, 20px) rotate(-1deg); }
        }

        /* Noise Texture */
        .noise {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.03;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
            pointer-events: none;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            padding: 1.2rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            backdrop-filter: blur(20px);
            background: rgba(10, 10, 15, 0.7);
            border-bottom: 1px solid var(--border);
            transition: all 0.3s ease;
        }

        nav.scrolled {
            padding: 0.8rem 5%;
            background: rgba(10, 10, 15, 0.9);
        }

        .logo {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -0.5px;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--gradient-1);
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--text);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--text);
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 8rem 5% 4rem;
            position: relative;
        }

        .hero-content {
            text-align: center;
            max-width: 900px;
        }

        /* Hero Profile Image */
        .hero-profile {
            margin-bottom: 2rem;
            position: relative;
            display: inline-block;
        }

        .hero-profile img {
            width: 160px;
            height: 160px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid transparent;
            background: var(--gradient-1);
            padding: 4px;
            transition: all 0.4s ease;
        }

        .hero-profile:hover img {
            transform: scale(1.05);
            box-shadow: 0 0 60px rgba(99, 102, 241, 0.4);
        }

        .hero-profile::before {
            content: '';
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            border-radius: 50%;
            background: var(--gradient-1);
            opacity: 0.2;
            filter: blur(20px);
            z-index: -1;
            animation: glowPulse 3s ease-in-out infinite;
        }

        @keyframes glowPulse {
            0%, 100% { opacity: 0.2; transform: scale(1); }
            50% { opacity: 0.4; transform: scale(1.05); }
        }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem 1.2rem;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 50px;
            font-size: 0.85rem;
            color: var(--primary-light);
            margin-bottom: 1.5rem;
            animation: fadeInUp 0.8s ease;
        }

        .hero-badge .dot {
            width: 8px;
            height: 8px;
            background: #22c55e;
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.2); }
        }

        .hero h1 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: clamp(2.5rem, 6vw, 5rem);
            font-weight: 700;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            letter-spacing: -2px;
        }

        .hero h1 .gradient-text {
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-subtitle {
            font-size: clamp(1rem, 2vw, 1.25rem);
            color: var(--text-muted);
            margin-bottom: 2.5rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 0.9rem 2rem;
            border-radius: 12px;
            font-size: 0.95rem;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            border: none;
        }

        .btn-primary {
            background: var(--gradient-1);
            color: white;
            box-shadow: 0 10px 40px rgba(99, 102, 241, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 20px 60px rgba(99, 102, 241, 0.4);
        }

        .btn-secondary {
            background: var(--bg-card);
            color: var(--text);
            border: 1px solid var(--border);
        }

        .btn-secondary:hover {
            background: var(--bg-card-hover);
            border-color: var(--primary-light);
            transform: translateY(-3px);
        }

        /* Stats Bar */
        .stats-bar {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin-top: 4rem;
            flex-wrap: wrap;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 2.5rem;
            font-weight: 700;
            background: var(--gradient-2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-top: 0.3rem;
        }

        /* Section Styles */
        section {
            padding: 6rem 5%;
            position: relative;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-tag {
            display: inline-block;
            padding: 0.4rem 1rem;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 50px;
            font-size: 0.8rem;
            color: var(--primary-light);
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .section-title {
            font-family: 'Space Grotesk', sans-serif;
            font-size: clamp(2rem, 4vw, 3rem);
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .section-desc {
            color: var(--text-muted);
            max-width: 600px;
            margin: 0 auto;
        }

        /* About Section */
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .about-visual {
            position: relative;
        }

        /* About Photo Card */
        .about-photo-card {
            position: relative;
            border-radius: 24px;
            overflow: hidden;
            background: var(--bg-card);
            border: 1px solid var(--border);
        }

        .about-photo-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--gradient-1);
            z-index: 2;
        }

        .about-photo-card img {
            width: 100%;
            height: auto;
            display: block;
            transition: transform 0.6s ease;
        }

        .about-photo-card:hover img {
            transform: scale(1.03);
        }

        .about-photo-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 2rem;
            background: linear-gradient(to top, rgba(10, 10, 15, 0.95) 0%, transparent 100%);
        }

        .about-photo-overlay h4 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.3rem;
            margin-bottom: 0.3rem;
        }

        .about-photo-overlay p {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        .about-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 24px;
            padding: 2.5rem;
            backdrop-filter: blur(20px);
            position: relative;
            overflow: hidden;
        }

        .about-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: var(--gradient-1);
        }

        .about-card h3 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .about-card p {
            color: var(--text-muted);
            line-height: 1.8;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .info-item {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .info-icon {
            width: 40px;
            height: 40px;
            border-radius: 10px;
            background: var(--bg-card-hover);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary-light);
            font-size: 1rem;
        }

        .info-text {
            font-size: 0.9rem;
        }

        .info-text strong {
            display: block;
            color: var(--text);
            font-weight: 600;
        }

        .info-text span {
            color: var(--text-muted);
            font-size: 0.85rem;
        }

        /* Skills Section */
        .skills-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .skill-category {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-category::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--gradient-1);
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .skill-category:hover {
            transform: translateY(-5px);
            border-color: rgba(99, 102, 241, 0.3);
        }

        .skill-category:hover::before {
            opacity: 0.03;
        }

        .skill-category > * {
            position: relative;
            z-index: 1;
        }

        .skill-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .skill-icon {
            width: 50px;
            height: 50px;
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3rem;
        }

        .skill-icon.tech { background: rgba(99, 102, 241, 0.15); color: #818cf8; }
        .skill-icon.ops { background: rgba(6, 182, 212, 0.15); color: #22d3ee; }
        .skill-icon.soft { background: rgba(236, 72, 153, 0.15); color: #f472b6; }

        .skill-header h3 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.2rem;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem;
        }

        .skill-tag {
            padding: 0.5rem 1rem;
            background: var(--bg-card-hover);
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 0.85rem;
            color: var(--text-muted);
            transition: all 0.3s ease;
        }

        .skill-tag:hover {
            background: rgba(99, 102, 241, 0.1);
            border-color: var(--primary-light);
            color: var(--text);
            transform: scale(1.05);
        }

        /* Experience Section */
        .experience-container {
            max-width: 900px;
            margin: 0 auto;
        }

        .timeline {
            position: relative;
            padding-left: 2rem;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 2px;
            background: var(--gradient-1);
            border-radius: 2px;
        }

        .timeline-item {
            position: relative;
            padding-bottom: 3rem;
            padding-left: 2rem;
        }

        .timeline-item:last-child {
            padding-bottom: 0;
        }

        .timeline-dot {
            position: absolute;
            left: -2rem;
            top: 0.5rem;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: var(--bg);
            border: 3px solid var(--primary);
            transform: translateX(-7px);
        }

        .timeline-item.active .timeline-dot {
            background: var(--primary);
            box-shadow: 0 0 20px rgba(99, 102, 241, 0.5);
        }

        .timeline-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.4s ease;
        }

        .timeline-card:hover {
            transform: translateX(10px);
            border-color: rgba(99, 102, 241, 0.3);
        }

        .timeline-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .timeline-title {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.3rem;
            font-weight: 600;
        }

        .timeline-company {
            color: var(--primary-light);
            font-weight: 500;
            font-size: 0.95rem;
        }

        .timeline-badge {
            padding: 0.3rem 0.8rem;
            background: rgba(34, 197, 94, 0.1);
            color: #22c55e;
            border-radius: 50px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .timeline-list {
            list-style: none;
            margin-top: 1rem;
        }

        .timeline-list li {
            position: relative;
            padding-left: 1.5rem;
            margin-bottom: 0.8rem;
            color: var(--text-muted);
            font-size: 0.9rem;
            line-height: 1.7;
        }

        .timeline-list li::before {
            content: '▸';
            position: absolute;
            left: 0;
            color: var(--primary-light);
        }

        /* Education Section */
        .education-container {
            max-width: 600px;
            margin: 0 auto;
        }

        .edu-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 2.5rem;
            text-align: cente
