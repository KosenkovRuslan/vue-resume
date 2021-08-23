<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'resume-' + block.type"
        :value="block.value"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeAvatar from "@/components/parts/ResumeAvatar";
import ResumeTitle from "@/components/parts/ResumeTitle";
import ResumeSubtitle from "@/components/parts/ResumeSubtitle";
import ResumeText from "@/components/parts/ResumeText";
export default {
  name: "AppView",
  props: ['blocks'],
  components:{ResumeAvatar, ResumeTitle, ResumeSubtitle, ResumeText}
}
</script>