<template>
  <div>
    <Beverage 
    :isIced="currentTemp === 'Cold'"
    :creamer="currentCream"
    :syrup="currentSyrup"
    :beverage="currentBase"
    />
    <ul>
      <li>
        <span>Temperature:</span>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      <li>
        <span>Creamer:</span>
        <template v-for="cream in creams" :key="cream">
          <label>
            <input
              type="radio"
              name="cream"
              :id="`r${cream}`"
              :value="cream"
              v-model="currentCream"
            />
            {{ cream }}
          </label>
        </template>
      </li>
      <li>
        <span>Syrup:</span>
        <template v-for="syrup in syrups" :key="syrup">
          <label>
            <input 
              type="radio" 
              name="syrup"
              :id="`r${syrup}`"
              :value="syrup"
              v-model="currentSyrup"
              />
              {{ syrup }}
          </label>
        </template>
      </li>
      <li>
        <span>Base Beverage:</span>
        <template v-for="base in bases" :key="base">
          <label>
            <input
              type="radio"
              name="base"
              :id="`r${base}`"
              :value="base"
              v-model="currentBase"
              />
              {{ base }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";
// Define reactive data
const temps = ref(["Hot", "Cold"]);
const creams = ref(["None", "Milk", "Cream", "Half & Half"]);
const syrups = ref(["None", "Vanilla", "Caramel", "Hazelnut"]);
const bases = ref(["Coffee", "Green Tea", "Black Tea"]);

const currentTemp = ref("Hot");
const currentCream = ref("None");
const currentSyrup = ref("None");
const currentBase = ref("Coffee");
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
span{
  font-weight: bold;
}
</style>
