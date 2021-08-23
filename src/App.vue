<template>
  <div class="container column">
    <app-form
      @add-block="addBlock"
    ></app-form>
    <app-view
      :blocks="blocks"
    ></app-view>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <app-comments
      v-else
      @load-comments="loadComments"
      :comments="comments"
    ></app-comments>
  </div>
</template>

<script>
import AppForm from "@/components/AppForm"
import AppView from "@/components/AppView"
import AppComments from "@/components/AppComments";
import AppLoader from "@/components/AppLoader";
export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    addBlock(block){
      this.blocks.push(block)
    },
    async loadComments() {
      this.loading = true
      const result = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=10')
      this.comments = await result.json()
      this.loading = false
    }
  },
  components: {AppForm, AppView, AppComments, AppLoader}
}
</script>
