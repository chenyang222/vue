<template>
  <div id="app">
    </h1>{{ title }}</h1>
    <input v-model="newitem" @keyup.enter="addNew">
    <ul v-for="item in items">
      <li v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
        {{ item.label }}
      </li>
    </ul>
  </div>
</template>

<script>

export default {
    data: function(){
        return{
            title:"this is ranchy's todo list",
            items:[
    
            ],
            newitem:""
        }
    },
    methods:{
        toggleFinish:function(item){

            item.isFinished = !item.isFinished

        },
        addNew:function(){
            this.items.push({
                label:this.newitem,
                isFinished:false
            })
            this.newitem = "";
        
        }

    }

}

</script>


<style>
.finished{
  text-decoration:underline
}

</style>
