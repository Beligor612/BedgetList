<template>
  <div class="form-ui">
    <el-form ref="form"
            :model="formData"
            label-width="120px"
            :rules = "rules">
      <!-- Select -->
    <el-form-item label="Type: " prop="type">
      <el-select v-model="formData.type"
                placeholder="Please select your type"
                >
        <el-option label="Income" value="INCOME"></el-option>
        <el-option label="Outcome" value="OUTCOME"></el-option>
      </el-select>
    </el-form-item>
    <el-form-item label="Comment: " prop ="comment">
      <el-input  v-model="formData.comment">
      </el-input>
    </el-form-item>
    <el-form-item label="Value: " prop="value">
      <el-input  v-model.number="formData.value" >

      </el-input>
    </el-form-item>
    <el-button type='primary' @click="submitForm">
      Submit
    </el-button>

    </el-form>
  </div>
</template>

<script>
export default {
  name: 'Form',
  data: ()=> ({
    formData: {
      type: '',
      value: 0,
      comment: ''
    },
    rules: {
      type: [
        {required: true, message: "Please select type budget", trigger: "blur"}
      ],
      comment: [
        {required: true, message: "Please enter comment", trigger: "blur"}
      ],
      value: [
        {required: true, message: "Please enter value", trigger: "blur"},
        {type: 'number', message: "Please enter number value", trigger: "blur"},
      ],

    }
  }),
  methods: {
    submitForm: function(){
      this.$refs.form.validate((valid)=>{
        if (valid){
          if(this.formData.value && this.formData.type === 'OUTCOME' && this.formData.value > 0){
            this.formData.value = -this.formData.value
          }
          this.$emit('submitForm', {... this.formData})
        }
      })
    }
  },
}
</script>

<style scoped>
  .form-ui{
    max-width: 500px;
    margin: auto;
    margin-top: 15px
  }
</style>