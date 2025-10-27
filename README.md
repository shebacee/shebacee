<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fathimath Sheba C - Portfolio</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #000;
            color: #fff;
            overflow-x: hidden;
        }

        #three-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .speed-lines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
            overflow: hidden;
        }

        .speed-line {
            position: absolute;
            width: 200px;
            height: 2px;
            background: linear-gradient(90deg, transparent, rgba(26, 115, 232, 0.8), transparent);
            animation: speedLine 2s linear infinite;
        }

        @keyframes speedLine {
            0% {
                left: -200px;
                opacity: 0;
            }
            50% {
                opacity: 1;
            }
            100% {
                left: 100%;
                opacity: 0;
            }
        }

        .container {
            position: relative;
            z-index: 2;
            max-width: 1400px;
            margin: 0 auto;
            padding: 80px 40px;
        }

        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
        }

        .hero-badge {
            display: inline-block;
            background: linear-gradient(135deg, #1a73e8 0%, #0d47a1 100%);
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 12px;
            letter-spacing: 3px;
            text-transform: uppercase;
            font-weight: 700;
            margin-bottom: 40px;
            box-shadow: 0 10px 40px rgba(26, 115, 232, 0.3);
            animation: slideIn 1s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .name {
            font-size: 100px;
            font-weight: 900;
            background: linear-gradient(135deg, #fff 0%, #1a73e8 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
            letter-spacing: -3px;
            line-height: 1.1;
            animation: slideIn 1.2s ease-out;
        }

        .title {
            font-size: 28px;
            color: #1a73e8;
            font-weight: 300;
            letter-spacing: 8px;
            text-transform: uppercase;
            margin-bottom: 50px;
            animation: slideIn 1.4s ease-out;
        }

        .tagline {
            font-size: 20px;
            color: rgba(255, 255, 255, 0.7);
            max-width: 700px;
            line-height: 1.8;
            font-weight: 300;
            animation: slideIn 1.6s ease-out;
        }

        .carbon-fiber {
            background: 
                repeating-linear-gradient(
                    45deg,
                    rgba(0, 0, 0, 0.3) 0px,
                    rgba(0, 0, 0, 0.3) 2px,
                    transparent 2px,
                    transparent 4px
                ),
                repeating-linear-gradient(
                    -45deg,
                    rgba(0, 0, 0, 0.3) 0px,
                    rgba(0, 0, 0, 0.3) 2px,
                    transparent 2px,
                    transparent 4px
                ),
                linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
        }

        .performance-card {
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(26, 115, 232, 0.3);
            border-radius: 20px;
            padding: 60px;
            margin: 60px 0;
            position: relative;
            overflow: hidden;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .performance-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(26, 115, 232, 0.1), transparent);
            transition: left 0.8s ease;
        }

        .performance-card:hover::before {
            left: 100%;
        }

        .performance-card:hover {
            transform: translateY(-10px);
            border-color: rgba(26, 115, 232, 0.6);
            box-shadow: 0 30px 60px rgba(26, 115, 232, 0.3);
        }

        .section-label {
            font-size: 12px;
            color: #1a73e8;
            letter-spacing: 4px;
            text-transform: uppercase;
            font-weight: 700;
            margin-bottom: 30px;
            display: inline-block;
            position: relative;
        }

        .section-label::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 40px;
            height: 2px;
            background: #1a73e8;
        }

        .section-content {
            font-size: 18px;
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.9;
            font-weight: 300;
        }

        .specs-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
            margin: 80px 0;
        }

        .spec-box {
            background: rgba(26, 115, 232, 0.05);
            border: 2px solid rgba(26, 115, 232, 0.2);
            border-radius: 15px;
            padding: 40px;
            text-align: center;
            position: relative;
            transition: all 0.4s ease;
            clip-path: polygon(15px 0, 100% 0, 100% calc(100% - 15px), calc(100% - 15px) 100%, 0 100%, 0 15px);
        }

        .spec-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(26, 115, 232, 0.1) 0%, transparent 100%);
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .spec-box:hover {
            border-color: #1a73e8;
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 50px rgba(26, 115, 232, 0.3);
        }

        .spec-box:hover::before {
            opacity: 1;
        }

        .spec-label {
            font-size: 11px;
            color: #1a73e8;
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 20px;
            font-weight: 700;
        }

        .spec-value {
            font-size: 16px;
            color: rgba(255, 255, 255, 0.9);
            line-height: 2;
            font-weight: 300;
        }

        .education-timeline {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin: 60px 0;
        }

        .timeline-item {
            background: rgba(10, 10, 10, 0.6);
            border-left: 4px solid #1a73e8;
            padding: 40px;
            position: relative;
            transition: all 0.4s ease;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -8px;
            top: 40px;
            width: 12px;
            height: 12px;
            background: #1a73e8;
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(26, 115, 232, 0.8);
        }

        .timeline-item:hover {
            background: rgba(26, 115, 232, 0.05);
            transform: translateX(10px);
        }

        .timeline-degree {
            font-size: 22px;
            color: #fff;
            font-weight: 700;
            margin-bottom: 15px;
            line-height: 1.3;
        }

        .timeline-details {
            font-size: 16px;
            color: rgba(255, 255, 255, 0.6);
            line-height: 1.8;
            font-weight: 300;
        }

        .showcase {
            background: linear-gradient(135deg, rgba(26, 115, 232, 0.1) 0%, rgba(13, 71, 161, 0.1) 100%);
            border: 2px solid rgba(26, 115, 232, 0.3);
            border-radius: 30px;
            padding: 100px;
            margin: 120px 0;
            position: relative;
            overflow: hidden;
        }

        .showcase::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(26, 115, 232, 0.1) 0%, transparent 70%);
            animation: rotate 15s linear infinite;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .showcase-label {
            font-size: 12px;
            color: #1a73e8;
            text-transform: uppercase;
            letter-spacing: 4px;
            margin-bottom: 20px;
            font-weight: 700;
            position: relative;
            z-index: 1;
        }

        .showcase-name {
            font-size: 96px;
            font-weight: 900;
            color: #fff;
            margin-bottom: 40px;
            letter-spacing: -2px;
            position: relative;
            z-index: 1;
            text-shadow: 0 0 40px rgba(26, 115, 232, 0.5);
        }

        .showcase-description {
            font-size: 18px;
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.9;
            max-width: 900px;
            font-weight: 300;
            position: relative;
            z-index: 1;
        }

        .contact-section {
            text-align: center;
            padding: 100px 0;
            position: relative;
        }

        .contact-title {
            font-size: 14px;
            color: #1a73e8;
            text-transform: uppercase;
            letter-spacing: 5px;
            margin-bottom: 30px;
            font-weight: 700;
        }

        .contact-email {
            font-size: 42px;
            color: #fff;
            text-decoration: none;
            font-weight: 700;
            display: inline-block;
            transition: all 0.3s ease;
            position: relative;
        }

        .contact-email::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 0;
            height: 3px;
            background: linear-gradient(90deg, #1a73e8, #0d47a1);
            transition: width 0.4s ease;
        }

        .contact-email:hover::after {
            width: 100%;
        }

        .contact-email:hover {
            color: #1a73e8;
            transform: scale(1.05);
        }

        .footer-text {
            font-size: 16px;
            color: rgba(255, 255, 255, 0.5);
            margin-top: 40px;
            font-style: italic;
            font-weight: 300;
        }

        .divider {
            width: 100%;
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(26, 115, 232, 0.5), transparent);
            margin: 100px 0;
        }

        @media (max-width: 768px) {
            .name {
                font-size: 56px;
            }

            .specs-grid,
            .education-timeline {
                grid-template-columns: 1fr;
            }

            .performance-card,
            .showcase {
                padding: 50px 30px;
            }

            .showcase-name {
                font-size: 52px;
            }

            .contact-email {
                font-size: 28px;
            }
        }

        .fade-in {
            animation: fadeInUp 1s ease-out forwards;
            opacity: 0;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .fade-in {
            transform: translateY(30px);
        }

        .delay-1 { animation-delay: 0.2s; }
        .delay-2 { animation-delay: 0.4s; }
        .delay-3 { animation-delay: 0.6s; }
        .delay-4 { animation-delay: 0.8s; }
    </style>
</head>
<body>
    <div id="three-container"></div>
    
    <div class="speed-lines">
        <div class="speed-line" style="top: 20%; animation-delay: 0s;"></div>
        <div class="speed-line" style="top: 40%; animation-delay: 0.3s;"></div>
        <div class="speed-line" style="top: 60%; animation-delay: 0.6s;"></div>
        <div class="speed-line" style="top: 80%; animation-delay: 0.9s;"></div>
    </div>

    <div class="container">
        <div class="hero">
            <div class="hero-badge">M PERFORMANCE</div>
            <h1 class="name">FATHIMATH<br>SHEBA C</h1>
            <p class="title">Frontend Developer</p>
            <p class="tagline">
                Engineering precision meets creative excellence. Building high-performance 
                applications with the attention to detail of German craftsmanship.
            </p>
        </div>

        <div class="divider"></div>

        <div class="performance-card carbon-fiber fade-in delay-1">
            <div class="section-label">Performance Overview</div>
            <div class="section-content">
                BCA graduate pursuing MCA in Data Analysis. I architect solutions with the precision 
                of a finely-tuned engine—every line of code optimized for performance and scalability.
                <br><br>
                Full-stack capabilities with frontend specialization. From initial concept to final 
                deployment, I deliver experiences that perform flawlessly under pressure.
                <br><br>
                Currently mastering React while continuously refining my craft. Always learning. 
                Always evolving. Always pushing the limits.
            </div>
        </div>

        <div class="performance-card carbon-fiber fade-in delay-2">
            <div class="section-label">Technical Specifications</div>
            <div class="specs-grid">
                <div class="spec-box">
                    <div class="spec-label">Frontend</div>
                    <div class="spec-value">HTML<br>CSS<br>JavaScript</div>
                </div>
                <div class="spec-box">
                    <div class="spec-label">Backend</div>
                    <div class="spec-value">Python<br>Django<br>MySQL</div>
                </div>
                <div class="spec-box">
                    <div class="spec-label">In Development</div>
                    <div class="spec-value">React</div>
                </div>
            </div>
        </div>

        <div class="performance-card carbon-fiber fade-in delay-3">
            <div class="section-label">Credentials</div>
            <div class="education-timeline">
                <div class="timeline-item">
                    <div class="timeline-degree">
                        Master of Computer Applications<br>
                        <span style="font-size: 16px; color: #1a73e8;">Data Analysis Specialization</span>
                    </div>
                    <div class="timeline-details">
                        Jain University, Bangalore<br>
                        Present
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-degree">
                        Bachelor of Computer Applications
                    </div>
                    <div class="timeline-details">
                        Kannur University, Kerala<br>
                        2022 - 2025<br>
                        CGPA: 7.4
                    </div>
                </div>
            </div>
        </div>

        <div class="showcase fade-in delay-4">
            <div class="showcase-label">Featured Build</div>
            <div class="showcase-name">EON</div>
            <div class="showcase-description">
                A full-stack hub for book trading, study collaborations, and blog-style thoughtwaves. 
                Features user-driven MCQs that auto-generate quizzes, robust content moderation via 
                admin panel, and an integrated chatbot for seamless user interaction. Built with 
                precision, optimized for performance, designed for scale.
            </div>
        </div>

        <div class="divider"></div>

        <div class="contact-section">
            <div class="contact-title">Let's Connect</div>
            <a href="mailto:shebacee.dev@gmail.com" class="contact-email">
                shebacee.dev@gmail.com
            </a>
            <p class="footer-text">
                trying to be better everyday. love to build stuff.
            </p>
        </div>
    </div>

    <script>
        // Three.js 3D Scene - BMW-inspired geometric elements
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
        
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.getElementById('three-container').appendChild(renderer.domElement);

        // Create BMW-inspired hexagonal grid
        const hexagons = [];
        const hexCount = 20;

        for (let i = 0; i < hexCount; i++) {
            const geometry = new THREE.CylinderGeometry(0.5, 0.5, 0.1, 6);
            const material = new THREE.MeshBasicMaterial({
                color: 0x1a73e8,
                wireframe: true,
                transparent: true,
                opacity: 0.2
            });
            const hex = new THREE.Mesh(geometry, material);
            
            // Arrange in a grid-like pattern
            const angle = (i / hexCount) * Math.PI * 2;
            const radius = 10 + Math.random() * 5;
            hex.position.x = Math.cos(angle) * radius;
            hex.position.y = (Math.random() - 0.5) * 10;
            hex.position.z = Math.sin(angle) * radius;
            
            hex.rotation.x = Math.PI / 2;
            
            hex.rotationSpeed = (Math.random() - 0.5) * 0.01;
            hex.floatSpeed = (Math.random() - 0.5) * 0.02;
            
            hexagons.push(hex);
            scene.add(hex);
        }

        // Add center piece - larger hexagon
        const centerGeometry = new THREE.CylinderGeometry(2, 2, 0.2, 6);
        const centerMaterial = new THREE.MeshBasicMaterial({
            color: 0x1a73e8,
            wireframe: true,
            transparent: true,
            opacity: 0.3
        });
        const centerHex = new THREE.Mesh(centerGeometry, centerMaterial);
        centerHex.rotation.x = Math.PI / 2;
        scene.add(centerHex);

        camera.position.z = 20;

        // Animation
        function animate() {
            requestAnimationFrame(animate);

            hexagons.forEach((hex, index) => {
                hex.rotation.z += hex.rotationSpeed;
                hex.position.y += Math.sin(Date.now() * 0.001 + index) * hex.floatSpeed;
            });

            centerHex.rotation.z += 0.005;

            renderer.render(scene, camera);
        }

        animate();

        // Handle resize
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        // Mouse parallax
        document.addEventListener('mousemove', (e) => {
            const mouseX = (e.clientX / window.innerWidth) * 2 - 1;
            const mouseY = -(e.clientY / window.innerHeight) * 2 + 1;
            
            camera.position.x += (mouseX * 3 - camera.position.x) * 0.05;
            camera.position.y += (mouseY * 3 - camera.position.y) * 0.05;
        });

        // Scroll parallax
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            centerHex.rotation.z = scrolled * 0.001;
        });
    </script>
</body>
</html>
