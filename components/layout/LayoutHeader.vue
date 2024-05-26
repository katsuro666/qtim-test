<template>
  <div class="header">
    <NuxtLink to="/"><img src="~/assets/icons/Qtim.svg" alt="logo" /></NuxtLink>

    <div class="header__info">
      <ul class="header__menu">
        <li class="menu__item">
          <NuxtLink to="/">Works</NuxtLink>
        </li>
        <li class="menu__item">
          <NuxtLink to="/">About</NuxtLink>
        </li>
      </ul>

      <div class="header__btns">
        <button class="btns__language">
          <img src="~/assets/icons/united-kingdom.svg" alt="flag of the uk" />
        </button>

        <button class="btns__work">Let's work</button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 40px;
}

.header__info {
  display: flex;
  align-items: center;
  gap: 91px;
}

.header__menu {
  display: flex;
  list-style: none;
  gap: 58px;
  margin: 0;
  padding: 0;
}

.menu__item > * {
  text-decoration: none;
  color: $dark-1;
}

.header__btns {
  display: flex;
  gap: 16px;

  & *:hover {
    cursor: pointer;
  }
}

.btns__language {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: transparent;
  width: 52px;
  height: 52px;
  border: rgba(0, 0, 0, 0.1) solid 2px;
  border-radius: 50%;
}

.btns__work {
  background-color: $dark-1;
  color: $text-light;
  border-radius: 50px;
  padding: 16px 32px;
}
</style>
