<template>
  <div class="c-monitoror-welcome" :class="classes">
    <template v-if="isNewUser">
      <h1 class="c-monitoror-welcome--title">Welcome</h1>
      <h2 class="c-monitoror-welcome--subtitle">You're almost there!</h2>
    </template>
    <template v-else>
      Named config list
    </template>
  </div>
</template>

<script lang="ts">
  import {Component, Vue} from 'vue-property-decorator'

  @Component({})
  export default class MonitororWelcome extends Vue {
    /**
     * Computed
     */

    get classes() {
      return {}
    }

    get isNewUser(): boolean {
      return this.$store.getters.isNewUser
    }

    /*
     * Methods
     */

    /*
     * Watchers
     */

  }
</script>

<style lang="scss">
  .c-monitoror-welcome {
    position: relative;
    padding-top: 260px;
    height: 100vh;
    animation: welcomeSlideIn 500ms ease 150ms both;

    &::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 500px;
      background: var(--color-dark-background);
      transform: skewY(-7deg) scaleY(2);
      transform-origin: bottom center;
      z-index: -1;
    }

    .c-monitoror-welcome--title {
      display: inline-block;
      margin: 0 auto;
      font-weight: 700;
      font-size: 72px;
      color: transparent;
      background: linear-gradient(to right, var(--color-action-required), var(--color-succeeded));
      -webkit-background-clip: text;
      background-size: 200% 100%;
      animation: gradient 10s ease infinite;
    }
    .c-monitoror-welcome--subtitle {
      font-weight: 300;
      font-size: 32px;
      margin: 0;
    }

    @keyframes gradient {
      0%,
      100% {
        background-position: 0 50%;
      }
      50% {
        background-position: 100% 50%;
      }
    }
  }

  @keyframes welcomeSlideIn {
    from {
      opacity: 0;
      transform: translateY(10%);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>
