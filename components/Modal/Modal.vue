<template>
  <div id="modal">
    <el-button
      :class="classButton"
      :size="sizeButton"
      :type="typeButton"
      @click="clickButton"
    >
      {{ nameButton }}
    </el-button>
    <el-dialog :title="titleModal" :visible.sync="dialogFormVisible">
      <slot name="content-modal" />

      <span slot="footer" class="dialog-footer">
        <!-- Button close modal -->
        <el-button size="small" @click="dialogFormVisible = false">
          {{ nameCloseButton }}
        </el-button>

        <!-- Button save -->
        <el-button size="small" type="primary" @click="save">
          {{ nameSaveButton }}
        </el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    nameButton: {
      type: String,
      default: ''
    },
    typeButton: {
      type: String,
      default: ''
    },
    sizeButton: {
      type: String,
      default: ''
    },
    classButton: {
      type: String,
      default: ''
    },
    titleModal: {
      type: String,
      default: ''
    },
    nameCloseButton: {
      type: String,
      default: 'Đóng'
    },
    nameSaveButton: {
      type: String,
      default: 'Lưu'
    }
  },
  data () {
    return {
      dialogFormVisible: false
    }
  },

  methods: {
    save () {
      this.dialogFormVisible = false
      this.$emit('save')
    },
    clickButton () {
      this.dialogFormVisible = true
      this.$emit('clickButton')
    }
  }
}
</script>

<style>
.pull-right {
  position: absolute;
  right: 0px;
}
#dialog {
  text-align: left !important;
}
</style>
