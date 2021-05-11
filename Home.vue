<template>
  <div class="home">
    <div class="bg-dark-custom">
      <div class="container">
        <div class="row pt-lg-3">
          <div class="col-12 col-md-7 col-lg-7 my-auto">
            <h1 class="text-white display-3 home-title-bold">
              Scegli il tuo nuovo
              <br />
              <span class="text-orange d-inline-block">{{ device }}</span>
            </h1>
            <p class="text-light lead">
              Acquista il dispositivo giusto per le tue esigenze,
              <br />
              scorri in basso per saperne di più!
            </p>
          </div>
          <div
            class="col-12 col-md-5 col-lg-5 home-img-wrapper mt-3 mt-lg-0 mb-3 mb-lg-0"
          >
            <img
              class="home-img d-lg-none img-fluid"
              src="@/assets/img/computer.png"
            />
            <img
              class="home-img d-none d-lg-block img-fluid"
              src="@/assets/img/md-computer.png"
            />
          </div>
        </div>
      </div>
    </div>
    <img
      style="margin-top: -1px; z-index: 1;"
      src="@/assets/img/home-background.svg"
    />

    <section>
      <div class="container">
        <div class="row">
          <h1 class="text-center display-4" style="font-weight: 800">
            <span class="text-red">Scopri</span> i nostri servizi
          </h1>
          <img
            class="mt-5"
            src="@/assets/img/scroll.svg"
            width="50"
            height="70"
          />
        </div>
      </div>
    </section>
    <HomeSection
      title="Trova il device <br> <span class='text-red'>che fa per te"
      description="Grazie al nostro ottimizzato algoritmo sempre aggiornato ti aiuteremo gratuitamente a trovare il miglior device che si adatta alle tue esigenze. Attraverso delle semplici domande, ti offriremo il prodotto migliore sotto ogni aspetto. Riceverai inoltre il link più conveniente e affidabile certificato dagli sviluppatori, con cui potrai facilmente acquistare il prodotto!"
      align="left"
    >
      <img src="@/assets/img/device.svg" class="img-fluid" />
      <template v-slot:button>
        <router-link to="/smartphone" tag="button" class="btn btn-primary"
          >Smartphone</router-link
        >
        <router-link to="/tablet" tag="button" class="btn btn-primary ml-2"
          >Tablet</router-link
        >
        <router-link to="/watch" tag="button" class="btn btn-primary ml-2"
          >Watch</router-link
        >
      </template>
    </HomeSection>
    <div class="container">
      <div class="row mx-auto">
        <Adsense
          class="mt-4"
          data-ad-client="ca-pub-3502991802426270"
          data-ad-slot="3936517990"
        />
      </div>
    </div>
    <HomeSection
      title="Ottieni una <br> <span class='text-red'>consulenza privata"
      description="Grazie ai creatori del sito potrai richiedere una consulenza personalizzata aggiuntiva via  mail o attivando una LIVE CHAT con noi in cui ti offriremo una consulenza ancora più specifica, risolveremo i tuoi dubbi e perplessità oltre a seguirti nel trovare i migliori annunci, affidabili e convenienti allo stesso tempo, anche di prodotti ricondizionati!"
      align="right"
    >
      <img class="img-fluid" src="@/assets/img/assistenza.png" />
      <template v-slot:button>
        <router-link class="btn btn-primary" to="/consulenza">
          Prenota ora
        </router-link>
      </template>
    </HomeSection>
    <div class="container">
      <div class="row mx-auto">
        <Adsense
          class="mt-4"
          data-ad-client="ca-pub-3502991802426270"
          data-ad-slot="3936517990"
        />
      </div>
    </div>
    <HomeSection
      title="Visita il nostro <br> <span class='text-red'>Store online!"
      description="Acquista comodamente da casa tua e ricevi il tuo ordine in poco giorni. Consulta il nostro catalogo, troverai ogni giorno nuovi prodotti e collezioni, e iscriviti alla newsletter per ricevere subito promozioni personalizzate e rimanere sempre aggiornato!"
      align="left"
    >
      <img class="img-fluid" src="@/assets/img/shop.png" />
      <template v-slot:button>
        <a class="btn btn-primary" href="https://shop.elping.it">
          Visita ora
        </a>
      </template>
    </HomeSection>
    <div class="container">
      <div class="row mx-auto">
        <Adsense
          class="mt-4"
          data-ad-client="ca-pub-3502991802426270"
          data-ad-slot="3936517990"
        />
      </div>
    </div>
    <HomeSection
      title="Consulta il nostro <br> <span class='text-red'>canale offerte</span>"
      description="Iscriviti al nostro canale telegram per ottenere ogni giorno nuove offerte e promozioni di tutti gli store online più conosciuti al mondo. Riceverai le migliori promo direttamente sul tuo smartphone, in modo completamente gratuito! Inoltre potrai essere il fortunato vincitore di buoni regalo per il nostro store"
      align="right"
    >
      <img src="@/assets/img/domotica.svg" />
      <template v-slot:button>
        <a class="btn btn-primary" href="https://t.me/offertelping">
          Iscriviti ora
        </a>
      </template>
    </HomeSection>
    <div class="container">
      <div class="row mx-auto">
        <Adsense
          class="mt-4"
          data-ad-client="ca-pub-3502991802426270"
          data-ad-slot="3936517990"
        />
      </div>
    </div>
    <HomeSection
      title="Entra a far parte della <br> <span class='text-red'>nostra community!"
      description="Scrivici cosa ne pensi della nostra piattaforma e in cosa possiamo migliorare. Clicca qui per rispondere a poche domande che ci aiuteranno a perfezionare l’esperienza dell’utente su elPinG!"
      align="left"
    >
      <img src="@/assets/img/teamwork.svg" />
      <template v-slot:button>
        <router-link class="btn btn-primary" to="sondaggio">
          Partecipa al sondaggio
        </router-link>
      </template>
    </HomeSection>
  </div>
</template>

<script>
import HomeSection from "@/components/HomeSection.vue";
import router from "@/router";
// @ is an alias to /src
export default {
  name: "Home",
  data() {
    return {
      devices: ["watch", "tablet", "smartphone"],
      device: "smartphone",
    };
  },
  created() {
    var remainingCharacters = [];
    var add = false;
    var typeInterval = null;
    const typeDelete = () => {
      let text = this.device.split("");
      if (add) {
        text.push(remainingCharacters[0]);
        remainingCharacters.shift();
        if (!remainingCharacters.length) {
          clearInterval(typeInterval);
          setTimeout(
            () => (typeInterval = setInterval(() => typeDelete(), 100)),
            2500
          );
          add = false;
        }
      } else {
        if (text.length === 1) {
          add = true;
          let word = this.devices[0];
          remainingCharacters = word.split("");
          this.devices.shift(word);
          this.devices.push(word);
        }
        text.pop();
      }
      this.device = text.join("");
    };
    setTimeout(
      () => (typeInterval = setInterval(() => typeDelete(), 100)),
      2000
    );
  },
  methods: {
    goShartphone() {
      router.push({ name: "Smartphone" });
    },
  },
  components: {
    HomeSection,
  },
};
</script>

<style scoped lang="scss">
.home-img-wrapper {
  position: relative;
  /*min-height: calc(100vw * 0.25);*/
}
@media (min-width: 992px) {
  .home-img {
    position: absolute;
  }
}
@media (min-width: 1400px) {
}
</style>
