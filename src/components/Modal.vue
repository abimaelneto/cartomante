<script>
export default {
  props: {
    open: Boolean,
    title: String,
    text: String,
  },
  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>

<template>
  <div class="modal" v-if="open">
    <div class="modal-content">
      <table class="table">
        <tr>
          <h1>{{ title }}</h1>
        </tr>
        <tr>
          <td id="tip">{{ text }}</td>
        </tr>
      </table>
      <button class="material-symbols-outlined" id="btn" @click="close">
        cancel
      </button>
    </div>
  </div>
</template>

<style>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  background-color: black;
  color: rgb(98, 10, 180);
  font-size: 50px;
  opacity: 80%;
  padding: 50px;
  border-radius: 8px;
}

h1 {
  color: rgb(88, 5, 88);
}

h2 {
  margin-top: 0;
}

#btn {
  margin-top: 10px;
  background: transparent;
  border: none;
  color: rgb(88, 5, 88);
  font-size: 3rem;
  cursor: grab;
  font-variation-settings: "FILL" 0, "wght" 400, "GRAD" 0, "opsz" 48;
}

.material-symbols-outlined {
}

#tip {
  font-family: "Amatic SC", cursive;
}

.table {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
