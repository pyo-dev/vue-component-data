<template>
  <div class="wrap">
    <div class="parnets-box">
      <div>{{ CONNECT_DATA.PARENT_DATA.grade }}학년 {{ CONNECT_DATA.PARENT_DATA.class }}반</div>
      <div>
        학년 : <input type="text" v-model="CONNECT_DATA.PARENT_DATA.grade">
        반 : <input type="text" v-model="CONNECT_DATA.PARENT_DATA.class">
      </div>
      <div>
        형 이름 : <input type="text" v-model="CONNECT_DATA.CHILD_DATA.first">
        동생 이름 : <input type="text" v-model="CONNECT_DATA.CHILD_DATA.second">
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
    <div class="flex-box">
      <div class="flex-item">
        <ChildFirst
          :CHILD_DATA="CONNECT_DATA.CHILD_DATA"
          @changeData="changeData"
        />
      </div>
      <div class="flex-item">
        <ChildSecond
          :CHILD_DATA="CONNECT_DATA.CHILD_DATA"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ChildFirst from '@/components/Child-first.vue'
import ChildSecond from '@/components/Child-second.vue'

export default {
  name: 'Home',
  
  components: {
    ChildFirst,
    ChildSecond
  },

  data() {
    return {
      CONNECT_DATA: {
        PARENT_DATA: {
          grade: 3,
          class: 2,
        },
        CHILD_DATA: {
          first: '이순신',
          second: '홍길동'
        }
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

  methods: {
    changeData(obj) {
      this.CONNECT_DATA.PARENT_DATA.grade = obj.PARENT_DATA.grade || this.CONNECT_DATA.PARENT_DATA.grade;
      this.CONNECT_DATA.PARENT_DATA.class = obj.PARENT_DATA.class || this.CONNECT_DATA.PARENT_DATA.class;
      this.CONNECT_DATA.CHILD_DATA.first = obj.CHILD_DATA.first || this.CONNECT_DATA.CHILD_DATA.first;
      this.CONNECT_DATA.CHILD_DATA.second = obj.CHILD_DATA.second || this.CONNECT_DATA.CHILD_DATA.second;
    }
  },
}
</script>
<style lang="scss">
  @import '@/assets/css/style.scss';
</style>