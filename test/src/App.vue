<template>
  <div id="app">
    <myheader :data-vue="dataVue"></myheader>
    <mylist :persons="persons"></mylist>
  </div>
</template>

<script>
  var dataOut={
    titleName: "通讯录"
  }
  var person=[
    {index:"A",group1:[
      {name:"A张三1",phone:"13411011191",sex:"male"},
      {name:"A女张三2",phone:"1311011192",sex:"female"},
      {name:"A不男不女张三4",phone:"1311011194",sex:"male"}
    ]},
    {index:"B",group1:[
      {name:"B李四1",phone:"13411011191",sex:"male"},
      {name:"B女李四2",phone:"1311011192",sex:"female"},
      {name:"B不男不女李四4",phone:"1311011194",sex:"male"}
    ]},
    {index:"C",group1:[
      {name:"C孙子1",phone:"13411011191",sex:"male"},
      {name:"C女孙子2",phone:"1311011192",sex:"female"},
      {name:"C不男不女孙子4",phone:"1311011194",sex:"male"}
    ]}
  ]
export default {
  name: 'App',
  data:function(){
    return{
      dataVue:dataOut,
      persons:person
    }
  }
}
</script>

<style>
  * {
    margin: 0px;
    padding: 0px;
  }
  /* body{
       height: 2000px;
   }*/
  #app{
    /*子绝父相*/
    position: relative;
  }
  ul{
    list-style: none;
  }
</style>
