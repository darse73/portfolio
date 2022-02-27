<template>
  <div class="wave">
    <canvas ref="myCanvas" :width="size.w" :height="size.h"></canvas>
  </div>
</template>

<script lang="ts">
import { ref, reactive, defineComponent, onMounted } from "vue";

export default defineComponent({
  setup() {
    const unit = 100,
      info = { seconds: 0, t: 0 };
    let myCanvas: any = ref(null);
    let size: any = reactive({
      w: document.documentElement.clientWidth, //Canvasのwidthをウィンドウの幅に合わせる
      h: 250, //波の高さ
    });

    onMounted(() => {
      init();
      changeWidth();
      window.addEventListener("resize", changeWidth);
    });

    const changeWidth = () => {
      size.w = document.documentElement.clientWidth;
    };

    const init = () => {
      // 各キャンバスの初期化
      myCanvas.value.contextCache = myCanvas.value.getContext("2d");
      // 共通の更新処理呼び出し
      update();
    };

    const update = () => {
      // 各キャンバスの描画
      draw(myCanvas, ["##99CCFF", "#99CCFF", "#99CCFF"]);

      // 共通の描画情報の更新
      info.seconds = info.seconds + 0.01;
      info.t = info.seconds * Math.PI;
      // 自身の再起呼び出し
      setTimeout(update, 35);
    };

    /**
     * Draw animation function.
     *
     * This function draws one frame of the animation, waits 20ms, and then calls
     * itself again.
     */

    const draw = (canvas: any, color: any) => {
      // 対象のcanvasのコンテキストを取得
      let context = canvas.value.contextCache;
      // キャンバスの描画をクリア
      context.clearRect(0, 0, size.w, size.h);

      //波の重なりを描画 drawWave(canvas, color[数字（波の数を0から数えて指定）], 透過, 波の幅のzoom,波の開始位置の遅れ )
      drawWave(canvas, color[0], 0.5, 3, 0);
      drawWave(canvas, color[1], 0.4, 2, 250);
      drawWave(canvas, color[2], 0.2, 1.6, 100);
    };

    /**
     * 波を描画
     * drawWave(色, 不透明度, 波の幅のzoom, 波の開始位置の遅れ)
     */

    const drawWave = (canvas: any, color: any, alpha: any, zoom: any, delay: any) => {
      const context = canvas.value.contextCache;
      context.fillStyle = color; //塗りの色
      context.globalAlpha = alpha;
      context.beginPath(); //パスの開始
      drawSine(canvas, info.t / 0.5, zoom, delay);
      context.lineTo(size.w + 10, size.h); //パスをCanvasの右下へ
      context.lineTo(0, size.h); //パスをCanvasの左下へ
      context.closePath(); //パスを閉じる
      context.fill(); //塗りつぶす
    };

    /**
     * Function to draw sine
     *
     * The sine curve is drawn in 10px segments starting at the origin.
     * drawSine(時間, 波の幅のzoom, 波の開始位置の遅れ)
     */

    const drawSine = (canvas: any, t: any, zoom: any, delay: any) => {
      const xAxis = Math.floor(size.h / 2);
      const yAxis = 0;
      const context = canvas.value.contextCache;
      // Set the initial x and y, starting at 0,0 and translating to the origin on
      // the canvas.
      let x = t; //時間を横の位置とする
      let y = Math.sin(x) / zoom;
      context.moveTo(yAxis, unit * y + xAxis); //スタート位置にパスを置く

      // Loop to draw segments (横幅の分、波を描画)
      for (let i = yAxis; i <= size.w + 10; i += 10) {
        x = t + (-yAxis + i) / unit / zoom;
        y = Math.sin(x - delay) / 3;
        context.lineTo(i, unit * y + xAxis);
      }
    };
    return {
      myCanvas,
      size,
    };
  },
});
</script>

<style lang="sass" scoped>
.wave
  height: 25rem
</style>
