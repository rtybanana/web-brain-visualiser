<template>
  <div class="pt-2">
    <ortho-x class="d-block mx-auto" style="max-height: calc(0.328 * (100vh - 56px - .5rem));" 
             :regions="regionsX" :connections="connections" :region-names="regionNames" 
             :n-neighbours="nNeighbours" :sorted-regions="sortedRegions">
    </ortho-x>
    <ortho-y class="d-block mx-auto" style="max-height: calc(0.328 * (100vh - 56px - .5rem));" 
             :regions="regionsY" :connections="connections" :region-names="regionNames" 
             :n-neighbours="nNeighbours" :sorted-regions="sortedRegions">
    </ortho-y>
    <ortho-z class="d-block mx-auto" style="max-height: calc(0.328 * (100vh - 56px - .5rem));" 
             :regions="regionsZ" :connections="connections" :region-names="regionNames" 
             :n-neighbours="nNeighbours" :sorted-regions="sortedRegions">
    </ortho-z>
  </div>
</template>

<script>
  module.exports = {
    components: {
      'ortho-x': loader('./components/ortho/ortho-x.vue'),
      'ortho-y': loader('./components/ortho/ortho-y.vue'),
      'ortho-z': loader('./components/ortho/ortho-z.vue')
    },
    props: {
      regions: Array,         // n_regions x 3 array describing regions center of mass
      connections: Array,     // n_connections length array of objects: {region1, region2, strength}
      regionNames: Array,     // n_regions length array containing region names
      sortedRegions: Array,   // n_regions length array containing the sort order of the region for highcharts colour matching
      nNeighbours: Map        // n_regions length map describing how many one hop neighbours each region has   
    },
    computed: {
      regionsX() {
        return this.getRegionCoords('x');
      },
      regionsY() {
        return this.getRegionCoords('y');
      },
      regionsZ() {
        return this.getRegionCoords('z');
      }
    },
    methods: {
      getRegionCoords(direction) {
        let dimensions = direction === 'x' ? [1, 2] : direction === 'y' ? [0, 2] : [0, 1];

        return this.regions.reduce((a, e) => {
          a.push([e[dimensions[0]], e[dimensions[1]]]);
          return a;
        }, []);
      }
    }
  };
</script>

<style>

</style>