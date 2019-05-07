<script>
import customH1 from './components/customH1';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    customH1,
  },
  data(){
    return{
      body: '<h1>Загрузка данных</h1>',
    }
  },
  render: function (createElement) {
    return createElement(
        'div',
        {
          domProps: {
            innerHTML: this.body
          }
        }
    )
  },
  mounted() {
    let self = this;
    axios.get('/article.html')
        .then(function (response) {
          self.body = response.data;
        })
        .catch(function (error) {
          console.log(error);
        })
  }
}
</script>
