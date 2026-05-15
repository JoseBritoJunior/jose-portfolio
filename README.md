<!DOCTYPE html>
<html lang="pt-br" class="scroll-smooth">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jose Brito | Desenvolvedor Web & Designer</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <!-- Three.js para o fundo 3D -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;700;800&display=swap');

        :root {
            --primary: #3b82f6;
            --secondary: #a855f7;
            --bg-dark: #030508;
        }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: var(--bg-dark);
            color: #ffffff;
            overflow-x: hidden;
        }

        /* Fundo 3D Canvas */
        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* Efeito Glassmorphism Premium */
        .glass-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
        }

        .glass-card:hover {
            background: rgba(255, 255, 255, 0.07);
            border-color: var(--primary);
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(59, 130, 246, 0.15);
        }

        /* Animação Flutuante */
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(1deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }

        .animate-float {
            animation: float 6s ease-in-out infinite;
        }

        .text-gradient {
            background: linear-gradient(135deg, #60a5fa 0%, #c084fc 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Glow Effects */
        .glow-blue {
            position: absolute;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(59, 130, 246, 0.2) 0%, transparent 70%);
            border-radius: 50%;
            filter: blur(50px);
            z-index: -1;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #05070a; }
        ::-webkit-scrollbar-thumb { background: #1e293b; border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: #3b82f6; }

        .nav-link {
            transition: all 0.3s;
            opacity: 0.7;
        }
        .nav-link:hover {
            opacity: 1;
            text-shadow: 0 0 10px rgba(59, 130, 246, 0.5);
        }

        /* Ponto verde pulsante */
        .pulse-green {
            box-shadow: 0 0 0 0 rgba(34, 197, 94, 0.7);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(34, 197, 94, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 10px rgba(34, 197, 94, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(34, 197, 94, 0); }
        }
    </style>
</head>

<body>
    <!-- Container para o fundo 3D -->
    <div id="canvas-container"></div>

    <!-- Cabeçalho -->
    <header class="fixed w-full z-50 transition-all duration-300" id="main-header">
        <nav class="container mx-auto px-6 py-5 flex justify-between items-center">
            <div class="text-2xl font-black tracking-tighter flex items-center gap-1 group cursor-pointer">
                <span class="text-white">JOSE</span>
                <span class="text-blue-500 group-hover:text-purple-500 transition-colors">BRITO</span>
            </div>

            <div class="hidden md:flex items-center space-x-10">
                <a href="#inicio" class="nav-link font-medium">Início</a>
                <a href="#servicos" class="nav-link font-medium">Serviços</a>
                <a href="#portfolio" class="nav-link font-medium">Portfólio</a>
                <a href="#sobre" class="nav-link font-medium">Sobre</a>
                <a href="#contato" class="bg-white/5 hover:bg-white/10 px-6 py-2 rounded-full border border-white/10 transition-all font-semibold">Contato</a>
            </div>

            <button class="md:hidden text-2xl" onclick="document.getElementById('mobile-menu').classList.toggle('hidden')">
                <i class="fa-solid fa-bars-staggered"></i>
            </button>
        </nav>
        <!-- Menu Mobile Simples -->
        <div id="mobile-menu" class="hidden md:hidden bg-black/95 absolute w-full p-6 border-b border-white/5 flex flex-col gap-4 text-center">
            <a href="#inicio" class="py-2" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Início</a>
            <a href="#servicos" class="py-2" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Serviços</a>
            <a href="#portfolio" class="py-2" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Portfólio</a>
            <a href="#sobre" class="py-2" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Sobre</a>
            <a href="#contato" class="py-2" onclick="document.getElementById('mobile-menu').classList.add('hidden')">Contato</a>
        </div>
    </header>

    <!-- Secção Hero -->
    <section id="inicio" class="min-h-screen pt-40 pb-20 px-6 flex items-center relative overflow-hidden">
        <div class="glow-blue top-20 -left-20"></div>
        <div class="container mx-auto grid md:grid-cols-2 gap-16 items-center">
            <div class="text-center md:text-left">
                <!-- Badges conforme a imagem solicitada -->
                <div class="flex flex-wrap items-center justify-center md:justify-start gap-3 mb-8">
                    <span class="bg-blue-500/10 text-blue-400 px-4 py-1.5 rounded-full text-[10px] md:text-xs font-bold tracking-widest uppercase border border-blue-500/20">
                        Desenvolvedor de Sites Profissionais
                    </span>
                    <div class="flex items-center gap-2 bg-green-500/10 text-green-500 px-4 py-1.5 rounded-full text-[10px] md:text-xs font-bold border border-green-500/20 uppercase tracking-widest">
                        <span class="w-2 h-2 bg-green-500 rounded-full pulse-green"></span>
                        Disponível para novos projetos
                    </div>
                </div>
                
                <h1 class="text-5xl md:text-7xl lg:text-8xl font-extrabold leading-[1.1] mb-8">
                    Tenha um site que <br>
                    <span class="text-gradient">vende por si.</span>
                </h1>
                
                <p class="text-gray-400 text-lg md:text-xl mb-12 max-w-xl leading-relaxed">
                    Ajudo empresas e profissionais liberais a conquistarem autoridade e venderem mais através de sites de alta conversão.
                </p>
                
                <div class="flex flex-col sm:flex-row gap-5 justify-center md:justify-start">
                    <a href="#portfolio" class="bg-blue-600 hover:bg-blue-500 text-white shadow-[0_0_20px_rgba(59,130,246,0.4)] px-10 py-5 rounded-2xl font-bold transition-all flex items-center justify-center gap-3 group">
                        Ver Portfólio 
                        <i class="fa-solid fa-arrow-right group-hover:translate-x-2 transition-transform"></i>
                    </a>
                    <a href="#servicos" class="glass-card px-10 py-5 rounded-2xl font-bold flex items-center justify-center gap-2 hover:bg-white/10">
                        Meus Serviços
                    </a>
                </div>
            </div>

            <div class="relative flex justify-center items-center h-full">
                <!-- Logotipo de Código Flutuante -->
                <div class="animate-float relative z-10 w-full max-w-md">
                    <div class="glass-card rounded-3xl overflow-hidden shadow-2xl">
                        <div class="bg-white/10 px-6 py-4 flex gap-2 border-b border-white/5">
                            <div class="w-3 h-3 rounded-full bg-red-500/50"></div>
                            <div class="w-3 h-3 rounded-full bg-yellow-500/50"></div>
                            <div class="w-3 h-3 rounded-full bg-green-500/50"></div>
                        </div>
                        <div class="p-10 font-mono text-sm leading-loose">
                            <div class="flex gap-4 mb-4">
                                <span class="text-purple-400">const</span>
                                <span class="text-blue-400">developer</span>
                                <span class="text-white">=</span>
                                <span class="text-white">{</span>
                            </div>
                            <div class="pl-8 mb-2">
                                <span class="text-gray-400">nome:</span>
                                <span class="text-green-400">'Jose Brito'</span>,
                            </div>
                            <div class="pl-8 mb-2">
                                <span class="text-gray-400">foco:</span>
                                <span class="text-green-400">'Alta Performance'</span>,
                            </div>
                            <div class="pl-8 mb-2">
                                <span class="text-gray-400">status:</span>
                                <span class="text-orange-400">'Coding...'</span>
                            </div>
                            <div class="text-white">};</div>
                            <div class="mt-8 text-blue-500/50 italic">// Transformando ideias</div>
                            <div class="text-blue-500/50 italic">// em realidade digital.</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Secção de Serviços -->
    <section id="servicos" class="py-32 relative z-10">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-bold mb-4">O que eu <span class="text-blue-500">ofereço</span></h2>
                <p class="text-gray-400">Soluções completas do design ao código de alto nível.</p>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <div class="glass-card p-10 rounded-3xl group">
                    <div class="w-16 h-16 bg-blue-600/20 rounded-2xl flex items-center justify-center mb-8 text-blue-500 text-3xl group-hover:bg-blue-600 group-hover:text-white transition-all">
                        <i class="fa-solid fa-bolt"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Sites Ultra Rápidos</h3>
                    <p class="text-gray-400 leading-relaxed">Desenvolvimento focado em performance extrema para que o seu site carregue instantaneamente e converta mais.</p>
                </div>
                <div class="glass-card p-10 rounded-3xl group">
                    <div class="w-16 h-16 bg-purple-600/20 rounded-2xl flex items-center justify-center mb-8 text-purple-500 text-3xl group-hover:bg-purple-600 group-hover:text-white transition-all">
                        <i class="fa-solid fa-pen-nib"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Web Designer</h3>
                    <p class="text-gray-400 leading-relaxed">Criação de interfaces modernas (UI) e experiências intuitivas (UX) que transmitem confiança e autoridade.</p>
                </div>
                <div class="glass-card p-10 rounded-3xl group">
                    <div class="w-16 h-16 bg-green-600/20 rounded-2xl flex items-center justify-center mb-8 text-green-500 text-3xl group-hover:bg-green-600 group-hover:text-white transition-all">
                        <i class="fa-solid fa-magnifying-glass-chart"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Otimização SEO</h3>
                    <p class="text-gray-400 leading-relaxed">Estratégias para que a sua marca seja encontrada no Google e ganhe destaque perante a concorrência.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Secção de Portfólio -->
    <section id="portfolio" class="py-32 relative overflow-hidden">
        <div class="container mx-auto px-6">
            <div class="max-w-2xl mb-20">
                <h2 class="text-5xl font-extrabold mb-6">Portfólio de <span class="text-gradient">Sucesso.</span></h2>
                <p class="text-gray-400 text-lg">Conheça alguns dos projetos que desenvolvi e como ajudei estas marcas a destacarem-se no digital.</p>
            </div>

            <div class="grid md:grid-cols-2 gap-12">
                <!-- Projeto 1 -->
                <div class="group relative">
                    <div class="glass-card rounded-[2.5rem] overflow-hidden">
                        <div class="h-[400px] bg-[#0d1117] relative flex items-center justify-center overflow-hidden">
                            <div class="absolute inset-0 bg-gradient-to-t from-[#030508] via-transparent to-transparent z-10"></div>
                            <div class="relative z-20 text-center transform group-hover:scale-110 transition-transform duration-700">
                                <h4 class="text-5xl font-black italic tracking-tighter opacity-20">RUSSO IMPORTS</h4>
                                <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-blue-500/20 blur-[80px] rounded-full"></div>
                            </div>
                        </div>
                        <div class="p-10 relative z-20">
                            <div class="flex justify-between items-start mb-6">
                                <div>
                                    <span class="text-blue-400 text-xs font-bold uppercase tracking-widest mb-2 block">E-commerce Elite</span>
                                    <h3 class="text-3xl font-bold">Russo Imports</h3>
                                </div>
                                <a href="https://russoimports.com.br" target="_blank" class="w-14 h-14 bg-white/5 rounded-2xl flex items-center justify-center hover:bg-blue-600 transition-all">
                                    <i class="fa-solid fa-arrow-up-right-from-square"></i>
                                </a>
                            </div>
                            <p class="text-gray-400 leading-relaxed mb-8">Plataforma otimizada para venda de eletrónicos e acessórios de luxo com foco em velocidade e UX.</p>
                            <div class="flex gap-3">
                                <span class="px-4 py-2 bg-white/5 rounded-xl text-xs font-medium border border-white/5">HTML/CSS</span>
                                <span class="px-4 py-2 bg-white/5 rounded-xl text-xs font-medium border border-white/5">JavaScript</span>
                                <span class="px-4 py-2 bg-white/5 rounded-xl text-xs font-medium border border-white/5">Tailwind</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Projeto 2 -->
                <div class="group relative">
                    <div class="glass-card rounded-[2.5rem] overflow-hidden">
                        <div class="h-[400px] bg-[#0d1117] relative flex items-center justify-center overflow-hidden">
                            <div class="absolute inset-0 bg-gradient-to-t from-[#030508] via-transparent to-transparent z-10"></div>
                            <div class="relative z-20 text-center transform group-hover:scale-110 transition-transform duration-700">
                                <h4 class="text-5xl font-black italic tracking-tighter opacity-20 text-purple-500">RPM AUTO TECH</h4>
                                <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-purple-500/20 blur-[80px] rounded-full"></div>
                            </div>
                        </div>
                        <div class="p-10 relative z-20">
                            <div class="flex justify-between items-start mb-6">
                                <div>
                                    <span class="text-purple-400 text-xs font-bold uppercase tracking-widest mb-2 block">Institucional</span>
                                    <h3 class="text-3xl font-bold">RPM Auto Tech</h3>
                                </div>
                                <a href="https://rpmautotech.com.br" target="_blank" class="w-14 h-14 bg-white/5 rounded-2xl flex items-center justify-center hover:bg-purple-600 transition-all">
                                    <i class="fa-solid fa-arrow-up-right-from-square"></i>
                                </a>
                            </div>
                            <p class="text-gray-400 leading-relaxed mb-8">Website para oficina especializada, focado em agendamentos e apresentação profissional de serviços.</p>
                            <div class="flex gap-3">
                                <span class="px-4 py-2 bg-white/5 rounded-xl text-xs font-medium border border-white/5">Web Design</span>
                                <span class="px-4 py-2 bg-white/5 rounded-xl text-xs font-medium border border-white/5">SEO</span>
                                <span class="px-4 py-2 bg-white/5 rounded-xl text-xs font-medium border border-white/5">React</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Secção Sobre -->
    <section id="sobre" class="py-32 relative z-10">
        <div class="container mx-auto px-6">
            <div class="glass-card p-12 md:p-16 rounded-[3rem] flex flex-col md:flex-row items-center gap-16">
                <div class="w-64 h-64 relative flex-shrink-0">
                    <div class="absolute inset-0 bg-blue-600/20 blur-3xl rounded-full"></div>
                    <div class="glass-card w-full h-full rounded-3xl flex items-center justify-center text-7xl font-black text-blue-500">
                        JB
                    </div>
                </div>
                <div>
                    <h2 class="text-4xl font-bold mb-6">Sobre <span class="text-blue-500">mim</span></h2>
                    <p class="text-gray-400 text-xl leading-relaxed mb-8">
                        Sou especialista em transformar visões de negócio em experiências digitais de alto impacto. Com foco em performance e design moderno, o meu objetivo é criar ferramentas que não apenas existam na internet, mas que tragam resultados reais e autoridade para os meus clientes.
                    </p>
                    <div class="flex flex-wrap gap-8">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-code text-blue-500 text-xl"></i>
                            <span class="font-bold">Código Limpo</span>
                        </div>
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-gauge-high text-blue-500 text-xl"></i>
                            <span class="font-bold">Alta Performance</span>
                        </div>
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-mobile-screen text-blue-500 text-xl"></i>
                            <span class="font-bold">100% Responsivo</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Secção Contato -->
    <section id="contato" class="py-32 px-6 relative">
        <div class="container mx-auto">
            <div class="glass-card rounded-[3rem] p-16 md:p-24 text-center relative overflow-hidden">
                <div class="absolute inset-0 bg-gradient-to-br from-blue-600/10 to-purple-600/10 -z-10"></div>
                <div class="relative z-10 max-w-4xl mx-auto">
                    <h2 class="text-4xl md:text-6xl font-extrabold mb-8">Vamos criar o <br><span class="text-gradient">extraordinário?</span></h2>
                    
                    <div class="grid md:grid-cols-3 gap-8 my-16">
                        <a href="mailto:josebritojr0@gmail.com" class="glass-card p-8 rounded-3xl hover:border-blue-500 transition-all group">
                            <i class="fa-regular fa-envelope text-3xl text-blue-500 mb-4 block group-hover:scale-110 transition"></i>
                            <p class="font-bold mb-1">E-mail</p>
                            <p class="text-sm text-gray-500">josebritojr0@gmail.com</p>
                        </a>
                        <a href="https://wa.me/5575988349896" target="_blank" class="glass-card p-8 rounded-3xl hover:border-green-500 transition-all group">
                            <i class="fa-brands fa-whatsapp text-3xl text-green-500 mb-4 block group-hover:scale-110 transition"></i>
                            <p class="font-bold mb-1">WhatsApp</p>
                            <p class="text-sm text-gray-500">(75) 98834-9896</p>
                        </a>
                        <a href="https://www.instagram.com/josebrito.dev/" target="_blank" class="glass-card p-8 rounded-3xl hover:border-pink-500 transition-all group">
                            <i class="fa-brands fa-instagram text-3xl text-pink-500 mb-4 block group-hover:scale-110 transition"></i>
                            <p class="font-bold mb-1">Instagram</p>
                            <p class="text-sm text-gray-500">@josebrito.dev</p>
                        </a>
                    </div>

                    <a href="https://wa.me/5575988349896" target="_blank" class="bg-white text-black hover:bg-blue-500 hover:text-white px-12 py-6 rounded-2xl font-black text-lg transition-all inline-block shadow-2xl">
                        SOLICITAR ORÇAMENTO AGORA
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Rodapé -->
    <footer class="py-20 border-t border-white/5 relative z-10">
        <div class="container mx-auto px-6 text-center">
            <div class="text-3xl font-black mb-4">JOSE <span class="text-blue-500">BRITO</span></div>
            <p class="text-gray-500 text-sm mb-8">Design & Code de Alto Nível © 2026. Todos os direitos reservados.</p>
            <div class="flex justify-center gap-6 text-gray-400">
                <a href="https://www.instagram.com/josebrito.dev/" target="_blank" class="hover:text-blue-400 transition"><i class="fa-brands fa-instagram text-2xl"></i></a>
                <a href="https://wa.me/5575988349896" target="_blank" class="hover:text-green-500 transition"><i class="fa-brands fa-whatsapp text-2xl"></i></a>
                <a href="mailto:josebritojr0@gmail.com" class="hover:text-white transition"><i class="fa-regular fa-envelope text-2xl"></i></a>
            </div>
        </div>
    </footer>

    <script>
        // --- THREE.JS BACKGROUND 3D ---
        const container = document.getElementById('canvas-container');
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });

        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
        container.appendChild(renderer.domElement);

        const particlesGeometry = new THREE.BufferGeometry();
        const particlesCount = 1500;
        const posArray = new Float32Array(particlesCount * 3);

        for (let i = 0; i < particlesCount * 3; i++) {
            posArray[i] = (Math.random() - 0.5) * 10;
        }

        particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));

        const material = new THREE.PointsMaterial({
            size: 0.005,
            color: '#3b82f6',
            transparent: true,
            opacity: 0.4,
            blending: THREE.AdditiveBlending
        });

        const particlesMesh = new THREE.Points(particlesGeometry, material);
        scene.add(particlesMesh);

        camera.position.z = 3;

        let mouseX = 0;
        let mouseY = 0;

        document.addEventListener('mousemove', (event) => {
            mouseX = event.clientX;
            mouseY = event.clientY;
        });

        function animate() {
            requestAnimationFrame(animate);
            particlesMesh.rotation.y += 0.0008;
            particlesMesh.rotation.x += 0.0004;

            const targetX = (mouseX - window.innerWidth / 2) * 0.0002;
            const targetY = (mouseY - window.innerHeight / 2) * 0.0002;
            
            particlesMesh.rotation.y += targetX;
            particlesMesh.rotation.x += targetY;

            renderer.render(scene, camera);
        }

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        window.onload = animate;

        // Header Scroll Effect
        window.addEventListener('scroll', () => {
            const header = document.getElementById('main-header');
            if (window.scrollY > 50) {
                header.classList.add('bg-[#030508]/90', 'backdrop-blur-xl', 'py-4', 'border-b', 'border-white/5');
                header.classList.remove('py-5');
            } else {
                header.classList.remove('bg-[#030508]/90', 'backdrop-blur-xl', 'py-4', 'border-b', 'border-white/5');
                header.classList.add('py-5');
            }
        });
    </script>
</body>

</html>
