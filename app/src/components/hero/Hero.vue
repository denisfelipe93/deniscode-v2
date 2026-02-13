<script setup lang="ts">
/* =========================================================
   Bloco 1 — Assets (ALTERE AQUI nomes/caminhos)
   ========================================================= */
import bg from "../../assets/hero-1200.webp";
import logoLight from "../../assets/logo-light.svg";
import { ref, onMounted } from "vue";

const bgSrc = bg.src;
const logoLightSrc = logoLight.src;

/* =========================================================
   Bloco 2 — Conteúdo (ALTERE AQUI textos/links)
   ========================================================= */
const nav = [
  { label: "Serviços", href: "#servicos" },
  { label: "Soluções", href: "#solucoes" },
  { label: "Sobre", href: "#sobre" },
  // { label: "Contato", href: "#contato" },
];

// (depois a gente revisa copy/cta com calma)
const title = "Infraestrutura que flui.";
const subtitle =
  "Do on-prem ao cloud, eu desenho e automatizo sua jornada com padrão enterprise e documentação clara.";
const cta = { label: "Começar", href: "#contato" };
const navCta = { label: "Agendar", href: "#contato" };

/* =========================================================
   Bloco 3 — Theme toggle (ALTERE AQUI se quiser outro padrão)
   ========================================================= */
const isDark = ref(false);

onMounted(() => {
  // pega o estado atual aplicado pelo script do Layout.astro
  isDark.value = document.documentElement.classList.contains("dark");
});

const toggleTheme = () => {
  isDark.value = !isDark.value;
  document.documentElement.classList.toggle("dark", isDark.value);
  localStorage.setItem("theme", isDark.value ? "dark" : "light");
};
</script>

