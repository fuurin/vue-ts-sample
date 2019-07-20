<template>
  <div class="home">
    <p>挨拶した回数: {{ count }}</p>
    <p v-if="isRegulars">いつもありがとうございます</p>
    <p>{{ greetText }}</p>
    <MyButton class="my-button" :greet="greetText" @clicked="onMyButtonClicked">挨拶する</MyButton>
    <ResetButton v-model="greetText"></ResetButton>

    <div v-for="item in items" :key="item">
      <i class="far fa-lightbulb"></i>
      <p class="has-text-danger">{{ item }}</p>
    </div>

  </div>
</template>

<script lang="ts">
import { Component, Watch, Vue } from 'vue-property-decorator';
import MyButton from '@/components/MyButton.vue';
import ResetButton from '@/components/ResetButton.vue';

@Component({
  components: {
    MyButton,
    ResetButton,
  },
})
export default class Home extends Vue {
  public greetText: string = 'Hello';
  private count: number = 0;
  private items: string[] = [];

  public get isRegulars(): boolean {
    return this.count >= 5;
  }

  @Watch('count')
  public countChanged() {
    if (this.count === 5) {
      alert('常連になりました');
    }
  }

  public onMyButtonClicked(count: number) {
    this.count = count;
    this.greetText = 'こんにちは';
    this.items.push('こんにちは ' + this.count);
  }
}
</script>
