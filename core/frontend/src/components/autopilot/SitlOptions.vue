<template>
  <div class="sitl-options pa-2">
    <!-- Simple placeholder for SITL options. Expand with real controls as needed. -->
    <v-checkbox
      v-model="isEnabled"
      label="Enable SITL option"
      hide-details
    />
    
    <div v-if="isEnabled" class="mt-2">
      <div id="sitl-options-container">
        <FlagOptionPair
          v-for="(p, index) in pairs"
          :key="index"
          ref="pairs"
        />
      </div>
      <v-btn @click="addPair" color="primary">Add Flag</v-btn>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import FlagOptionPair from './FlagOptionPair.vue';

export default Vue.extend({
  name: 'SitlOptions',
  data () {
    return {
      isEnabled: false,
      // keep a simple array to drive dynamic FlagOptionPair children
      pairs: [ { flag: '', value: '' } ],
    }
  },
  components: {
    FlagOptionPair,
  },
  methods: {
    addPair: function(event: Event) {
      // push a new placeholder into the pairs array so Vue will create
      // another FlagOptionPair via the v-for in the template
      (this as any).pairs.push({ flag: '', value: '' });
    },
    getData: function(event: Event) {
      // This method can be called by the parent component to retrieve all flag/value pairs
      let refs: any = (this as any).$refs.pairs || [];
      return refs.map((r: any) => r.getData());
    },
  },
})
</script>

<style scoped>
.sitl-options {
  min-height: 40px;
}
</style>
