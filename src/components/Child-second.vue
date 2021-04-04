<template>
  <div>
    쌍둥이 동생 <br>
    이름: {{ CHILD_DATA.second }}  <br>
    별명: {{ NICK_NAME.second }} 
    <div class="parnets-box">
      <div>바꿔볼까</div>
      <div>
        형 별명 : <input type="text" v-model="NICK_NAME.first">
      </div>
      <div class="bt-wrap">
        <button @click="clickBtn">바꿔</button>
      </div>
    </div>
  </div>
</template>

<script>
  import EventBus from '@/common/event-bus';

  export default {
    name: 'Child-second',

    props: ['CHILD_DATA'],

    data() {
      return {
        NICK_NAME: {
            first: '거북선',
            second: '도둑'
        },
      }
    },

    mounted () {
        this.changeNickSecond();
    },

    methods: {
      clickBtn(){
        EventBus.$emit('changeNickFirst', this.NICK_NAME.first);
      },

      changeNickSecond() {
        EventBus.$on('changeNickSecond', (data) => {
          this.NICK_NAME.second = data;
        });
      }
    },
  }
</script>