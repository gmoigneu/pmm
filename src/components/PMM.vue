<template>
  <div class="pmm">
     <h2 class="text-2xl mb-6 font-bold leading-7 text-gray-900 sm:text-3xl sm:truncate">
      Precision Method
    </h2>
    <div class="container mx-auto mb-4">
      <div class="grid grid-cols-3 gap-1">
      <div class="px-4">
        <p>ISO</p>
        <select class="p-4 w-full bg-gray-100" v-model="iso" @change="showSettings()">
          <option v-for="(isoValue, index) in isos" :key="index" :value="isoValue">{{ isoValue}}</option>
        </select>
      </div>
      <div class="px-4">
        <p>EV</p>
        <select class="p-4 w-full bg-gray-100" v-model="ev" @change="showSettings()">
        <option v-for="evValue in 29" :key="evValue" :value="evValue - 7">{{ evValue - 7}}</option>
      </select>
      </div>
      <div class="px-4">
        <p>Shift</p>
        <select class="p-4 w-full bg-gray-100" v-model="shift" @change="showSettings()">
        <option v-for="shiftValue in 9" :key="shiftValue" :value="shiftValue - 5">{{ shiftValue - 5}}</option>
      </select>
      </div>
      </div>
    </div>

    <Settings :settings="settings" />
  </div>
</template>

<script>
import Settings from './Settings.vue'

export default {
  name: "PMM",
  components: {
    Settings,
  },
  data() {
    return {
      iso: 100,
      ev: 0,
      shift: 0,
      isos: [
        100,
        200,
        400,
        800,
        1600,
        3200
      ],
      speeds: [
        '60',
        '30',
        '15',
        '8',
        '4',
        '2',
        '1',
        '1/2',
        '1/4',
        '1/8',
        '1/15',
        '1/30',
        '1/60',
        '1/125',
        '1/250',
        '1/500',
        '1/1000',
        '1/2000',
        '1/4000',
        '1/8000',
      ],
      apertures: [
        '1.0',
        '1.4',
        '2',
        '2.8',
        '4',
        '5.6',
        '8',
        '11',
        '16',
        '22',
      ],
      settings: []
    };
  },
  created: function () {
    this.showSettings()
  },
  methods: {
    showSettings() {
      let isoShift = Math.log2(this.iso / 100);
      let evValue = this.ev + isoShift;
      this.settings = []
      this.apertures.forEach((aperture, index) => {
        let speed = this.speeds[6+evValue-index-this.shift]
        if(speed) {
          this.settings.push({
            speed: speed,
            aperture: aperture
          })
        }
      })
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
