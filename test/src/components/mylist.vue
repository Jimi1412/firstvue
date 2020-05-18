<template>
  <div id="mylist">
    <div>
      <ul>
        <li v-for="item in persons">
          <div class="indexChar">{{item.index}}</div>
          <ul>
            <li  v-for="it in item.group1" @click="nameClick(it)">
              <div :class="it.sex=='male'? 'divHead male':'divHead female'"></div>
              <div>{{it.name}}</div>
            </li>
          </ul>
        </li>
      </ul>
    </div>
    <div class="allChars" ref="allChars">
      <ul>
        <li v-for="item in allIndex" @click="clickIdx(item)">{{item}}</li>
      </ul>
    </div>
  </div>
</template>
<script>
    import mymsgbox from './MyMsgBox.js'
    export default {
        name: 'mylist',
        props:{
          persons:{
            type:Array,
            default:[]
          }
        },
        methods:{
          nameClick:function(it){
            mymsgbox({
              name:it.name,
              phone:it.phone,
              sex:it.sex,
              call:function(ev){
                alert("打电话给"+it.name+"\r\n号码是："+it.phone)
              },
              cancel:function(ev){
                var div=document.getElementById("mymsgbox")
                document.body.removeChild(div)
              }
            });
          },
          clickIdx:function(item){
            var divs=document.getElementsByClassName("indexChar");
            for(var i =0;i<divs.length;i++){
              if(divs[i].innerText==item){
                var topvalue=divs[i].offsetTop;
                //   游览器的兼容
                document.body.scrollTop=topvalue;
                if(document.body.scrollTop==0){
                  document.documentElement.scrollTop=topvalue;
                }
                break;
              }
            }
          }
        },
        computed:{
          allIndex:function(){
            var list=[];
            for(var i=0;i<this.persons.length;i++){
              list.push(this.persons[i].index)
            }
            return list;
          }
        },
        mounted:function(){
          var winHeight=window.innerHeight;
          var divHeight=this.$refs.allChars.offsetHeight;
          var locate=(winHeight-50-divHeight)/2
          this.$refs.allChars.style.marginTop=(locate+50)+'px';
        }
      }
</script>
<style>
  #mylist{
    position: absolute;
    width: 100%;
    left: 0px;
    top: 50px;
  }
  .indexChar{
    height: 50px;
    line-height: 50px;
    width: 100%;
    background-color: #cccccc;
    font-size: 20px;
    /*缩进*/
    text-indent: 10px;
  }
  /*兄弟选择器  每个联系人的样式*/
  .indexChar+ul>li{
    height: 80px;
    line-height: 80px;
    width: 100%;
    background-color: white;
    font-size: 20px;
    border-bottom: 1px solid grey;
  }
  .divHead{
    width: 50px;
    height:  50px;
    border-radius: 50%;
    float: left;
    border: 5px solid grey;
    /*上右下左*/
    margin: 9px 10px 5px 10px;
  }
  .male{
    background:url("../assets/male.jpg") 0 0 no-repeat;
    background-size:contain;
  }
  .female{
    background:url("../assets/female.jpg") 0 0 no-repeat;
    background-size:contain;
  }
  /*侧边栏*/
  .allChars{
    width: 40px;
    /*background-color: pink;*/
    position: fixed;
    right: 5px;
    top: 0px;
    font-size: 20px;
    text-align: center;
  }
</style>
