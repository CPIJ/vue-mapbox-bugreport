<template>
  <div style="width: 100vw; height: 100vh">
    <MglMap
      :accessToken="accessToken"
      :center="[0,0]"
      :zoom="12"
      :mapStyle="'mapbox://styles/mapbox/streets-v9'">
        <MglMarker
          :color="color"
          :coordinates="[0,0]"
        >
          <MglPopup>
              <button :style="{color}" @click="changeColor">Change color</button>
          </MglPopup>
        </MglMarker>
    </MglMap>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import { MglMap, MglMarker, MglPopup } from 'vue-mapbox';

@Component({
  components: { MglMap, MglMarker, MglPopup },
})
export default class App extends Vue {
  private readonly accessToken = 'pk.eyJ1IjoiY3BnLWlzIiwiYSI6ImNrM3ByMWU0ejA1dGkzaW8xa3FkNXliZzgifQ.dFGAIiUDnKvrOP3ZFIR7bw'

  private readonly colors = ['green', '#CCC', 'red', 'blue', '#FFF000']

  private currentIndex = 0;

  private color = this.colors[this.currentIndex];

  private changeColor(): void {
    this.currentIndex += 1;
    this.currentIndex = this.currentIndex % this.colors.length;

    this.color = this.colors[this.currentIndex];
  }
}

</script>
