<template>
  <div class="home grid">
    <section class="container">
      <div class="info-wrapper grid">
        <img src="../assets/images/general/face.svg" alt="User Avatar" />

        <div class="message">
          <h1>Front-end Challenge!</h1>
          <p>This is a design that you will need to code and impress us.</p>

          <div
            :class="[
              currentTab !== 'RegistrationForm' ? 'registered' : '',
              'button-wrapper',
            ]"
          >
            <button class="bg-img" @click="nextPage">
              <span>Next</span>
            </button>
          </div>
        </div>
      </div>
    </section>

    <transition name="slide-in" appear mode="out-in">
      <component class="content-wrapper" :is="currentStep"></component>
    </transition>
  </div>
</template>

<script>
import RegistrationForm from '@/components/RegistrationForm.vue';
import WorldToday from '@/components/WorldToday.vue';

export default {
  name: 'Home',

  components: {
    RegistrationForm,
    WorldToday,
  },

  data() {
    return {
      currentTab: 'RegistrationForm',
    };
  },

  methods: {
    nextPage() {
      if (this.currentTab !== 'WorldToday') {
        this.currentTab = 'WorldToday';
      } else this.currentTab = 'RegistrationForm';
    },
  },

  computed: {
    currentStep() {
      if (this.currentTab) {
        return this.currentTab;
      }

      return 'div';
    },
  },
};
</script>

<style scoped>
.home {
  grid-template-columns: 1.3fr 2fr;
  height: 100vh;
}

.home > .container {
  background-color: var(--yellow);
  z-index: 999;
}

.info-wrapper {
  grid-template-rows: repeat(2, 1fr);
  width: 60%;
  height: 100%;
  margin: auto;
}

img {
  width: 180px;
  margin: auto;
  margin-bottom: 50px;
}

.message {
  margin-top: 50px;
  text-align: center;
}

h1 {
  margin-bottom: 20px;
  font-size: var(--text-lg);
  font-weight: 700;
}

.button-wrapper {
  margin-top: 50px;
  text-align: center;
}

button {
  width: 50px;
  height: 50px;
  border: 1px solid transparent;
  border-radius: 50%;
  margin: auto;
  background-color: var(--black);
  background-image: url('../assets/images/icons/arrow.svg');
  background-size: 30%;
  background-position: 20px;
}

.registered button {
  background-position: 18px;
  transform: rotate(180deg);
}

button span {
  width: 0;
  height: 0;
  opacity: 0;
}

.slide-in-enter-active,
.slide-in-leave-active {
  transition: transform 0.5s;
}

.slide-in-enter,
.slide-in-leave-to {
  transform: translateX(-100%);
}

.slide-in-enter-to,
.slide-in-leave {
  transform: translateX(0);
}

@media only screen and (max-width: 500px) {
  .home {
    grid-template-columns: 1fr;
  }

  section {
    height: 100vh;
  }

  .content-wrapper {
    height: 100vh;
    overflow-x: hidden;
    overflow-y: auto;
  }

  button {
    transform: rotate(90deg);
  }

  .registered button {
    transform: rotate(270deg);
  }

  .slide-in-enter,
  .slide-in-leave-to {
    transform: translateX(0);
    transform: translateY(-100%);
  }

  .slide-in-enter-to,
  .slide-in-leave {
    transform: translate(0);
  }
}
</style>
