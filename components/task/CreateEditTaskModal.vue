<template>
  <div id="create-edit-task">
    <Modal
      :size-button="sizeButton"
      :type-button="typeButton"
      :class-button="classButton"
      :name-button="nameButton"
      :title-modal="titleModal"
      @clickButton="clickButton"
      @save="save"
    >
      <div slot="content-modal">
        <el-form :model="form">
          <!-- Tên công việc  -->
          <el-form-item label="Tên công việc" :label-width="formLabelWidth">
            <el-input
              v-model="form.name"
              placeholder="Tên công việc"
              autocomplete="off"
            />
          </el-form-item>

          <!-- Mô tả công việc -->
          <el-form-item label="Mô tả công việc" :label-width="formLabelWidth">
            <el-input
              v-model="form.description"
              type="textarea"
              :rows="3"
              placeholder="Mô tả công việc"
            />
          </el-form-item>

          <!-- Ngày bắt đầu -->
          <el-form-item label="Ngày bắt đầu" :label-width="formLabelWidth">
            <el-date-picker
              v-model="form.startDate"
              placeholder="Ngày bắt đầu"
              type="date"
            />
          </el-form-item>

          <!-- Ngày kết thúc -->
          <el-form-item label="Ngày kết thúc" :label-width="formLabelWidth">
            <el-date-picker
              v-model="form.endDate"
              placeholder="Ngày kết thúc"
              type="date"
            />
          </el-form-item>
        </el-form>
      </div>
    </Modal>
  </div>
</template>

<script>
import Modal from '../Modal/Modal'

export default {
  name: 'CreateEditTaskModal',
  components: {
    Modal
  },
  props: {
    // eslint-disable-next-line vue/require-default-prop
    form: {
      type: Object
    },

    nameButton: {
      type: String,
      default: 'Thêm mới'
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
      default: 'Thêm mới'
    }
  },
  data () {
    return {
      formLabelWidth: '120px'
    }
  },
  methods: {
    save () {
      this.$emit('save', this.form)
    },
    clickButton () {
      this.$emit('clickButton')
    }
  }
}
</script>

<style></style>
