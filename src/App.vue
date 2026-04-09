<script setup lang="ts">
import {
  ArrowRightLeft,
  ClipboardList,
  Hammer,
  MapPin,
  Package,
  QrCode,
  ScanLine,
  Warehouse,
  Wrench,
} from "lucide-vue-next";

const miniStats = [
  { value: "Dochádzka", label: "príchody, odchody, prestávky", icon: ClipboardList },
  { value: "Výkaz", label: "práce, materiál, tím", icon: Hammer },
  { value: "Pracoviská", label: "prehľad naprieč stavbami", icon: Warehouse },
];

const featureCards = [
  {
    title: "Dochádzka cez QR",
    text: "Príchod a odchod sa zapisuje skenom QR kódu priamo na pracovisku.",
    icon: QrCode,
  },
  {
    title: "Poloha pri skene",
    text: "Pri QR evidencii sa kontroluje poloha, takže dochádzku nie je jednoduché obísť.",
    icon: MapPin,
  },
  {
    title: "Vlastné práce a materiály",
    text: "Firma si môže vytvárať vlastné typy prác aj vlastný zoznam materiálov.",
    icon: Wrench,
  },
];

const outcomes = [
  "menej telefonátov",
  "menej dopĺňania spätne",
  "presnejšia dochádzka cez QR",
  "jasnejší stav materiálu na sklade",
];

const heroRows = [
  { label: "Použitý materiál", icon: Package },
  { label: "Vykonané práce", icon: Hammer },
  { label: "Dochádzka pracovníkov", icon: ClipboardList },
];

const materialItems = ["Betón B20", "Cement 25kg", "Istič B16"];

const stockItems = [
  { item: "Kábel CYKY-J 3x1.5", qty: "50 m", qtyClass: "text-[#16a34a]" },
  { item: "T-kus PPR 20", qty: "50 ks", qtyClass: "text-[#16a34a]" },
  { item: 'Ventil guľový 1/2"', qty: "-35 ks", qtyClass: "text-[#ef4444]" },
];
</script>

