<template>
  <div class="menu-title-row">
    <span class="uppercase">{{$t("menu.boards")}}</span>
    <Tooltip :content="newBoardShortcutString"
             placement="bottom"
             :transfer="true">
      <Icon type="ios-add"
            size="24"
            class="add-icon"
            @click="showNewBoardModal"/>
    </Tooltip>
    <Tooltip :content="findItemsShortcutString"
             class="add-icon-container"
             placement="bottom"
             :transfer="true">
      <Icon type="ios-search"
            size="18"
            class="add-icon"
            @click="showFindItemModal"/>
    </Tooltip>
  </div>
</template>

<script>
  import keyShortcutMixin from './../../keyShortcutStringMixin'

  export default {
    name: 'MenuTitleRow',
    mixins: [keyShortcutMixin],
    computed: {
      newBoardShortcutString () {
        return `${this.$t("menu.add_new_board")} - ${this.shortcutString('addNewBoard')}`
      },
      findItemsShortcutString () {
        return `${this.$t("menu.find_item")} - ${this.shortcutString('showFindItem')}`
      }
    },
    methods: {
      showNewBoardModal () {
        this.$store.dispatch('showNewBoardModal')
      },
      showFindItemModal () {
        this.$store.dispatch('showFindItemModal')
      }
    }
  }
</script>

<style scoped>
  .menu-title-row {
    user-select: none;
    font-size: 18px;
    color: #fff;
    font-weight: bold;
    margin: 0 0 16px 0;
  }

  .add-icon-container {
    float: right;
  }

  .add-icon {
    color: #cecece;
    padding-bottom: 2px;
    cursor: pointer;
    transition: all .3s;
  }

  .add-icon:hover {
    color: #fff;
    text-shadow: 0 0 5px #D2DBDE;
  }

</style>
