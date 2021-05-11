<template>
  <div>
    <section class="mt-5 noselect">
      <div class="container bg-light-grey rounded-corner position-relative">
        <template v-if="displayModal">
          <ModalDialog @hide="closeModal" />
        </template>
        <div class="row py-5" :class="displayModal && 'blur'">
          <div
            class="d-none d-md-block col-md-2 col-lg-3 pl-lg-4 border-right"
            style="position: relative;"
            ref="lineContainer"
          >
            <Sidebar
              v-for="(item, index) in questions"
              :key="index"
              :shortName="item.displayName || item.shortName"
              :index="index"
              :sidebarLength="questions.length"
              @clicked="handleSideBarClick"
              :currentQuestion="currentQuestion"
            />
            <div class="line" ref="line"></div>
          </div>
          <div class="col-12 col-md-10 col-lg-9 px-md-5 my-auto">
            <survey-questions
              :currentQuestion="this.questions[this.currentQuestion]"
              :brands="brands"
              @onAnswerChange="handleUserAnswer"
              :defaultUserAnswer="defaultUserAnswer"
              :currentQuestionNumber="currentQuestion"
            />
            <div
              class="d-flex justify-content-lg-around"
              v-if="
                podiumDevices.length && currentQuestion === questions.length - 1
              "
            >
              <div
                v-for="(item, index) in podiumDevices"
                :key="index"
                class="text-center"
              >
                <div v-html="item.url.amazon" />
                <h6 class="mt-1">{{ item.nome }}</h6>
              </div>
            </div>

            <div class="text-center mt-5">
              <button
                class="btn bg-orange text-light mr-2"
                v-on:click="skipOrBack"
                v-if="currentQuestion !== 0"
              >
                Indietro
              </button>
              <button
                v-if="currentQuestion !== questions.length - 1"
                class="btn bg-red text-light"
                v-on:click="next"
              >
                Avanti
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section>
      <div class="container mt-5">
        <div class="row mx-auto">
          <Adsense
            class="my-4"
            data-ad-client="ca-pub-3502991802426270"
            data-ad-slot="3936517990"
          />
        </div>
        <div class="row">
          <div class="col-12 col-lg-8">
            <h1 class="display-5">
              Vuoi sapere come funziona <br />
              <span class="text-red">il nostro algoritmo?</span>
            </h1>
            <p class="lead">
              Il nostro algoritmo di ricerca si basa su una serie di operazioni
              e calcoli più o meno complessi che individuano il dispositivo
              perfetto per le tue esigenze. <br />Tutto parte dal nostro
              database, dove sono raccolti i dati: decine di variabili e
              informazioni su centinaia di prodotti in commercio. Il database
              viene costantemente aggiornato, in base all’evoluzione dei prezzi,
              i test approfonditi, le recensioni dei clienti, il confronto con i
              modelli in commercio e le caratteristiche dei dispositivi. <br />
              Partendo da questi dati, il sistema li confronta con le tue
              esigenze, mostrandoti solo le soluzioni migliori!
            </p>
          </div>
          <div class="col-12 col-lg-4 my-auto">
            <img src="@/assets/img/AI.svg" />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import ModalDialog from "@/components/ModalDialog";
import Sidebar from "@/components/Sidebar.vue";
import { answer } from "@/assets/js/theOracle";
import SurveyQuestions from "@/components/survey/index.vue";
export default {
  data() {
    return {
      displayModal: false,
      currentQuestion: 0,
      podiumDevices: [],
      userAnswer: this.defaultUserAnswer,
    };
  },
  mounted() {
    this.$refs.line.style.height = `${this.$refs.lineContainer.offsetHeight}px`;
  },
  computed: {
    getCurrentQuestion() {
      return this.questions[this.currentQuestion];
    },
  },
  methods: {
    next() {
      if (this.currentQuestion === this.questions.length - 2) {
        console.log("userAnswer:", this.userAnswer);
        answer(this.userAnswer)
          .then((res) => {
            console.log(res);
            this.podiumDevices = res;
            this.userAnswer = this.defaultUserAnswer; // Reset answer
          })
          .catch((err) => {
            switch (err) {
              case "noDevicesInSelectedPriceRange":
                this.displayModal = true;
                this.currentQuestion = 1;
                this.userAnswer.prezzo = [100, 1500];
                console.log("No devices in range");
                break;

              default:
                break;
            }
          });
      }

      console.log(this.userAnswer);

      if (this.currentQuestion + 1 < this.questions.length) {
        this.currentQuestion++;
      }
    },
    skipOrBack() {
      this.currentQuestion > 0 && this.currentQuestion--;
    },
    handleCheckBox(e) {
      if (e.target.checked) {
        this.userAnswer.brands.push(e.target.id);
      } else {
        this.userAnswer.brands.pop(e.target.id);
      }
    },
    handleSideBarClick(index) {
      index !== this.questions.length - 1 && (this.currentQuestion = index);
    },
    handleUserAnswer(userAnswer) {
      this.userAnswer = { ...this.userAnswer, ...userAnswer };
    },
    closeModal() {
      this.displayModal = false;
    },
  },
  components: {
    Sidebar,
    ModalDialog,
    SurveyQuestions,
  },
  props: ["questions", "brands", "defaultUserAnswer"],
};
</script>

<style scoped>
.shadow {
  -webkit-box-shadow: 50px 50px 42px 0px rgba(0, 0, 0, 0.2);
  -moz-box-shadow: 50px 50px 42px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 50px 50px 42px 0px rgba(0, 0, 0, 0.2);
}
.blur {
  filter: blur(1px);
  -webkit-filter: blur(1px);
}
</style>
