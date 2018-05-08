<template>
  <div class="WeekChooser">
      <div class="WeekChooser__inner">
        <button class="WeekChooser__arrow" type="button" @click="goToPrev()">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-chevron-left"><polyline points="15 18 9 12 15 6"></polyline></svg>
        </button>
        <div class="WeekChooser__center">
          <span class="WeekChooser__week">Vecka: {{ week }}</span>
          <span class="WeekChooser__year"> ({{ year }})</span>
        </div>
        <button class="WeekChooser__arrow" type="button" @click="goToNext()">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-chevron-right"><polyline points="9 18 15 12 9 6"></polyline></svg>
        </button>
      </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    year: 2018,
    week: 19
  }),
  methods: {
    goToPrev() {
      this.week--;
      if (this.week < 1) {
        this.week = 52;
        this.year--;
      }
      this.$emit("changed", `${this.year}-${this.week}`);
    },
    goToNext() {
      this.week++;
      if (this.week > 52) {
        this.week = 1;
        this.year++;
      }
      this.$emit("changed", `${this.year}-${this.week}`);
    }
  }
};
</script>

<style lang="scss">
.WeekChooser {
  border-bottom: 1px solid #ddd;
  text-align: center;
  padding: 30px;
  display: flex;
  justify-content: center;
  &__inner {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  &__center {
    margin: 0 20px;
  }
}
</style>
