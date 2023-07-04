<template>
  <div>
    <h1>Sistem Widget</h1>
    <div id="widgets">
      <WidgetLokasi />
      <WidgetStopwatch />
      <WidgetFoto />
    </div>
  </div>
</template>

<script>
import WidgetLokasi from "./components/Widgetgame.vue";
import WidgetStopwatch from "./components/WidgetStopwatch.vue";
import WidgetFoto from "./components/WidgetFoto.vue";

export default {
  name: "App",
  components: {
    WidgetLokasi,
    WidgetStopwatch,
    WidgetFoto,
  },
};
</script>

<style>
#widgets {
  display: flex;
  justify-content: space-around;
  margin-top: 50px;
}
</style>
