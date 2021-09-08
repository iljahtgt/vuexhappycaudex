<template>
  <div class="message-alert">
    <div class="alert alert-dismissible"
      :class="'alert-' + item.status"
      v-for="(item, i) in messages" :key="i">
      {{ item.message }}
      <button type="button" class="close" @click="REMOVEMESSAGE(i)" aria-label="Close">
        <span aria-hidden="true">&times;</span>
      </button>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapMutations} from 'vuex';

export default {
  name: 'AlertMessage',
  computed: {
    ...mapGetters('AlertModule', ['messages']),
  },
  methods: {
    ...mapMutations('AlertModule', ['REMOVEMESSAGE']),
    // updateMessage(message, status) {
    //   const timestamp = Math.floor(new Date() / 1000);
    //   this.messages.push({
    //     message,
    //     status,
    //     timestamp,
    //   });
    //   this.removeMessageWithTiming(timestamp);
    // },
    // removeMessageWithTiming(timestamp) {
    //   const vm = this;
    //   setTimeout(() => {
    //     vm.messages.forEach((item, i) => {
    //       if (item.timestamp === timestamp) {
    //         vm.messages.splice(i, 1);
    //       }
    //     });
    //   }, 5000);
    // },
  },
};
</script>

<style scope>
.message-alert {
  position: fixed;
  max-width: 50%;
  top: 56px;
  right: 20px;
  z-index: 1100;
}
</style>
