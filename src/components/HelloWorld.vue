<template lang="pug">
  canvas(ref="draws" width='500' height='1000')
</template>

<script>

export default {
  name: 'HelloWorld',
  data() {
    return {
      presetLine: [{ type: 'v', site: 200 }]
    }
  },
  components: {},
  mounted() {
    let colors = ['#f00', '#0f0', '#00f', '#0ff'];

    let canvas = this.$refs.draws;
    let gr = canvas.getContext("2d");

    let y0 = 0;
    let height = canvas.height;
    let stepY = Math.round(height / 10);
    console.log(stepY)
    gr.beginPath();
//Вертикальная линия
    gr.moveTo(40, y0);
    gr.lineTo(40, height + y0);

    for (let i = y0; i < height + 1; i += stepY) {
      gr.moveTo(40, height - i);
      gr.lineTo(0, height - i);

      gr.fillText(i, 0, height-i+10);
    }

    gr.lineWidth = 2;
    gr.stroke();
    gr.closePath();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
