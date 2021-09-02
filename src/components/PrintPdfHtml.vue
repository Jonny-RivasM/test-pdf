<template>

  <h1>{{ title }}</h1>
  <label for="">¿Te gustan los animales?</label>
  <input type="radio" id="uno" :value="true" v-model="selected.exp">
  <label for="uno">Si</label>
  <br>
  <input type="radio" id="Dos" :value="false" v-model="selected.exp">
  <label for="Dos">No</label>
  <br>
  <div v-if="selected.exp">
    <label for="">Tienes perro</label>
    <input type="radio" id="tres" :value="true" v-model="selected1.exp">
    <label for="tres">Si</label>
    <input type="radio" id="cuatro" :value="false" v-model="selected1.exp">
    <label for="tres">No</label>
  </div>
  <span>Valor total: {{ addAmount }}</span>

  <button @click="makePDF">Download PDF</button>

</template>

<script>

import html2canvas from "html2canvas";
import jspdf from "jspdf";

export default {
  name: "PrintPdfHtml",
  props: {
  },
  data: function (){
    return {
      title: 'String',
      selected: {
        exp: null,
      },
      selected1: {
        exp: null,
      },
      count: 0,
    }
  },
  computed: {
      addAmount: function () {
        this.count = 0;
        if (this.selected.exp) {
          this.count += 10;
          if (this.selected1.exp) {
            this.count += 10;
          } else if (!this.selected1.exp) {
            this.count += 5;
          }
        } else if (!this.selected.exp) {
          this.count += 5;
        }
        return this.count;
      },
  },
  methods: {
    makePDF() {
      window.html2canvas = html2canvas;
      var doc = new jspdf("p","pt","a4");
      doc.html(document.querySelector("#app"), {
        callback: function (pdf) {
          pdf.save("mypdf.pdf");
        }
      })

    }
  },
}
</script>

<style scoped>

</style>
