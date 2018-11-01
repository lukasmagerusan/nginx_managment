<template>
  <div>
    <el-card class="box-card">
      <div slot="header">
        <span>Agape Livestream</span>
      </div>
      <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="250px" class="demo-ruleForm">
        <el-form-item label="Stream to Youtube" prop="delivery">
          <el-switch v-model="ruleForm.delivery"></el-switch>
        </el-form-item>
        <el-form-item label="Stream to Facebook" prop="delivery">
          <el-switch v-model="ruleForm.delivery"></el-switch>
        </el-form-item>
        <el-form-item label="Activity type" prop="type">
          <el-checkbox-group v-model="ruleForm.type">
            <el-checkbox label="Online activities" name="type"></el-checkbox>
            <el-checkbox label="Promotion activities" name="type"></el-checkbox>
            <el-checkbox label="Offline activities" name="type"></el-checkbox>
            <el-checkbox label="Simple brand exposure" name="type"></el-checkbox>
          </el-checkbox-group>
        </el-form-item>
        <el-form-item label="Resources" prop="resource">
          <el-radio-group v-model="ruleForm.resource">
            <el-radio label="Sponsorship"></el-radio>
            <el-radio label="Venue"></el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item label="Activity form" prop="desc">
          <el-input type="textarea" v-model="ruleForm.desc"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">Create</el-button>
          <el-button @click="resetForm('ruleForm')">Reset</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data () {
      return {
        ruleForm: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
        rules: {
          name: [
            {required: true, message: 'Please input Activity name', trigger: 'blur'},
            {min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur'}
          ],
          region: [
            {required: true, message: 'Please select Activity zone', trigger: 'change'}
          ],
          date1: [
            {type: 'date', required: true, message: 'Please pick a date', trigger: 'change'}
          ],
          date2: [
            {type: 'date', required: true, message: 'Please pick a time', trigger: 'change'}
          ],
          type: [
            {type: 'array', required: true, message: 'Please select at least one activity type', trigger: 'change'}
          ],
          resource: [
            {required: true, message: 'Please select activity resource', trigger: 'change'}
          ],
          desc: [
            {required: true, message: 'Please input activity form', trigger: 'blur'}
          ]
        }
      }
    },
    methods: {
      submitForm (formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!')
          } else {
            console.log('error submit!!')
            return false
          }
        })
      },
      resetForm (formName) {
        this.$refs[formName].resetFields()
      }
    }
  }
</script>
<style>
  .text {
    font-size: 14px;
    line-height: 20px;
  }

  .item {
    margin-bottom: 18px;
  }

  .box-card {
    margin: 100px auto;
    width: 500px;
  }
</style>
