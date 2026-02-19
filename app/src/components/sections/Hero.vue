<script setup lang="ts">
/* =========================================================
   Bloco 1 — Assets
   ========================================================= */
import bg from "../../assets/hero-1200.webp";
import logoLight from "../../assets/logo-light.svg";
import { ref, onMounted, onBeforeUnmount, watch } from "vue";

const bgSrc = bg.src;
const logoLightSrc = logoLight.src;

/* =========================================================
   Bloco 2 — Conteúdo
   ========================================================= */
const nav = [
  { label: "Serviços", href: "#servicos" },
  { label: "Soluções", href: "#solucoes" },
  { label: "Sobre", href: "#sobre" },
];

const title = "Infraestrutura que flui.";
const subtitle =
  "Do on-prem ao cloud, eu desenho e automatizo sua jornada com padrão enterprise e documentação clara.";

const cta = { label: "Começar", href: "#contato" };
const navCta = { label: "Agendar", href: "#contato" };

/* =========================================================
   Bloco 3 — Theme toggle (mantido para desktop)
   ========================================================= */
const isDark = ref(false);

onMounted(() => {
  isDark.value = document.documentElement.classList.contains("dark");
});

const toggleTheme = () => {
  isDark.value = !isDark.value;
  document.documentElement.classList.toggle("dark", isDark.value);
  localStorage.setItem("theme", isDark.value ? "dark" : "light");
};

/* =========================================================
   Bloco 4 — Mobile menu state
   ========================================================= */
const mobileOpen = ref(false);
const closeMobile = () => (mobileOpen.value = false);

const onKeydown = (e: KeyboardEvent) => {
  if (e.key === "Escape") closeMobile();
};

onMounted(() => window.addEventListener("keydown", onKeydown));
onBeforeUnmount(() => window.removeEventListener("keydown", onKeydown));

watch(mobileOpen, (open) => {
  document.body.style.overflow = open ? "hidden" : "";
});

/* =========================================================
   Bloco 5 — Social links (ALTERE AQUI)
   ========================================================= */
const socials = [
  { label: "X", href: "https://x.com/DenisCode_" },
  { label: "YouTube", href: "https://www.youtube.com/@odeniscode" },
  { label: "Instagram", href: "https://www.instagram.com/denisc0de" },
];
</script>

