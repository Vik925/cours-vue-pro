<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!-- First modal -->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>
          <modal title="First modal" v-show="modalFirst" @close="false">
            <div slot="body">
              <p>Text Text Text Text Text</p>
              <button class="btn btnPrimary" @click="modalFirst = !modalFirst">well</button>
            </div>
          </modal>

          <!-- Second modal -->
          <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show modal with form</button>
          <modal title="Modal whis form" v-show="modalSecond.show" @close="modalSecond.show = false">
            <div slot="body">
              <form @submit.prevent="submitSecondForm">
                <label>Name:</label>
                <input type="text" required v-model="modalSecond.name" />
                <label>Email:</label>
                <input type="email" required v-model="modalSecond.email" />
                <button class="btn btnPrimary">submit</button>
              </form>
            </div>
          </modal>

          <button class="btn btnPrimary" @click="modalValidate = !modalValidate">
            Show modal with form + validate
          </button>
          <modalValidate v-show="modalValidate" @close="modalValidate = false" />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
  import modal from '@/components/UI/Modal.vue';
  import modalValidate from '@/components/ModalValidate.vue';

  export default {
    components: { modal, modalValidate },
    data() {
      return {
        modalFirst: false,
        modalSecond: {
          show: false,
          name: '',
          email: '',
        },
        modalValidate: false,
      };
    },
    methods: {
      submitSecondForm() {
        console.log({
          name: this.modalSecond.name,
          email: this.modalSecond.email,
        });
        (this.modalSecond.name = ''), (this.modalSecond.email = ''), (this.modalSecond.show = false);
      },
    },
  };
</script>
