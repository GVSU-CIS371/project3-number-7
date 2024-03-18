<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />
    <Contents>
      <template v-slot:top>
          <template v-if="creamer !== 'None' && syrup !== 'None'">
            <Creamer :name="creamer" />
          </template>
      </template>

      <template v-slot:mid>
        <template v-if="syrup !== 'None' "> <!--if there is syrup, render it-->
          <Syrup :name="syrup"/>
        </template>
        <template v-else-if="creamer !== 'None'"> <!--otherwise, if there is creamer, render it here. If neither, render none of these--> 
          <Creamer :name="creamer" />
        </template>
      </template>

      <template v-slot:bottom>
        <Base :name="beverage"/>
      </template>
    </Contents>
  </Mug>
</template>
<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

type Props = {
  isIced: boolean;
  creamer: string;
  syrup: string;
  beverage: string;
};
defineProps<Props>();


</script>
