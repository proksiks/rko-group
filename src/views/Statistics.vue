<template>
  <div class="statistics">
    <div class="statistics__wrapper">
      <div class="statistics__boxes">
        <div class="statistics__box">
          <div class="statistics__head statistics__head_border">
            <div class="statistics__title">Заработок</div>
            <div class="statistics__select">
              <SimpleSelect :options="options" v-model="income" placeholder="Выберите дату" />
            </div>
          </div>
          <table class="statistics__balances">
            <thead>
              <tr>
                <th>Всего, RUB</th>
                <th>Баланс, RUB</th>
                <th>Холд, RUB</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>0</td>
                <td>0</td>
                <td>0</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="statistics__box">
          <div class="statistics__head">
            <div class="statistics__title">Баланс</div>
          </div>
          <table class="statistics__table">
            <thead>
              <tr>
                <th>Валюта</th>
                <th>Всего</th>
                <th>Баланс</th>
                <th>Холд</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>RUB</td>
                <td>0</td>
                <td>0</td>
                <td>0</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <div class="statistics__item statistics__item_first">
        <div class="statistics__box">
          <div class="statistics__head">
            <div class="statistics__title">Баланс</div>
            <div class="statistics__select">
              <SimpleSelect :options="options" v-model="balance" placeholder="Выберите дату" />
            </div>
          </div>
          <div class="statistics__chart statistics-chart">
            <div class="statistics-chart__filters">
              <button class="statistics-chart__filter statistics-chart__filter_active">Лиды</button>
              <button class="statistics-chart__filter">Конверсии</button>
              <button class="statistics-chart__filter">Доход</button>
            </div>
            <Chart />
          </div>
        </div>
      </div>
      <div class="statistics__item">
        <div class="statistics__box">
          <div class="statistics__head">
            <div class="statistics__title">Последнии операции по заявкам</div>
            <router-link class="statistics__link" to="/applications">
              <SvgIcon class="statistics__svg" name="prime-link" />
            </router-link>
          </div>
          <div class="statistics__auto-scroll">
            <table class="statistics__operations">
              <thead>
                <tr>
                  <th>Дата</th>
                  <th>Номер</th>
                  <th>Статус</th>
                  <th>Оффер</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>2023-07-09</td>
                  <td>174</td>
                  <td>Отправлен</td>
                  <td>(5) Райфайзен</td>
                </tr>
                <tr>
                  <td>2023-07-09</td>
                  <td>237</td>
                  <td>Отклонён</td>
                  <td>(1) МТС Банк RKO</td>
                </tr>
                <tr>
                  <td>2023-07-09</td>
                  <td>187</td>
                  <td>Выполнен</td>
                  <td>(3) Локо Банк RKO</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

    <div class="statistics__sub-title">Конверсии</div>

    <div class="statistics__inputs">
      <div class="statistics__item">
        <DateSelect />
      </div>
      <div class="statistics__item">
        <CustomSelect
          title="Офферы"
          placeholder="Выберите оффер"
          icon="/images/icons/loupe.svg"
          :sublistItems="offers"
        />
      </div>

      <div class="statistics__item">
        <CustomSelect title="Статус (Конверсии)" placeholder="Выберите статус" :sublistItems="status" arrow />
      </div>

      <div class="statistics__item">
        <CustomSelect
          title="ID Конверсии"
          placeholder="ID Конверсии"
          icon="/images/icons/loupe.svg"
          :sublistItems="offers"
        />
      </div>

      <div class="statistics__apply">
        <Button class="statistics__apply-button" yellow>Применить</Button>
      </div>
    </div>

    <div class="statistics__info">
      <table class="statistics__info-table">
        <thead>
          <tr>
            <th>ID</th>
            <th>Дата создания</th>
            <th>Оффер</th>
            <th>ГЕО | IP</th>
            <th>Устройство</th>
            <th>Статус</th>
            <th>Доход</th>
            <th>Sub1</th>
            <th>Sub2</th>
            <th>Sub3</th>
            <th>Referrer</th>
            <th>Комментарий</th>
            <th>ID Рекламодателя</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>ID0043</td>
            <td>2023-07-09</td>
            <td>(1) Локо Банк RKO</td>
            <td>65:5453:543</td>
            <td>-</td>
            <td>Отправлен</td>
            <td>799</td>
            <td></td>
            <td></td>
            <td></td>
            <td>-</td>
            <td>-</td>
            <td>4000</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
  import Chart from "@/components/shared/Chart.vue";
  import SvgIcon from "@/components/shared/SvgIcon.vue";
  import SimpleSelect from "@/components/shared/SimpleSelect.vue";
  import CustomSelect from "@/components/shared/CustomSelect.vue";
  import Button from "@/components/shared/Button.vue";
  import DateSelect from "@/components/shared/DateSelect.vue";
  import { reactive, ref } from "@vue/reactivity";
  const options = reactive(["за сегодня", "за неделю", "за месяц", "за год"]);

  const balance = ref("за сегодня");
  const income = ref("за сегодня");
</script>

<style scoped lang="scss">
  @import "@/assets/scss/pages/_statistics.scss";
</style>
