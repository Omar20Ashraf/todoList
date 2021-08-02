<template>
	<div class="container">
		
		<div class="heading">
			<h2 id="title">ToDo List</h2>

			<addItemForm v-on:relodList="getList()" />

		</div>

		<listView :items="items" v-on:relodList="getList()"/>
	</div>
</template>

<script>
	import addItemForm from './AddItemForm';

	import listView from './ListView';

export default {

  name: 'AppComponent',
  components : {
  	addItemForm,
  	listView,
  },
  data() {
    return {
    	items:[]
    };
  },

  methods:{
  	getList(){
  		axios.get('api/item')
  		     .then(response => {
  		     		this.items = response.data
  		     })
  		     .catch(error =>{
  		     		console.log( error )
  		     })
  	}
  },

  created(){
  	this.getList();
  }
};
</script>

<style scoped>

	.container{
		width: 350px;
		margin: auto;
	}

	.heading{
		background: #e6e6e6;
		padding: 10px;
	}

	#title{
		text-align: center;
	}
</style>
