<script setup lang="ts">
/* =========================================================
   Solutions.vue — Seção "Soluções"
   Template premium + tech (sem blog por enquanto)
   ========================================================= */

type Solution = {
  title: string;
  description: string;
  bullets: string[];
  href: string;
};

const title = "Soluções";
const subtitle =
  "Pacotes práticos para organizar sua TI e deixar a operação estável, segura e fácil de manter.";

const items: Solution[] = [
  {
    title: "Wi-Fi & Rede bem resolvidos",
    description:
      "Cobertura, performance e segmentação do jeito certo — sem gambiarra e com documentação.",
    bullets: ["Mapeamento de cobertura", "VLANs e SSIDs", "Padronização e diagrama"],
    href: "#contato",
  },
  {
    title: "Servidor estável e previsível",
    description:
      "Organizo o básico que mais quebra: updates, backup, desempenho e boas práticas de serviços.",
    bullets: ["Revisão de saúde", "Rotinas e backup", "Ajustes de performance"],
    href: "#contato",
  },
  {
    title: "Microsoft 365 sem bagunça",
    description:
      "Acesso, segurança e colaboração com padrão — sem sustos com permissões e configurações soltas.",
    bullets: ["MFA e identidade", "SharePoint/OneDrive", "Boas práticas e governança"],
    href: "#contato",
  },
];

const cta = { label: "Agendar avaliação", href: "#contato" };
</script>

<template>
  <section id="solucoes" class="relative py-16 md:py-24">
    <!-- BG sutil -->
    <div class="pointer-events-none absolute inset-0 -z-10">
      <div
        class="absolute inset-0 bg-[radial-gradient(ellipse_at_top,rgba(56,189,248,0.10),rgba(0,0,0,0)_55%)]"
      />
    </div>

    <div class="mx-auto max-w-6xl px-5">
      <!-- Header -->
      <div class="flex flex-col gap-3 md:flex-row md:items-end md:justify-between">
        <div class="max-w-2xl">
          <p class="text-xs font-semibold uppercase tracking-widest text-zinc-500 dark:text-zinc-400">
            SOLUÇÕES
          </p>

          <h2
            class="mt-2 text-2xl font-extrabold tracking-tight text-zinc-900 dark:text-white md:text-4xl"
          >
            {{ title }}
          </h2>

          <p class="mt-3 text-base leading-7 text-zinc-600 dark:text-zinc-300">
            {{ subtitle }}
          </p>
        </div>

        <a
          :href="cta.href"
          class="mt-6 inline-flex h-11 items-center justify-center rounded-full bg-zinc-900 px-6 text-sm font-semibold text-white shadow-sm transition hover:bg-zinc-800 dark:bg-white dark:text-black dark:hover:bg-zinc-100 md:mt-0"
        >
          {{ cta.label }}
        </a>
      </div>

      <!-- Grid -->
      <div class="mt-10 grid gap-6 md:mt-12 md:grid-cols-3">
        <article
          v-for="card in items"
          :key="card.title"
          class="group relative overflow-hidden rounded-2xl border border-zinc-200 bg-white/70 p-6 shadow-[0_12px_40px_-28px_rgba(0,0,0,0.45)] backdrop-blur-sm transition hover:-translate-y-0.5 hover:shadow-[0_18px_55px_-30px_rgba(0,0,0,0.55)]
                 dark:border-white/10 dark:bg-white/5"
        >
          <!-- brilho sutil -->
          <div
            class="pointer-events-none absolute -top-24 left-1/2 h-40 w-40 -translate-x-1/2 rounded-full bg-sky-500/10 blur-3xl opacity-0 transition group-hover:opacity-100"
          />

          <h3 class="text-lg font-bold text-zinc-900 dark:text-white">
            {{ card.title }}
          </h3>

          <p class="mt-2 text-sm leading-6 text-zinc-600 dark:text-zinc-300">
            {{ card.description }}
          </p>

          <ul class="mt-4 space-y-2 text-sm text-zinc-700 dark:text-zinc-200">
            <li v-for="b in card.bullets" :key="b" class="flex items-start gap-2">
              <span class="mt-2 inline-block h-1.5 w-1.5 shrink-0 rounded-full bg-sky-500/90" />
              <span>{{ b }}</span>
            </li>
          </ul>

          <div class="mt-6">
            <a
              :href="card.href"
              class="inline-flex items-center gap-2 text-sm font-semibold text-zinc-900 transition group-hover:gap-2.5 dark:text-white"
            >
              Conversar sobre isso
              <span
                class="inline-block translate-x-0 transition-transform duration-200 group-hover:translate-x-0.5"
                aria-hidden="true"
              >
                →
              </span>
            </a>
          </div>
        </article>
      </div>

      <!-- Rodapé curto -->
      <div class="mt-10 rounded-2xl border border-zinc-200 bg-white/60 p-6 text-sm text-zinc-600 backdrop-blur-sm dark:border-white/10 dark:bg-white/5 dark:text-zinc-300">
        <span class="font-semibold text-zinc-900 dark:text-white">Dica:</span>
        se você não sabe qual solução se encaixa, eu faço um diagnóstico rápido e te digo o melhor caminho.
      </div>
    </div>
  </section>
</template>
