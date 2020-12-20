<template>
  <div id="app" v-cloak>
    <!--<img alt="Vue logo" src="./assets/logo.png">
    <input v-model="message" placeholder="edit">
    <br>
    <div>
      <button @click="show = !show">Click</button>
      <button @click="di()">di</button>
    </div>
    <input type="checkbox" v-model="agree" name="" id="">dong y dieu khoan
    <input type="radio" value="hn" v-model="city" name="city" id="">hn
    <input type="radio" value="dn" v-model="city" name="city" id="">dn
    <input type="radio" value="hcm" v-model="city" name="city" id="">hcm
    {{city}}
    <div v-show="show">Lop hoc full stack</div>
    <select v-model="language" name="" id="" multiple>
      <option value="html">html</option>
      <option value="css">css</option>
      <option value="js">js</option>
    </select>
    <br> 
    <a href="#" @click.prevent = "curentTab = 1">Tab1</a>
    <a href="#" @click.prevent = "curentTab = 2">Tab2</a>
    <a href="#" @click.prevent = "curentTab = 3">Tab3</a>
    <div v-show="curentTab == 1 ">noi dung 1</div>
    <div v-show="curentTab == 2 ">noi dung 2</div>
    <div v-show="curentTab == 3 ">noi dung 3</div>
    <div v-hide></div>
    <div>
      <button v-show="curentTab > 1 " @click="curentTab--">next</button>
      <button v-show="curentTab < 4 " @click="curentTab++">next</button>
      <button>back</button>
    </div>
    <select v-model="link" name="" id="">
      <option value="http://laptrinhcuocsong.com">ltcs</option>
      <option value="http://nhaccuatui.com">nct</option>
      <option value="http://zingmp3.com">mp3</option>
    </select>
    <a :href="link">Click </a> 
    <input type="text" name="" id="" :disabled = 'lock'> 
    <button @click="lock = !lock" :class="{xanh: lock, do: !lock}">
        <span v-show="lock == false">Lock</span>
        <span v-show="lock == true">Unlock</span>
    </button>
    <input type="text" name="" id="" v-model="newStudent">
    <button @click="students.push(newStudent)">Add</button>
    <div v-for = "(student, index) in students" :key="index">
      {{ student }} {{index}}
    </div>-->
    
    <div class="list">
      <div v-for="(language, index) in languages" @click="language.selected = !language.selected" :key="index" :class="{selected: language.selected}">
      {{language.name}}
    </div>
    </div>
    <hr>
    <div>
      <button @click="add('abc')">Add</button>
      <button>Remove</button>
    </div>
    <hr>
    <div class="list">
      <div v-for="(selectedLanguage, index) in selectedLanguages" @click="selectedLanguage.selected = !selectedLanguage.selected" :key="index" :class="{selected: selectedLanguage.selected}">
      {{selectedLanguage.name}}
    </div>
<<<<<<< HEAD
    </div>-->
    <!-- Ngay 17/12/2020-->
=======
    </div>
>>>>>>> 0ebda1fd303542b9fb14359130863d66ac77cd05
    <Menu/>
    <Article
      v-for="(article, index) in articles"
      :key="index"
      :article="article"
    />
    <input type="text" v-model="person.name" ref="name">
    <ul>
      <li><a href="#" @click.prevent="page = 1">1</a></li>
      <li><a href="#" @click.prevent="page = 2">2</a></li>
      <li><a href="#" @click.prevent="page = 3">3</a></li>
    </ul>
    <div v-for="(product, index) in products" :key="index">
      <h3>{{ product.name }}</h3>
      <div>{{ product.price | formatMoney }}</div>
    </div>
    <hr>
    <div>{{ products.reduce((total, product) => total + product.price, 0) | formatMoney }}</div>
  </div>
</template>

<script>
import Menu from './components/Menu.vue';
import Article from './components/Article.vue';
export default {
  data() {
    return {
      /**
      message:'doan cong trun',
      show: true,
      agree: false,
      city: 'hn',
      curentTab: 1,
      hide: true,
      link: 'http://laptrinhcuocsong.com',
      lock: true,
      newStudent: '',
      students: ['a', 'b', 'c']
      */
     //ngay 17/12/2020 
      languages: [
        {name: 'html', selected: false},
        {name: 'css', selected: false},
        {name: 'js', selected: false},
        {name: 'python', selected: false},
        {name: 'C', selected: false}
      ],
      selectedLanguages: [
        {name: 'nodejs', selected: false}
      ],
      articles: [
        {title: 'bai viet 1', content: 'noi dung 1'},
        {title: 'bai viet 2', content: 'noi dung 2'},
        {title: 'bai viet 3', content: 'noi dung 3'},
        {title: 'bai viet 4', content: 'noi dung 4'},
      ],
      person: {
        name: ''
      },
      page: 1,
      products: [
        {name: 'iphone', price: 1000000},
        {name: 'iphonex', price: 11000000}
      ]
    }
  },
  mounted() {
    this.$refs.name.focus()
  },
  watch: {
    page: function() {
      this.loadData();
    },
    person: {
    handler: function(newvValue, oldValue) {
      console.log(newvValue, oldValue);
      },
      deep: true
    }
  },
  methods: {
    loadData: function() {
      console.log('load data');
    }
  },
  components: {
    Menu,
    Article
  },
  filters: {
    formatMoney: function(money) {
      return Number((money).toFixed(1)).toLocaleString()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
span {
  border: 1px solid black;
  display: inline-block;
  margin-right: 5px;
  padding: 3px 10px;
  border-radius: 2px;
}
.selected {
  background-color: green;
}
</style>
