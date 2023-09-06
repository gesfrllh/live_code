
<template>
  <div
    class="border-2 h-screen flex flex-col gap-8 items-center justify-center"
  >
    <div class="flex gap-4">
      <div class="border-2 py-2 px-2 rounded-lg">
        <input
          class="border-none outline-none"
          v-model="item"
          @change="validateInput"
        />
      </div>
      <div
        class="border-2 px-4 py-2 rounded-lg cursor-pointer"
        @click="addItem"
      >
        submit
      </div>
      <div v-if="validate" class="text-red-700 py-2 px-2">Harus di isi</div>
    </div>
    <div class="flex flex-col gap-2">
      <div v-for="v in list" :key="v">
        <div class="border-2 px-4 py-2 rounded-lg hover:border-red-600">
          {{ v.items }}
        </div>
      </div>
    </div>
  </div>
</template>
<script >
export default {
  data() {
    return {
      item: "",
      list: [],
      validate: false,
    };
  },
  methods: {
    addItem() {
      if(this.item !== ''){
        const data = {
          items: this.item,
        };
        this.list.push(data);
        this.item = "";
        this.validate = false
      } else {
        this.validate = true
      }
    },
    validateInput() {
      if (this.item === "") {
        this.validate = true;
      } else {
        this.validate = false;
      }
    },
  },
};
</script>
