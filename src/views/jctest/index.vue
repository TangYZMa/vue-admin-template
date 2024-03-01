<template>
  <div class="app-container">
    <div>
      <el-form ref="form" :model="form" label-width="120px">

        <el-form-item label="GET">
          <el-input v-model="form.desc" type="textarea" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">Create</el-button>
          <el-button @click="onCancel">Cancel</el-button>
        </el-form-item>
      </el-form>
    </div>
    <hr>
    <div class="spacer"></div>
    <div>
      <el-form ref="form2" :model="form2" label-width="120px">
        <el-form-item label="Activity form">
          <el-input v-model="form2.desc" type="textarea" :rows="10" />
          <el-input v-model="form2.desc" type="textarea" />
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        desc: ''
      },
      form2: {
        desc: ''
      }
    }
  },
  methods: {
    onSubmit() {
      try {
        const response = axios.get('/info');
        this.responseData = JSON.stringify(response.data);
      } catch (error) {
        console.error('Error fetching data: ', error);
      }
    },
    onCancel() {
      this.$message({
        message: 'cancel!',
        type: 'warning'
      })
    }
  }
}
</script>

<style scoped>
.line {
  text-align: center;
}
.spacer {
  height:20px;
}
</style>