<template>
  <section class="relative overflow-hidden">
    <div class="relative min-h-[80vh] md:min-h-[88vh]">
      <!-- Background -->
      <div class="absolute inset-0">
        <img :src="bgSrc" alt="" class="h-full w-full object-cover" />
        <div class="absolute inset-0 bg-black/55"></div>
        <div
          class="absolute inset-0 bg-[radial-gradient(ellipse_at_center,rgba(0,0,0,0.05)_0%,rgba(0,0,0,0.60)_70%,rgba(0,0,0,0.75)_100%)]"
        ></div>
      </div>

      <!-- Navbar -->
      <header class="absolute left-0 right-0 top-0 z-20">
        <div
          class="bg-black/35 backdrop-blur-xl ring-1 ring-white/10 shadow-[0_18px_60px_-30px_rgba(0,0,0,0.95)]"
        >
          <div class="mx-auto flex max-w-6xl items-center justify-between px-5 py-4">
            <a
              href="/"
              class="inline-flex items-center justify-center rounded-lg px-2 py-1 transition hover:bg-white/5"
              aria-label="DenisCode"
            >
              <img :src="logoLightSrc" alt="DenisCode" class="h-7 w-auto" />
            </a>

            <!-- Desktop -->
            <div class="hidden items-center gap-6 md:flex">
              <nav class="flex items-center gap-6 text-sm">
                <a
                  v-for="item in nav"
                  :key="item.href"
                  :href="item.href"
                  class="group relative text-white/80 transition hover:text-white"
                >
                  {{ item.label }}
                  <span
                    class="pointer-events-none absolute -bottom-2 left-0 h-[2px] w-0 rounded-full bg-white/70 transition-all duration-200 group-hover:w-full"
                  ></span>
                </a>
              </nav>

              <div class="h-6 w-px bg-white/10"></div>

              <!-- Toggle (desktop only) -->
              <button
                type="button"
                @click="toggleTheme"
                class="group inline-flex h-10 w-10 items-center justify-center rounded-full bg-white/5 text-white/80 ring-1 ring-white/10 transition hover:bg-white/10 hover:text-white focus:outline-none focus:ring-2 focus:ring-white/20"
                :aria-label="isDark ? 'Ativar tema claro' : 'Ativar tema escuro'"
              >
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

              <!-- CTA desktop -->
              <a
                :href="navCta.href"
                class="group inline-flex h-10 items-center justify-center rounded-full bg-white/10 px-5 text-sm font-semibold text-white ring-1 ring-white/15 backdrop-blur-md transition
                       hover:bg-white/15 hover:ring-white/25 focus:outline-none focus:ring-2 focus:ring-white/25
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

            <!-- Mobile -->
            <div class="flex items-center gap-3 md:hidden">
              <button
                type="button"
                class="inline-flex h-10 w-10 items-center justify-center rounded-full bg-white/5 text-white/85 ring-1 ring-white/10 transition hover:bg-white/10 focus:outline-none focus:ring-2 focus:ring-white/20"
                :aria-label="mobileOpen ? 'Fechar menu' : 'Abrir menu'"
                @click="mobileOpen = !mobileOpen"
              >
                <svg
                  v-if="!mobileOpen"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="none"
                  class="h-5 w-5"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M4 6h16" />
                  <path d="M4 12h16" />
                  <path d="M4 18h16" />
                </svg>

                <svg
                  v-else
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="none"
                  class="h-5 w-5"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M18 6 6 18" />
                  <path d="M6 6l12 12" />
                </svg>
              </button>
            </div>
          </div>
        </div>
        
        <!-- =========================================================
          Mobile Menu — TOP Drawer (premium + minimal)
         ========================================================= -->
        <div v-show="mobileOpen" class="md:hidden">
          <!-- backdrop -->
          <button
            type="button"
            class="fixed inset-0 z-30 bg-black/55"
            aria-label="Fechar menu"
            @click="closeMobile"
          ></button>

          <!-- panel (top, abaixo da navbar) -->
          <div
            class="fixed left-0 right-0 top-[72px] z-40 mx-auto w-[92%] max-w-[560px] rounded-2xl bg-black/55 backdrop-blur-2xl ring-1 ring-white/10 shadow-[0_20px_70px_-35px_rgba(0,0,0,0.95)] overflow-hidden"
            style="padding-top: env(safe-area-inset-top)"
          >
            <!-- header minimal (toggle + close) -->
            <div class="flex items-center justify-between px-4 pt-4 pb-3">
              <div class="flex items-center gap-2">
                <!-- toggle tema -->
                <button
                  type="button"
                  @click="toggleTheme"
                  class="group inline-flex h-10 w-10 items-center justify-center rounded-full bg-white/5 text-white/85 ring-1 ring-white/10 transition hover:bg-white/10 focus:outline-none focus:ring-2 focus:ring-white/20"
                  :aria-label="isDark ? 'Ativar tema claro' : 'Ativar tema escuro'"
                  :title="isDark ? 'Tema escuro' : 'Tema claro'"
                >
                  <!-- Sun (quando LIGHT) -->
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

                  <!-- Moon (quando DARK) -->
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
              </div>

              <!-- close -->
              <button
                type="button"
                class="inline-flex h-10 w-10 items-center justify-center rounded-full bg-white/5 text-white/85 ring-1 ring-white/10 transition hover:bg-white/10 focus:outline-none focus:ring-2 focus:ring-white/20"
                aria-label="Fechar"
                @click="closeMobile"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="none"
                  class="h-5 w-5"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M18 6 6 18" />
                  <path d="M6 6l12 12" />
                </svg>
              </button>
            </div>

            <!-- links -->
            <div class="px-2 pb-4">
              <nav class="grid gap-1 px-2">
                <a
                  v-for="item in nav"
                  :key="item.href"
                  :href="item.href"
                  class="flex items-center justify-between rounded-2xl px-4 py-3 text-base font-semibold text-white/90 transition hover:bg-white/10 active:bg-white/15"
                  @click="closeMobile"
                >
                  <span>{{ item.label }}</span>
                  <span class="text-white/35 text-sm">›</span>
                </a>
              </nav>

              <div class="mx-4 my-4 h-px bg-white/10"></div>

              <!-- CTA -->
              <div class="px-2">
                <a
                  :href="navCta.href"
                  class="inline-flex h-12 w-full items-center justify-center rounded-2xl bg-white/10 px-6 text-sm font-semibold text-white ring-1 ring-white/15 transition hover:bg-white/15 hover:ring-white/25 focus:outline-none focus:ring-2 focus:ring-white/25"
                  @click="closeMobile"
                >
                  <span class="inline-flex items-center gap-2">
                    {{ navCta.label }}
                    <span class="opacity-70">→</span>
                  </span>
                </a>

                <!-- socials -->
                <div class="mt-4 flex items-center justify-center gap-4">
                  <!-- X -->
                  <a
                    href="https://x.com/DenisCode_"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="inline-flex h-11 w-11 items-center justify-center rounded-full bg-white/5 ring-1 ring-white/10 text-white/80 transition hover:bg-white/10 hover:text-white"
                    aria-label="X"
                    title="X"
                  >
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-5 w-5">
                      <path d="M18.244 2H21l-6.53 7.46L22 22h-6.828l-5.35-7.002L3.8 22H1l7.07-8.08L2 2h7l4.84 6.35L18.244 2Zm-1.197 18h1.89L7.86 3.9H5.83l11.217 16.1Z" />
                    </svg>
                  </a>

                  <!-- YouTube -->
                  <a
                    href="https://www.youtube.com/@odeniscode"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="inline-flex h-11 w-11 items-center justify-center rounded-full bg-white/5 ring-1 ring-white/10 text-white/80 transition hover:bg-white/10 hover:text-white"
                    aria-label="YouTube"
                    title="YouTube"
                  >
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-5 w-5">
                      <path d="M21.6 7.2a3.02 3.02 0 0 0-2.12-2.14C17.6 4.6 12 4.6 12 4.6s-5.6 0-7.48.46A3.02 3.02 0 0 0 2.4 7.2 31.7 31.7 0 0 0 2 12a31.7 31.7 0 0 0 .4 4.8 3.02 3.02 0 0 0 2.12 2.14c1.88.46 7.48.46 7.48.46s5.6 0 7.48-.46a3.02 3.02 0 0 0 2.12-2.14A31.7 31.7 0 0 0 22 12a31.7 31.7 0 0 0-.4-4.8ZM10 15.5v-7l6 3.5-6 3.5Z" />
                    </svg>
                  </a>

                  <!-- Instagram -->
                  <a
                    href="https://www.instagram.com/denisc0de"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="inline-flex h-11 w-11 items-center justify-center rounded-full bg-white/5 ring-1 ring-white/10 text-white/80 transition hover:bg-white/10 hover:text-white"
                    aria-label="Instagram"
                    title="Instagram"
                  >
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" class="h-5 w-5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <rect x="3" y="3" width="18" height="18" rx="5" ry="5" />
                      <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37Z" />
                      <path d="M17.5 6.5h.01" />
                    </svg>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>


      </header>

      <!-- Hero content -->
      <div class="relative mx-auto flex max-w-6xl px-5">
        <div
          class="flex min-h-[80vh] w-full flex-col items-center justify-end pt-24 pb-10 text-center md:min-h-[88vh] md:pt-24 md:pb-24"
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
            {{ cta.label }}
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
