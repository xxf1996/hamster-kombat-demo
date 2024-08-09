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
              <div class=" color-yellow font-size-5">💰</div>
              <span class="font-bold line-height-none">0</span>
              <div class="i-carbon-information-filled font-size-5 color-gray-600" />
            </div>
          </div>
          <div class="demo-profile__menu-divider" />
          <div class="i-carbon-settings font-size-7" />
        </div>
      </div>
    </div>
    <main class="demo-main" ref="mainContainer">
      <div class="demo-main__tasks">
        <div class="demo-main__tasks-item">
          <img class="demo-main__tasks-img" src="@/assets/logo.png" />
          <p class="demo-main__tasks-text">Task 1</p>
          <p class="demo-main__tasks-time">09:03</p>
        </div>
        <div class="demo-main__tasks-item">
          <img class="demo-main__tasks-img" src="@/assets/logo.png" />
          <p class="demo-main__tasks-text">Task 2</p>
          <p class="demo-main__tasks-time">20:05</p>
        </div>
        <div class="demo-main__tasks-item">
          <img class="demo-main__tasks-img" src="@/assets/logo.png" />
          <p class="demo-main__tasks-text">Task 3</p>
          <p class="demo-main__tasks-time">03:04</p>
        </div>
        <div class="demo-main__tasks-item">
          <img class="demo-main__tasks-img" src="@/assets/logo.png" />
          <p class="demo-main__tasks-text">Task 4</p>
          <p class="demo-main__tasks-time">13:04</p>
        </div>
      </div>
      <div class="demo-main__money">
        <span>💰</span>
        <span>{{ money.toLocaleString() }}</span>
      </div>
      <div class="demo-main__shushu" ref="shushu">
        <div class="demo-main__shushu-bg"></div>
        <img class="demo-main__shushu-img" src="@/assets/shushu.png" />
      </div>
      <div class="demo-main__lightning">
        <div class="demo-main__lightning-left">
          <span class="font-size-8">⚡</span>
          <span>{{ remainingLightning }}</span>/
          <span>{{ totalLightning }}</span>
        </div>
        <div class="demo-main__lightning-right">
          <span class="font-size-8">🚀</span>
          Boost
        </div>
      </div>
    </main>
    <footer class="demo-footer">
      <div class="demo-footer__menu demo-footer__menu-actived">
        <img class="demo-footer__menu-img" src="@/assets/logo.png" />
        <p class="demo-footer__menu-text">Menu 1</p>
      </div>
      <div class="demo-footer__menu">
        <img class="demo-footer__menu-img" src="@/assets/logo.png" />
        <p class="demo-footer__menu-text">Menu 2</p>
      </div>
      <div class="demo-footer__menu">
        <img class="demo-footer__menu-img" src="@/assets/logo.png" />
        <p class="demo-footer__menu-text">Menu 3</p>
      </div>
      <div class="demo-footer__menu">
        <img class="demo-footer__menu-img" src="@/assets/logo.png" />
        <p class="demo-footer__menu-text">Menu 4</p>
      </div>
      <div class="demo-footer__menu">
        <img class="demo-footer__menu-img" src="@/assets/logo.png" />
        <p class="demo-footer__menu-text">Menu 5</p>
      </div>
      <div class="demo-footer__menu">
        <img class="demo-footer__menu-img" src="@/assets/logo.png" />
        <p class="demo-footer__menu-text">Menu 6</p>
      </div>
    </footer>
  </section>
</template>

<script lang="ts" setup>
import { onMounted, ref } from 'vue';

const money = ref(8723487)
const totalLightning = ref(1000)
const remainingLightning = ref(1000)
const shushu = ref<HTMLDivElement>()
const mainContainer = ref<HTMLDivElement>()
let addLightningTimerId: number | null = null

function addLightning() {
  addLightningTimerId = window.setTimeout(() => {
    if (remainingLightning.value < totalLightning.value) {
      remainingLightning.value += 1
      addLightning()
    } else {
      addLightningTimerId = null
    }
  }, 1000)
}

