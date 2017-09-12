<template>
  <div id="app">
    </h1>{{ title }}</h1>
    <input v-model="newItem" @keyup.enter="addNew">
    <ul v-for="item in items">
      <li v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
        {{ item.label }}
      </li> 
    </ul>
    
    <component-a msgfromfather='world' v-on:child-tell-me-something='listenToMyBoy'></component-a>
  	<p>
  		child tells me: {{ childWords }}
  	</p>
  	
  </div>
</template>

<script>

import Store from './storge';
import componentA from './components/Hello.vue';

export default {
    data: function(){
        return{
            title:"this is ranchy's todo list",
            items: Store.fetch(),
            newItem:'',
            childWords:''
        }
    },
    watch:{
        items:{
            handler:function(items){

                Store.save(items);
            },
            deep: true
        }
    },
    methods:{
        toggleFinish:function(item){

            item.isFinished = !item.isFinished

        },
        addNew:function(){
            this.items.push({
                label:this.newItem,
                isFinished:false
            })
            this.newItem = "";
            
        },
        listenToMyBoy:function(msg){
        		this.childWords = msg;
        }

    },
    components:{ componentA }

}

</script>


<style>
.finished{
  text-decoration:underline
}

</style>
