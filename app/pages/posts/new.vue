<template>
  <section class="container post-page">
    <el-card style="float:1">
      <div slot="header" class="clearfix">
        <el-input placeholder="タイトルを入力" v-model="formData.title"/>
      </div>
      <div>
        <el-input placeholder="本文入力・・・・・" type="textarea" rows="15" v-model="formData.body"/>
      </div>
      <div class="text-right" style="textarea" rows="15" v-model="formData.body">
        <el-button type="primary" @click="publish" round>
        <span class="el-icon-upload2">
          <span>Publish</span>
        </span>
        </el-button>
      </div>
    </el-card>
  </section>
</template>

<script>
  import {mapGetters, mapActions} from 'vuex'

  export default {
    asyncData({redirect, store}) {
      if (!store.getters['user']) {
        redirect('/')
      }
      return {
        formData: {
          title: '',
          body: ''
        }
      }
    },
    computed: {
      ...mapGetters(['user'])
    },
    methods: {
      async publish() {
        const payload = {
          user: this.user,
          ...this.formData,
        }
        await this.publishPost({payload})
        this.$router.push('/posts')
      },
      ...mapActions('user', ['updateUser']),
      ...mapActions('posts', ['publishPost'])
    }
  }
</script>
<style>
  .posts_page .el-table__row {
    cursor: pointer;
  }
</style>
