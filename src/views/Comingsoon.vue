   <template>
    
      <div class="commingsoon">
          <div v-if="device <= 767">
           <a href="/">
            <img src="@/assets/landing-page/mobile-comingsoon-image.jpg" class="img-fluid"/>
           </a>
          </div>
          <div v-else-if="device >= 768  &&  device <= 1024 ">
            <a href="/">
            <img src="@/assets/landing-page/ipad-mini-comingsoon-image.jpg" class="img-fluid"/>
            </a>
          </div>
      </div>
   </template>
  <script>
  import AppLayout from "@/layouts/AppLayout";
  import { mapGetters } from "vuex";
  export default {

    data() {
        return {
          device : null,
        };
    },
    computed: {
      ...mapGetters(["currentUser"]),
    },
    methods: {
      openModal(id) {
        this.$bvModal.show(id);
      },
      closeModal(id) {
        this.$bvModal.hide(id);
      },
    },
    mounted() {
        this.device = screen.width
    },
  };
  </script>
  
  <style scoped lang="scss">
  #app {
    height: 100%;
  }
  .commingsoon img
  {
    height: 100vh;
    width: 100%;
  }
  </style>
  