<template>
  <div class="min-h-screen bg-[#f6f7f5] text-[#171717]">
    <header class="mx-auto flex max-w-6xl items-center justify-between px-5 py-5 sm:px-6 lg:px-8">
      <div class="text-[15px] font-semibold tracking-[-0.02em]">Mirela</div>
      <div class="hidden items-center gap-6 text-sm text-[#5f655f] md:flex">
        <a href="#prehlad" class="hover:text-[#171717]">Prehľad</a>
        <a href="#prehlad-appky" class="hover:text-[#171717]">Prehľad appky</a>
        <a href="#vysledok" class="hover:text-[#171717]">Výsledok</a>
      </div>
    </header>

    <main>
      <section
        class="mx-auto grid max-w-6xl gap-10 px-5 pb-14 pt-4 sm:px-6 lg:grid-cols-[1.02fr_0.98fr] lg:px-8 lg:pb-20 lg:pt-8"
      >
        <div class="flex flex-col justify-center">
          <div
            class="mb-4 inline-flex w-fit items-center gap-2 rounded-full bg-[#e8f3ea] px-3 py-1.5 text-xs font-medium text-[#18984a]"
          >
            <span class="h-2 w-2 rounded-full bg-[#16a34a]" />
            Pre stavebné a terénne firmy
          </div>

          <h1 class="max-w-3xl text-4xl font-semibold leading-[1.02] tracking-[-0.05em] sm:text-5xl lg:text-[64px]">
            Menej chaosu na stavbe.
            <br />
            Viac jasných záznamov.
          </h1>

          <p class="mt-5 max-w-xl text-base leading-7 text-[#616661] sm:text-lg sm:leading-8">
            Dochádzka cez QR, materiál, sklad a vykonané práce v jednoduchej mobilnej aplikácii,
            ktorú vie použiť vedúci aj pracovník.
          </p>

          <div class="mt-8 flex flex-wrap gap-3">
            <a
              href="#prehlad-appky"
              class="rounded-[18px] bg-[#16a34a] px-5 py-3 text-sm font-semibold text-white shadow-[0_10px_30px_rgba(22,163,74,0.22)]"
            >
              Pozrieť appku
            </a>
            <a
              href="#prehlad"
              class="rounded-[18px] border border-[#d9ddd8] bg-white px-5 py-3 text-sm font-semibold text-[#1d1f1d]"
            >
              Čo rieši
            </a>
          </div>

          <div class="mt-10 grid gap-3 sm:grid-cols-3">
            <div
              v-for="item in miniStats"
              :key="item.value"
              class="rounded-[22px] border border-[#e1e4df] bg-white px-4 py-4"
            >
              <div class="flex items-center gap-3">
                <div class="grid h-10 w-10 place-items-center rounded-[14px] bg-[#e8f3ea] text-[#16a34a]">
                  <component :is="item.icon" :size="18" />
                </div>
                <div class="text-sm font-semibold text-[#171717]">{{ item.value }}</div>
              </div>
              <div class="mt-3 text-sm leading-6 text-[#6a6f6a]">{{ item.label }}</div>
            </div>
          </div>
        </div>

        <div class="relative flex items-center justify-center">
          <div class="absolute left-8 top-10 h-40 w-40 rounded-full bg-[#dff0e2] blur-3xl" />
          <div class="absolute bottom-4 right-8 h-40 w-40 rounded-full bg-[#edf2ec] blur-3xl" />

          <div class="relative w-full max-w-[460px]">
            <div
              class="absolute -left-8 top-6 hidden h-[260px] w-[220px] overflow-hidden rounded-[30px] border border-[#dfe4de] bg-white/95 shadow-[0_20px_50px_rgba(20,20,20,0.08)] lg:block"
            >
              <div class="relative h-full w-full bg-[linear-gradient(180deg,#f8faf8_0%,#eef4ef_100%)] p-5">
                <div class="absolute right-4 top-4 h-14 w-14 rounded-[16px] border border-[#dbe4dc] bg-white" />
                <div
                  class="absolute right-7 top-7 grid h-8 w-8 place-items-center rounded-[10px] bg-[#e8f3ea] text-[#16a34a]"
                >
                  <QrCode :size="16" />
                </div>

                <div class="absolute left-5 top-10 h-16 w-20 rounded-[14px] bg-[#dfe9e0]" />
                <div class="absolute left-16 top-16 h-20 w-24 rounded-[16px] bg-[#e7efe8]" />
                <div class="absolute left-8 top-[118px] h-[2px] w-24 bg-[#d6ddd7]" />
                <div class="absolute left-12 top-[106px] h-10 w-10 rounded-full border-2 border-[#d7dfd9]" />

                <div class="absolute bottom-6 left-5 right-5 rounded-[22px] border border-[#dfe4de] bg-white/90 p-4">
                  <div class="flex items-end gap-3">
                    <div class="relative h-20 w-14">
                      <div class="absolute bottom-0 left-4 h-9 w-6 rounded-t-[10px] bg-[#1f2937]" />
                      <div class="absolute bottom-8 left-2 h-8 w-10 rounded-[12px] bg-[#16a34a]" />
                      <div class="absolute bottom-[58px] left-4 h-5 w-6 rounded-full bg-[#16a34a]" />
                      <div class="absolute bottom-[34px] left-0 h-3 w-6 rotate-[25deg] rounded-full bg-[#16a34a]" />
                      <div class="absolute bottom-[26px] right-0 h-3 w-7 -rotate-[30deg] rounded-full bg-[#16a34a]" />
                    </div>

                    <div class="flex-1">
                      <div class="mb-3 flex items-center gap-2 text-[#16a34a]">
                        <ScanLine :size="16" />
                        <span class="text-xs font-semibold uppercase tracking-[0.16em]">QR scan</span>
                      </div>
                      <div class="h-10 rounded-[14px] border border-dashed border-[#bcd1bf] bg-[#f7fbf8]" />
                      <div class="mt-3 flex items-center gap-2 text-[#5f655f]">
                        <MapPin :size="14" class="text-[#16a34a]" />
                        <span class="text-xs">kontrola polohy pri evidencii</span>
                      </div>
                    </div>
                  </div>

                  <div class="mt-4 flex gap-2">
                    <div class="h-10 w-10 rounded-[12px] bg-[#e8f3ea]" />
                    <div class="h-10 w-10 rounded-[12px] bg-[#eef4ef]" />
                    <div class="h-10 w-10 rounded-[12px] bg-[#e3ebe4]" />
                  </div>
                </div>
              </div>
            </div>

            <div
              class="absolute -right-5 bottom-10 hidden w-[210px] rounded-[26px] border border-[#dfe4de] bg-white/95 p-4 shadow-[0_20px_50px_rgba(20,20,20,0.08)] lg:block"
            >
              <div class="flex items-center gap-3">
                <div class="grid h-11 w-11 place-items-center rounded-[14px] bg-[#eef4ef] text-[#16a34a]">
                  <Package :size="20" />
                </div>
                <div>
                  <div class="text-sm font-semibold">Materiál na stavbe</div>
                  <div class="text-xs text-[#7a7f7a]">boxy, sklad, pohyby</div>
                </div>
              </div>
              <div class="mt-4 grid grid-cols-3 gap-2">
                <div class="h-12 rounded-[14px] bg-[#e8f3ea]" />
                <div class="h-12 rounded-[14px] bg-[#eef4ef]" />
                <div class="h-12 rounded-[14px] bg-[#e3ebe4]" />
              </div>
            </div>

            <div
              class="relative mx-auto w-full max-w-[430px] rounded-[36px] border border-[#dfe4de] bg-[#fbfbfa] p-4 shadow-[0_25px_80px_rgba(20,20,20,0.08)]"
            >
              <div class="mb-4 flex items-center justify-between rounded-[24px] border border-[#e6e9e4] bg-white px-4 py-4">
                <div class="flex items-center gap-3">
                  <div class="grid h-12 w-12 place-items-center rounded-[16px] bg-[#e8f3ea] text-[#16a34a]">
                    <Package :size="22" />
                  </div>
                  <div>
                    <div class="text-sm font-semibold">Sklad pracoviska</div>
                    <div class="text-xs text-[#7b807b]">príjem, výdaj, pohyby</div>
                  </div>
                </div>
                <div class="grid h-10 w-10 place-items-center rounded-[14px] bg-[#eef4ef] text-[#16a34a]">
                  <ArrowRightLeft :size="18" />
                </div>
              </div>

              <div class="rounded-[28px] border border-[#e5e8e3] bg-white p-5">
                <div class="flex items-center justify-between">
                  <div>
                    <div class="text-[13px] font-medium uppercase tracking-[0.16em] text-[#9ba09a]">Dnes</div>
                    <div class="mt-1 text-[28px] font-semibold tracking-[-0.04em]">Nitra Juh - Hala B</div>
                  </div>
                  <div class="rounded-full bg-[#e8f3ea] px-3 py-2 text-sm font-semibold text-[#16a34a]">0.0 h</div>
                </div>

                <div class="mt-5 rounded-[24px] border border-[#e7e9e5] bg-[#fafbfa] p-4">
                  <div class="text-[15px] text-[#707570]">Začiatok smeny</div>
                  <div class="mt-1 text-[40px] font-semibold tracking-[-0.05em]">11:56</div>
                </div>

                <div class="mt-4 space-y-3">
                  <div
                    v-for="row in heroRows"
                    :key="row.label"
                    class="flex items-center justify-between rounded-[20px] border border-[#edf0eb] bg-[#f7f8f6] px-4 py-4 text-[17px] font-medium text-[#353935]"
                  >
                    <div class="flex items-center gap-3">
                      <div class="text-[#16a34a]">
                        <component :is="row.icon" :size="18" />
                      </div>
                      <span>{{ row.label }}</span>
                    </div>
                    <span class="text-[#9aa09a]">→</span>
                  </div>
                </div>

                <div class="mt-5 grid gap-3 sm:grid-cols-2">
                  <button
                    type="button"
                    class="rounded-[18px] border-2 border-[#16a34a] px-4 py-3 text-sm font-semibold text-[#16a34a]"
                  >
                    PRIDAŤ PRÁCU
                  </button>
                  <button
                    type="button"
                    class="rounded-[18px] border-2 border-[#16a34a] px-4 py-3 text-sm font-semibold text-[#16a34a]"
                  >
                    MATERIÁL
                  </button>
                </div>

                <button
                  type="button"
                  class="mt-3 w-full rounded-[18px] bg-[#374151] px-4 py-4 text-base font-semibold text-white"
                >
                  ODCHOD
                </button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="prehlad" class="border-y border-[#e2e5e0] bg-white/70">
        <div class="mx-auto max-w-6xl px-5 py-16 sm:px-6 lg:px-8">
          <div class="max-w-3xl">
            <div class="text-sm font-medium text-[#6a6f6a]">Čo rieši</div>
            <h2 class="mt-2 text-3xl font-semibold tracking-[-0.04em] sm:text-4xl">
              Jedna appka pre to, čo sa na stavbe zapisuje každý deň.
            </h2>
            <p class="mt-4 max-w-2xl text-base leading-7 text-[#5f645f] sm:text-lg sm:leading-8">
              Namiesto rozbitých poznámok, správ a spätného dopĺňania má firma jeden jasný tok:
              QR príchod, záznam práce, materiál, sklad, detail dňa.
            </p>
          </div>

          <div class="mt-10 grid gap-4 md:grid-cols-3">
            <div
              v-for="card in featureCards"
              :key="card.title"
              class="rounded-[28px] border border-[#e1e4df] bg-[#f8f9f7] p-6"
            >
              <div class="grid h-12 w-12 place-items-center rounded-[16px] bg-[#e8f3ea] text-[#16a34a]">
                <component :is="card.icon" :size="22" />
              </div>
              <h3 class="mt-5 text-xl font-semibold tracking-[-0.03em]">{{ card.title }}</h3>
              <p class="mt-3 text-sm leading-7 text-[#616661]">{{ card.text }}</p>
            </div>
          </div>
        </div>
      </section>

      <section id="prehlad-appky" class="mx-auto max-w-[1560px] px-5 py-16 sm:px-6 lg:px-8 lg:py-20">
        <div class="max-w-2xl">
          <div class="text-sm font-medium text-[#6a6f6a]">Ako to vyzerá</div>
          <h2 class="mt-2 text-3xl font-semibold tracking-[-0.04em] sm:text-4xl">
            Navrhnuté pre mobil, nie pre komplikované školenie.
          </h2>
        </div>

        <div class="mt-10 grid justify-items-center gap-8 md:grid-cols-2 2xl:grid-cols-4">
          <div class="h-full w-full max-w-[390px] rounded-[32px] border border-[#dfe4de] bg-white p-5 shadow-sm">
            <div class="mx-auto max-w-[350px] overflow-hidden rounded-[24px] border border-[#e8ebe6] bg-[#f6f7f5] p-4">
              <div class="rounded-[22px] border border-[#e8ebe6] bg-white p-4">
                <div class="text-[13px] font-medium uppercase tracking-[0.16em] text-[#9ba09a]">Domov</div>
                <div class="mt-3 rounded-[18px] bg-[#e8f3ea] px-4 py-3 text-sm font-semibold text-[#16a34a]">
                  Aktuálna smena · 0.0 h
                </div>
                <div class="mt-4 space-y-3">
                  <div class="rounded-[18px] border border-[#ebeeea] bg-[#fafbfa] px-4 py-4 text-sm text-[#474b47]">
                    Začiatok smeny · 11:56
                  </div>
                  <div class="rounded-[18px] border border-[#ebeeea] bg-[#fafbfa] px-4 py-4 text-sm text-[#474b47]">
                    Použitý materiál
                  </div>
                  <div class="rounded-[18px] border border-[#ebeeea] bg-[#fafbfa] px-4 py-4 text-sm text-[#474b47]">
                    Vykonané práce
                  </div>
                </div>
                <button
                  type="button"
                  class="mt-4 w-full rounded-[18px] bg-[#374151] px-4 py-3 text-sm font-semibold text-white"
                >
                  ODCHOD
                </button>
              </div>
            </div>
            <div class="px-2 pb-2 pt-5">
              <div class="flex items-center gap-2 text-lg font-semibold tracking-[-0.03em]">
                <ClipboardList :size="18" class="text-[#16a34a]" />
                Domovská obrazovka
              </div>
              <div class="mt-2 text-sm leading-7 text-[#616661]">
                To najdôležitejšie bez zbytočných blokov a bez dlhého čítania.
              </div>
            </div>
          </div>

          <div class="h-full w-full max-w-[390px] rounded-[32px] border border-[#dfe4de] bg-white p-5 shadow-sm">
            <div class="mx-auto max-w-[350px] overflow-hidden rounded-[24px] border border-[#e8ebe6] bg-[#f6f7f5] p-4">
              <div class="rounded-[22px] border border-[#e8ebe6] bg-white p-4">
                <div class="text-[13px] font-medium uppercase tracking-[0.16em] text-[#9ba09a]">Správa materiálov</div>
                <div class="mt-3 rounded-[18px] border border-[#e3e7e2] bg-[#fafbfa] px-4 py-4 text-sm text-[#6a6f6a]">
                  Hľadať materiál...
                </div>
                <div class="mt-4 flex gap-2 overflow-hidden">
                  <div class="rounded-full bg-[#16a34a] px-4 py-2 text-sm font-semibold text-white">Všetko</div>
                  <div class="rounded-full border border-[#d8ddd8] bg-white px-4 py-2 text-sm text-[#454945]">
                    Elektro
                  </div>
                  <div class="rounded-full border border-[#d8ddd8] bg-white px-4 py-2 text-sm text-[#454945]">
                    Istice
                  </div>
                </div>
                <div class="mt-4 space-y-3">
                  <div v-for="item in materialItems" :key="item" class="rounded-[18px] bg-[#eef2ea] px-4 py-4">
                    <div class="text-base font-semibold tracking-[-0.02em]">{{ item }}</div>
                    <div class="mt-1 text-sm text-[#666b66]">Kategória · Jednotka</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="px-2 pb-2 pt-5">
              <div class="flex items-center gap-2 text-lg font-semibold tracking-[-0.03em]">
                <Package :size="18" class="text-[#16a34a]" />
                Materiál bez rozptyľovania
              </div>
              <div class="mt-2 text-sm leading-7 text-[#616661]">
                Rýchle vyhľadanie, filtrovanie a pridanie do záznamu.
              </div>
            </div>
          </div>

          <div class="h-full w-full max-w-[390px] rounded-[32px] border border-[#dfe4de] bg-white p-5 shadow-sm">
            <div class="mx-auto max-w-[350px] overflow-hidden rounded-[24px] border border-[#e8ebe6] bg-[#f6f7f5] p-4">
              <div class="rounded-[22px] border border-[#e8ebe6] bg-white p-4">
                <div class="text-[13px] font-medium uppercase tracking-[0.16em] text-[#9ba09a]">Sklad</div>
                <div class="mt-3 flex items-center justify-between rounded-[18px] bg-[#eef4ef] px-4 py-4">
                  <div>
                    <div class="text-sm font-semibold text-[#1c1f1c]">Prešov Stavba</div>
                    <div class="mt-1 text-xs text-[#7a7f7a]">Počet položiek: 3</div>
                  </div>
                  <div class="rounded-[14px] bg-[#dff0e2] px-3 py-2 text-sm font-semibold text-[#16a34a]">Pohyby</div>
                </div>
                <div class="mt-4 rounded-[18px] border border-[#e3e7e2] bg-[#fafbfa] px-4 py-4 text-sm text-[#6a6f6a]">
                  Hľadať materiál...
                </div>
                <div class="mt-4 space-y-3">
                  <div
                    v-for="stock in stockItems"
                    :key="stock.item"
                    class="flex items-center justify-between rounded-[18px] border border-[#ebeeea] bg-white px-4 py-4"
                  >
                    <div>
                      <div class="text-sm font-semibold text-[#1f2320]">{{ stock.item }}</div>
                      <div class="mt-1 text-xs text-[#7b807b]">Zmena · 9.4.2026</div>
                    </div>
                    <div :class="['text-base font-semibold', stock.qtyClass]">{{ stock.qty }}</div>
                  </div>
                </div>
                <div class="mt-4 grid grid-cols-2 gap-3">
                  <button
                    type="button"
                    class="rounded-[18px] border border-[#d8ddd8] bg-white px-4 py-3 text-sm font-semibold text-[#1d1f1d]"
                  >
                    Výdaj
                  </button>
                  <button
                    type="button"
                    class="rounded-[18px] bg-[#16a34a] px-4 py-3 text-sm font-semibold text-white"
                  >
                    Príjem
                  </button>
                </div>
              </div>
            </div>
            <div class="px-2 pb-2 pt-5">
              <div class="flex items-center gap-2 text-lg font-semibold tracking-[-0.03em]">
                <Warehouse :size="18" class="text-[#16a34a]" />
                Sklad priamo pri stavbe
              </div>
              <div class="mt-2 text-sm leading-7 text-[#616661]">
                Aktuálny stav, pohyby, príjem a výdaj materiálu bez ďalšieho systému.
              </div>
            </div>
          </div>

          <div class="h-full w-full max-w-[390px] rounded-[32px] border border-[#dfe4de] bg-white p-5 shadow-sm">
            <div class="mx-auto max-w-[350px] overflow-hidden rounded-[24px] border border-[#e8ebe6] bg-[#f6f7f5] p-4">
              <div class="rounded-[22px] border border-[#e8ebe6] bg-white p-4">
                <div class="text-[13px] font-medium uppercase tracking-[0.16em] text-[#9ba09a]">Detail záznamu</div>
                <div class="mt-3 rounded-[18px] bg-[#eef4ef] px-4 py-4 text-sm font-semibold text-[#374151]">
                  Nitra Juh - Hala B · 14.03.2026
                </div>
                <div class="mt-4 rounded-[20px] border border-[#e8ebe6] bg-[#fafbfa] p-4">
                  <div class="text-base font-semibold">Pracovný čas</div>
                  <div class="mt-3 rounded-[16px] bg-white px-4 py-3 text-sm text-[#4a4f4a]">
                    22:08 → 22:10 · 0.0h
                  </div>
                </div>
                <div class="mt-4 space-y-4">
                  <div>
                    <div class="text-base font-semibold">Materiál</div>
                    <div class="mt-1 text-sm text-[#8a8f8a]">Zatiaľ žiadny materiál</div>
                  </div>
                  <div>
                    <div class="text-base font-semibold">Vykonané práce</div>
                    <div class="mt-1 text-sm text-[#8a8f8a]">Zatiaľ žiadne práce</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="px-2 pb-2 pt-5">
              <div class="flex items-center gap-2 text-lg font-semibold tracking-[-0.03em]">
                <Hammer :size="18" class="text-[#16a34a]" />
                Jeden detail, všetko spolu
              </div>
              <div class="mt-2 text-sm leading-7 text-[#616661]">
                Dochádzka, materiál a práce v jednom zázname bez chaosu.
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="border-t border-[#e2e5e0] bg-[#f8faf8]">
        <div class="mx-auto max-w-6xl px-5 py-16 sm:px-6 lg:px-8">
          <div class="grid gap-6 lg:grid-cols-3">
            <div class="rounded-[28px] border border-[#e1e4df] bg-white p-6">
              <div class="text-sm font-medium text-[#6a6f6a]">QR dochádzka</div>
              <h3 class="mt-2 text-2xl font-semibold tracking-[-0.03em]">Presnejší príchod a odchod</h3>
              <p class="mt-3 text-sm leading-7 text-[#616661]">
                Dochádzka sa zapisuje cez QR kód na pracovisku, nie len ručným potvrdením.
              </p>
            </div>
            <div class="rounded-[28px] border border-[#e1e4df] bg-white p-6">
              <div class="text-sm font-medium text-[#6a6f6a]">Poloha pri skene</div>
              <h3 class="mt-2 text-2xl font-semibold tracking-[-0.03em]">Kontrola pri evidencii</h3>
              <p class="mt-3 text-sm leading-7 text-[#616661]">
                Pri skene sa kontroluje poloha pracovníka, takže evidenciu nie je jednoduché obísť na diaľku.
              </p>
            </div>
            <div class="rounded-[28px] border border-[#e1e4df] bg-white p-6">
              <div class="text-sm font-medium text-[#6a6f6a]">Vlastné číselníky</div>
              <h3 class="mt-2 text-2xl font-semibold tracking-[-0.03em]">Firma si nastaví vlastné práce a materiály</h3>
              <p class="mt-3 text-sm leading-7 text-[#616661]">
                Nie si viazaný na pevný zoznam. Každá firma si vie vytvoriť vlastné práce aj vlastné materiály.
              </p>
            </div>
          </div>
        </div>
      </section>

      <section id="vysledok" class="border-t border-[#e2e5e0] bg-white/70">
        <div class="mx-auto max-w-6xl px-5 py-16 sm:px-6 lg:px-8">
          <div class="grid gap-10 lg:grid-cols-[0.95fr_1.05fr] lg:items-center">
            <div>
              <div class="text-sm font-medium text-[#6a6f6a]">Výsledok pre firmu</div>
              <h2 class="mt-2 text-3xl font-semibold tracking-[-0.04em] sm:text-4xl">
                Menej vysvetľovania. Menej hľadania. Viac jasného stavu.
              </h2>
            </div>

            <div class="grid gap-3 sm:grid-cols-2">
              <div
                v-for="item in outcomes"
                :key="item"
                class="rounded-[24px] border border-[#e1e4df] bg-[#f8f9f7] px-5 py-5 text-sm font-medium text-[#2c302d]"
              >
                {{ item }}
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>
