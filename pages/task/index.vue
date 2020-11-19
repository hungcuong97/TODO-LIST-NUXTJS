<template>
  <div id="task">
    <h1>Quản lý công việc</h1>
    <el-row>
      <!-- Input tìm kiếm dữ liệu bảng công việc -->
      <el-col :span="4">
        <el-input
          v-model="search"
          class="input-search"
          size="small"
          placeholder="Nhập từ tìm kiếm"
        />
      </el-col>

      <!-- Button thêm công việc -->
      <el-col :offset="14" :span="6">
        <CreateEditTaskModal
          size-button="small"
          class-button="pull-right"
          name-button="Thêm mới công việc"
          title-modal="Thêm mới công việc"
          type-button="success"
          :form="addTask"
          @save="handleAddTask"
        />
      </el-col>
    </el-row>

    <el-table
      :data="
        tableData.filter(
          (data) =>
            !search ||
            data.name.toLowerCase().includes(search.toLowerCase()) ||
            data.description.toLowerCase().includes(search.toLowerCase()) ||
            data.startDate.toLowerCase().includes(search.toLowerCase()) ||
            data.endDate.toLowerCase().includes(search.toLowerCase())
        )
      "
      style="width: 100%"
    >
      <el-table-column label="Tên công việc" prop="name" />
      <el-table-column label="Mô tả công việc" prop="description" />
      <el-table-column label="Ngày bắt đầu" prop="startDate" />
      <el-table-column label="Ngày kết thúc" prop="endDate" />
      <el-table-column label="Hành động">
        <template slot-scope="scope" class="inline-flex">
          <!-- Chỉnh sửa công việc -->
          <CreateEditTaskModal
            size-button="mini"
            name-button="Edit"
            title-modal="Chỉnh sửa công việc"
            :form="editTask"
            @save="handleEditTask"
            @clickButton="clickEdit(scope.$index, scope.row)"
          />

          <!-- Xóa công việc -->
          <el-button
            id="delete"
            size="mini"
            type="danger"
            @click="clickDelete(scope.$index)"
          >
            Delete
          </el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
// import { formatDate } from '../../helper/formatDatePicker'
import CreateEditTaskModal from '../../components/task/CreateEditTaskModal.vue'

export default {
  name: 'Task',
  components: {
    CreateEditTaskModal
  },
  data () {
    return {
      sizeButtonAddTask: 'min',

      addTask: {
        name: '',
        description: '',
        startDate: '',
        endDate: ''
      },

      rowEdit: '',
      editTask: {
        name: '',
        description: '',
        startDate: '',
        endDate: ''
      },

      tableData: [
        {
          name: 'Công việc 1',
          description: 'Miêu tả công việc 1',
          startDate: '2020-11-11',
          endDate: '2020-11-30'
        },
        {
          name: 'Công việc 2',
          description: 'Miêu tả công việc 2',
          startDate: '2020-10-12',
          endDate: '2020-11-25'
        },
        {
          name: 'Công việc 3',
          description: 'Miêu tả công việc 3',
          startDate: '2020-10-25',
          endDate: '2020-12-10'
        },
        {
          name: 'Công việc 4',
          description: 'Miêu tả công việc 4',
          startDate: '2020-11-15',
          endDate: '2020-12-30'
        }
      ],
      search: '',
      filtedData: []
    }
  },

  methods: {
    handleAddTask (data) {
      data.startDate = this.$dayjs(data.startDate).format('YYYY-MM-DD')
      data.endDate = this.$dayjs(data.endDate).format('YYYY-MM-DD')
      this.tableData = [...this.tableData, data]
      this.addTask = {
        name: '',
        description: '',
        startDate: '',
        endDate: ''
      }
    },

    handleEditTask (data) {
      data.startDate = this.$dayjs(data.startDate).format('YYYY-MM-DD')
      data.endDate = this.$dayjs(data.endDate).format('YYYY-MM-DD')
      this.tableData.splice(this.rowEdit, 1, data)
    },

    clickEdit (index, row) {
      this.rowEdit = index
      this.editTask = this._.clone(row)
    },

    clickDelete (index) {
      this.tableData.splice(index, 1)
    }
  }
}
</script>

<style>
.input-search {
  margin-bottom: 10px;
}

#task > h1 {
  margin-top: 0;
  margin-bottom: 10px;
  font-size: 24px;
}

.cell {
  display: inline-flex;
}

#delete {
  margin-left: 10px;
}
</style>
