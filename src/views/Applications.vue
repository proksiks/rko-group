<template>
  <div class="applications">
    <div class="applications__head">
      <router-link class="applications__link" to="/applications">
        <SvgIcon class="applications__icon" name="form" />
        <div class="applications__link-text">Заявки</div>
      </router-link>
      <!--<router-link class="applications__link" to="/referrals">
        <SvgIcon class="applications__icon" name="services" />
        <div class="applications__link-text">Реф.Ссылки</div>
      </router-link>-->
      <Button class="applications__button" icon="export" yellow>Экспорт</Button>
      <Button class="applications__button" icon="plus" to="/applications/create" purple> Создать заявку </Button>
    </div>
    <div class="applications__inputs">
      <div class="applications__item">
        <DateSelect />
      </div>
      <div class="applications__item">
        <CustomInput title="ИНН" placeholder="Введите ИНН" :sublistItems="dates" />
      </div>
      <div class="applications__item">
        <CustomInput title="Телефон" placeholder="Введите телефон" :sublistItems="dates" />
      </div>
      <div class="applications__item">
        <CustomSelect
          title="Офферы"
          placeholder="Выберите оффер"
          icon="/images/icons/loupe.svg"
          :sublistItems="offers"
        />
      </div>
      <div class="applications__item">
        <CustomSelect title="Статус" placeholder="Выберите статус" :sublistItems="status" arrow />
      </div>
      <div class="applications__apply">
        <Button class="applications__apply-button" yellow>Применить</Button>
      </div>
    </div>
    <div class="applications__info">
      <table class="applications__table">
        <thead>
          <tr>
            <th>Даты</th>
            <th>Номер</th>
            <th>ИНН</th>
            <th>Юр.лицо</th>
            <th>Телефон</th>
            <th>Город</th>
            <th>Продукт</th>
            <th>Оффер</th>
            <th>Статус</th>
            <th>Детализация</th>
            <th>Доход</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>2023-07-09</td>
            <td>174</td>
            <td>63120000000</td>
            <td>Степанов Олег Александрович</td>
            <td>89999999999</td>
            <td>г.Сызрань Самарская обл.</td>
            <td>RKO</td>
            <td>(1) Локо Банк RKO</td>
            <td>Отправлен</td>
            <td>-</td>
            <td>4000

              <div class="new">
                <SvgIcon class="new__icon" name="new" />
                <div class="new__prompt">

                  <a href="#">Ссылка:</a>
                  Примечание: реферальная ссылка
                </div>
              </div>
            </td>
          </tr>
          <tr>
            <td>2023-07-09</td>
            <td>174</td>
            <td>63120000000</td>
            <td>Степанов Олег Александрович</td>
            <td>89999999999</td>
            <td>г.Сызрань Самарская обл.</td>
            <td>RKO</td>
            <td>(1) Локо Банк RKO</td>
            <td>Отправлен</td>
            <td>-</td>
            <td>4000</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
  import SvgIcon from "@/components/shared/SvgIcon.vue";
  import Button from "@/components/shared/Button.vue";
  import CustomSelect from "@/components/shared/CustomSelect.vue";
  import CustomInput from "@/components/shared/CustomInput.vue";
  import DateSelect from "@/components/shared/DateSelect.vue";

  const showSelect = false;
  const hasPoint = false;

  const dates = [
    {
      title: "Сегодня",
      value: "date-1",
    },
    {
      title: "Вчера",
      value: "date-2",
    },
    {
      title: "Неделя",
      value: "date-3",
    },
    {
      title: "Месяц",
      value: "date-4",
    },
    {
      title: "Квартал",
      value: "date-5",
    },
  ];
  const status = [
    {
      title: "Ошибка",
      value: "status-1",
    },
    {
      title: "Новый",
      value: "status-2",
    },
    {
      title: "Отправлен",
      value: "status-3",
    },
    {
      title: "Холд",
      value: "status-4",
    },
    {
      title: "Принято",
      value: "status-5",
    },
    {
      title: "Отменена",
      value: "status-5",
    },
  ];
  const offers = [
    {
      title: "(3) Локо Банк РКО",
      value: "offer-1",
    },
    {
      title: "(12) Касса Тинькофф",
      value: "offer-2",
    },
    {
      title: "(10) Тинькофф - Кредит для Бизнеса",
      value: "offer-3",
    },
    {
      title: "(3) Локо Банк РКО",
      value: "offer-1",
    },
    {
      title: "(12) Касса Тинькофф",
      value: "offer-2",
    },
    {
      title: "(10) Тинькофф - Кредит для Бизнеса",
      value: "offer-3",
    },
  ];
</script>

<style scoped lang="scss">
  @import "@/assets/scss/pages/_applications.scss";
</style>
