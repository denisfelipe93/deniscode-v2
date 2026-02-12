<script setup lang="ts">
/* =========================================================
   Bloco 1 — Assets (ALTERE AQUI nomes/caminhos)
   ========================================================= */
import bg from "../../assets/hero-1200.webp";
import logoLight from "../../assets/logo-light.svg";

const bgSrc = bg.src;
const logoLightSrc = logoLight.src;

/* =========================================================
   Bloco 2 — Conteúdo (ALTERE AQUI textos/links)
   ========================================================= */
const nav = [
  { label: "Serviços", href: "#servicos" },
  { label: "Soluções", href: "#solucoes" },
  { label: "Sobre", href: "#sobre" },
  { label: "Contato", href: "#contato" },
];

const title = "Infraestrutura que flui.";
const subtitle =
  "Do on-prem ao cloud, eu desenho e automatizo sua jornada com padrão enterprise e documentação clara.";

const cta = { label: "Começar", href: "#contato" };
</script>

<template>
  <!-- =========================================================
       Bloco 3 — Hero wrapper (ALTERE AQUI altura)
       ========================================================= -->
  <section class="relative overflow-hidden">
    <div class="relative min-h-[80vh] md:min-h-[88vh]">
      <!-- =========================================================
           Bloco 4 — Background + overlay (ALTERE AQUI contraste)
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
           Bloco 5 — Navbar glass FULL WIDTH (igual mockup)
           ========================================================= -->
      <header class="absolute left-0 right-0 top-0 z-10">
        <!-- faixa full-width -->
        <div class="bg-white/10 backdrop-blur-md ring-1 ring-white/10">
          <!-- container interno -->
          <div class="mx-auto flex max-w-6xl items-center justify-between px-5 py-4">
            <!-- logo -->
            <a
              href="/"
              class="inline-flex items-center justify-center p-1 transition hover:opacity-90"
              aria-label="DenisCode"
            >
              <img :src="logoLightSrc" alt="DenisCode" class="h-7 w-auto" loading="eager" />
            </a>

            <!-- menu -->
            <nav class="hidden items-center gap-6 text-sm text-white/80 md:flex">
              <a
                v-for="item in nav"
                :key="item.href"
                :href="item.href"
                class="transition hover:text-white"
              >
                {{ item.label }}
              </a>
            </nav>
          </div>
        </div>
      </header>

      <!-- =========================================================
           Bloco 6 — Conteúdo central (badge + título + subtítulo + 1 CTA)
           ========================================================= -->
      <div class="relative mx-auto flex max-w-6xl px-5">
        <div class="flex min-h-[80vh] w-full flex-col items-center justify-center pt-24 text-center md:min-h-[88vh] md:pt-28">

          <!-- Título -->
          <h1 class="max-w-4xl text-4xl font-extrabold tracking-tight text-white md:text-6xl">
            {{ title }}
          </h1>

          <!-- Subtítulo -->
          <p class="mt-5 max-w-2xl text-base leading-7 text-white/80 md:text-lg">
            {{ subtitle }}
          </p>

          <!-- Botão único (mockup-like) -->
          <a
            :href="cta.href"
            class="mt-8 inline-flex h-12 items-center justify-center rounded-full bg-sky-500 px-7 text-sm font-bold text-white shadow-[0_12px_28px_-14px_rgba(56,189,248,0.8)] transition hover:bg-sky-400 focus:outline-none focus:ring-2 focus:ring-sky-300 focus:ring-offset-2 focus:ring-offset-black"
          >
            {{ cta.label }} <span class="ml-2">→</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
