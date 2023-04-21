<template>
    <Page class="page">
      <ActionBar title="Прогноз погоды" />
      <ScrollView>
        <StackLayout class="div">
          
          <Label class="label" text="Введите название города" />
          <TextField class="text-field" v-model="cityName" />
          <Button class="button" text="Узнать погоду" @tap="getWeather" />

          <StackLayout orientation="horizontal">
            <StackLayout>
              <Label class="day" text="Пятница" v-if="dt_txt_1"/>
              <Label class="label" :text="description_1" v-if="description_1" />
              <Label class="label" :text="'температура: ' + temperature_1 + '°C'" v-if="temperature_1" />
              <Label class="label" :text="'ощущается как' + ': ' + feels_like_1 + '°C'" v-if="feels_like_1" />
              <Label class="label" :text="'давление' + ': ' + pressure_1 + ' мм рт.ст.'" v-if="pressure_1" />
              <Label class="label" :text="'скорость ветра' + ': ' + wind_1 + ' м/с'" v-if="wind_1" />
              <Label class="label" v-else-if="loading" text="Загрузка..." />
              <Label class="label" v-else-if="error" text="Ошибка" />
            </StackLayout>
            <StackLayout class="test" width="50%">
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/01d@2x.png" width="140" height="140" v-if="icon_id_01_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/02d@2x.png" width="140" height="140" v-if="icon_id_02_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/03d@2x.png" width="140" height="140" v-if="icon_id_03_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/04d@2x.png" width="140" height="140" v-if="icon_id_04_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/09d@2x.png" width="140" height="140" v-if="icon_id_09_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/10d@2x.png" width="140" height="140" v-if="icon_id_10_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/11d@2x.png" width="140" height="140" v-if="icon_id_11_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/13d@2x.png" width="140" height="140" v-if="icon_id_13_1"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/50d@2x.png" width="140" height="140" v-if="icon_id_50_1"/>
            </StackLayout>
          </StackLayout>
          <StackLayout orientation="horizontal">
            <StackLayout>
              <Label class="day" text="Суббота" v-if="dt_txt_2"/>
              <Label class="label" :text="description_2" v-if="description_2" />
              <Label class="label" :text="'температура: ' + temperature_2 + '°C'" v-if="temperature_2" />
              <Label class="label" :text="'ощущается как' + ': ' + feels_like_2 + '°C'" v-if="feels_like_2" />
              <Label class="label" :text="'давление' + ': ' + pressure_2 + ' мм рт.ст.'" v-if="pressure_2" />
              <Label class="label" :text="'скорость ветра' + ': ' + wind_2 + ' м/с'" v-if="wind_2" />
              <Label class="label" v-else-if="loading" text="Загрузка..." />
              <Label class="label" v-else-if="error" text="Ошибка" />
            </StackLayout>
            <StackLayout class="test" width="50%">
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/01d@2x.png" width="140" height="140" v-if="icon_id_01_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/02d@2x.png" width="140" height="140" v-if="icon_id_02_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/03d@2x.png" width="140" height="140" v-if="icon_id_03_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/04d@2x.png" width="140" height="140" v-if="icon_id_04_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/09d@2x.png" width="140" height="140" v-if="icon_id_09_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/10d@2x.png" width="140" height="140" v-if="icon_id_10_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/11d@2x.png" width="140" height="140" v-if="icon_id_11_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/13d@2x.png" width="140" height="140" v-if="icon_id_13_2"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/50d@2x.png" width="140" height="140" v-if="icon_id_50_2"/>
            </StackLayout>
          </StackLayout>
          <StackLayout orientation="horizontal">
            <StackLayout>
              <Label class="day" text="Воскресенье" v-if="dt_txt_3"/>
              <Label class="label" :text="description_3" v-if="description_3" />
              <Label class="label" :text="'температура: ' + temperature_3 + '°C'" v-if="temperature_3" />
              <Label class="label" :text="'ощущается как' + ': ' + feels_like_3 + '°C'" v-if="feels_like_3" />
              <Label class="label" :text="'давление' + ': ' + pressure_3 + ' мм рт.ст.'" v-if="pressure_3" />
              <Label class="label" :text="'скорость ветра' + ': ' + wind_3 + ' м/с'" v-if="wind_3" />
              <Label class="label" v-else-if="loading" text="Загрузка..." />
              <Label class="label" v-else-if="error" text="Ошибка" />
            </StackLayout>
            <StackLayout class="test" width="50%">
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/01d@2x.png" width="140" height="140" v-if="icon_id_01_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/02d@2x.png" width="140" height="140" v-if="icon_id_02_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/03d@2x.png" width="140" height="140" v-if="icon_id_03_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/04d@2x.png" width="140" height="140" v-if="icon_id_04_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/09d@2x.png" width="140" height="140" v-if="icon_id_09_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/10d@2x.png" width="140" height="140" v-if="icon_id_10_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/11d@2x.png" width="140" height="140" v-if="icon_id_11_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/13d@2x.png" width="140" height="140" v-if="icon_id_13_3"/>
              <Image class="img" horizontalAlignment="right" src="https://openweathermap.org/img/wn/50d@2x.png" width="140" height="140" v-if="icon_id_50_3"/>
            </StackLayout>
          </StackLayout>
          
          
        </StackLayout>
      </ScrollView>
    </Page>
  </template>

