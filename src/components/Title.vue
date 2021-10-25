<template>
  <div class="title" :class="{active: isActive}">{{ title }}</div>
</template>

<script lang="ts">
import {Component, Prop, Vue} from "vue-property-decorator";

@Component
export default class Title extends Vue {
  @Prop() private title!: string;
  @Prop() public isActive!: boolean
}
</script>
<style lang="scss">
.title{
  padding: 15px 40px;
  margin: 20px;
  font-size: 16px;
  font-weight: 600;
  border: 2px solid #42b883;
  border-radius: 4px;
  cursor: pointer;

  &.active {
    border: 2px solid #eb5a46;
    color: #eb5a46;
  }
}
</style>