function addMoney(touch: Touch) {
  if (remainingLightning.value < 1) {
    return
  }

  if (!mainContainer.value) {
    return
  }

  money.value += 1
  remainingLightning.value -= 1

  // console.log('touch', touch)
  const number = document.createElement('div')
  number.classList.add('demo-main__number')
  number.innerText = '+1'
  number.style.top = `${touch.pageY - window.scrollY}px`
  number.style.left = `${touch.pageX}px`
  number.onanimationend = e => {
    mainContainer.value?.removeChild(number)
  }
  mainContainer.value.appendChild(number)
  number.style.animationPlayState = 'running'

  if (addLightningTimerId) {
    window.clearTimeout(addLightningTimerId)
  }

  addLightning()
}

function initTouchEvent(container: HTMLDivElement) {
  container.addEventListener('touchend', e => {
    // console.log(e)
    for (let i = 0; i < e.changedTouches.length; i++) {
      addMoney(e.changedTouches.item(i)!)
    }
  })
}

onMounted(() => {
  if (shushu.value) {
    initTouchEvent(shushu.value)
  }
})
</script>

<style lang="scss">
$bg-color: rgba(black, 0.99);

@keyframes DotFlush {
  0% {
    opacity: 0;
  }
  60% {
    opacity: 1;
  }
  70% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

@keyframes NumberMoving {
  0% {
    transform: translate3d(-50%, -50%, 0);
    opacity: 1;
  }
  100% {
    transform: translate3d(-50%, -150px, 0);
    opacity: 0;
  }
}

.demo {
  @apply w-screen flex flex-col;
  background-color: $bg-color;
  color: rgba(white, 0.9);

  &-icon {
    font-size: 28px;
    cursor: pointer;
  }

  &-header {
    @apply flex h-10 justify-between items-center p-4 sticky top-0;
    background-color: $bg-color;
    z-index: 999;
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
      @apply flex items-center justify-between gap-4 py-4;
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
      @apply flex flex-1 flex-col w-30;

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

    &__number {
      @apply fixed font-size-8 font-bold;
      animation: NumberMoving 1s ease-in-out;
      animation-fill-mode: both;
      animation-play-state: paused;
    }

    &__tasks {
      @apply flex justify-between gap-2 p-4 mt-4;

      &-item {
        @apply relative flex flex-1 flex-col items-center py-2 rounded-lg bg-gray-800;

        &::after {
          content: '';
          @apply absolute top-2 right-2 w-2 h-2 rounded-lg;
          background-color: rgba(white, 0.8);
          animation: DotFlush 1s infinite;
        }
      }

      &-img {
        @apply w-10 h-10;
      }

      &-text {
        @apply my-1;
      }

      &-time {
        @apply mt-4 mb-0 text-sm text-gray-500;
      }
    }

    &__money {
      @apply flex justify-center items-center gap-2 font-size-8 font-bold;
    }

    &__shushu {
      @apply flex justify-center items-center relative mt-6;

      &-bg {
        @apply w-80 h-80 rounded-full;
        background: radial-gradient(circle at 50% 50%, rgb(44, 56, 219), rgb(17, 17, 48));
      }

      &-img {
        @apply w-75 h-75 absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
      }
    }

    &__lightning {
      @apply flex justify-between items-center p-4 font-bold;

      &-left {
        @apply flex items-center gap-2 font-size-5;
      }

      &-right {
        @apply flex items-center gap-2 font-size-4;
      }
    }
  }

  &-footer {
    @apply flex items-center gap-2 sticky bottom-0 p-2 bg-gray-800;

    &__menu {
      @apply flex-1 py-2 text-center;

      &-actived {
        @apply bg-dark-500 rounded-md;
      }

      &-img {
        @apply w-6 h-6;
      }

      &-text {
        @apply my-0 font-size-3;
      }
    }
  }
}
</style>
