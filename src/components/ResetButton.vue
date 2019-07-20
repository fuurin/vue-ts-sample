<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';

@Component
export default class ResetButton extends Vue {
  @Prop()
  public value!: string;

  private initialValue!: string;

  @Emit()
  public input(value: string) {}

  public created() {
    this.initialValue = this.value;
  }

  public onClick() {
    this.input(this.initialValue);
  }
}
</script>

<style scoped>

</style>
