<template>
  <div class="offers">
    <HeadLayout :head="head" />
    <div class="offers__content">
      <ul class="offers__filters">
        <li class="offers__filter" v-for="(link, i) in filters" :key="i" v-show="link.show">
          <button class="offers__link" :class="{ active: i == 0 }" @click="showMoreFilters(link)">
            {{ link.title }}
          </button>
        </li>
      </ul>
      <ul class="offers__articles">
        <li class="offers__article" v-for="offer in offers" :key="offer.id">
          <OffevSmallArticle :offer="offer" />
        </li>
      </ul>

      <nav class="offers__pagination">
        <ul class="offers__pagination-list">
          <li class="offers__pagination-item">
            <router-link class="offers__pagination-link"  to="#">
              <SvgIcon class="offers__pagination-icon" name="left" />
            </router-link>
          </li>
          <li class="offers__pagination-item">
            <span class="offers__pagination-link offers__pagination-link_active"> 1 </span>
          </li>
          <li class="offers__pagination-item"><router-link class="offers__pagination-link" to="#"> 2 </router-link></li>
          <li class="offers__pagination-item"><router-link class="offers__pagination-link" to="#"> 3 </router-link></li>
          <li class="offers__pagination-item offers__pagination-item_desctop"><router-link class="offers__pagination-link" to="#"> 4 </router-link></li>
          <li class="offers__pagination-item offers__pagination-item_desctop"><router-link class="offers__pagination-link" to="#"> 5 </router-link></li>
          <li class="offers__pagination-item">
            <SvgIcon class="offers__pagination-icon" name="more" />
          </li>
          <li class="offers__pagination-item">
            <router-link class="offers__pagination-link" to="#"> 10 </router-link>
          </li>
          <li class="offers__pagination-item">
            <router-link class="offers__pagination-link" to="#"> 20 </router-link>
          </li>

          <router-link class="offers__pagination-link" to="#">
            <SvgIcon class="offers__pagination-icon" name="right" />
          </router-link>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script setup>
  import SvgIcon from "@/components/shared/SvgIcon.vue";
  import OffevSmallArticle from "@/components/shared/OffevSmallArticle.vue";
  import HeadLayout from "@/components/shared/HeadLayout.vue";
  import { ref } from "@vue/reactivity";

  const filters = ref([
    {
      title: "Все предложения",
      show: true,
    },
    {
      title: "Регистрация бизнеса",
      show: true,
    },
    {
      title: "РКО",
      show: true,
    },
    {
      title: "Заявка на РКО",
      show: false,
    },
    {
      title: "Заявка на РКО по фер ссылке",
      show: false,
    },
    {
      title: "Заявка на кредитную карту",
      show: true,
    },
  ]);

  const head = {
    link: "/offers",
    icon: "bank",
    title: "Предложения",
  };

  const offers = [
    {
      logo: "images/logos/logo-bank-open.svg",
      name: "Открытие Банк",
      filter: "РКО",
      price: 5000,
      award: 2,
      offerLink: "/offers/offer",
      list: [
        "<b>0 ₽</b> безлимитные рублевые платежи",
        "<b>До 2 000 000 ₽ бесплатно</b> переводы физ.лицам в месяц",
        "<b>До 5 000 000 ₽ бесплатно</b> внутренние переводы ИП на личный счет",
        "<b>Кэшбэк до 5%</b> по бизнес-карте",
        "<b>до 450 000 ₽</b> на развитие бизнеса от партнеров Банка",
      ],
    },
    {
      logo: "images/logos/mts-bank-logo.jpg",
      name: "МТС Банк",
      filter: "РКО",
      price: 2400,
      award: 4,
      list: [
        "<b>Преимущества открытия счета в МТС Банке:</b>",
        "<b>Реквизиты сразу после заявки:</b> работайте с договорами контрагентов без ожидания.",
        "<b>Бесплатные переводы: </b> совершайте бесплатные переводы на счета физлиц до 1 млн. ₽.",
        "<b>Бонусы от партнеров:</b> откройте счет и получайте доступ к предложениям от партнеров.",
        "<b>Надежность:</b> входим в ТОП-40 банков по активам.",
      ],
    },
  ];

  function showMoreFilters(e) {
    if (e.title == "РКО") {
      filters.value.forEach((element) => {
        element.show = true;
      });
    } else {
      filters.value.forEach((element) => {
        if (element.title == "Заявка на РКО") {
          element.show = false;
        }
        if (element.title == "Заявка на РКО по фер ссылке") {
          element.show = false;
        }
      });
    }
  }
</script>

<style scoped lang="scss">
  @import "@/assets/scss/pages/_offers.scss";
</style>
