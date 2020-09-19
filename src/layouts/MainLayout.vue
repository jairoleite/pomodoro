<template>
  <div class="layout-pomodoro" :style="'background-color:'+backgroundColor+'!important'">
    <div class="container">
      <header>
        <div class="logo">
          <q-icon name="check_circle" size="28px" color="white" />
          <span>Pomodoro</span>
        </div>
        <div class="actions">
          <q-btn
            outline
            size="12px"
            class="q-mr-sm"
            icon="insert_chart"
            style="color: white;"
            label="Report"
          />
          <q-btn
            outline
            size="12px"
            class="q-mr-sm"
            icon="settings"
            style="color: white;"
            label="Setting"
          />
          <q-btn outline size="12px" icon="perm_identity" style="color: white;" label="Login" />
        </div>
      </header>

      <q-linear-progress :value="progress" color="white" class="q-mt-sm" />

      <div class="main">
        <div class="block-central">
          <div class="top-buttons">
            <span
              :class="selectedTime == 'vinte' ? 'top-buttons-selected-1500' : ''"
              @click="clickSelectCount(1500)"
            >Pomodoro</span>
            <span
              :class="selectedTime == 'cinco' ? 'top-buttons-selected-300' : ''"
              @click="clickSelectCount(300)"
            >Short Break</span>
            <span
              :class="selectedTime == 'quinze' ? 'top-buttons-selected-900' : ''"
              @click="clickSelectCount(900)"
            >Long Break</span>
          </div>

          <div class="display">
            <span>{{display}}</span>
          </div>

          <button v-if="!start" @click="clickStart">
            <span :style="'color:'+backgroundColor+'!important'">START</span>
          </button>
          <button v-else @click="clickStop" class="btn-pause">
            <span :style="'color:'+backgroundColor+'!important'">STOP</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// we import all of `date`
import { date } from "quasar";

export default {
  name: "Pomodoro",
  data() {
    return {
      start: false,
      selectedDisplay: 1500,
      display: "25:00",
      selectedTime: "vinte",
      countTime: null,
      backgroundColor: "#f05a56",
      progress: 0.0,
      total: 1500,
    };
  },
  methods: {
    clickStart() {
      this.countdown();
      this.start = true;
    },
    clickStop() {
      this.start = false;
    },

    clickSelectCount(number) {
      this.selectedDisplay = number;
      this.total = number;
      //mostra na tela a contagem
      this.display =
        number == 1500 ? "25:00" : number == 300 ? "05:00" : "15:00";
      //menu selecionado
      this.selectedTime =
        number == 1500 ? "vinte" : number == 300 ? "cinco" : "quinze";
      //cor de fundo
      this.backgroundColor =
        number == 1500 ? "#f05a56" : number == 300 ? "#4ca6a9" : "#498fc1";

      //parar contagem
      if (this.countTime) {
        clearInterval(this.countTime);
      }

      //estado normal de start
      this.start = false;
    },

    countdown() {
      //diminui o primeiro segundo..
      if (
        this.display == "25:00" ||
        this.display == "05:00" ||
        this.display == "15:00"
      ) {
        this.selectedDisplay--;
      }

      this.countTime = setInterval(() => {
        //se pausar mata o intervalo
        if (!this.start) {
          clearInterval(this.countTime);
          return;
        }

        let min = parseInt(this.selectedDisplay / 60);
        let seg = this.selectedDisplay % 60;

        if (min < 10) {
          min = "0" + min;
          min = min.substr(0, 2);
        }

        if (seg <= 9) {
          seg = "0" + seg;
        }

        this.display = min + ":" + seg;
        this.selectedDisplay--;

        //se estiver zerado para a contagem
        if (this.display == "00:00") {
          clearInterval(this.countTime);
        }

        let percent = ((this.total - this.selectedDisplay) * 100) / this.total;
        this.progress = parseFloat(`0.${"" + String(percent).split(".")[0]}`);
        // console.log(String(percent).split(".")[0]);
        console.log(percent.toFixed());
      }, 1000);
    },
  },
};
</script>

<style src="./style.css"></style>
