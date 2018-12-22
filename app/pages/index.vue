<template>
  <section class="container">
    <el-card style="flex:1">
      <div class="clearfix" slot="header">
        <span>ログイン</span>
      </div>
      <from>
        <div class="from-content">
          <sapn>ユーザーID</sapn>
          <el-input placeholder="" v-model="fromData.id"></el-input>
        </div>
        <div class="from-content">
          <el-checkbox v-model="isCreateMode">アカウント作成</el-checkbox>
        </div>
        <div class="text-right">
          <el-button type="primary">{{buttonText}}</el-button>
        </div>
      </from>
    </el-card>
  </section>
</template>

<script>
export default {
  asyncData() {
    return {
      isCreateMode: false,
      fromData: {
        id: ''
      }
    }
  },
  computed: {
    buttonText() {
      return this.isCreateMode ? '新規登録' : 'ログイン'
    }
  }
}
</script>

<style scoped>
  .from-content {
    margin: 16px 0;
  }
</style>
