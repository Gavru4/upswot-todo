<template>
  <div class="modal" v-if="isModalOpen" @click.stop="openModal">
    <div @click.stop class="modal__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from "vuex";
export default {
  name: "my-modal",
  computed: mapGetters({
    isModalOpen: "todo/isModalOpen",
  }),
  methods: {
    ...mapMutations({
      toggleModal: "todo/toggleModal",
    }),

    openModal() {
      this.toggleModal();
    },
  },
};
</script>

<style lang="scss" scoped>
.modal {
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
  z-index: 99;
}

.modal__content {
  margin: auto;
  border-radius: 12px;
  min-height: 50px;
  width: 300px;
  padding: 30px;

  background: white;
  @media screen and (min-width: 480px) {
    width: 450px;
  }
  @media screen and (min-width: 768px) {
    width: 700px;
    padding: 50px;
  }
}
</style>
