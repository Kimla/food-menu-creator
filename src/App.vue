<template>
  <div id="app">
    <WeekChooser @changed="handleWeekChange"/>
    <div class="FoodMenu">

      <div class="FoodMenu__inputHolder">
        <label for="monday">Måndag</label>
        <input id="monday" name="monday" v-model="menus[currentMenu].monday.main" placeholder="Husman...">
        <input id="monday" name="monday" v-model="menus[currentMenu].monday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__inputHolder">
        <label for="tuesday">Tisdag</label>
        <input id="tuesday" name="tuesday" v-model="menus[currentMenu].tuesday.main" placeholder="Husman...">
        <input id="tuesday" name="tuesday" v-model="menus[currentMenu].tuesday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__inputHolder">
        <label for="wednesday">Onsdag</label>
        <input id="wednesday" name="wednesday" v-model="menus[currentMenu].wednesday.main" placeholder="Husman...">
        <input id="wednesday" name="wednesday" v-model="menus[currentMenu].wednesday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__inputHolder">
        <label for="thursday">Torsdag</label>
        <input id="thursday" name="thursday" v-model="menus[currentMenu].thursday.main" placeholder="Husman...">
        <input id="thursday" name="thursday" v-model="menus[currentMenu].thursday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__inputHolder">
        <label for="friday">Fredag</label>
        <input id="friday" name="friday" v-model="menus[currentMenu].friday.main" placeholder="Husman...">
        <input id="friday" name="friday" v-model="menus[currentMenu].friday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__inputHolder">
        <label for="saturday">Lördag</label>
        <input id="saturday" name="saturday" v-model="menus[currentMenu].saturday.main" placeholder="Husman...">
        <input id="saturday" name="saturday" v-model="menus[currentMenu].saturday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__inputHolder">
        <label for="sunday">Söndag</label>
        <input id="sunday" name="sunday" v-model="menus[currentMenu].sunday.main" placeholder="Husman...">
        <input id="sunday" name="sunday" v-model="menus[currentMenu].sunday.secondary" placeholder="Pasta...">
      </div>

      <div class="FoodMenu__saveHolder">
        <button class="button" @click="save()">Spara</button>
      </div>

    </div>
    
  </div>
</template>

<script>
import WeekChooser from "./components/WeekChooser";

export default {
  name: "app",
  components: {
    WeekChooser
  },
  data: () => ({
    currentMenu: "2018-19",
    menus: {}
  }),
  methods: {
    handleWeekChange(val) {
      this.currentMenu = val;
      if (!this.menus[this.currentMenu]) {
        this.createInitialObject();
      }
    },
    save() {
      window.alert(JSON.stringify(this.menus[this.currentMenu], null, 4));
    },
    createInitialObject() {
      this.menus[this.currentMenu] = {
        monday: {
          main: "",
          secondary: ""
        },
        tuesday: {
          main: "",
          secondary: ""
        },
        wednesday: {
          main: "",
          secondary: ""
        },
        thursday: {
          main: "",
          secondary: ""
        },
        friday: {
          main: "",
          secondary: ""
        },
        saturday: {
          main: "",
          secondary: ""
        },
        sunday: {
          main: "",
          secondary: ""
        }
      };
    }
  },
  beforeMount() {
    if (!this.menus[this.currentMenu]) {
      this.createInitialObject();
    }
  }
};
</script>

<style lang="scss">
@import "~normalize.css/normalize";
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica,
    Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  font-size: 18px;
}

* {
  box-sizing: border-box;
}

a,
button {
  text-decoration: none;
  color: inherit;
  transition: 0.25s;
}

button {
  font-weight: 400;
  cursor: pointer;
  background-color: transparent;
  padding: 0;
}

img,
svg {
  max-width: 100%;
  height: auto;
}

strong,
b {
  font-weight: bold;
}

ol,
ul {
  margin: 0;
  padding: 0;
}

button,
input,
optgroup,
select,
textarea {
  font-family: inherit;
  background-color: transparent;
  outline: 0;
  border: 0;
  border-radius: 0;
  color: inherit;
  font-size: inherit;
  font-weight: inherit;
}

input[type="text"],
input[type="email"],
input[type="search"],
input[type="number"],
textarea {
  -webkit-appearance: none;
}

:-moz-focusring,
::-moz-focus-outer {
  border: 0 !important;
  outline: 0 !important;
}

.button {
  padding: 24px 30px;
  min-width: 220px;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 3px;
  background-color: #3f51b5;
  color: #ffffff;
  text-transform: uppercase;
  border-radius: 50px;
}

.FoodMenu {
  padding: 50px 0;
  width: 600px;
  margin: 0 auto;
  &__inputHolder {
    margin-bottom: 20px;
  }
  &__saveHolder {
    text-align: center;
    margin-top: 40px;
  }
  label {
    display: inline-block;
    margin-bottom: 8px;
  }
  input {
    display: block;
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-bottom: 10px;
    transition: border-color 0.25s;
    &:last-child {
      margin-bottom: 0;
    }
    &:focus {
      border-color: #3f51b5;
    }
  }
}
</style>
