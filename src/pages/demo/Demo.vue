<template>
  <section class="demo">
    <header class="demo-header">
      <div class="i-carbon-close demo-icon" />
      <div>
        <h2>Hamster Kombat</h2>
      </div>
      <div class="i-carbon-overflow-menu-vertical demo-icon" />
    </header>
    <div class="demo-profile">
      <div class="demo-profile__top">
        <div class="demo-profile__top-left">
          <img class="demo-profile__avatar" src="@/assets/shushu.png" />
          <div class="demo-profile__skin">
            <p class="demo-profile__skin-text">Buy skin</p>
            <img class="demo-profile__skin-img" src="@/assets/shushu-skin.png" />
          </div>
          <p class="demo-profile__name">Shu(CEO)</p>
        </div>
        <div class="demo-profile__top-right">
          <span class="font-size-5">🔑</span>
          <span class="font-bold">0</span>
          <div class="i-carbon-chevron-right color-gray-600"></div>
        </div>
      </div>
      <div class="demo-profile__bottom">
        <div class="demo-profile__bronze">
          <div class="demo-profile__bronze-top">
            <span class="flex items-center gap-1">Bronze<div class="i-carbon-chevron-right" /></span>
            <span class=" color-gray-500">
              <span class="color-gray-200">1</span>/11
            </span>
          </div>
          <div class="demo-profile__bronze-bottom" />
        </div>
        <div class="demo-profile__menu">
          <img class="demo-profile__menu-avatar" src="@/assets/shushu.png" />
          <div class="demo-profile__menu-divider" />
          <div>
            <p class="font-size-2 color-gray-400 text-center line-height-none mt-0 mb-2">Profit per hour</p>
            <div class="flex justify-center items-center gap-1">
              <div class="i-carbon-currency-dollar color-yellow font-size-5"/>
              <span class="font-bold line-height-none">0</span>
              <div class="i-carbon-information-filled font-size-5 color-gray-600" />
            </div>
          </div>
          <div class="demo-profile__menu-divider" />
          <div class="i-carbon-settings font-size-7" />
        </div>
      </div>
    </div>
    <main class="demo-main">

    </main>
    <footer class="demo-footer">

    </footer>
  </section>
</template>

<script lang="ts" setup>

</script>

<style lang="scss" scoped>
$bg-color: rgba(black, 0.99);
.demo {
  @apply w-screen h-screen flex flex-col;
  background-color: $bg-color;
  color: rgba(white, 0.9);

  &-icon {
    font-size: 28px;
    cursor: pointer;
  }

  &-header {
    @apply flex h-10 justify-between items-center p-4;
  }

  &-profile {
    @apply p-4;

    &__top {
      @apply flex justify-between items-center;

      &-left {
        @apply flex items-center;
      }

      &-right {
        @apply flex items-center gap-2 rounded-full py-1 px-2;
        background-color: rgba(white, 0.1);
      }
    }

    &__bottom {
      @apply flex items-center justify-between py-4;
    }

    &__avatar {
      @apply w-10 h-10 rounded-lg bg-gray-200;
      border: 3px solid $bg-color;
      z-index: 1;
    }

    &__skin {
      @apply flex h-10 items-center rounded-lg pl-4 -ml-2 mr-2;
      background: linear-gradient(to right, red, orange);

      &-text {
        @apply w-5 text-sm;
        line-height: 1.1;
      }

      &-img {
        @apply w-10 h-10;
      }
    }

    &__bronze {
      @apply flex flex-col w-30;

      &-top {
        @apply flex justify-between items-center;
      }

      &-bottom {
        @apply relative w-full h-2 mt-2 rounded-full;
        background-color: rgba(white, 0.1);
        border: 1px solid rgba(white, 0.2);

        &::after {
          content: '';
          @apply absolute top-0 left-0 w-1/3 h-full rounded-full;
          background: linear-gradient(to right, rgb(106, 224, 106), rgb(165, 138, 240), rgb(107, 17, 241));
        }
      }
    }

    &__menu {
      @apply flex items-center gap-4 rounded-full px-2 py-1;
      background-color: rgba(white, 0.1);
      border: 1px solid rgba(white, 0.2);

      &-avatar {
        @apply w-10 h-10;
      }

      &-divider {
        @apply h-7;
        width: 1px;
        background-color: rgba(white, 0.2);
      }
    }
  }

  &-main {
    @apply flex-1 -mt-4 bg-dark-900;
    border-top-left-radius: 50px;
    border-top-right-radius: 50px;
    border-top: 3px solid rgb(238, 205, 71);
    box-shadow: 0 -5px 60px 0 rgba(238, 205, 71, 0.3);
  }

  &-footer {
    @apply h-15 bg-dark-700;
  }
}
</style>
