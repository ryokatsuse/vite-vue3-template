<template>
  <ul>
    <li v-for="(user, i) in users" :key="i">{{ user }}</li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  async setup() {
    // APIリクエストのモック 2000ms後にユーザー名の配列を返す
    const fetchUsers = () => {
      return new Promise<string[]>(resolve => {
        setTimeout(() => {
          resolve(['Jon', 'Bob', 'Nancy'])
        }, 2000)
      })
    };

　　 // ユーザー名を取得
    // setup()内で読んでいるのでVue.js 2系で言うonCreated()と同じライフサイクルで実施される。
    const users = await fetchUsers();

    return {
      users
    }
  }
});
</script>

<style lang="scss">

ul {
  li {
    list-style: none;
  }
}

</style>