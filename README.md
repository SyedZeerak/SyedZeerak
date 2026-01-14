<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Syed Wajdan Zeerak - Interactive Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 50%, #0a0e27 100%);
            color: #fff;
            overflow-x: hidden;
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            padding: 60px 20px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 40px;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 255, 0.1), transparent);
            animation: rotate 6s linear infinite;
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .header-content {
            position: relative;
            z-index: 1;
        }

        h1 {
            font-size: 3.5em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #00ffff, #00ff88);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: glow 2s ease-in-out infinite;
        }

        @keyframes glow {
            0%, 100% { filter: drop-shadow(0 0 10px rgba(0, 255, 255, 0.5)); }
            50% { filter: drop-shadow(0 0 20px rgba(0, 255, 255, 0.8)); }
        }

        .subtitle {
            font-size: 1.5em;
            color: #00ffff;
            margin-bottom: 30px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .social-btn {
            padding: 12px 30px;
            background: rgba(0, 255, 255, 0.1);
            border: 2px solid #00ffff;
            border-radius: 25px;
            color: #00ffff;
            text-decoration: none;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .social-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(0, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.5s, height 0.5s;
        }

        .social-btn:hover::before {
            width: 300px;
            height: 300px;
        }

        .social-btn:hover {
            background: rgba(0, 255, 255, 0.2);
            transform: scale(1.05);
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
        }

        .social-btn span {
            position: relative;
            z-index: 1;
        }

        .tabs {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 40px;
            flex-wrap: wrap;
        }

        .tab {
            padding: 15px 30px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid transparent;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 1.1em;
        }

        .tab:hover {
            background: rgba(0, 255, 255, 0.1);
            border-color: #00ffff;
            transform: translateY(-3px);
        }

        .tab.active {
            background: linear-gradient(45deg, #00ffff, #00ff88);
            color: #0a0e27;
            font-weight: bold;
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.5);
        }

        .content-section {
            display: none;
            animation: fadeIn 0.5s;
        }

        .content-section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .achievement-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .achievement-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .achievement-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .achievement-card:hover::before {
            left: 100%;
        }

        .achievement-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 10px 40px rgba(0, 255, 255, 0.3);
            border-color: #00ffff;
        }

        .achievement-icon {
            font-size: 3em;
            margin-bottom: 15px;
        }

        .achievement-title {
            font-size: 1.3em;
            color: #00ffff;
            margin-bottom: 10px;
        }

        .achievement-desc {
            color: #ccc;
            line-height: 1.6;
        }

        .skill-container {
            margin-top: 20px;
        }

        .skill-category {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .skill-category h3 {
            color: #00ffff;
            margin-bottom: 20px;
            font-size: 1.5em;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .skill-tag {
            padding: 10px 20px;
            background: linear-gradient(45deg, rgba(0, 255, 255, 0.2), rgba(0, 255, 136, 0.2));
            border: 1px solid #00ffff;
            border-radius: 20px;
            transition: all 0.3s;
            cursor: pointer;
        }

        .skill-tag:hover {
            transform: scale(1.1) rotate(2deg);
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
            background: linear-gradient(45deg, rgba(0, 255, 255, 0.4), rgba(0, 255, 136, 0.4));
        }

        .project-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s;
            cursor: pointer;
        }

        .project-card:hover {
            transform: translateX(10px);
            box-shadow: -10px 10px 40px rgba(0, 255, 255, 0.3);
            border-color: #00ffff;
        }

        .project-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
        }

        .project-icon {
            font-size: 2.5em;
        }

        .project-title {
            font-size: 1.8em;
            color: #00ffff;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin: 15px 0;
        }

        .tech-badge {
            padding: 5px 15px;
            background: rgba(0, 255, 136, 0.2);
            border: 1px solid #00ff88;
            border-radius: 15px;
            font-size: 0.9em;
        }

        .metric {
            display: inline-block;
            padding: 8px 16px;
            background: linear-gradient(45deg, #ff6b35, #ff8c42);
            border-radius: 20px;
            margin: 5px;
            font-weight: bold;
        }

        .contact-section {
            text-align: center;
            padding: 40px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .contact-form {
            max-width: 500px;
            margin: 30px auto;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            color: #fff;
            font-size: 1em;
            transition: all 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #00ffff;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
        }

        .submit-btn {
            padding: 15px 50px;
            background: linear-gradient(45deg, #00ffff, #00ff88);
            border: none;
            border-radius: 25px;
            color: #0a0e27;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }

        .submit-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.6);
        }

        .stats-counter {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .stat-box {
            text-align: center;
            padding: 30px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s;
        }

        .stat-box:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.3);
        }

        .stat-number {
            font-size: 3em;
            color: #00ffff;
            font-weight: bold;
            display: block;
        }

        .stat-label {
            font-size: 1.1em;
            color: #ccc;
            margin-top: 10px;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2em;
            }

            .subtitle {
                font-size: 1.2em;
            }

            .tabs {
                flex-direction: column;
            }

            .achievement-grid {
                grid-template-columns: 1fr;
            }
        }

        .timeline {
            position: relative;
            padding: 20px 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(180deg, #00ffff, #00ff88);
        }

        .timeline-item {
            position: relative;
            margin: 40px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .timeline-content {
            width: 45%;
            padding: 20px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s;
        }

        .timeline-content:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.3);
        }

        .timeline-dot {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 20px;
            height: 20px;
            background: #00ffff;
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.8);
            z-index: 2;
        }

        @media (max-width: 768px) {
            .timeline::before {
                left: 20px;
            }

            .timeline-item {
                flex-direction: column;
                align-items: flex-start;
            }

            .timeline-content {
                width: calc(100% - 60px);
                margin-left: 40px;
            }

            .timeline-dot {
                left: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="stars" id="stars"></div>

    <div class="container">
        <div class="header">
            <div class="header-content">
                <h1>SYED WAJDAN ZEERAK</h1>
                <p class="subtitle">🚀 Data Scientist | AI Engineer | Computer Vision Specialist</p>
                <div class="social-links">
                    <a href="https://linkedin.com/in/syed-wajdan-zeerak" class="social-btn" target="_blank">
                        <span>💼 LinkedIn</span>
                    </a>
                    <a href="https://kaggle.com/Syed-Zeerak" class="social-btn" target="_blank">
                        <span>🏆 Kaggle</span>
                    </a>
                    <a href="https://github.com/SyedZeerak" class="social-btn" target="_blank">
                        <span>💻 GitHub</span>
                    </a>
                    <a href="mailto:clashzeerak@gmail.com" class="social-btn">
                        <span>📧 Email</span>
                    </a>
                </div>
            </div>
        </div>

        <div class="tabs">
            <div class="tab active" onclick="showSection('about')">👨‍💻 About</div>
            <div class="tab" onclick="showSection('achievements')">🏆 Achievements</div>
            <div class="tab" onclick="showSection('experience')">💼 Experience</div>
            <div class="tab" onclick="showSection('projects')">🚀 Projects</div>
            <div class="tab" onclick="showSection('skills')">⚡ Skills</div>
            <div class="tab" onclick="showSection('contact')">📬 Contact</div>
        </div>

        <div id="about" class="content-section active">
            <div class="achievement-card">
                <h2 style="color: #00ffff; margin-bottom: 20px;">About Me</h2>
                <p style="line-height: 1.8; color: #ccc; font-size: 1.1em;">
                    I'm a passionate Data Scientist and AI Engineer specializing in Computer Vision, Machine Learning, and Business Intelligence. 
                    Currently pursuing my BS in Data Science at Air University, Islamabad, I focus on developing innovative AI solutions 
                    that transform complex data into actionable insights.
                </p>
                <p style="line-height: 1.8; color: #ccc; font-size: 1.1em; margin-top: 15px;">
                    With hands-on experience in industry projects and competitive data science, I'm committed to pushing the boundaries 
                    of what's possible with AI and machine learning technologies.
                </p>
            </div>

            <div class="stats-counter">
                <div class="stat-box">
                    <span class="stat-number" data-target="90">0</span>
                    <span class="stat-label">% CV Accuracy</span>
                </div>
                <div class="stat-box">
                    <span class="stat-number" data-target="330">0</span>
                    <span class="stat-label">% ML Boost</span>
                </div>
                <div class="stat-box">
                    <span class="stat-number" data-target="300">0</span>
                    <span class="stat-label">+ Students Mentored</span>
                </div>
                <div class="stat-box">
                    <span class="stat-number" data-target="130">0</span>
                    <span class="stat-label">+ Districts Analyzed</span>
                </div>
            </div>
        </div>

        <div id="achievements" class="content-section">
            <div class="achievement-grid">
                <div class="achievement-card">
                    <div class="achievement-icon">🥇</div>
                    <h3 class="achievement-title">National Champion</h3>
                    <p class="achievement-desc">DataFest'24 winner with Pakistan Bureau of Statistics. Led comprehensive data analysis across 130+ districts.</p>
                </div>
                <div class="achievement-card">
                    <div class="achievement-icon">🥈</div>
                    <h3 class="achievement-title">Power BI Expert</h3>
                    <p class="achievement-desc">Runner-up at Analytix Camp 2025. Demonstrated advanced BI and visualization capabilities.</p>
                </div>
                <div class="achievement-card">
                    <div class="achievement-icon">⚡</div>
                    <h3 class="achievement-title">330% Performance Boost</h3>
                    <p class="achievement-desc">Developed Gated MoE model improving R² from 0.2088 to 0.8991 for salary prediction.</p>
                </div>
                <div class="achievement-card">
                    <div class="achievement-icon">🎯</div>
                    <h3 class="achievement-title">90% CV Accuracy</h3>
                    <p class="achievement-desc">Created YOLOv11-based SKU recognition system at PepsiCo achieving 90% mAP@50.</p>
                </div>
                <div class="achievement-card">
                    <div class="achievement-icon">👥</div>
                    <h3 class="achievement-title">VP Leadership</h3>
                    <p class="achievement-desc">Vice President of Data & AI Society, mentoring 300+ students in data science.</p>
                </div>
                <div class="achievement-card">
                    <div class="achievement-icon">📈</div>
                    <h3 class="achievement-title">70% Automation</h3>
                    <p class="achievement-desc">Reduced manual reporting time through intelligent BI automation for global clients.</p>
                </div>
            </div>
        </div>

        <div id="experience" class="content-section">
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-content">
                        <h3 style="color: #00ffff; margin-bottom: 10px;">AI & Data Analytics Intern</h3>
                        <h4 style="color: #00ff88;">PepsiCo</h4>
                        <p style="color: #999; margin: 10px 0;">July 2024 - August 2024 | Islamabad</p>
                        <ul style="margin-top: 15px; color: #ccc; line-height: 1.8;">
                            <li>Developed YOLOv11 CV model with 90% mAP@50 accuracy</li>
                            <li>Created data pipeline with 1,000+ annotated images</li>
                            <li>Deployed models to Hugging Face Spaces</li>
                            <li>Conducted real-world retail validation testing</li>
                        </ul>
                    </div>
                    <div class="timeline-dot"></div>
                    <div style="width: 45%;"></div>
                </div>

                <div class="timeline-item">
                    <div style="width: 45%;"></div>
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <h3 style="color: #00ffff; margin-bottom: 10px;">Freelance BI Consultant</h3>
                        <h4 style="color: #00ff88;">Remote - Global</h4>
                        <p style="color: #999; margin: 10px 0;">August 2024 - Present</p>
                        <ul style="margin-top: 15px; color: #ccc; line-height: 1.8;">
                            <li>Delivering solutions across USA, UK, EU, Pakistan</li>
                            <li>70% reduction in manual reporting time</li>
                            <li>Power Query, DAX, REST API integrations</li>
                            <li>End-to-end project lifecycle management</li>
                        </ul>
                    </div>
                </div>

                <div class="timeline-item">
                    <div class="timeline-content">
                        <h3 style="color: #00ffff; margin-bottom: 10px;">Vice President</h3>
                        <h4 style="color: #00ff88;">Data & AI Society, Air University</h4>
                        <p style="color: #999; margin: 10px 0;">2023 - 2025</p>
                        <ul style="margin-top: 15px; color: #ccc; line-height: 1.8;">
                            <li>Organized national seminars with SAP, IGNITE</li>
                            <li>Led competitions with 300+ participants</li>
                            <li>Mentored aspiring data scientists</li>
                            <li>Established strategic tech partnerships</li>
                        </ul>
                    </div>
                    <div class="timeline-dot"></div>
                    <div style="width: 45%;"></div>
                </div>
            </div>
        </div>

        <div id="projects" class="content-section">
            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🧠</div>
                    <h3 class="project-title">Gated Mixture-of-Experts for Salary Prediction</h3>
                </div>
                <p style="color: #ccc; line-height: 1.8; margin: 15px 0;">
                    Revolutionary ML architecture achieving 330% performance improvement. Scraped 1,000+ job listings from Rozee.pk, 
                    implemented advanced feature engineering with TF-IDF and SVD.
                </p>
                <div class="project-tech">
                    <span class="tech-badge">Python</span>
                    <span class="tech-badge">Scikit-learn</span>
                    <span class="tech-badge">XGBoost</span>
                    <span class="tech-badge">Power BI</span>
                    <span class="tech-badge">Web Scraping</span>
                </div>
                <div>
                    <span class="metric">R² 0.2088 → 0.8991</span>
                    <span class="metric">330% Improvement</span>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🗺️</div>
                    <h3 class="project-title">Pakistan Districts Socioeconomic Analysis</h3>
                </div>
                <p style="color: #ccc; line-height: 1.8; margin: 15px 0;">
                    Comprehensive analysis of 130+ Pakistani districts using advanced clustering algorithms. Identified 4 distinct 
                    socioeconomic clusters and provided data-driven policy recommendations.
                </p>
                <div class="project-tech">
                    <span class="tech-badge">Python</span>
                    <span class="tech-badge">Pandas</span>
                    <span class="tech-badge">KMeans</span>
                    <span class="tech-badge">t-SNE</span>
                    <span class="tech-badge">PCA</span>
                </div>
                <div>
                    <span class="metric">130+ Districts</span>
                    <span class="metric">4 Clusters</span>
                    <span class="metric">National Impact</span>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <div class="project-icon">🎯</div>
                    <h3 class="project-title">Real-time SKU Recognition System</h3>
                </div>
                <p style="color: #ccc; line-height: 1.8; margin: 15px 0;">
                    Production-grade computer vision system for retail product recognition deployed at PepsiCo. 
                    Handles real-time inference across diverse conditions.
                </p>
                <div class="project-tech">
                    <span class="tech-badge">YOLOv11</span>
                    <span class="tech-badge">OpenCV</span>
                    <span class="tech-badge">Python</span>
                    <span class="tech-badge">Hugging Face</span>
                </div>
                <div>
                    <span class="metric">90% mAP@50</span>
                    <span class="metric">1,000+ Images</span>
                    <span class="metric">Production Ready</span>
                </div>
            </div>
        </div>

        <div id="skills" class="content-section">
            <div class="skill-container">
                <div class="skill-category">
                    <h3>💻 Programming & Tools</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">SQL</span>
                        <span class="skill-tag">Git</span>
                        <span class="skill-tag">Flask</span>
                        <span class="skill-tag">REST APIs</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>🤖 Machine Learning & AI</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Scikit-learn</span>
                        <span class="skill-tag">XGBoost</span>
                        <span class="skill-tag">OpenCV</span>
                        <span class="skill-tag">YOLO</span>
                        <span class="skill-tag">TensorFlow</span>
                        <span class="skill-tag">Deep Learning</span>
                        <span class="skill-tag">Computer Vision</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>📊 Data Analysis & Visualization</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Pandas</span>
                        <span class="skill-tag">NumPy</span>
                        <span class="skill-tag">Power BI</span>
                        <span class="skill-tag">DAX</span>
                        <span class="skill-tag">Power Query</span>
                        <span class="skill-tag">Excel</span>
                        <span class="skill-tag">Matplotlib</span>
                        <span class="skill-tag">Seaborn</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>🌐 Web Scraping & Automation</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Selenium</span>
                        <span class="skill-tag">BeautifulSoup</span>
                        <span class="skill-tag">Scrapy</span>
                        <span class="skill-tag">Automation</span>
                    </div>
                </div>
            </div>
        </div>

        <div id="contact" class="content-section">
            <div class="contact-section">
                <h2 style="color: #00ffff; margin-bottom: 20px; font-size: 2.5em;">Let's Connect!</h2>
                <p style="color: #ccc; font-size: 1.2em; margin-bottom: 30px;">
                    I'm always interested in collaborating on innovative AI/ML projects, discussing data science challenges, 
                    or exploring new opportunities. Feel free to reach out!
                </p>
                
                <div style="display: flex; justify-content: center; gap: 30px; flex-wrap: wrap; margin: 30px 0;">
                    <div style="text-align: center;">
                        <div style="font-size: 3em; margin-bottom: 10px;">📧</div>
                        <a href="mailto:clashzeerak@gmail.com" style="color: #00ffff; text-decoration: none;">
                            clashzeerak@gmail.com
                        </a>
                    </div>
                    <div style="text-align: center;">
                        <div style="font-size: 3em; margin-bottom: 10px;">📍</div>
                        <p style="color: #ccc;">Islamabad, Pakistan</p>
                    </div>
                    <div style="text-align: center;">
                        <div style="font-size: 3em; margin-bottom: 10px;">🎓</div>
                        <p style="color: #ccc;">Air University</p>
                    </div>
                </div>

                <div style="margin-top: 40px;">
                    <h3 style="color: #00ffff; margin-bottom: 20px;">Current Focus</h3>
                    <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 15px;">
                        <span class="skill-tag">🔬 Advanced CV Research</span>
                        <span class="skill-tag">🏆 Kaggle Competitions</span>
                        <span class="skill-tag">💼 Global BI Consulting</span>
                        <span class="skill-tag">🌐 Open Source ML</span>
                        <span class="skill-tag">👥 AI Mentorship</span>
                    </div>
                </div>

                <p style="margin-top: 40px; font-style: italic; color: #00ff88; font-size: 1.3em;">
                    "Transforming data into intelligence, one algorithm at a time"
                </p>
            </div>
        </div>
    </div>

    <script>
        // Create animated stars
        function createStars() {
            const starsContainer = document.getElementById('stars');
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.width = Math.random() * 3 + 'px';
                star.style.height = star.style.width;
                star.style.animationDelay = Math.random() * 3 + 's';
                starsContainer.appendChild(star);
            }
        }

        // Tab switching
        function showSection(sectionId) {
            const sections = document.querySelectorAll('.content-section');
            const tabs = document.querySelectorAll('.tab');
            
            sections.forEach(section => section.classList.remove('active'));
            tabs.forEach(tab => tab.classList.remove('active'));
            
            document.getElementById(sectionId).classList.add('active');
            event.target.classList.add('active');

            // Animate counters when showing about section
            if (sectionId === 'about') {
                animateCounters();
            }
        }

        // Animated counter
        function animateCounters() {
            const counters = document.querySelectorAll('.stat-number');
            counters.forEach(counter => {
                const target = parseInt(counter.getAttribute('data-target'));
                const duration = 2000;
                const increment = target / (duration / 16);
                let current = 0;

                const updateCounter = () => {
                    current += increment;
                    if (current < target) {
                        counter.textContent = Math.floor(current);
                        requestAnimationFrame(updateCounter);
                    } else {
                        counter.textContent = target;
                    }
                };

                counter.textContent = '0';
                updateCounter();
            });
        }

        // Intersection Observer for scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Initialize
        window.addEventListener('DOMContentLoaded', () => {
            createStars();
            animateCounters();

            // Observe all cards for scroll animations
            document.querySelectorAll('.achievement-card, .project-card, .skill-category').forEach(el => {
                el.style.opacity = '0';
                el.style.transform = 'translateY(20px)';
                el.style.transition = 'all 0.6s ease-out';
                observer.observe(el);
            });
        });

        // Add particle effect on mouse move
        document.addEventListener('mousemove', (e) => {
            if (Math.random() > 0.95) {
                const particle = document.createElement('div');
                particle.style.position = 'fixed';
                particle.style.left = e.clientX + 'px';
                particle.style.top = e.clientY + 'px';
                particle.style.width = '4px';
                particle.style.height = '4px';
                particle.style.background = '#00ffff';
                particle.style.borderRadius = '50%';
                particle.style.pointerEvents = 'none';
                particle.style.zIndex = '9999';
                particle.style.opacity = '1';
                particle.style.transition = 'all 1s ease-out';
                document.body.appendChild(particle);

                setTimeout(() => {
                    particle.style.opacity = '0';
                    particle.style.transform = 'translateY(-50px)';
                }, 50);

                setTimeout(() => {
                    particle.remove();
                }, 1000);
            }
        });
    </script>
</body>
</html>
