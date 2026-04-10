<template>
  <NavBar background="dark" text="white" :overlay="false" :sticky="true" />

  <div class="q-pa-xl q-mt-xl text-body1">
    <span class="text-h3 block">Impressum</span>
    Eigentümer, Herausgeber und für den Inhalt dieser Website verantwortlich:
    <br />
    <br />
    <span class="text-h6 block">Ordination Dr. Isabelle Olivia</span>
    Salinenplatz 2A/1<br />
    4820, Bad Ischl<br />
    Tel. +43 6132 28200 <br />
    Mail office@dentolivia.at <br />
    <br />
    Unternehmensgegenstand: Zahnarztpraxis <br />
    Mitglied bei der Zahnärztekammer, VPNR 461184<br />
    Zuständige Behörde: Bezirksgericht Bad Ischl<br />
    <br />

    <span class="text-h6 block">Bankverbindung</span>
    Sparkasse Salzkammergut<br />
    BIC: SKBIAT21XXX<br />
    IBAN: AT36 2031 4055 0006 9124 <br />
    Lautend auf Dr. Isabelle Olivia <br />
    <br />

    <span class="text-h6 block">Aufgabe der Website:</span>
    Die Ordination Dr. Isabelle Olivia informiert auf dieser Website umfassend und detailliert über Produkte,
    Dienstleistungen, deren Auftragsabwicklung und Lieferbedingungen im Gesundheitswesen. Durch
    diese Präsentation erfüllt die Ordination Dr. Isabelle Olivia in vollem Umfang die Informationspflicht
    nach § 5 Abs. 1 ECG (E-Commerce-Gesetz). Sollten Sie über diese Informationen hinaus weitere
    Daten benötigen, stehen wir Ihnen gerne zur Verfügung.
    <br />
    <br />

    <span class="text-h6 block">Texte:</span>
    Die Texte der Internetpräsentation sind geistiges Eigentum der Ordination Dr. Isabelle Olivia und sind
    somit nach § 2 Abs. 3 des Urheberrechtsgesetzes urheberrechtlich geschützt.
    <br />
    <br />

    <span class="text-h6 block">Bildmaterial:</span>
    Das Bildmaterial (Fotos, Grafiken, Illustrationen, . . .) sind Eigentum der Ordination Dr.
    Isabelle Olivia oder wurden der Ordination Dr. Isabelle Olivia von den jeweiligen Eigentümern für diesen Zweck
    (Darstellung im Rahmen der Website) zur Verfügung gestellt und sind nach § 3 Abs. 1 und 2 des
    Urheberrechtsgesetzes geschützt.
    <br />
    <br />

    <span class="text-h6 block">Haftungsausschluss, Links zu externen Inhalten:</span>
    Auf dieser Website finden Sie auch Links zu anderen Internetpräsentationen. Die Ordination Dr.
    Isabelle Olivia übernimmt keinerlei Verantwortung und Haftung für dort dargestellte Inhalte und dort
    vorhandenen Links zu weiteren Präsentationen da keinerlei Einfluss auf deren Inhalte genommen
    werden kann. Sollten wider Erwarten nicht passende Inhalte dargestellt werden oder Links nicht
    mehr aktuell sein, bitten wir Sie uns umgehend zu informieren.
    <br />
    <br />

    <span class="text-h6 block">Branding, Kreation und Webdesign:</span>
    Konzept, Design und Umsetzung von .BAT Infotainment
  </div>

  <Footer />
</template>

<script setup lang="ts">
import { onMounted } from 'vue'

import NavBar from '@/components/NavBar.vue'
import Footer from '@/components/FooterComponent.vue'

onMounted(() => {
  window.scrollTo(0, 0)
})
</script>