<script>
import { Http } from '@nativescript/core'

export default {
  data() {
    return {
      dt_txt_1: null,
      cityName_1: '',
      wind_1: null,
      description_1: null,
      pressure_1: null,
      feels_like_1: null,
      temperature_1: null,
      icon_id_1: null,

      dt_txt_2: null,
      cityName_2: '',
      wind_2: null,
      description_2: null,
      pressure_2: null,
      feels_like_2: null,
      temperature_2: null,
      icon_id_2: null,

      dt_txt_3: null,
      cityName_3: '',
      wind_3: null,
      description_3: null,
      pressure_3: null,
      feels_like_3: null,
      temperature_3: null,
      icon_id_3: null,

      
      loading: false,
      error: false,

      icon_id_01_1: null,
      icon_id_02_1: null,
      icon_id_03_1: null,
      icon_id_04_1: null,
      icon_id_09_1: null,
      icon_id_10_1: null,
      icon_id_11_1: null,
      icon_id_13_1: null,
      icon_id_50_1: null,

      icon_id_01_2: null,
      icon_id_02_2: null,
      icon_id_03_2: null,
      icon_id_04_2: null,
      icon_id_09_2: null,
      icon_id_10_2: null,
      icon_id_11_2: null,
      icon_id_13_2: null,
      icon_id_50_2: null,

      icon_id_01_3: null,
      icon_id_02_3: null,
      icon_id_03_3: null,
      icon_id_04_3: null,
      icon_id_09_3: null,
      icon_id_10_3: null,
      icon_id_11_3: null,
      icon_id_13_3: null,
      icon_id_50_3: null,
    };
  },
  methods: {
    getWeather() {
      this.loading = true;
      this.error = false;

      this.icon_id_01_1 = null,
      this.icon_id_02_1 = null,
      this.icon_id_03_1 = null,
      this.icon_id_04_1 = null,
      this.icon_id_09_1 = null,
      this.icon_id_10_1 = null,
      this.icon_id_11_1 = null,
      this.icon_id_13_1 = null,
      this.icon_id_50_1 = null,

      this.icon_id_01_2 = null,
      this.icon_id_02_2 = null,
      this.icon_id_03_2 = null,
      this.icon_id_04_2 = null,
      this.icon_id_09_2 = null,
      this.icon_id_10_2 = null,
      this.icon_id_11_2 = null,
      this.icon_id_13_2 = null,
      this.icon_id_50_2 = null,

      this.icon_id_01_3 = null,
      this.icon_id_02_3 = null,
      this.icon_id_03_3 = null,
      this.icon_id_04_3 = null,
      this.icon_id_09_3 = null,
      this.icon_id_10_3 = null,
      this.icon_id_11_3 = null,
      this.icon_id_13_3 = null,
      this.icon_id_50_3 = null,



      Http.request({
        url: `https://api.openweathermap.org/data/2.5/forecast?q=${this.cityName}&appid=a582e94516825c0150c39d41b0eeb93b&units=metric&lang=ru`,
        method: 'GET'
      }).then(response => {
        console.log(response)
        const result = response.content.toJSON();

        this.dt_txt_1 = result.list[0].dt_txt;
        this.temperature_1 = result.list[0].main.temp;
        this.feels_like_1 = result.list[0].main.feels_like;
        this.icon_id_1 = result.list[0].weather[0].icon;
        this.pressure_1 = result.list[0].main.pressure;
        this.description_1 = result.list[0].weather[0].description;
        this.wind_1 = result.list[0].wind.speed;
        switch (this.icon_id_1) {
          case '01d':
            this.icon_id_01_1 = this.icon_id_1;
            break;
            case '02d':
            this.icon_id_02_1 = this.icon_id_1;
            break;
            case '03d':
            this.icon_id_03_1 = this.icon_id_1;
            break;
            case '04d':
            this.icon_id_04_1 = this.icon_id_1;
            break;
            case '09d':
            this.icon_id_09_1 = this.icon_id_1;
            break;
            case '10d':
            this.icon_id_10_1 = this.icon_id_1;
            break;
            case '11d':
            this.icon_id_11_1 = this.icon_id_1;
            break;
            case '13d':
            this.icon_id_13_1 = this.icon_id_1;
            break;
            case '50d':
            this.icon_id_50_1 = this.icon_id_1;
            break;
        }
        
        this.dt_txt_2 = result.list[7].dt_txt;
        this.temperature_2 = result.list[7].main.temp;
        this.feels_like_2 = result.list[7].main.feels_like;
        this.icon_id_2 = result.list[7].weather[0].icon;
        this.pressure_2 = result.list[7].main.pressure;
        this.description_2 = result.list[7].weather[0].description;
        this.wind_2 = result.list[7].wind.speed;
        switch (this.icon_id_2) {
          case '01d':
            this.icon_id_01_2 = this.icon_id_2;
            break;
            case '02d':
            this.icon_id_02_2 = this.icon_id_2;
            break;
            case '03d':
            this.icon_id_03_2 = this.icon_id_2;
            break;
            case '04d':
            this.icon_id_04_2 = this.icon_id_2;
            break;
            case '09d':
            this.icon_id_09_2 = this.icon_id_2;
            break;
            case '10d':
            this.icon_id_10_2 = this.icon_id_2;
            break;
            case '11d':
            this.icon_id_11_2 = this.icon_id_2;
            break;
            case '13d':
            this.icon_id_13_2 = this.icon_id_2;
            break;
            case '50d':
            this.icon_id_50_2 = this.icon_id_2;
            break;
        }

        this.dt_txt_3 = result.list[15].dt_txt;
        this.temperature_3 = result.list[15].main.temp;
        this.feels_like_3 = result.list[15].main.feels_like;
        this.icon_id_3 = result.list[15].weather[0].icon;
        this.pressure_3 = result.list[15].main.pressure;
        this.description_3 = result.list[15].weather[0].description;
        this.wind_3 = result.list[15].wind.speed;
        switch (this.icon_id_3) {
          case '01d':
            this.icon_id_01_3 = this.icon_id_3;
            break;
            case '02d':
            this.icon_id_02_3 = this.icon_id_3;
            break;
            case '03d':
            this.icon_id_03_3 = this.icon_id_3;
            break;
            case '04d':
            this.icon_id_04_3 = this.icon_id_3;
            break;
            case '09d':
            this.icon_id_09_3 = this.icon_id_3;
            break;
            case '10d':
            this.icon_id_10_3 = this.icon_id_3;
            break;
            case '11d':
            this.icon_id_11_3 = this.icon_id_3;
            break;
            case '13d':
            this.icon_id_13_3 = this.icon_id_3;
            break;
            case '50d':
            this.icon_id_50_3 = this.icon_id_3;
            break;
        }

        this.loading = false;
      }).catch(error => {
        this.loading = false;
        this.error = true;
        console.log(error)
      })
      
    }
  }
};
</script>

<style scoped lang="scss">
    @import '@nativescript/theme/scss/variables/blue';

    // Custom styles

    .day {
      color: rgb(255, 255, 255);
      font-size: 28px;
    }
    .label {
      color: rgb(255, 255, 255);
      font-size: 18px;
    }
    .div {
      background-color: rgb(73, 142, 231);
    }
    .text-field {
      font-size: 18px;
      color: rgb(255, 255, 255);
    }
    .img {
      margin-top: 90px;
    }

</style>
