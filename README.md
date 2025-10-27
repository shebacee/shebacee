<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fathimath Sheba C - Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Noto Sans', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #e8eef5 100%);
            color: #2d3748;
            overflow-x: hidden;
            position: relative;
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 100px 40px;
            position: relative;
            z-index: 1;
        }

        .hero {
            min-height: 80vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            margin-bottom: 120px;
        }

        .lily-decoration {
            position: absolute;
            opacity: 0.15;
            pointer-events: none;
        }

        .lily-1 {
            top: -50px;
            right: 100px;
            font-size: 120px;
            animation: float 6s ease-in-out infinite;
        }

        .lily-2 {
            bottom: 50px;
            left: 80px;
            font-size: 100px;
            animation: float 7s ease-in-out infinite 1s;
        }

        @keyframes float {

            0%,
            100% {
                transform: translateY(0) rotate(0deg);
            }

            50% {
                transform: translateY(-30px) rotate(5deg);
            }
        }

        .name {
            font-size: 72px;
            font-weight: 300;
            color: #1a202c;
            margin-bottom: 20px;
            letter-spacing: 2px;
            animation: fadeIn 1.2s ease-out;
        }

        .name-highlight {
            font-weight: 700;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
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

        .title {
            font-size: 20px;
            color: #718096;
            font-weight: 400;
            letter-spacing: 6px;
            text-transform: uppercase;
            margin-bottom: 40px;
            animation: fadeIn 1.4s ease-out;
        }

        .subtitle {
            font-size: 18px;
            color: #4a5568;
            max-width: 600px;
            line-height: 1.8;
            font-weight: 300;
            animation: fadeIn 1.6s ease-out;
        }

        .card {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(20px);
            border-radius: 30px;
            padding: 60px;
            margin-bottom: 60px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.08);
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.05) 0%, rgba(118, 75, 162, 0.05) 100%);
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 30px 80px rgba(102, 126, 234, 0.2);
        }

        .card:hover::before {
            opacity: 1;
        }

        .card-title {
            font-size: 14px;
            color: #667eea;
            letter-spacing: 4px;
            text-transform: uppercase;
            margin-bottom: 30px;
            font-weight: 600;
            position: relative;
            z-index: 1;
        }

        .card-content {
            font-size: 17px;
            color: #4a5568;
            line-height: 1.9;
            font-weight: 300;
            position: relative;
            z-index: 1;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
            margin: 80px 0;
        }

        .tech-card {
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 35px;
            text-align: center;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid rgba(102, 126, 234, 0.1);
            position: relative;
        }

        .tech-card::after {
            content: '🌸';
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 24px;
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .tech-card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 40px rgba(102, 126, 234, 0.15);
            border-color: rgba(102, 126, 234, 0.3);
        }

        .tech-card:hover::after {
            opacity: 0.3;
        }

        .tech-label {
            font-size: 12px;
            color: #667eea;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .tech-items {
            font-size: 15px;
            color: #4a5568;
            line-height: 1.8;
            font-weight: 300;
        }

        .education-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin: 60px 0;
        }

        .education-card {
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 25px;
            padding: 40px;
            border-left: 4px solid #667eea;
            transition: all 0.4s ease;
        }

        .education-card:hover {
            transform: translateX(10px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.12);
        }

        .education-degree {
            font-size: 20px;
            color: #1a202c;
            font-weight: 600;
            margin-bottom: 15px;
            line-height: 1.4;
        }

        .education-details {
            font-size: 15px;
            color: #718096;
            line-height: 1.8;
            font-weight: 300;
        }

        .project-showcase {
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
            border-radius: 40px;
            padding: 80px;
            margin: 100px 0;
            position: relative;
            overflow: hidden;
        }

        .project-showcase::before {
            content: '🌺';
            position: absolute;
            font-size: 200px;
            opacity: 0.05;
            top: -50px;
            right: -50px;
            animation: rotate 20s linear infinite;
        }

        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }

            to {
                transform: rotate(360deg);
            }
        }

        .project-label {
            font-size: 12px;
            color: #667eea;
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .project-name {
            font-size: 64px;
            font-weight: 700;
            color: #1a202c;
            margin-bottom: 30px;
            letter-spacing: -1px;
        }

        .project-description {
            font-size: 18px;
            color: #4a5568;
            line-height: 1.9;
            max-width: 700px;
            font-weight: 300;
        }

        .contact-section {
            text-align: center;
            padding: 80px 0;
            position: relative;
        }

        .contact-email {
            font-size: 32px;
            color: #667eea;
            font-weight: 600;
            text-decoration: none;
            display: inline-block;
            transition: all 0.3s ease;
            margin-bottom: 30px;
        }

        .contact-email:hover {
            transform: scale(1.05);
            color: #764ba2;
        }

        .contact-message {
            font-size: 16px;
            color: #718096;
            font-style: italic;
            font-weight: 300;
        }

        .divider {
            width: 100px;
            height: 2px;
            background: linear-gradient(90deg, transparent, #667eea, transparent);
            margin: 60px auto;
        }

        @media (max-width: 768px) {
            .name {
                font-size: 42px;
            }

            .grid {
                grid-template-columns: 1fr;
            }

            .education-section {
                grid-template-columns: 1fr;
            }

            .card {
                padding: 40px;
            }

            .project-showcase {
                padding: 50px 30px;
            }

            .project-name {
                font-size: 42px;
            }

            .lily-1,
            .lily-2 {
                display: none;
            }
        }

        .animate-in {
            animation: slideUp 0.8s ease-out forwards;
            opacity: 0;
        }

        @keyframes slideUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .animate-in {
            transform: translateY(30px);
        }

        .delay-1 {
            animation-delay: 0.2s;
        }

        .delay-2 {
            animation-delay: 0.4s;
        }

        .delay-3 {
            animation-delay: 0.6s;
        }

        .delay-4 {
            animation-delay: 0.8s;
        }
    </style>
</head>

<body>
    <canvas id="canvas"></canvas>

    <div class="container">
        <div class="hero">
            <div class="lily-decoration lily-1">🌸</div>
            <div class="lily-decoration lily-2">🌸</div>

            <h1 class="name">
                <span class="name-highlight">FATHIMATH</span> SHEBA C
            </h1>
            <p class="title">Frontend Developer</p>
            <p class="subtitle">
                Building elegant solutions with clean code and thoughtful design.
                From concept to deployment, I create experiences that matter.
            </p>
        </div>

        <div class="card animate-in delay-1">
            <h2 class="card-title">About</h2>
            <div class="card-content">
                BCA graduate pursuing MCA in Data Analysis. I specialize in creating scalable,
                user-centric applications with a focus on frontend excellence.
                <br><br>
                Full-stack capabilities with expertise in AI integration. I don't just write
                code—I craft experiences. Currently expanding my skills in React while
                continuously exploring emerging technologies.
                <br><br>
                Self-motivated learner with a passion for building things that solve real problems.
            </div>
        </div>

        <div class="card animate-in delay-2">
            <h2 class="card-title">Tech Stack</h2>
            <div class="grid">
                <div class="tech-card">
                    <div class="tech-label">Frontend</div>
                    <div class="tech-items">HTML<br>CSS<br>JavaScript</div>
                </div>
                <div class="tech-card">
                    <div class="tech-label">Backend</div>
                    <div class="tech-items">Python<br>Django<br>MySQL</div>
                </div>
                <div class="tech-card">
                    <div class="tech-label">Learning</div>
                    <div class="tech-items">React</div>
                </div>
            </div>
        </div>

        <div class="card animate-in delay-3">
            <h2 class="card-title">Education</h2>
            <div class="education-section">
                <div class="education-card">
                    <div class="education-degree">
                        Master of Computer Applications<br>
                        <span style="font-size: 16px; color: #667eea;">Data Analysis</span>
                    </div>
                    <div class="education-details">
                        Jain University, Bangalore<br>
                        Present
                    </div>
                </div>
                <div class="education-card">
                    <div class="education-degree">
                        Bachelor of Computer Applications
                    </div>
                    <div class="education-details">
                        Kannur University, Kerala<br>
                        2022 - 2025<br>
                        CGPA: 7.4
                    </div>
                </div>
            </div>
        </div>

        <div class="project-showcase animate-in delay-4">
            <div class="project-label">Featured Project</div>
            <div class="project-name">EON</div>
            <div class="project-description">
                Eon is a full-stack hub for book trading, study collabs & blog-style thoughtwaves. Features user-driven MCQs that
                auto-generate quizzes, content moderation via admin panel, and a chatbot.
            </div>
        </div>

        <div class="divider"></div>

        <div class="contact-section">
            <a href="mailto:shebacee.dev@gmail.com" class="contact-email">
                shebacee.dev@gmail.com
            </a>
            <p class="contact-message">
                trying to be better everyday. love to build stuff.
            </p>
        </div>
    </div>

    <script>
        // 3D Floating petals animation
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        class Petal {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height - canvas.height;
                this.size = Math.random() * 15 + 8;
                this.speedY = Math.random() * 1 + 0.5;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.rotation = Math.random() * 360;
                this.rotationSpeed = Math.random() * 2 - 1;
                this.opacity = Math.random() * 0.3 + 0.2;
            }

            update() {
                this.y += this.speedY;
                this.x += this.speedX;
                this.rotation += this.rotationSpeed;

                if (this.y > canvas.height) {
                    this.y = -20;
                    this.x = Math.random() * canvas.width;
                }

                if (this.x > canvas.width) {
                    this.x = 0;
                } else if (this.x < 0) {
                    this.x = canvas.width;
                }
            }

            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.rotate(this.rotation * Math.PI / 180);
                ctx.globalAlpha = this.opacity;

                ctx.fillStyle = '#667eea';
                ctx.beginPath();
                ctx.arc(0, 0, this.size, 0, Math.PI * 2);
                ctx.fill();

                ctx.fillStyle = '#764ba2';
                ctx.beginPath();
                ctx.arc(this.size * 0.3, 0, this.size * 0.6, 0, Math.PI * 2);
                ctx.fill();

                ctx.restore();
            }
        }

        const petals = [];
        for (let i = 0; i < 30; i++) {
            petals.push(new Petal());
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            petals.forEach(petal => {
                petal.update();
                petal.draw();
            });

            requestAnimationFrame(animate);
        }

        animate();

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        // Intersection Observer for scroll animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, { threshold: 0.1 });

        document.querySelectorAll('.animate-in').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>

</html>
