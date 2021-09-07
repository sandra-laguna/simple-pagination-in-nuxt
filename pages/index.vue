<template>
  <div id="heroes">
    <h1 class="my-8 text-center text-green-600 text-6xl font-bold">Simple pagination in Nuxt.js</h1>
    <table class="max-w-5xl mx-auto table-auto">
      <thead class="justify-between">
        <tr class="bg-green-600">
          <td class="px-16 py-2">
            <span class="text-gray-100 font-semibold">Hero Name</span>
          </td>
          <td class="px-16 py-2">
            <span class="text-gray-100 font-semibold">Universe</span>
          </td>
        </tr>
      </thead>
      <tbody class="bg-gray-200">
        <tr v-for="(hero, i) in heroes" :key="i" v-show="setPaginate(i)" class="bg-white border-b-2 border-gray-200">
          <td class="text-center ml-2">{{ hero.name }}</td>
          <td class="text-center ml-2">{{ hero.universe }}</td>
        </tr>
      </tbody>
    </table>
    <div id="pagination" class="flex justify-center my-4">
      <a href="#" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-100 relative inline-flex items-center px-4 py-2 border text-sm font-medium" v-for="(page_index, i) in paginate_total" :key="i" @click.prevent="updateCurrent(i + 1)">
      {{ i + 1 }}
      </a>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Simple pagination in Nuxt.js",
      link: [{ rel: "canonical", hid: "canonical", href: `${this.$config.baseUrl}/` }]
    };
  },
    created() {
     this.paginate_total = this.heroes.length/this.paginate;
   },
   data: () => ({
      current: 1,
      heroes: [
        { name: 'Wolverine', universe: 'Marvel'},
        { name: 'Batman', universe: 'DC' },
        { name: 'Beast', universe: 'Marvel'},
        { name: 'Superman', universe: 'DC' },
        { name: 'Wonder Woman', universe: 'DC' },
        { name: 'Iceman', universe: 'Marvel'},
        { name: 'Black Panther', universe: 'Marvel'},
        { name: 'Beast Boy', universe: 'DC' },
        { name: 'Captain America', universe: 'Marvel'},
        { name: 'Hawkgirl', universe: 'DC' },
        { name: 'Cyclops', universe: 'Marvel'},
        { name: 'Green Lantern', universe: 'DC' },
        { name: 'Thor', universe: 'Marvel'},
        { name: 'Flash', universe: 'DC' },
        { name: 'Spider-man', universe: 'Marvel'},
        { name: 'Martian Manhunter', universe: 'DC' },
        { name: 'Nightwing', universe: 'DC' },
        { name: 'Raven', universe: 'DC' },
        { name: 'Hulk', universe: 'Marvel'},
        { name: 'Shehulk', universe: 'Marvel'}
     ],
     paginate: 5,
     paginate_total: 0,
     status_filter: ''
   }),
   methods: {
     setPaginate: function (i) {
       if (this.current == 1) {
         return i < this.paginate;
       }
       else {
         return (i >= (this.paginate * (this.current - 1)) && i < (this.current * this.paginate));
       }
     },
     updateCurrent: function (i) {
       this.current = i;
     }
   }
};
</script>
