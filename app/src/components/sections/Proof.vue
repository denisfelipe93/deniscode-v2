<script setup lang="ts">
/* =========================================================
   ProofA.vue — Prova visual (grid premium)
   ALTERE AQUI: imagens e textos (Bloco 1 e 2)
   ========================================================= */

/* =========================================================
   Bloco 1 — Imagens (ALTERE AQUI os nomes dos arquivos)
   Dica: deixe em src/assets/portfolio/
   ========================================================= */
const images = {
  wifi1: "/app/src/assets/portifolio/ubiquiti-instalation.png",
  wifi2: "/src/assets/portfolio/wifi-02.jpg",
  sust1: "/src/assets/portfolio/sustentacao-01.jpg",
};

/* =========================================================
   Bloco 2 — Conteúdo (ALTERE AQUI os textos)
   ========================================================= */
const heading = "Trabalho real. Entrega organizada.";
const subheading =
  "Fotos de instalação, ajustes e sustentação — com padrão, documentação e foco em estabilidade.";

const items = [
  {
    title: "Wi-Fi Ubiquiti / UniFi",
    desc: "Cobertura, performance e rede organizada para o dia a dia.",
    img: images.wifi1,
  },
  {
    title: "Rede bem configurada",
    desc: "Padrão, segmentação quando faz sentido e configuração limpa.",
    img: images.wifi2,
  },
  {
    title: "Sustentação",
    desc: "Rotina simples para reduzir incidentes e facilitar manutenção.",
    img: images.sust1,
  },
];

const cta = { label: "Agendar uma conversa", href: "#contato" };
</script>

<template>
  <section id="prova" class="px-5 py-16 md:py-24">
    <div class="mx-auto max-w-6xl">
      <!-- Header -->
      <div class="max-w-2xl">
        <p class="text-xs font-semibold uppercase tracking-widest text-zinc-500 dark:text-white/60">
          Prova
        </p>
        <h2 class="mt-3 text-3xl font-extrabold tracking-tight text-zinc-900 dark:text-white md:text-4xl">
          {{ heading }}
        </h2>
        <p class="mt-4 text-base leading-7 text-zinc-600 dark:text-white/75 md:text-lg">
          {{ subheading }}
        </p>
      </div>

      <!-- Grid -->
      <div class="mt-10 grid gap-5 md:grid-cols-3 md:gap-6">
        <article
          v-for="it in items"
          :key="it.title"
          class="group overflow-hidden rounded-2xl border border-zinc-200 bg-white shadow-sm transition
                 hover:-translate-y-0.5 hover:shadow-md
                 dark:border-white/10 dark:bg-white/5"
        >
          <div class="relative aspect-[4/3] overflow-hidden">
            <img
              :src="it.img"
              :alt="it.title"
              class="h-full w-full object-cover transition duration-300 group-hover:scale-[1.03]"
              loading="lazy"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/45 via-black/0 to-black/0"></div>
          </div>

          <div class="p-6">
            <h3 class="text-base font-bold text-zinc-900 dark:text-white">
              {{ it.title }}
            </h3>
            <p class="mt-2 text-sm leading-6 text-zinc-600 dark:text-white/75">
              {{ it.desc }}
            </p>

            <a
              :href="cta.href"
              class="mt-5 inline-flex items-center gap-2 text-sm font-semibold text-zinc-900 hover:opacity-80 dark:text-white"
            >
              {{ cta.label }} <span aria-hidden="true">→</span>
            </a>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>
