<template>
  <div>
    <div class="change-title">
      <input
          class="change-title__input"
          type="text"
          v-model="inputValue"
      >
      <button class="change-title_btn btn" @click="changeTitle()">
        Change Title
      </button>
    </div>

    <div class="titles-container">
      <Title
          v-for="(title, index) in getTitles"
          :key=index
          :title="title.title"
          :isActive="index === titleIndex"
          @click.native="chooseIndex(index)"
      />
    </div>

    <button class="btn" @click="shuffleArray(getTitles)">
      Shuffle
    </button>
  </div>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';

import Title from "@/components/Title.vue";

@Component({
  components: {
    Title
  }
})
export default class Container extends Vue {
  public inputValue: string = '';
  public titleIndex: number | null = null;
  public titles: { title: string }[] = [
    {
      title: 'Title 1'
    },
    {
      title: 'Title 2'
    },
    {
      title: 'Title 3'
    },
    {
      title: 'Title 4'
    },
    {
      title: 'Title 5'
    },
    {
      title: 'Title 6'
    }
  ];

  get getTitles(): { title: string }[] {
    return this.titles
  }

  /**
   * Changes chosen title.
   */
  public changeTitle() {
    if (this.titleIndex === null) {
      alert('Choose title to change')
      return
    }
    this.titles[this.titleIndex].title = this.inputValue;
    this.$forceUpdate();
  }

  /**
   * Sets index of clicked title to variable.
   * @param {number} index - Index of title chosen.
   */
  public chooseIndex(index: number) {
    this.titleIndex = index;
  }

  /**
   * Shuffles any array.
   * @param {array} array - Array that will be shuffled.
   */
  public shuffleArray(array: any[]): void {
    let currentIndex = array.length, randomIndex;

    while (currentIndex != 0) {

      randomIndex = Math.floor(Math.random() * currentIndex);
      currentIndex--;

      [array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
    }

    this.$forceUpdate();
  }


}
</script>
<style lang="scss">
.change-title {
  &__input {
    display: block;
    margin: 20px auto;
    font-size: 20px;
    padding: 5px;
    width: 179px;
  }
}

.titles-container {
  margin: 40px auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  width: fit-content;
}

.btn {
  font-weight: normal;
  letter-spacing: 1.4px;
  background-color: #42b883;
  color: #dddddd;
  padding: 15px 40px;
  border-radius: 4px;
  border: none;
  text-transform: uppercase;
  transition: all 0.2s ease-in-out;

  &:hover {
    color: #ffffff;
    box-shadow: 0 5px 15px #42b883;
    border: none;
  }
}
</style>
