<template>
  <div class="inventoryList">
    <ul>
      <li class="headings">
        <h4 class="idField">Id.</h4>
        <h4>Name.</h4>
        <h4>Manufacturer.</h4>
        <h4>Part nr.</h4>
        <h4>Price.</h4>
        <div class="deleteColumn"></div>
      </li>

      <li v-for="(item, index) in list">
        <span class="idField">{{ item.id }}</span>
        <div>
          <input id="display_name" type="text" v-model="item.display_name">
        </div>
        <div>
          <input id="manufacturer" type="text" v-model="item.manufacturer">
        </div>
        <div>
          <input id="part_nr" type="text" v-model="item.part_nr">
        </div>
        <div>
          <input id="price" type="text" v-model="item.price">
        </div>
        <a href="#" class="deleteColumn" @click="remove(index)">
          <i class="icon fa fa-remove"></i>
        </a>
      </li>
    </ul>

    <div class="controls">
      <a href="#"
        class="button"
        @click="addrow">

        <i class="icon fa fa-plus"/>
        <span>Add row</span>
      </a>

      <a href="#"
        class="button"
        @click="save">
        <i class="icon fa fa-save"/>
        <span>Save</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'inventoryList',

  props: {
    list: {
      type: Array
    }
  },

  methods: {
    save () {
      this.$emit('save')
    },

    addrow () {
      this.$emit('addrow')
    },

    remove (index) {
      this.$emit('delete', index)
    }
  },

  data () {
    return {
    }
  }
}
</script>

<style lang="sass" scoped>

.inventoryList
  border: 1px solid #aaa
  border-radius: 5px
  box-shadow: 5px 6px 10px -5px rgba(0,0,0,0.4)
  max-width: 800px
  margin: 0 auto
  background: #C5D9E2
  color: #3e3c3c
  font-size: 16px

  ul
    list-style-type: none
    padding: 0
    margin: 0
    border-radius: 3px

  li
    display: flex
    padding: 8px
    justify-content: space-between
    background: #FEFFFE

    .idField
      flex: 0 1 2rem
      align-self: center

    .deleteColumn
      flex: 0 1 2rem
      align-self: center

      .icon
        width: 100%
        height: 100%
        color: #3e3c3c
        transition: color .3s ease

        &:hover
          color: tomato

    &.headings
      border-bottom: 1px solid #aaa
      background: transparent

      > h4
        margin: 8px 0 0 2px

    > *
      flex: 1
      text-align: left

    &:nth-child(even)
      background-color: #e6edef

    input
      border: none
      background: initial
      transition: background .2s ease
      padding: 4px
      width: auto
      border: 1px solid transparent

      &:hover, &:focus
        background: #fff
        border: 1px solid #ccc

  .controls
    border-top: 1px solid #aaa
    padding: 16px
    text-align: right

    .icon
      padding-right: 4px

    .button
      background: #fefffe
      border: 1px solid #aaa
      border-radius: 5px
      padding: .5rem 2rem
      text-transform: uppercase
      text-decoration: none
      font-size: .75rem
      font-weight: 900
      color: #3e3c3c
      transition: background .2s ease

      &:hover
        background: #eee

</style>