<template>
  <!-- =========================================================
       Bloco 4 — Hero wrapper (ALTERE AQUI altura)
       ========================================================= -->
  <section class="relative overflow-hidden">
    <div class="relative min-h-[80vh] md:min-h-[88vh]">
      <!-- =========================================================
           Bloco 5 — Background + overlay (ALTERE AQUI contraste)
           ========================================================= -->
      <div class="absolute inset-0">
        <img :src="bgSrc" alt="" class="h-full w-full object-cover" />

        <!-- overlay escuro (mockup-like) -->
        <div class="absolute inset-0 bg-black/55"></div>

        <!-- vinheta suave (bordas mais escuras) -->
        <div
          class="absolute inset-0 bg-[radial-gradient(ellipse_at_center,rgba(0,0,0,0.05)_0%,rgba(0,0,0,0.60)_70%,rgba(0,0,0,0.75)_100%)]"
        ></div>
      </div>

      <!-- =========================================================
          Bloco 6 — Navbar premium FULL WIDTH (mockup-like)
          ALTERE AQUI: altura, blur, espaçamento, links e CTA
          ========================================================= -->
      <header class="absolute left-0 right-0 top-0 z-10">
        <!-- faixa única (uma peça só) -->
        <div
          class="bg-black/35 backdrop-blur-xl ring-1 ring-white/10 shadow-[0_18px_60px_-30px_rgba(0,0,0,0.95)]"
        >
          <div class="mx-auto flex max-w-6xl items-center justify-between px-5 py-4">
            <!-- Logo -->
            <a
              href="/"
              class="inline-flex items-center justify-center rounded-lg px-2 py-1 transition hover:bg-white/5"
              aria-label="DenisCode"
            >
              <img :src="logoLightSrc" alt="DenisCode" class="h-7 w-auto" />
            </a>

            <!-- Direita: menu + ações -->
            <div class="hidden items-center gap-6 md:flex">
              <!-- Menu -->
              <nav class="flex items-center gap-6 text-sm">
                <a
                  v-for="item in nav"
                  :key="item.href"
                  :href="item.href"
                  class="group relative text-white/80 transition hover:text-white"
                >
                  {{ item.label }}
                  <!-- underline animado -->
                  <span
                    class="pointer-events-none absolute -bottom-2 left-0 h-[2px] w-0 rounded-full bg-white/70 transition-all duration-200 group-hover:w-full"
                  ></span>
                </a>
              </nav>

              <!-- Separador sutil -->
              <div class="h-6 w-px bg-white/10"></div>

              <!-- Toggle tema (fica discreto e alinhado) -->
              <button
                type="button"
                @click="toggleTheme"
                class="group inline-flex h-10 w-10 items-center justify-center rounded-full bg-white/5 text-white/80 ring-1 ring-white/10 transition hover:bg-white/10 hover:text-white focus:outline-none focus:ring-2 focus:ring-white/20"
                :aria-label="isDark ? 'Ativar tema claro' : 'Ativar tema escuro'"
                :title="isDark ? 'Tema escuro' : 'Tema claro'"
              >
                <!-- Sun icon (quando está LIGHT) -->
                <svg
                  v-if="!isDark"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="none"
                  class="h-[18px] w-[18px] opacity-90 transition duration-200 ease-out group-hover:opacity-100 group-hover:scale-[1.06] transform-gpu origin-center"
                  stroke="currentColor"
                  stroke-width="1.75"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <circle cx="12" cy="12" r="4" />
                  <path d="M12 2v2" />
                  <path d="M12 20v2" />
                  <path d="M4.93 4.93l1.41 1.41" />
                  <path d="M17.66 17.66l1.41 1.41" />
                  <path d="M2 12h2" />
                  <path d="M20 12h2" />
                  <path d="M4.93 19.07l1.41-1.41" />
                  <path d="M17.66 6.34l1.41-1.41" />
                </svg>

                <!-- Moon icon (quando está DARK) -->
                <svg
                  v-else
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="none"
                  class="h-[18px] w-[18px] opacity-90 transition duration-200 ease-out group-hover:opacity-100 group-hover:scale-[1.06] transform-gpu origin-center"
                  stroke="currentColor"
                  stroke-width="1.75"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M21 12.8A8.5 8.5 0 1 1 11.2 3a6.5 6.5 0 0 0 9.8 9.8Z" />
                </svg>
              </button>

              <!-- CTA Navbar (premium, simples: texto + seta sem círculo) -->
              <a
                :href="cta.href"
                class="group inline-flex h-10 items-center justify-center rounded-full bg-white/10 px-5 text-sm font-semibold text-white ring-1 ring-white/15 backdrop-blur-md transition
                      hover:bg-white/15 hover:ring-white/25
                      focus:outline-none focus:ring-2 focus:ring-white/25
                      shadow-[0_14px_40px_-28px_rgba(0,0,0,0.9)]"
              >
                <span class="inline-flex items-center gap-2">
                  {{ navCta.label }}
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    fill="none"
                    class="h-4 w-4 opacity-80 transition-transform duration-200 group-hover:translate-x-0.5 group-hover:opacity-100"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    aria-hidden="true"
                  >
                    <path d="M5 12h12" />
                    <path d="M13 6l6 6-6 6" />
                  </svg>
                </span>
              </a>
            </div>
          </div>
        </div>
      </header>



      <!-- =========================================================
           Bloco 7 — Conteúdo central (ALTERE AQUI posição/textos)
           ========================================================= -->
      <div class="relative mx-auto flex max-w-6xl px-5">
        <div
          class="flex min-h-[80vh] w-full flex-col items-center justify-end pt-20 pb-14 text-center md:min-h-[88vh] md:pt-24 md:pb-24"
        >
          <h1
            class="max-w-4xl text-4xl font-extrabold tracking-tight text-white drop-shadow-[0_14px_34px_rgba(0,0,0,0.75)] md:text-6xl"
          >
            {{ title }}
          </h1>

          <p
            class="mt-5 max-w-2xl text-base leading-7 text-white/85 drop-shadow-[0_10px_22px_rgba(0,0,0,0.65)] md:text-lg"
          >
            {{ subtitle }}
          </p>

          <a
            :href="cta.href"
            class="mt-8 inline-flex h-12 items-center justify-center rounded-full bg-gradient-to-b from-sky-400 to-sky-600 px-10 text-sm font-bold text-white shadow-[0_20px_45px_-18px_rgba(56,189,248,0.9)] transition hover:from-sky-300 hover:to-sky-500 focus:outline-none focus:ring-2 focus:ring-sky-300 focus:ring-offset-2 focus:ring-offset-black"
          >
             {{ cta.label }} <!--<span class="ml-2">→</span> -->
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
