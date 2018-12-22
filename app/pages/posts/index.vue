<template>
  <section class="conteiner post-page">
    <el-card>
      <div slot="header" class="clearfix">
        <span>新規投稿</span>
      </div>
    </el-card>
    <el-table :data="showPosts" style="width: 100%" class="table">
      <el-table-column prop="title" label="タイトル"></el-table-column>
      <el-table-column prop="user.id" label="投稿者" width="180"></el-table-column>
      <el-table-column prop="created_at" label="投稿日時" width="240"></el-table-column>
    </el-table>
  </section>
</template>

<script>
  export default {
    computed: {
      showPosts() {
        return [
          {
            id: '001',
            title: 'タイトル',
            body: 'テキストやテキストやテキストやテキストやテキストやテキストやテキストやテキストやテキストやテキストやテキストやテキストや',
            created_at: '2018/12/22　20:23:00',
            user: {
              id: 'belowt'
            }
          },
          {
            id: '002',
            title: 'WAI',
            body: 'WAIやで',
            created_at: '2018/12/22　20:23:00',
            user: {
              id: 'wwww'
            }
          },

        ]
      }
    }
  }
</script>

<style scoped>
  .post-page .el-table__row {
    cursor: pointer;
  }
</style>
