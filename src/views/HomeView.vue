<template>
  <div class="home">
    <div class="row">
      <div class="col-2">
        <select-view v-model="cityIdx" :options="cities"></select-view>
        <!-- <select class="form-select" aria-label="Default select example">
          <option selected disabled>請選擇縣市</option>
          <option v-for="item in cities" :key="item" :value="cities">{{item}}</option>
        </select> -->
      </div>
      <div class="col-2">
        <select-view v-model="areaIdx" :options="areas"></select-view>
      </div>
      {{address}}
    </div>
  </div>
</template>

<script>
import twCities from '@/assets/TwCities.json'
import SelectView from '@/components/SelectView'
export default {
  components: {
    SelectView
  },
  data () {
    return {
      cityIdx: 0,
      areaIdx: 0
    }
  },
  computed: {
    cities () {
      return twCities.map(item => item.name)
    },
    selectedCity () {
      return twCities[this.cityIdx]
    },
    areas () {
      return this.selectedCity.districts.map(item => item.name)
    },
    address () {
      const city = this.selectedCity.name
      const area = this.selectedCity.districts[this.areaIdx].name
      return `${city}${area}`
    }
  },
  watch: {
    selectedCity () {
      this.areaIdx = 0
    }
  }
}
</script>
