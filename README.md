# goncellen.github.io
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Cuidado e Proteção em Toda Vida • Cartilha Digital UERGS</title>
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- Google Fonts: Plus Jakarta Sans & Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">

  <!-- Tailwind Configuration -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            display: ['Plus Jakarta Sans', 'sans-serif'],
          },
          colors: {
            cream: '#FAF7F2',
            sand: '#F2ECE1',
            terracotta: {
              50: '#FDF4F2',
              100: '#FCE6E1',
              500: '#E06D53',
              600: '#C8563D',
            },
            sage: {
              50: '#F1F8F5',
              100: '#DCEFE7',
              500: '#2E8B6E',
              600: '#226E56',
              700: '#195442',
            },
            petrol: {
              700: '#1D4E5F',
              800: '#143A47',
              900: '#0D2832',
            }
          }
        }
      }
    }
  </script>

  <style>
    body {
      background-color: #FAF7F2;
      color: #0D2832;
      overflow-x: hidden;
    }

    /* Animações Suaves */
    @keyframes floatSlow {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-8px); }
    }

    @keyframes pulseSoft {
      0%, 100% { transform: scale(1); opacity: 0.9; }
      50% { transform: scale(1.06); opacity: 1; }
    }

    @keyframes fadeSlideUp {
      from {
        opacity: 0;
        transform: translateY(18px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .animate-float {
      animation: floatSlow 4.5s ease-in-out infinite;
    }

    .animate-float-delayed {
      animation: floatSlow 5.2s ease-in-out 1.2s infinite;
    }

    .animate-pulse-soft {
      animation: pulseSoft 3s ease-in-out infinite;
    }

    .page-enter {
      animation: fadeSlideUp 0.45s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    /* Flip Card 3D para Mitos e Verdades */
    .perspective-1000 {
      perspective: 1000px;
    }

    .flip-card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      transition: transform 0.65s cubic-bezier(0.4, 0.2, 0.2, 1);
      transform-style: preserve-3d;
    }

    .flip-card.flipped .flip-card-inner {
      transform: rotateY(180deg);
    }

    .flip-card-front,
    .flip-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      -webkit-backface-visibility: hidden;
      backface-visibility: hidden;
      border-radius: 1.25rem;
    }

    .flip-card-back {
      transform: rotateY(180deg);
    }

    /* Custom Scrollbar */
    ::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #FAF7F2;
    }
    ::-webkit-scrollbar-thumb {
      background: #D6CEC0;
      border-radius: 999px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #B8AE9E;
    }
  </style>
</head>
<body class="min-h-screen flex flex-col justify-between selection:bg-terracotta-100 selection:text-petrol-900">

  <!-- Barra Superior Fixa (Navegação e Modo de Leitura) -->
  <header class="sticky top-0 z-40 bg-cream/90 backdrop-blur-md border-b border-sand transition-all">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 py-3 flex items-center justify-between gap-3">
      <!-- Logo / Título Compacto -->
      <button onclick="goToSection(0)" class="flex items-center gap-2.5 text-left group focus:outline-none">
        <div class="w-9 h-9 rounded-xl bg-gradient-to-br from-terracotta-500 to-sage-500 flex items-center justify-center text-white shadow-sm group-hover:scale-105 transition-transform">
          <!-- Ícone Coração + Escudo -->
          <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
          </svg>
        </div>
        <div>
          <span class="font-display font-bold text-sm sm:text-base text-petrol-900 block leading-tight">Cuidado & Proteção</span>
          <span class="text-[11px] font-medium text-sage-600 uppercase tracking-wider">Cartilha UERGS</span>
        </div>
      </button>

      <!-- Controles de Modo e Menu -->
      <div class="flex items-center gap-2">
        <!-- Toggle Modo Paginado vs Contínuo -->
        <button id="viewModeBtn" onclick="toggleViewMode()" class="px-3 py-1.5 rounded-full text-xs font-semibold bg-sand hover:bg-terracotta-100 text-petrol-800 transition-colors flex items-center gap-1.5 shadow-sm" title="Alternar modo de visualização">
          <svg id="viewModeIcon" class="w-4 h-4 text-terracotta-600" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16"/>
          </svg>
          <span id="viewModeText" class="hidden sm:inline">Ver Tudo</span>
        </button>

        <!-- Botão Sumário / Capítulos -->
        <button onclick="toggleDrawer()" class="px-3 py-1.5 rounded-full text-xs font-semibold bg-petrol-800 hover:bg-petrol-900 text-white transition-colors flex items-center gap-1.5 shadow-sm">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/>
          </svg>
          <span>Capítulos</span>
        </button>
      </div>
    </div>

    <!-- Barra de Progresso -->
    <div id="progressWrapper" class="w-full h-1.5 bg-sand">
      <div id="progressBar" class="h-full bg-gradient-to-r from-terracotta-500 via-sage-500 to-petrol-700 transition-all duration-500" style="width: 12.5%;"></div>
    </div>
  </header>

  <!-- Menu Lateral (Drawer de Capítulos) -->
  <div id="chapterDrawer" class="fixed inset-0 z-50 hidden">
    <div onclick="toggleDrawer()" class="absolute inset-0 bg-petrol-900/40 backdrop-blur-xs transition-opacity"></div>
    <div class="absolute right-0 top-0 bottom-0 w-80 max-w-[85vw] bg-cream shadow-2xl p-6 flex flex-col justify-between overflow-y-auto">
      <div>
        <div class="flex items-center justify-between pb-4 border-b border-sand">
          <h3 class="font-display font-bold text-lg text-petrol-900">Sumário da Cartilha</h3>
          <button onclick="toggleDrawer()" class="p-2 rounded-full hover:bg-sand text-petrol-800">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12"/>
            </svg>
          </button>
        </div>

        <nav class="mt-4 space-y-2" id="drawerNavList">
          <!-- Preenchido via JS -->
        </nav>
      </div>

      <div class="pt-6 border-t border-sand text-xs text-petrol-700">
        <p class="font-semibold">Projeto de Educação em Saúde</p>
        <p class="opacity-80 mt-0.5">UERGS • Porto Alegre, 2026</p>
      </div>
    </div>
  </div>

  <!-- Container Principal da Cartilha -->
  <main id="cartilhaContainer" class="flex-1 max-w-5xl w-full mx-auto px-4 sm:px-6 py-6 sm:py-10 space-y-12">

    <!-- ===================================================================== -->
    <!-- SEÇÃO 0: CAPA / INTRODUÇÃO                                            -->
    <!-- ===================================================================== -->
    <section data-step="0" class="cartilha-section page-enter bg-white rounded-3xl p-6 sm:p-10 md:p-12 shadow-sm border border-sand relative overflow-hidden">
      <!-- Elementos decorativos de fundo -->
      <div class="absolute -top-20 -right-20 w-72 h-72 rounded-full bg-terracotta-50 opacity-80 pointer-events-none"></div>
      <div class="absolute -bottom-24 -left-16 w-64 h-64 rounded-full bg-sage-50 opacity-80 pointer-events-none"></div>

      <div class="relative z-10 grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
        <!-- Texto da Capa -->
        <div class="lg:col-span-7 space-y-5 text-center lg:text-left">
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-sage-100 text-sage-700 text-xs font-bold tracking-wide uppercase">
            <span class="w-2 h-2 rounded-full bg-sage-500 animate-ping"></span>
            Educação em Saúde • UERGS
          </div>

          <h1 class="font-display font-extrabold text-3xl sm:text-4xl md:text-5xl text-petrol-900 leading-[1.15]">
            Cuidado e Proteção em <span class="text-terracotta-500">Toda Vida</span>
          </h1>

          <p class="text-base sm:text-lg text-petrol-700 font-medium leading-relaxed">
            Sexualidade, respeito e prevenção em todas as idades. Uma conversa acolhedora que aproxima gerações e protege vidas.
          </p>

          <div class="pt-2 flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-3">
            <button onclick="nextStep()" class="w-full sm:w-auto px-7 py-3.5 rounded-2xl bg-terracotta-500 hover:bg-terracotta-600 text-white font-display font-bold text-base shadow-md hover:shadow-lg transition-all flex items-center justify-center gap-2 group">
              <span>Começar Leitura</span>
              <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
              </svg>
            </button>
            <button onclick="goToSection(3)" class="w-full sm:w-auto px-5 py-3.5 rounded-2xl bg-sand/80 hover:bg-sand text-petrol-800 font-semibold text-sm transition-colors">
              Quiz: Mitos e Verdades
            </button>
          </div>
        </div>

        <!-- Ilustração SVG Vetorial: Gerações Conectadas com Afeto -->
        <div class="lg:col-span-5 flex justify-center">
          <div class="w-full max-w-xs sm:max-w-sm animate-float">
            <svg viewBox="0 0 400 360" fill="none" xmlns="http://www.w3.org/2000/svg" class="w-full h-auto drop-shadow-sm">
              <!-- Círculo de Acolhimento -->
              <circle cx="200" cy="180" r="150" fill="#FDF4F2" />
              <circle cx="200" cy="180" r="122" stroke="#DCEFE7" stroke-width="4" stroke-dasharray="10 8" />
              
              <!-- Laço de Conexão entre Gerações -->
              <path d="M85 210 C130 120, 270 120, 315 210" stroke="#E06D53" stroke-width="6" stroke-linecap="round" opacity="0.35"/>
              <path d="M95 235 C150 285, 250 285, 305 235" stroke="#2E8B6E" stroke-width="6" stroke-linecap="round" opacity="0.35"/>

              <!-- Figura 1: Pessoa Jovem (Esquerda) -->
              <g transform="translate(65, 130)">
                <circle cx="45" cy="42" r="26" fill="#F4A28C"/>
                <!-- Cabelo -->
                <path d="M20 38 C20 15, 70 15, 70 38 C70 25, 20 25, 20 38 Z" fill="#143A47"/>
                <circle cx="24" cy="24" r="10" fill="#143A47"/>
                <!-- Corpo -->
                <path d="M12 115 C12 82, 78 82, 78 115 Z" fill="#E06D53"/>
                <!-- Sorriso -->
                <path d="M39 47 Q45 53 51 47" stroke="#143A47" stroke-width="2.5" stroke-linecap="round"/>
              </g>

              <!-- Figura 2: Pessoa Adulta (Centro/Topo) -->
              <g transform="translate(152, 85)">
                <circle cx="48" cy="45" r="29" fill="#D98A73"/>
                <path d="M19 42 C19 14, 77 14, 77 42" fill="#0D2832"/>
                <path d="M10 128 C10 88, 86 88, 86 128 Z" fill="#2E8B6E"/>
                <path d="M41 51 Q48 58 55 51" stroke="#0D2832" stroke-width="2.5" stroke-linecap="round"/>
              </g>

              <!-- Figura 3: Pessoa Idosa (Direita) -->
              <g transform="translate(245, 130)">
                <circle cx="45" cy="42" r="26" fill="#F2B8A2"/>
                <!-- Cabelo Grisaiho / Coque -->
                <circle cx="45" cy="14" r="12" fill="#E2E8F0"/>
                <path d="M19 40 C19 18, 71 18, 71 40" fill="#CBD5E1"/>
                <!-- Óculos -->
                <circle cx="37" cy="41" r="6" stroke="#1D4E5F" stroke-width="2"/>
                <circle cx="53" cy="41" r="6" stroke="#1D4E5F" stroke-width="2"/>
                <line x1="43" y1="41" x2="47" y2="41" stroke="#1D4E5F" stroke-width="2"/>
                <!-- Corpo -->
                <path d="M12 115 C12 82, 78 82, 78 115 Z" fill="#1D4E5F"/>
                <path d="M39 51 Q45 56 51 51" stroke="#143A47" stroke-width="2.2" stroke-linecap="round"/>
              </g>

              <!-- Coração Central Pulsante -->
              <g transform="translate(176, 222)" class="animate-pulse-soft">
                <rect x="0" y="0" width="48" height="48" rx="16" fill="#FFFFFF" stroke="#FCE6E1" stroke-width="2"/>
                <path d="M24 34.5l-1.3-1.2C18 29.1 15 26.3 15 22.9 15 20.1 17.2 18 20 18c1.6 0 3.1.7 4 1.9.9-1.2 2.4-1.9 4-1.9 2.8 0 5 2.1 5 4.9 0 3.4-3 6.2-7.7 10.4L24 34.5z" fill="#E06D53"/>
              </g>
            </svg>
          </div>
        </div>
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 1: SEXUALIDADE NÃO TEM IDADE                                    -->
    <!-- ===================================================================== -->
    <section data-step="1" class="cartilha-section page-enter bg-white rounded-3xl p-6 sm:p-10 shadow-sm border border-sand">
      <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 pb-6 border-b border-sand">
        <div>
          <span class="text-xs font-bold uppercase tracking-wider text-terracotta-600 bg-terracotta-50 px-3 py-1 rounded-full">Capítulo 01</span>
          <h2 class="font-display font-extrabold text-2xl sm:text-3xl text-petrol-900 mt-2">Sexualidade não tem idade</h2>
        </div>
        <p class="text-sm text-petrol-700 max-w-md">
          Falar de sexualidade é falar de saúde, afeto, prazer e escolhas seguras. <strong>A idade não protege ninguém das ISTs.</strong>
        </p>
      </div>

      <!-- Cards por Fase da Vida -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-5 mt-7">
        <!-- Card Jovens -->
        <div class="rounded-2xl bg-terracotta-50/70 border border-terracotta-100 p-6 flex flex-col justify-between hover:-translate-y-1 transition-transform">
          <div>
            <div class="w-12 h-12 rounded-2xl bg-terracotta-500 text-white flex items-center justify-center mb-4 shadow-xs">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13 10V3L4 14h7v7l9-11h-7z"/>
              </svg>
            </div>
            <h3 class="font-display font-bold text-lg text-petrol-900">Juventude</h3>
            <p class="text-sm text-petrol-700 mt-2 leading-relaxed">
              Precisa de informação confiável, acolhimento sem julgamentos e liberdade para tirar dúvidas com segurança.
            </p>
          </div>
          <div class="mt-4 pt-3 border-t border-terracotta-100 text-xs font-semibold text-terracotta-600">
            ✓ Direito ao sigilo e orientação
          </div>
        </div>

        <!-- Card Adultos -->
        <div class="rounded-2xl bg-sage-50/70 border border-sage-100 p-6 flex flex-col justify-between hover:-translate-y-1 transition-transform">
          <div>
            <div class="w-12 h-12 rounded-2xl bg-sage-500 text-white flex items-center justify-center mb-4 shadow-xs">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/>
              </svg>
            </div>
            <h3 class="font-display font-bold text-lg text-petrol-900">Vida Adulta</h3>
            <p class="text-sm text-petrol-700 mt-2 leading-relaxed">
              O cuidado deve continuar em todas as fases, inclusive em relações estáveis. Prevenção é acordo e responsabilidade mútua.
            </p>
          </div>
          <div class="mt-4 pt-3 border-t border-sage-100 text-xs font-semibold text-sage-600">
            ✓ Testagem e diálogo no casal
          </div>
        </div>

        <!-- Card Idosos -->
        <div class="rounded-2xl bg-sand/70 border border-sand p-6 flex flex-col justify-between hover:-translate-y-1 transition-transform">
          <div>
            <div class="w-12 h-12 rounded-2xl bg-petrol-700 text-white flex items-center justify-center mb-4 shadow-xs">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/>
              </svg>
            </div>
            <h3 class="font-display font-bold text-lg text-petrol-900">Pessoa Idosa</h3>
            <p class="text-sm text-petrol-700 mt-2 leading-relaxed">
              Tem pleno direito ao desejo, à intimidade, à autonomia e ao atendimento em saúde sem deboche ou preconceito.
            </p>
          </div>
          <div class="mt-4 pt-3 border-t border-sand text-xs font-semibold text-petrol-800">
            ✓ Prazer e proteção sem preconceito
          </div>
        </div>
      </div>

      <!-- Destaque Final -->
      <div class="mt-6 p-4 rounded-2xl bg-petrol-900 text-white flex items-center gap-3.5">
        <div class="w-10 h-10 rounded-xl bg-white/10 flex items-center justify-center shrink-0 text-terracotta-500">
          <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 20 20">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z" clip-rule="evenodd"/>
          </svg>
        </div>
        <p class="text-xs sm:text-sm leading-relaxed">
          <strong>Lembre-se:</strong> Ninguém deve sentir vergonha por ter vida sexual ativa. Cuidar da saúde sexual é um ato de respeito consigo e com quem você se relaciona.
        </p>
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 2: DIÁLOGO SEM TABU EM FAMÍLIA                                  -->
    <!-- ===================================================================== -->
    <section data-step="2" class="cartilha-section page-enter bg-white rounded-3xl p-6 sm:p-10 shadow-sm border border-sand">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
        <!-- Ilustração SVG Diálogo -->
        <div class="lg:col-span-4 flex flex-col items-center text-center">
          <div class="w-48 h-48 animate-float-delayed">
            <svg viewBox="0 0 220 220" fill="none" xmlns="http://www.w3.org/2000/svg" class="w-full h-full">
              <circle cx="110" cy="110" r="95" fill="#F1F8F5"/>
              <!-- Balão de fala 1 -->
              <rect x="30" y="55" width="95" height="58" rx="18" fill="#E06D53"/>
              <path d="M50 113 L42 128 L66 113 Z" fill="#E06D53"/>
              <line x1="48" y1="77" x2="105" y2="77" stroke="white" stroke-width="4" stroke-linecap="round"/>
              <line x1="48" y1="91" x2="88" y2="91" stroke="white" stroke-width="4" stroke-linecap="round" opacity="0.8"/>

              <!-- Balão de fala 2 -->
              <rect x="92" y="102" width="98" height="60" rx="18" fill="#1D4E5F"/>
              <path d="M168 162 L176 177 L152 162 Z" fill="#1D4E5F"/>
              <!-- Coração dentro do balão -->
              <path d="M141 143l-1.1-1C136.5 138.8 134 136.6 134 133.8c0-2.2 1.8-4 4-4 1.3 0 2.5.6 3.2 1.5.7-.9 1.9-1.5 3.2-1.5 2.2 0 4 1.8 4 4 0 2.8-2.5 5-5.9 8.2l-1.4 1z" fill="#DCEFE7"/>
            </svg>
          </div>
          <span class="text-xs font-bold uppercase tracking-wider text-sage-600 mt-2">Capítulo 02</span>
          <h2 class="font-display font-extrabold text-2xl text-petrol-900 mt-1">Diálogo sem tabu em família</h2>
          <p class="text-xs sm:text-sm text-petrol-700 mt-2">
            Uma boa conversa não começa com sermão, mas com escuta e confiança.
          </p>
        </div>

        <!-- Abas Interativas: O que dizer vs Como escutar -->
        <div class="lg:col-span-8">
          <div class="flex p-1.5 rounded-2xl bg-sand mb-5">
            <button id="tabDizerBtn" onclick="switchDialogTab('dizer')" class="flex-1 py-2.5 px-4 rounded-xl font-display font-bold text-sm transition-all bg-white text-petrol-900 shadow-xs">
              💬 O que dizer
            </button>
            <button id="tabEscutarBtn" onclick="switchDialogTab('escutar')" class="flex-1 py-2.5 px-4 rounded-xl font-display font-bold text-sm transition-all text-petrol-700 hover:text-petrol-900">
              👂 Como escutar
            </button>
          </div>

          <!-- Conteúdo Aba 1: O que dizer -->
          <div id="tabDizerContent" class="space-y-3">
            <p class="text-xs font-semibold uppercase tracking-wider text-terracotta-600 mb-2">Frases práticas de acolhimento:</p>
            <div class="p-4 rounded-2xl bg-terracotta-50/70 border border-terracotta-100 flex items-start gap-3">
              <span class="text-terracotta-500 font-bold text-lg leading-none">“</span>
              <p class="text-sm text-petrol-900 font-medium">Se tiver alguma dúvida sobre prevenção, podemos procurar informação juntos.</p>
            </div>
            <div class="p-4 rounded-2xl bg-terracotta-50/70 border border-terracotta-100 flex items-start gap-3">
              <span class="text-terracotta-500 font-bold text-lg leading-none">“</span>
              <p class="text-sm text-petrol-900 font-medium">Você não precisa ter vergonha de conversar sobre saúde.</p>
            </div>
            <div class="p-4 rounded-2xl bg-terracotta-50/70 border border-terracotta-100 flex items-start gap-3">
              <span class="text-terracotta-500 font-bold text-lg leading-none">“</span>
              <p class="text-sm text-petrol-900 font-medium">Quero ouvir o que você pensa, sem julgar. A prevenção é importante em qualquer idade.</p>
            </div>
          </div>

          <!-- Conteúdo Aba 2: Como escutar -->
          <div id="tabEscutarContent" class="hidden space-y-3">
            <p class="text-xs font-semibold uppercase tracking-wider text-sage-600 mb-2">Atitudes para quem escuta:</p>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
              <div class="p-4 rounded-2xl bg-sage-50 border border-sage-100">
                <span class="font-bold text-sage-700 text-sm block">✓ Sem piadas ou deboche</span>
                <p class="text-xs text-petrol-700 mt-1">Não interrompa nem ridicularize dúvidas de jovens ou pessoas idosas.</p>
              </div>
              <div class="p-4 rounded-2xl bg-sage-50 border border-sage-100">
                <span class="font-bold text-sage-700 text-sm block">✓ Respeite a privacidade</span>
                <p class="text-xs text-petrol-700 mt-1">Respeite o tempo de cada pessoa e evite perguntas invasivas.</p>
              </div>
              <div class="p-4 rounded-2xl bg-sage-50 border border-sage-100">
                <span class="font-bold text-sage-700 text-sm block">✓ Sem ameaças ou broncas</span>
                <p class="text-xs text-petrol-700 mt-1">O medo afasta o diálogo; o acolhimento aproxima.</p>
              </div>
              <div class="p-4 rounded-2xl bg-sage-50 border border-sage-100">
                <span class="font-bold text-sage-700 text-sm block">✓ Busque apoio profissional</span>
                <p class="text-xs text-petrol-700 mt-1">Não sabe responder? Procurem juntos uma equipe de saúde do SUS.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 3: MITOS E VERDADES (FLIP CARDS INTERATIVOS)                    -->
    <!-- ===================================================================== -->
    <section data-step="3" class="cartilha-section page-enter bg-white rounded-3xl p-6 sm:p-10 shadow-sm border border-sand">
      <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-4 pb-6">
        <div>
          <span class="text-xs font-bold uppercase tracking-wider text-petrol-700 bg-sand px-3 py-1 rounded-full">Capítulo 03 • Interativo</span>
          <h2 class="font-display font-extrabold text-2xl sm:text-3xl text-petrol-900 mt-2">Mitos e Verdades</h2>
          <p class="text-sm text-petrol-700 mt-1">Toque ou clique em cada cartão para virar e descobrir a resposta.</p>
        </div>
        <div class="text-xs font-bold text-sage-700 bg-sage-50 px-3.5 py-2 rounded-xl border border-sage-100">
          Cartões revelados: <span id="flippedCounter">0</span> / 5
        </div>
      </div>

      <!-- Grid de 5 Flip Cards -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5" id="mythsGrid">
        <!-- Gerado dinamicamente via JS para código limpo -->
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 4: KIT PREVENÇÃO COMBINADA                                      -->
    <!-- ===================================================================== -->
    <section data-step="4" class="cartilha-section page-enter bg-white rounded-3xl p-6 sm:p-10 shadow-sm border border-sand">
      <div class="max-w-2xl">
        <span class="text-xs font-bold uppercase tracking-wider text-sage-700 bg-sage-50 px-3 py-1 rounded-full">Capítulo 04</span>
        <h2 class="font-display font-extrabold text-2xl sm:text-3xl text-petrol-900 mt-2">Kit Prevenção Combinada</h2>
        <p class="text-sm text-petrol-700 mt-1">
          Diferentes métodos que se complementam. Escolha com a equipe de saúde o que faz mais sentido para sua rotina.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-5 mt-7">
        <!-- Item 1: Preservativos -->
        <div class="p-6 rounded-2xl bg-cream border border-sand flex gap-4 items-start">
          <div class="w-14 h-14 rounded-2xl bg-terracotta-100 text-terracotta-600 flex items-center justify-center shrink-0">
            <!-- SVG Preservativo / Escudo -->
            <svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
            </svg>
          </div>
          <div>
            <div class="flex items-center gap-2 flex-wrap">
              <h3 class="font-display font-bold text-lg text-petrol-900">Preservativo Interno e Externo</h3>
              <span class="text-[11px] font-bold px-2 py-0.5 rounded-md bg-sage-100 text-sage-700">Grátis no SUS</span>
            </div>
            <ul class="text-xs sm:text-sm text-petrol-700 mt-2 space-y-1">
              <li>• Protege contra HIV, outras ISTs e gravidez não planejada.</li>
              <li>• Use do começo ao fim em relações orais, vaginais ou anais.</li>
              <li>• <strong>Atenção:</strong> nunca reutilize e nunca use dois juntos.</li>
            </ul>
          </div>
        </div>

        <!-- Item 2: Gel Lubrificante -->
        <div class="p-6 rounded-2xl bg-cream border border-sand flex gap-4 items-start">
          <div class="w-14 h-14 rounded-2xl bg-petrol-700/10 text-petrol-700 flex items-center justify-center shrink-0">
            <!-- SVG Gota -->
            <svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 2.69l5.66 5.66a8 8 0 11-11.31 0z"/>
            </svg>
          </div>
          <div>
            <h3 class="font-display font-bold text-lg text-petrol-900">Gel Lubrificante</h3>
            <ul class="text-xs sm:text-sm text-petrol-700 mt-2 space-y-1">
              <li>• Reduz o atrito, aumenta o conforto e evita que o preservativo rompa.</li>
              <li>• Use apenas produtos <strong>à base de água ou silicone</strong>.</li>
              <li>• Evite produtos oleosos (danificam o látex).</li>
            </ul>
          </div>
        </div>

        <!-- Item 3: Testagem e Vacinas -->
        <div class="p-6 rounded-2xl bg-cream border border-sand flex gap-4 items-start">
          <div class="w-14 h-14 rounded-2xl bg-sage-100 text-sage-700 flex items-center justify-center shrink-0">
            <!-- SVG Vacina / Teste -->
            <svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
            </svg>
          </div>
          <div>
            <h3 class="font-display font-bold text-lg text-petrol-900">Testagem & Vacinas</h3>
            <ul class="text-xs sm:text-sm text-petrol-700 mt-2 space-y-1">
              <li>• <strong>Testes rápidos:</strong> HIV, sífilis e hepatites B e C na UBS.</li>
              <li>• <strong>Vacinação:</strong> HPV e Hepatite B disponíveis no SUS conforme indicação.</li>
            </ul>
          </div>
        </div>

        <!-- Item 4: PrEP vs PEP -->
        <div class="p-6 rounded-2xl bg-cream border border-sand flex gap-4 items-start">
          <div class="w-14 h-14 rounded-2xl bg-terracotta-500 text-white flex items-center justify-center shrink-0">
            <!-- SVG Comprimido / Relógio -->
            <svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
            </svg>
          </div>
          <div>
            <h3 class="font-display font-bold text-lg text-petrol-900">PrEP e PEP (Prevenção ao HIV)</h3>
            <ul class="text-xs sm:text-sm text-petrol-700 mt-2 space-y-1">
              <li>• <strong>PrEP (Antes):</strong> comprimidos diários/programados antes da exposição (não previne outras ISTs).</li>
              <li>• <strong>PEP (Depois):</strong> urgência em até <strong>72 horas</strong> após relação de risco.</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 5: SINAIS DE ALERTA & EMERGÊNCIA PEP 72H                        -->
    <!-- ===================================================================== -->
    <section data-step="5" class="cartilha-section page-enter space-y-6">
      <!-- Bloco Sinais de Alerta -->
      <div class="bg-white rounded-3xl p-6 sm:p-10 shadow-sm border border-sand">
        <span class="text-xs font-bold uppercase tracking-wider text-terracotta-600 bg-terracotta-50 px-3 py-1 rounded-full">Capítulo 05</span>
        <h2 class="font-display font-extrabold text-2xl sm:text-3xl text-petrol-900 mt-2">Conhecer para Prevenir</h2>
        <p class="text-sm text-petrol-700 mt-1">
          HIV, sífilis, gonorreia, clamídia, herpes, HPV e hepatites virais são exemplos de ISTs. Fique atento(a) a:
        </p>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3.5 mt-6">
          <div class="p-4 rounded-2xl bg-terracotta-50/60 border border-terracotta-100">
            <span class="text-lg">🩹</span>
            <p class="font-bold text-sm text-petrol-900 mt-1">Feridas ou Bolhas</p>
            <p class="text-xs text-petrol-700 mt-0.5">Verrugas ou lesões na região genital, anal ou na boca.</p>
          </div>
          <div class="p-4 rounded-2xl bg-terracotta-50/60 border border-terracotta-100">
            <span class="text-lg">💧</span>
            <p class="font-bold text-sm text-petrol-900 mt-1">Corrimento</p>
            <p class="text-xs text-petrol-700 mt-0.5">Secreção diferente do habitual com ou sem odor.</p>
          </div>
          <div class="p-4 rounded-2xl bg-terracotta-50/60 border border-terracotta-100">
            <span class="text-lg">🔥</span>
            <p class="font-bold text-sm text-petrol-900 mt-1">Dor ou Ardência</p>
            <p class="text-xs text-petrol-700 mt-0.5">Desconforto ao urinar ou durante a relação sexual.</p>
          </div>
          <div class="p-4 rounded-2xl bg-petrol-900 text-white">
            <span class="text-lg">⚠️</span>
            <p class="font-bold text-sm mt-1">Sem Sintomas!</p>
            <p class="text-xs text-white/85 mt-0.5">Muitas ISTs não dão sinais. Não espere sintomas para fazer testes.</p>
          </div>
        </div>
      </div>

      <!-- Banner Urgência PEP 72h -->
      <div class="rounded-3xl bg-gradient-to-r from-terracotta-600 to-terracotta-500 text-white p-6 sm:p-8 shadow-md flex flex-col md:flex-row items-center justify-between gap-6">
        <div class="space-y-2 text-center md:text-left">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/20 text-xs font-bold uppercase tracking-wider">
            ⏱️ Atendimento de Urgência • PEP
          </div>
          <h3 class="font-display font-extrabold text-xl sm:text-2xl">
            Teve relação desprotegida ou o preservativo rompeu?
          </h3>
          <p class="text-sm text-white/95 max-w-2xl leading-relaxed">
            Procure imediatamente uma unidade de saúde do SUS. A <strong>Profilaxia Pós-Exposição (PEP)</strong> deve começar o quanto antes — no máximo em <strong>até 72 horas</strong> — e dura 28 dias. Também é indicada em casos de violência sexual.
          </p>
        </div>
        <div class="shrink-0 bg-white text-terracotta-600 rounded-2xl p-4 text-center shadow-sm min-w-[140px]">
          <span class="block text-3xl font-display font-extrabold">72h</span>
          <span class="text-xs font-bold uppercase tracking-wide text-petrol-800">Prazo Máximo</span>
        </div>
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 6: O SUS CUIDA DE VOCÊ & QUEBRA-GELO                            -->
    <!-- ===================================================================== -->
    <section data-step="6" class="cartilha-section page-enter bg-white rounded-3xl p-6 sm:p-10 shadow-sm border border-sand">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
        <!-- Coluna 1: Checklist SUS -->
        <div class="lg:col-span-7 space-y-4">
          <span class="text-xs font-bold uppercase tracking-wider text-sage-700 bg-sage-50 px-3 py-1 rounded-full">Capítulo 06 • Gratuito e Sigiloso</span>
          <h2 class="font-display font-extrabold text-2xl sm:text-3xl text-petrol-900">O SUS está aqui para cuidar</h2>
          <p class="text-sm text-petrol-700">
            Na Unidade Básica de Saúde (UBS) mais próxima você encontra gratuitamente:
          </p>

          <ul class="space-y-2.5 pt-1">
            <li class="flex items-center gap-3 p-3 rounded-xl bg-sage-50/70 border border-sage-100 text-sm text-petrol-900 font-medium">
              <span class="w-6 h-6 rounded-full bg-sage-500 text-white flex items-center justify-center text-xs font-bold shrink-0">✓</span>
              Conversa acolhedora sobre saúde sexual sem julgamentos
            </li>
            <li class="flex items-center gap-3 p-3 rounded-xl bg-sage-50/70 border border-sage-100 text-sm text-petrol-900 font-medium">
              <span class="w-6 h-6 rounded-full bg-sage-500 text-white flex items-center justify-center text-xs font-bold shrink-0">✓</span>
              Retirada de preservativos internos, externos e gel lubrificante
            </li>
            <li class="flex items-center gap-3 p-3 rounded-xl bg-sage-50/70 border border-sage-100 text-sm text-petrol-900 font-medium">
              <span class="w-6 h-6 rounded-full bg-sage-500 text-white flex items-center justify-center text-xs font-bold shrink-0">✓</span>
              Testes rápidos e orientação para HIV, sífilis e hepatites virais
            </li>
            <li class="flex items-center gap-3 p-3 rounded-xl bg-sage-50/70 border border-sage-100 text-sm text-petrol-900 font-medium">
              <span class="w-6 h-6 rounded-full bg-sage-500 text-white flex items-center justify-center text-xs font-bold shrink-0">✓</span>
              Vacinação (HPV e Hepatite B), avaliação para PrEP/PEP e tratamento
            </li>
          </ul>

          <p class="text-xs text-petrol-700 bg-sand/70 p-3.5 rounded-xl">
            <strong>Adolescentes:</strong> têm direito ao atendimento com privacidade, acolhimento e confidencialidade garantidos pelo Ministério da Saúde.
          </p>
        </div>

        <!-- Coluna 2: Gerador Interativo de Perguntas Quebra-Gelo -->
        <div class="lg:col-span-5 flex flex-col justify-between rounded-3xl bg-petrol-900 text-white p-6 sm:p-7 relative overflow-hidden">
          <div class="absolute -right-10 -bottom-10 w-40 h-40 rounded-full bg-sage-500/20 pointer-events-none"></div>

          <div>
            <span class="inline-block px-3 py-1 rounded-full bg-white/15 text-xs font-bold uppercase tracking-wider text-sage-100">
              Dinâmica em Família
            </span>
            <h3 class="font-display font-bold text-xl mt-3">Uma conversa que protege</h3>
            <p class="text-xs text-white/80 mt-1">
              Não sabe como puxar assunto? Sorteie uma pergunta quebra-gelo:
            </p>

            <!-- Cartão da Pergunta Sorteada -->
            <div class="mt-5 p-5 rounded-2xl bg-white/10 border border-white/15 min-h-[120px] flex items-center justify-center text-center">
              <p id="icebreakerText" class="font-display font-bold text-base sm:text-lg text-cream leading-snug">
                “O que você gostaria de saber sobre prevenção?”
              </p>
            </div>
          </div>

          <div class="mt-5 flex gap-2">
            <button onclick="nextIcebreaker()" class="flex-1 py-3 px-4 rounded-xl bg-terracotta-500 hover:bg-terracotta-600 text-white font-display font-bold text-sm transition-colors flex items-center justify-center gap-2 shadow-sm">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/>
              </svg>
              <span>Nova Pergunta</span>
            </button>
            <button onclick="copyIcebreaker()" id="copyBtn" class="py-3 px-4 rounded-xl bg-white/15 hover:bg-white/25 text-white font-semibold text-xs transition-colors" title="Copiar pergunta">
              Copiar
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- ===================================================================== -->
    <!-- SEÇÃO 7: CRÉDITOS E FONTES                                            -->
    <!-- ===================================================================== -->
    <section data-step="7" class="cartilha-section page-enter bg-sand/70 rounded-3xl p-6 sm:p-10 border border-sand">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="space-y-3">
          <span class="text-xs font-bold uppercase tracking-wider text-petrol-700">Expediente</span>
          <h2 class="font-display font-extrabold text-xl sm:text-2xl text-petrol-900">
            Cuidado e Proteção em Toda Vida
          </h2>
          <p class="text-sm text-petrol-800 leading-relaxed">
            Material educativo elaborado por <strong>Ellen Cristina Gonçalves da Silva</strong> e <strong>Julia Fraga Borges</strong>.
          </p>
          <p class="text-xs text-petrol-700">
            Universidade Estadual do Rio Grande do Sul (UERGS)<br>
            Curso de Administração: Sistemas e Serviços de Saúde • Porto Alegre, 2026.
          </p>
          <div class="pt-2">
            <p class="text-[11px] text-petrol-700 bg-white/80 p-3 rounded-xl border border-sand">
              <strong>Aviso:</strong> Conteúdo educativo e informativo. Não substitui avaliação, diagnóstico ou orientação individual de profissional de saúde.
            </p>
          </div>
        </div>

        <div class="space-y-3">
          <span class="text-xs font-bold uppercase tracking-wider text-sage-700">Fontes Oficiais • Ministério da Saúde</span>
          <ul class="space-y-2 text-xs font-medium text-petrol-800">
            <li>
              <a href="https://www.gov.br/saude/pt-br/assuntos/saude-de-a-a-z/i/ist/prevencao" target="_blank" rel="noopener" class="flex items-center justify-between p-2.5 rounded-xl bg-white hover:bg-sage-50 transition-colors border border-sand">
                <span>Prevenção das Infecções Sexualmente Transmissíveis (IST)</span>
                <span class="text-sage-600">↗</span>
              </a>
            </li>
            <li>
              <a href="https://www.gov.br/saude/pt-br/assuntos/saude-de-a-a-z/s/saude-da-pessoa-idosa/sexualidade-da-pessoa-idosa" target="_blank" rel="noopener" class="flex items-center justify-between p-2.5 rounded-xl bg-white hover:bg-sage-50 transition-colors border border-sand">
                <span>Sexualidade da Pessoa Idosa</span>
                <span class="text-sage-600">↗</span>
              </a>
            </li>
            <li>
              <a href="https://www.gov.br/saude/pt-br/assuntos/saude-de-a-a-z/s/saude-do-adolescente" target="_blank" rel="noopener" class="flex items-center justify-between p-2.5 rounded-xl bg-white hover:bg-sage-50 transition-colors border border-sand">
                <span>Saúde do Adolescente e Jovens</span>
                <span class="text-sage-600">↗</span>
              </a>
            </li>
            <li>
              <a href="https://www.gov.br/saude/pt-br/assuntos/saude-de-a-a-z/a/aids-hiv/pep" target="_blank" rel="noopener" class="flex items-center justify-between p-2.5 rounded-xl bg-white hover:bg-sage-50 transition-colors border border-sand">
                <span>Profilaxia Pós-Exposição (PEP) & Pré-Exposição (PrEP)</span>
                <span class="text-sage-600">↗</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>

  </main>

  <!-- Barra Inferior de Navegação Paginada (Visível no modo Cartilha Paginada) -->
  <footer id="paginationFooter" class="sticky bottom-0 z-30 bg-cream/95 backdrop-blur-md border-t border-sand py-3 px-4 sm:px-6">
    <div class="max-w-5xl mx-auto flex items-center justify-between gap-4">
      <button id="prevBtn" onclick="prevStep()" class="px-4 py-2.5 rounded-xl bg-sand hover:bg-terracotta-100 disabled:opacity-40 disabled:pointer-events-none text-petrol-900 font-display font-bold text-sm flex items-center gap-1.5 transition-colors">
        <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7"/>
        </svg>
        <span>Anterior</span>
      </button>

      <!-- Indicador de Página / Bolinhas -->
      <div class="flex flex-col items-center">
        <div id="stepDots" class="flex items-center gap-1.5">
          <!-- Bolinhas geradas via JS -->
        </div>
        <span id="stepLabel" class="text-[11px] font-semibold text-petrol-700 mt-1">Capa • 1 de 8</span>
      </div>

      <button id="nextBtn" onclick="nextStep()" class="px-5 py-2.5 rounded-xl bg-petrol-800 hover:bg-petrol-900 disabled:opacity-40 disabled:pointer-events-none text-white font-display font-bold text-sm flex items-center gap-1.5 transition-colors shadow-xs">
        <span id="nextBtnText">Próximo</span>
        <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7"/>
        </svg>
      </button>
    </div>
  </footer>

  <!-- Toast de Notificação (Substitui alert) -->
  <div id="toastMsg" class="fixed bottom-20 left-1/2 -translate-x-1/2 z-50 px-4 py-2.5 rounded-full bg-petrol-900 text-white text-xs font-semibold shadow-lg opacity-0 pointer-events-none transition-opacity duration-300">
    Pergunta copiada!
  </div>

  <!-- Scripts de Interatividade -->
  <script>
    // Dados dos Capítulos
    const chapters = [
      { title: "Capa: Cuidado e Proteção", short: "Capa" },
      { title: "1. Sexualidade Não Tem Idade", short: "Cap. 1" },
      { title: "2. Diálogo Sem Tabu em Família", short: "Cap. 2" },
      { title: "3. Mitos e Verdades (Quiz)", short: "Cap. 3" },
      { title: "4. Kit Prevenção Combinada", short: "Cap. 4" },
      { title: "5. Sinais de Alerta & PEP 72h", short: "Cap. 5" },
      { title: "6. O SUS Cuida & Quebra-Gelo", short: "Cap. 6" },
      { title: "Créditos e Fontes Oficiais", short: "Créditos" }
    ];

    // Dados dos 5 Mitos e Verdades
    const mythsData = [
      {
        myth: "“IST é assunto só de jovem.”",
        truth: "As ISTs podem atingir pessoas de qualquer idade. A prevenção deve acompanhar toda a vida."
      },
      {
        myth: "“Se a pessoa parece saudável, não tem IST.”",
        truth: "Muitas ISTs não apresentam sintomas visíveis. A testagem regular é fundamental após exposição."
      },
      {
        myth: "“Em uma relação estável não existe risco.”",
        truth: "O risco depende das práticas e da saúde, não do estado civil. Conversar e testar faz parte do cuidado."
      },
      {
        myth: "“Usar dois preservativos protege mais.”",
        truth: "Nunca use dois preservativos juntos! O atrito entre eles facilita o rompimento."
      },
      {
        myth: "“Pessoas idosas não precisam de orientação sexual.”",
        truth: "Informação, prevenção e atendimento respeitoso são direitos garantidos em todas as fases da vida."
      }
    ];

    // Perguntas Quebra-Gelo
    const icebreakers = [
      "“O que você gostaria de saber sobre prevenção?”",
      "“Você sabe onde conseguir preservativos gratuitamente?”",
      "“Quando foi a última vez que conversamos sobre saúde?”",
      "“Como podemos apoiar uns aos outros sem julgamentos?”"
    ];

    let currentStep = 0;
    let isContinuousMode = false;
    let revealedSet = new Set();
    let icebreakerIndex = 0;

    // Inicialização
    document.addEventListener('DOMContentLoaded', () => {
      renderMyths();
      renderNavigationUI();
      updateView();
    });

    // Renderizar Flip Cards de Mitos e Verdades
    function renderMyths() {
      const grid = document.getElementById('mythsGrid');
      grid.innerHTML = mythsData.map((item, idx) => `
        <div onclick="flipCard(this, ${idx})" class="flip-card perspective-1000 h-56 cursor-pointer select-none group">
          <div class="flip-card-inner">
            <!-- Frente (Mito) -->
            <div class="flip-card-front bg-cream border-2 border-sand group-hover:border-terracotta-500 p-6 flex flex-col justify-between transition-colors">
              <div class="flex items-center justify-between">
                <span class="text-xs font-extrabold uppercase tracking-wider text-terracotta-600 bg-terracotta-100 px-2.5 py-1 rounded-lg">Afirmação #${idx + 1}</span>
                <span class="text-xs text-petrol-700 font-medium flex items-center gap-1">
                  Virar
                  <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9"/>
                  </svg>
                </span>
              </div>
              <p class="font-display font-bold text-base sm:text-lg text-petrol-900 leading-snug">
                ${item.myth}
              </p>
              <span class="text-[11px] font-semibold text-petrol-700/70">Toque para revelar</span>
            </div>

            <!-- Verso (Verdade) -->
            <div class="flip-card-back bg-sage-600 text-white p-6 flex flex-col justify-between shadow-md">
              <div class="flex items-center justify-between">
                <span class="text-xs font-extrabold uppercase tracking-wider bg-terracotta-500 text-white px-2.5 py-1 rounded-lg">MITO!</span>
                <span class="text-xs text-sage-100 font-semibold">Verdade ✓</span>
              </div>
              <p class="text-sm font-medium leading-relaxed text-white">
                ${item.truth}
              </p>
              <span class="text-[11px] text-sage-100">Toque para voltar</span>
            </div>
          </div>
        </div>
      `).join('');
    }

    function flipCard(cardEl, index) {
      cardEl.classList.toggle('flipped');
      revealedSet.add(index);
      document.getElementById('flippedCounter').textContent = revealedSet.size;
    }

    // Abas de Diálogo (Seção 2)
    function switchDialogTab(tab) {
      const dizerBtn = document.getElementById('tabDizerBtn');
      const escutarBtn = document.getElementById('tabEscutarBtn');
      const dizerContent = document.getElementById('tabDizerContent');
      const escutarContent = document.getElementById('tabEscutarContent');

      if (tab === 'dizer') {
        dizerBtn.className = 'flex-1 py-2.5 px-4 rounded-xl font-display font-bold text-sm transition-all bg-white text-petrol-900 shadow-xs';
        escutarBtn.className = 'flex-1 py-2.5 px-4 rounded-xl font-display font-bold text-sm transition-all text-petrol-700 hover:text-petrol-900';
        dizerContent.classList.remove('hidden');
        escutarContent.classList.add('hidden');
      } else {
        escutarBtn.className = 'flex-1 py-2.5 px-4 rounded-xl font-display font-bold text-sm transition-all bg-white text-petrol-900 shadow-xs';
        dizerBtn.className = 'flex-1 py-2.5 px-4 rounded-xl font-display font-bold text-sm transition-all text-petrol-700 hover:text-petrol-900';
        escutarContent.classList.remove('hidden');
        dizerContent.classList.add('hidden');
      }
    }

    // Gerador Quebra-Gelo (Seção 6)
    function nextIcebreaker() {
      icebreakerIndex = (icebreakerIndex + 1) % icebreakers.length;
      const el = document.getElementById('icebreakerText');
      el.style.opacity = '0';
      setTimeout(() => {
        el.textContent = icebreakers[icebreakerIndex];
        el.style.opacity = '1';
      }, 150);
    }

    function copyIcebreaker() {
      const text = icebreakers[icebreakerIndex];
      const tempInput = document.createElement('textarea');
      tempInput.value = text;
      document.body.appendChild(tempInput);
      tempInput.select();
      document.execCommand('copy');
      document.body.removeChild(tempInput);

      const toast = document.getElementById('toastMsg');
      toast.style.opacity = '1';
      setTimeout(() => {
        toast.style.opacity = '0';
      }, 2200);
    }

    // Navegação e UI
    function renderNavigationUI() {
      const drawerList = document.getElementById('drawerNavList');
      const dotsContainer = document.getElementById('stepDots');

      drawerList.innerHTML = chapters.map((ch, idx) => `
        <button onclick="goToSection(${idx}); toggleDrawer();" class="w-full text-left px-3.5 py-2.5 rounded-xl text-sm font-medium transition-colors flex items-center justify-between hover:bg-sand text-petrol-800 drawer-item" data-idx="${idx}">
          <span>${ch.title}</span>
          <span class="text-xs opacity-50">→</span>
        </button>
      `).join('');

      dotsContainer.innerHTML = chapters.map((_, idx) => `
        <button onclick="goToSection(${idx})" aria-label="Ir para página ${idx + 1}" class="step-dot h-2 rounded-full transition-all bg-sand hover:bg-terracotta-500 w-2" data-idx="${idx}"></button>
      `).join('');
    }

    function updateView() {
      const sections = document.querySelectorAll('.cartilha-section');
      const total = sections.length;

      sections.forEach((sec, idx) => {
        if (isContinuousMode) {
          sec.classList.remove('hidden');
        } else {
          if (idx === currentStep) {
            sec.classList.remove('hidden');
            sec.classList.remove('page-enter');
            void sec.offsetWidth; // força reflow da animação
            sec.classList.add('page-enter');
          } else {
            sec.classList.add('hidden');
          }
        }
      });

      // Atualiza barra de progresso
      const progressPercent = isContinuousMode ? 100 : ((currentStep + 1) / total) * 100;
      document.getElementById('progressBar').style.width = `${progressPercent}%`;

      // Atualiza bolinhas e textos
      document.querySelectorAll('.step-dot').forEach((dot, idx) => {
        if (idx === currentStep) {
          dot.classList.remove('w-2', 'bg-sand');
          dot.classList.add('w-6', 'bg-terracotta-500');
        } else {
          dot.classList.remove('w-6', 'bg-terracotta-500');
          dot.classList.add('w-2', 'bg-sand');
        }
      });

      document.querySelectorAll('.drawer-item').forEach((item, idx) => {
        if (idx === currentStep && !isContinuousMode) {
          item.classList.add('bg-terracotta-50', 'text-terracotta-600', 'font-bold');
        } else {
          item.classList.remove('bg-terracotta-50', 'text-terracotta-600', 'font-bold');
        }
      });

      document.getElementById('stepLabel').textContent = `${chapters[currentStep].short} • ${currentStep + 1} de ${total}`;
      document.getElementById('prevBtn').disabled = currentStep === 0;
      document.getElementById('nextBtn').disabled = currentStep === total - 1;
      document.getElementById('nextBtnText').textContent = currentStep === total - 2 ? 'Créditos' : 'Próximo';

      // Rodapé de paginação
      const footer = document.getElementById('paginationFooter');
      if (isContinuousMode) {
        footer.classList.add('hidden');
      } else {
        footer.classList.remove('hidden');
      }
    }

    function nextStep() {
      if (currentStep < chapters.length - 1) {
        currentStep++;
        updateView();
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    }

    function prevStep() {
      if (currentStep > 0) {
        currentStep--;
        updateView();
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    }

    function goToSection(idx) {
      currentStep = idx;
      updateView();
      if (isContinuousMode) {
        const target = document.querySelector(`.cartilha-section[data-step="${idx}"]`);
        if (target) target.scrollIntoView({ behavior: 'smooth' });
      } else {
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    }

    function toggleViewMode() {
      isContinuousMode = !isContinuousMode;
      const btnText = document.getElementById('viewModeText');
      btnText.textContent = isContinuousMode ? 'Modo Paginado' : 'Ver Tudo';
      updateView();
    }

    function toggleDrawer() {
      const drawer = document.getElementById('chapterDrawer');
      drawer.classList.toggle('hidden');
    }
  </script>
</body>
</html>
