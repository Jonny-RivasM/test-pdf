<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <PrintPdf title="Hola mundo vue"/>
</template>

<script>
import PrintPdf from './components/PrintPdfHtml.vue'
import html2canvas from "html2canvas";
import jspdf from "jspdf";

export default {
  name: 'App',
  components: {
    PrintPdf
  },
}
</script>

<style>

</style>
