<!-- <template>
  <div class="footer-wrapper">
footer
  </div>
</template>

<script setup lang="ts">

</script>

<style lang="scss" scoped>
.footer-wrapper {
  background-color: $footer-bg;
}
</style> -->

<template>
  <footer class="footer">
    <div class="footer__content">
      <div class="content-text">
        Is there a project?
        <h1 class="content-text__title">
          Let's work
          <br />
          together
        </h1>
      </div>

      <div class="footer__contact">
        <div class="contact">
          <span>For all questions</span>
          <a href="tel:+79202780068" class="contact__link">+7 (920) 278—00—68</a>
          <a href="mailto:qtim@agency.com" class="contact__link">qtim@agency.com</a>
        </div>

        <div class="contact">
          <span>Office in Russia</span>
          <span>139 Ruben Station Lake, Drew, NM 52678</span>
          <a href="#" class="location__btn"><img src="~/assets/icons/btn-location.svg" alt="location" /></a>
        </div>

        <div class="contact">
          <span>Office in Dubai</span>
          <span>139 Ruben Station Lake, Drew, NM 52678</span>
          <a href="#" class="location__btn"><img src="~/assets/icons/btn-location.svg" alt="location" /></a>
        </div>
      </div>
    </div>

    <div class="footer__bottom">
      <div class="bottom__links">
        <a href="#" class="links__item">Facebook</a>
        <a href="#" class="links__item">Instagram</a>
        <a href="#" class="links__item">Telegram</a>
      </div>

      <div class="bottom__btn">
        <span>Go</span>
      </div>

      <div class="bottom__links">
        <a href="#" class="links__item">Behance</a>
        <a href="#" class="links__item">LinkedIn</a>
        <a href="#" class="links__item">Privacy Policy</a>
      </div>
    </div>
  </footer>
</template>

<script setup></script>

<style lang="scss" scoped>
.footer {
  background-color: $footer-bg;
  font-size: 16px;
  padding: 140px 112px 30px;
}

.footer__content {
  display: flex;
  justify-content: space-between;
}

.content-text__title {
  font-size: 112px;
  font-weight: 400;
  margin-top: 56px;
  text-decoration: underline 1px;
  text-underline-offset: 15px;
}

.footer__contact {
  display: flex;
  flex-direction: column;
  gap: 36px;
  margin-top: 75px;
}

.contact {
  display: flex;
  flex-direction: column;
  gap: 12px;

  &__link {
    color: inherit;
    width: max-content;
    text-decoration: none;

    &:hover {
      text-decoration: underline;
    }
  }
}

.location__btn {
  width: 32px;
  height: 32px;
}

.footer__bottom {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: end;
  margin-top: 143px;
}

.bottom__links {
  display: flex;
  gap: 32px;
}

.links__item {
  color: inherit;
  text-decoration: underline 0.4px;
  text-underline-offset: 6px;
}

.bottom__btn {
  position: absolute;
  left: calc(50% - 358px / 2);
  bottom: -10px;
  display: flex;
  justify-content: center;
  align-items: end;
  background-color: $dark-1;
  width: 358px;
  height: 179px;
  border-top-left-radius: 200px;
  border-top-right-radius: 200px;

  & span {
    color: $gray-1;
    font-size: 32px;
    margin-bottom: 25px;
  }

  &:hover {
    background-color: $gray-2;
    cursor: pointer;
  }
}
</style>
