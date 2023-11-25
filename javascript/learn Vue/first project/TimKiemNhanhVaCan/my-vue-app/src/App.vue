<template>
  <div :class="['hihi', statusButton]">
    <span :style="{ color: 'red', background: stkatusButton }">
      {{ nameuser }}</span>
  </div>
  <div v-html="nameuser"></div>

  <div v-show="nameuser == 'tai Pham'">hihi</div>
  <hr />

  <input name="search" placeholder="search items" @:keyup="onInputSearch($event)" :value="inputText" />

  <template v-for="item in dataNotification" :key="item._id">
    <div>{{ item.name || "" }}</div>
  </template>
</template>

<script>
const DATA_USERS = [
  {
    _id: 0,
    name: "Tèo Pham",
  },
  {
    _id: 1,
    name: "Tí Pham",
  },
  {
    _id: 2,
    name: "Bắc Pham",
  },
];

export default {
  name: "app",
  data() {
    return {
      nameuser: "tai Pham22",
      statusButton: "info23332",
      dataNotification: [...DATA_USERS],
      inputText: "",
      timeStrigger: "",
    };
  },
  methods: {
    onChangeItem(data, event) {
      if (!data) return;

      this.step += data;
    },
    onInputSearch(event) {
      this.inputText;
      const callBack = () => {
        const inputValue = (event.target.value + "").trim();
        this.inputText = inputValue;

        const formatInput = inputValue.toLowerCase();

        if (formatInput) {
          return (this.dataNotification = DATA_USERS.filter((e) =>
            e.name.toLowerCase().startsWith(formatInput)
          ));
        }
        this.dataNotification = DATA_USERS;
      };

      this.timeStrigger && clearTimeout(this.timeStrigger);
      this.timeStrigger = setTimeout(() => {
        callBack();
      }, 500);
    },
  },
};
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.info {
  background: blue;
}
</style>
