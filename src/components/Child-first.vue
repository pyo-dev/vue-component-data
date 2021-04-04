<template>
  <div>
    쌍둥이 형 <br>
    이름: {{ CHILD_DATA.first }}  <br>
    별명: {{ NICK_NAME.first }} 
    <div class="parnets-box">
      <div>바꿔볼까</div>
      <div>
        동생 별명 : <input type="text" v-model="NICK_NAME.second">
      </div>
      <div class="bt-wrap">
        <button @click="clickBtn">바꿔</button>
      </div>
    </div>
    <div class="parnets-box">
      <div>바꿔볼까</div>
      <div>
        학년 : <input type="text" v-model="CHANGE_DATA.PARENT_DATA.grade">
        반 : <input type="text" v-model="CHANGE_DATA.PARENT_DATA.class">
      </div>
      <div>
        형 이름 : <input type="text" v-model="CHANGE_DATA.CHILD_DATA.first">
        동생 이름 : <input type="text" v-model="CHANGE_DATA.CHILD_DATA.second">
      </div>
      <div class="bt-wrap">
        <button @click="changeData(CHANGE_DATA)">바꿔</button>
      </div>
    </div>
  </div>
</template>

<script>

  import EventBus from '@/common/event-bus';

  export default {
    name: 'Child-first',

    props: ['CHILD_DATA'],

    data() {
      return {
        NICK_NAME: {
            first: '거북선',
            second: '도둑'
        },
        CHANGE_DATA: {
          PARENT_DATA: {
            grade: '',
            class: '',
          },
          CHILD_DATA: {
            first: '',
            second: ''
          }
        }
      }
    },

    mounted () {
        this.changeNickFirst();
    },

    methods: {
      changeData() {
        this.$emit('changeData', this.CHANGE_DATA);
      },

      clickBtn(){
        EventBus.$emit('changeNickSecond', this.NICK_NAME.second);
      },

      changeNickFirst() {
        EventBus.$on('changeNickFirst', (data) => {
          this.NICK_NAME.first = data;
        });
      }
    },
  }
</script>