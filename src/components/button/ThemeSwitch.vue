<template>
  <div
    @click="toggleDarkMode"
    class="toggle"
    :class="{ 'light-toggle': !isDarkMode, 'dark-toggle': isDarkMode }"
  >
    <div
      class="toggle-switch"
      :class="{ 'toggle-left': !isDarkMode, 'toggle-right': isDarkMode }"
    >
      <img class="toggleIcon" v-if="!isDarkMode" src="@/assets/icons/sun.svg" />
      <img class="toggleIcon" v-if="isDarkMode" src="@/assets/icons/moon.svg" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'ThemeSwitch',
  computed: {
    isDarkMode() {
      return this.$store.getters.isDarkMode
    },
  },
  methods: {
    toggleDarkMode() {
      this.$store.commit('toggleDarkMode')
    },
  },
}
</script>

<style scoped lang="scss">
.toggle {
  border-radius: 10px;
  width: 175px;
  @media (max-width: 900px) {
    width: 135px;
  }
  box-sizing: border-box;
  display: flex;
  cursor: pointer;
}

.light-toggle {
  background: linear-gradient(346.78deg, #f7fcfc 0%, #fafcfa 100%);
  border: 1px solid rgba(0, 0, 0, 0.04);
  box-shadow: inset 0px 5px 10px rgba(0, 0, 0, 0.1);
}

.dark-toggle {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: inset 0px 5px 10px rgba(255, 255, 255, 0.1);
}

.toggle-switch {
  margin: 2px;
  padding: 15px 35px;
  border-radius: 8px;
  @media (max-width: 900px) {
    padding: 10px 28px;
    margin: 1px;
  }
}

.toggle-left {
  transform: translateX(0);
  background: #ffffff;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}

.toggle-right {
  transform: translateX(92%);
  background: #1b233f;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}
.toggleIcon {
  @media (max-width: 900px) {
    width: 12px;
  }
}
</style>
