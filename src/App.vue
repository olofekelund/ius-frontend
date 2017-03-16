<template>
  <div id="app">
    <InventoryList
      :list="list"
      @addrow="addRow"
      @save="save"
      @delete="deleteRow">
    </InventoryList>
  </div>
</template>

<script>
import InventoryList from './components/InventoryList'

export default {
  name: 'app',
  components: {
    InventoryList
  },

  methods: {
    addRow () {
      this.idCounter++

      var newItem = {
        id: this.idCounter,
        part_nr: '',
        display_name: '',
        manufacturer: '',
        price: ''
      }

      this.list.push(newItem)
    },

    save () {
      // skicka this.list till server och ta emot svar som antingen uppdaterar listan eller
      // ger ett felmeddelande till användaren. (ifall allting går bra så borde listan vi får tillbaka vara likadan som den som skickades)
    },

    deleteRow (index) {
      this.list.splice(index, 1)
    }
  },

  created () {
    this.idCounter = this.list.length
  },

  data () {
    return {
      idCounter: 0,

      list: [
        {
          id: 1,
          part_nr: '6614272-8',
          display_name: 'Mccray',
          manufacturer: 'Egestas A Dui Institute',
          price: '$57.98'
        },
        {
          id: 2,
          part_nr: '32547852-7',
          display_name: 'Guerra',
          manufacturer: 'Sed Pharetra Felis LLP',
          price: '$59.60'
        },
        {
          id: 3,
          part_nr: '45740096-9',
          display_name: 'Mcfarland',
          manufacturer: 'Sed Neque Foundation',
          price: '$62.99'
        },
        {
          id: 4,
          part_nr: '5054940-2',
          display_name: 'Baxter',
          manufacturer: 'Ac Mattis Velit Institute',
          price: '$38.04'
        },
        {
          id: 5,
          part_nr: '27254124-8',
          display_name: 'Deleon',
          manufacturer: 'Integer Vulputate PC',
          price: '$99.94'
        },
        {
          id: 6,
          part_nr: '17958397-6',
          display_name: 'Palmer',
          manufacturer: 'Massa Non Incorporated',
          price: '$66.89'
        },
        {
          id: 7,
          part_nr: '49144112-7',
          display_name: 'Hobbs',
          manufacturer: 'Dictum Proin LLC',
          price: '$8.52'
        },
        {
          id: 8,
          part_nr: '10975454-4',
          display_name: 'Rosa',
          manufacturer: 'Non Sollicitudin Foundation',
          price: '$53.00'
        },
        {
          id: 9,
          part_nr: '12502401-7',
          display_name: 'Hess',
          manufacturer: 'Phasellus Vitae Associates',
          price: '$26.40'
        },
        {
          id: 10,
          part_nr: '50894170-6',
          display_name: 'Robertson',
          manufacturer: 'Pede Nonummy Ltd',
          price: '$65.81'
        }
      ]
    }
  }
}
</script>

<style lang="sass">
#app
  font-family: 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  margin-top: 32px
</style>
