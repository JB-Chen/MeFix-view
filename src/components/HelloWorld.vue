<template>
  <div v-loading.fullscreen.lock="fullscreenLoading">
    <!-- 导航栏 -->
      <div class="nav d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom box-shadow" :style="isTransparent">
        <h5 class="my-0 mr-md-auto font-weight-normal"><span style="color:#000;font-weight: bold;">MeFix</span>|智能设备的完美服务站</h5>
        <nav class="my-2 my-md-0 mr-md-3">
          <a class="p-2 text-dark" href="#">首页</a>
          <a class="p-2 text-dark" href="#fixMoney">维修报价</a>
          <a class="p-2 text-dark" href="#order">续约订单</a>
          <a class="p-2 text-dark" href="#question">常见问题</a>
        </nav>
        <a class="btn btn-outline-primary" href="#">登录</a>
    </div>

    <!-- 幻灯片 -->
    <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
      <ol class="carousel-indicators">
        <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
        <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
        <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
      </ol>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img class="d-block w-100" src="https://static.shanxiuxia.com/best2.0/images/banner.a3bd6269.png" alt="First slide">
        </div>
        <div class="carousel-item">
          <img class="d-block w-100" src="https://static.shanxiuxia.com/best2.0/images/banner.008e06f5.png" alt="Second slide">
        </div>
        <div class="carousel-item">
          <img class="d-block w-100" src="https://static.shanxiuxia.com/best2.0/images/banner.495d943d.png" alt="Third slide">
        </div>
      </div>
      <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
      </a>
      <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
      </a>
    </div>

    <!-- 介绍 -->
    <div class="intro">
      <!-- 服务介绍 -->
      <div class="mateNum">
         <p>服务覆盖<span class="number">{{mateNum}}</span>在校大学生</p>
      </div>
      <!-- 维修介绍 -->
      <div class="introCompenent imgF">
         <img src="http://best.shanxiuxia.com/images/index/in-door.svg" alt="..." class="rounded">
         <span>免费上门</span>
      </div>
       <div class="introCompenent">
         <img src="http://best.shanxiuxia.com/images/index/engineer.svg" alt="..." class="rounded">
         <span>专业工程师</span>
      </div>
       <div class="introCompenent">
         <img src="http://best.shanxiuxia.com/images/index/baoxiu.svg" alt="..." class="rounded">
         <span>半年保修</span>
      </div>
       <div class="introCompenent">
         <img src="http://best.shanxiuxia.com/images/index/pinzhi.svg" alt="..." class="rounded">
         <span>品质配件</span>
      </div>
       <div class="introCompenent imgL">
         <img src="http://best.shanxiuxia.com/images/index/luxiang.svg" alt="..." class="rounded">
         <span>全程录像</span>
      </div>
    </div>

    <!-- 品牌手机维修报价 -->
    <div id="fixMoney">

        <div class="brand">
          <li v-for="(item,index) in list" :key="index" class="b_name" :data-type="Btype[index]" @click="changeItem(index)"><p>{{item.b_name}}</p></li>
        </div>
        <div style="width:100%;height:2%;background-color:#F5F5F5;"></div>
        <div class="model" >
          <li class="m_name" v-for="(item,index) in modelLists" :key="index" :data-type="Mtype[index]" @click="changeFaults(index)">
            {{item.model_name}}
            <span class="badge badge-pill badge-danger" style="margin-left:10px;" v-if="index==0">热门</span>
          </li>
          
        </div>
        <div class="faults">
          <div class="f_L">
            <div class="f_name" v-for="(item,index) in faultsL" :key="index">
              <div style="width:65%;color:#000;font-size:18px;">
                <div style="width:50%;float:left;height:50px;line-height:50px;">{{item.breakName}}</div>
                 
                <div style="width:50%;height:100%;float:right;">
                  <span style="color:#EE7700;font-size:24px;"> ￥{{item.newMoney}}</span>
                   <li style="list-style-type:none;text-decoration:line-through;color:#999999;font-size:15px;">￥{{item.oldMoney}}</li>
                </div>
              </div>
             
              <a href="#order" @click="changeBreakInf(item.breakName,item.newMoney)">
                <button type="button" class="btn btn-outline-warning" style="border:1px solid #EE7A59;color:#EE7A59;">立即下单</button>
              </a>
              </div>
            
          </div>

         <div class="f_R">
            <div class="f_name" v-for="(item,index) in faultsR" :key="index">
              <div style="width:65%;color:#000;font-size:18px;">
                <div style="width:50%;float:left;height:50px;line-height:50px;">{{item.breakName}}</div>
                 
                <div style="width:50%;height:100%;float:right;">
                  <span style="color:#EE7700;font-size:24px;"> ￥{{item.newMoney}}</span>
                   <li style="list-style-type:none;text-decoration:line-through;color:#999999;font-size:15px;">￥{{item.oldMoney}}</li>
                </div>
              </div>
             
             <a href="#order" @click="changeBreakInf(item.breakName,item.newMoney)">
                <button type="button" class="btn btn-outline-warning" style="border:1px solid #EE7A59;color:#EE7A59;">立即下单</button>
              </a>
              </div>
            
          </div>
        </div>
    </div>


    <div class="card mb-3">
      <img class="card-img-top" src="http://best.shanxiuxia.com/images/index/service-think.png" alt="Card image cap">
      <div class="card-body" style="margin-top:-200px;color:#fff;">
        <h5 class="card-title">MeFix</h5>
        <p class="card-text">属于大学生的智能设备服务站，打造“数码咨询+数码二手+电子维修+手机租赁+二手回收”的智能设备消费闭环</p>
        <p class="card-text"><small  style="color:#fff">用心提供服务</small></p>
      </div>
    </div>
   
    <!-- 填写订单表格 -->
    <div id="order" v-loading="loading" element-loading-text="提交订单中" element-loading-spinner="el-icon-loading" element-loading-background="rgba(0, 0, 0, 0.8)">
      <div style="width:80%;height:100%;margin-left:20%;">
          <p style="color:#000;font-weight:blod;font-size:40px;margin-right:20%">我要预约</p>
          <el-form ref="form" :model="form" label-width="80px" class="col-md-12 col-sm-12">
              <el-form-item label="品牌型号" class="col-md-10 col-sm-10">
                <el-select v-model="form.brandName" placeholder="请选择手机品牌" class="col-md-4 col-sm-4" @change="changeOrderItem()">
                  <el-option v-for="(item,index) in list" :key="index" :label="item.b_name" :value="item.b_name"></el-option>
                </el-select>

                <el-select v-model="form.modelName" placeholder="请选择手机型号" class="col-md-6 col-sm-6" @change="changeOrderFaults()">
                  <el-option v-for="(item,index) in modelLists" :key="index" :label="item.model_name" :value="item.model_name"></el-option>
                </el-select>
              </el-form-item>

              <el-form-item label="故障类型" class="col-md-10 col-sm-10">
                <el-select v-model="form.breakName" placeholder="请选择故障类型" class="col-md-10 col-sm-10" @change="changeOrderMoney()">
                  <el-option v-for="(item,index) in breakList" :key="index" :label="item.breakName" :value="item.breakName"></el-option>
                </el-select>
              </el-form-item>

              <el-form-item label="维修方式" class="col-md-10 col-sm-10">
                <el-select v-model="form.fixMethod" placeholder="请选择维修方法" class="col-md-10 col-sm-10" @change="changeFixMethod()">
                  <el-option v-for="(item,index) in fixMethod" :key="index" :label="item" :value="item"></el-option>
                </el-select>
              </el-form-item>


              <el-form-item label="" class="col-md-9 col-sm-9" v-if="form.fixMethod == '邮寄维修'">
                <el-alert type="success" class="col-md-11 col-sm-11" style="float:right;margin-right:-10px">{{fixAddress}}</el-alert>
              </el-form-item>
             
              <el-form-item label="选择网点" class="col-md-10 col-sm-10" v-if="form.fixMethod == '网点维修'">
                <el-select v-model="form.address" placeholder="请选择对应网点" class="col-md-10 col-sm-10">
                  <el-option v-for="(item,index) in addressList" :key="index" :label="item.address" :value="item.address"></el-option>
                </el-select>
              </el-form-item>


              <el-form-item label="预留信息" class="col-md-10 col-sm-10">
                <el-input v-model="form.name" placeholder="姓名" class="col-md-4 col-sm-4"></el-input>
                <el-input v-model="form.phoneNum" placeholder="电话号码" class="col-md-6 col-sm-6"></el-input>
              </el-form-item>


              <el-form-item label="你的地址" class="col-md-12 col-sm-12" v-if="form.fixMethod == '上门维修'">
                <v-distpicker class="col-md-6 col-sm-6" style="float:left" @selected="onSelected"></v-distpicker>
              </el-form-item>
              
              <el-form-item label="" class="col-md-10 col-sm-10" v-if="form.fixMethod == '上门维修'">
               
                <el-input v-model="form.address" placeholder="具体位置" class="col-md-10 col-sm-10"></el-input>
              </el-form-item>
                
              <el-form-item label="备注" class="col-md-10 col-sm-10">
                <el-input v-model="form.content" placeholder="内容" class="col-md-10 col-sm-10"></el-input>
              </el-form-item>

              <el-form-item class="col-md-10 col-sm-10">
              <p style="color:#EE7700;font-size:30px;float:left" class="col-md-4 col-sm-4">
                ￥{{form.newMoney}}
              </p>
              </el-form-item>

              <el-form-item class="col-md-3 col-sm-3" style="margin-top:-20px">
                <el-checkbox class="col-md-3 col-sm-4" v-model="form.checked"> 提交订单即同意 <a>维修服务协议</a> </el-checkbox>
              </el-form-item>

              <el-form-item class="col-md-9 col-sm-9">
                <el-button class="col-md-3 col-sm-3" type="primary" style="float:right" @click="submitForm">立即创建</el-button>
              </el-form-item>
            </el-form>
      </div>
    
    </div>

    <!-- 常见问题 -->
    <div id="question" >
        <h2 style="color:#000;font-weight:blod;font-size:35px;">你可能会关心的问题</h2>
        <div style="width:100%;">
          <p style="font-size:20px;color:#000;font-weight:blod;">
            现在开放哪些高校？
          </p><br/><br/>
          <p>
            meFix现在已经开通了珠海市6所本科院校，北理，北师，吉珠，中山大学，暨南大学，UIC等均可提供上门维修业务！
          </p>
        </div><br/><br/>

      <div style="width:100%;">
          <p style="font-size:20px;color:#000;font-weight:blod;">
            不支持上门的学习怎么办？
          </p><br/><br/>
          <p>
           未覆盖上门维修学校学生可以选择寄修服务，将需要维修的设备邮寄到最近的维修中心，mefix负责双向顺丰邮寄费用，详情可咨询客服。 
          </p>
      </div><br/><br/>

       <div style="width:100%;">
          <p style="font-size:20px;color:#000;font-weight:blod;">
            下单后的服务流程是怎样的?
          </p><br/><br/>
          <p>
           请保持电话畅通，闪修侠工程师/客服会尽快联系您，确认设备故障及上门时间地点，工程师会在约定的时间内上门维修，维修完成后用户在线支付。
          </p>
      </div><br/><br/>

      
       <div style="width:100%;">
          <p style="font-size:20px;color:#000;font-weight:blod;">
            外屏碎和内外屏都碎怎么区分？
          </p><br/><br/>
          <p>
           如果屏幕碎了，但图像可以正常显示，就只是外屏碎。如果图片显示不正常或者完全无法显示，则内屏也碎了。 
          </p>
      </div><br/><br/>

      <div style="width:100%;">
          <p style="font-size:20px;color:#000;font-weight:blod;">
            更换的配件是保修时长多久？
          </p><br/><br/>
          <p>
           更换的配件保修期一般为180天（内存升级及软件升级服务除外） 
          </p>
      </div><br/><br/>



       <div style="width:100%;">
          <p style="font-size:20px;color:#000;font-weight:blod;">
            新电池更换后出现不耐用的情况是怎么回事？
          </p><br/><br/>
          <p>
           电池出厂都不是满电，一般情况下会有虚电。新电池刚使用，因为电芯未完全被激活，导致电量不稳定不耐用等情况，属于正常现象，首次充电6-8小时为宜，以后每次充电只充4-6小时即可。 
          </p>
      </div><br/><br/>

        
    </div>

   
    <!--页脚 -->
    <footer class="footer">
      <p class="mb-1">&copy; 2017-2018 github for JB-Chen</p>
      <ul class="list-inline">
        <li class="list-inline-item"><a href="#">粤ICP</a></li>
        <li class="list-inline-item"><a href="#">未备案</a></li>
        <li class="list-inline-item"><a href="#">等待支持</a></li>
      </ul>
    </footer>

    <!-- 返回顶部和联系客服 -->
    <div class="addFunc" :style="funcTransparent">
      <div class="block one" @click="backTop()">
        <img src="../assets/top.png">
        <p>放回顶部</p>
      </div>
      <div class="block two">
        <img src="../assets/iphone.png">
        <p>客服</p>
      </div>
    </div>


  </div>
</template>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.nav{
  position: fixed;
  top: 0px;
  left: 0px;
  z-index: 666;
  width:100%;
  height: 60px;
}
.carousel{
  margin-top: 62px;
}
.intro{
  
  background-color: #fff;
  height: 290px;
  width: 100%;
  padding-left: 15%;
  padding-right: 15%;
  margin-bottom: 50px;
  .mateNum{
    padding-top:30px;
    color: #333333;
    font-size: 25px;
    letter-spacing: 8px;
    font-family: "微软雅黑";
    padding-bottom: 10px;
    .number{
      font-size: 45px;
      color:#F37B46;
      font-weight: bold;
    }
  }
  .introCompenent{
    margin-left: 5%;
    float: left;
    width: 15%;
    height: 180px;
    padding-bottom: 10px;
    img{
      width: 100%;
      height: 100px;
    }
  }
}
#fixMoney{
  margin-top:100px;
  width: 80%;
  background-color: #fff;
  height: 750px;
  margin: auto;
  margin-bottom: 40px;
  .brand{
      width: 100%;
      height: 13%;
      // background-color: red;
      .b_name{
        float: left;
        width: 14.28%;
        height: 100%;
        border-right: 2px solid #EDEDED;
        display: flex;
        justify-content:center;
        align-items:Center;
        color: #000;
         
        p{
          
          font-size: 20px;
        }
      }
      li[data-type='1']{
        color:#EE7A59;
        border:1px solid #EE7A59;
        border-bottom:4px solid #EE7A59;
        
      }
    }
    .model{
      width: 20%;
      height: 85%;
      // background-color: blue;
      float: left;
      overflow-y:scroll;

      .m_name{
        width: 100%;
        height: 14.2%;
        display: flex;
        justify-content: center;
        align-items: center;
        color:black;
        font-size: 18px;
      }

      li[data-type="1"]{
        border-left: 5px solid #333333;
        background-color: #ECEEEF;
      }
    }
    .faults{
      width:80%;
      height: 85%;
      // background-color: green;
      float: right; 
      .f_L{
        width: 50%;
        height: 100%;
        // background-color: red;
        float: left;
        border-right: 1px solid #CCCCCC;
        overflow: hidden;
      }
      .f_R{
        width: 50%;
        height: 100%;
        float: right;
      }
      .f_name{
        width: 100%;
        height: 14.2%;
        // background-color: #4444;
        display: flex;
        justify-content: center;
        align-items: center;
      }
    }
}
.addFunc{
  width: 6%;
  height: 200px;
  right: 0px;
  top:500px;
  position: fixed;
  .one{
    background-color: #EE7700;
  }
  .two{
    background-color: #fff;
  }
  .block{
    height: 50%;
    width:100%;
    img{
      margin-top:20px;
      width: 50px;
      height:50px;
    
    }
    p{
      text-align: center;
    }
  }
}
#order{
  padding-top:100px;
  background-color: #fff;
  margin-bottom: 100px;
}
#question{
  width:80%;
  // height: 500px;
  margin: auto;
  padding-top:40px;
  p{
    float: left;
  }
}
.form-row{
  width: 100%;
  .form-group{
    width: 100%;
  }
}

.footer{
  margin-top:40px;
  margin-bottom:40px;
}
</style>
<script>
 import VDistpicker from 'v-distpicker'
import Axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      mateNum:0,
      isTransparent:'opacity:1;',
      funcTransparent:'opacity:0;',
    
      faultsL:[],
      faultsR:[],


      list:null,
      Btype:[],
      modelLists:null,
      Mtype:[],
      breakList:null,

      brandName:'苹果',
      modelName:null,
      breakName:null,

      form:{
        brandName:'苹果',
        modelName:'',
        breakName:'',
        oldMoney:'',
        newMoney:'0',
        fixMethod:'上门维修',
        name:'',
        phoneNum:'',
        address:'',
        content:'',
        checked:true
      },

      fixMethod:['上门维修','邮寄维修','网点维修'],

      fixAddress:'请将手机寄到：北京理工大学珠海学院       收件人：陈锦彬     联系电话：0000-0000-0000',

      addressList:null,

      fullscreenLoading:false,

      loading:false
    }
  },
  components: { VDistpicker },
  mounted(){
    window.addEventListener('scroll',this.handleScroll);
    this.autoAdd();
  },
  created(){
    this.getBrandData(); 
    this.getAddressData()
  },
  methods:{
    getAddressData() {
      var api = 'api/tp5/public/index.php/Index/Index/getAddressData'
      Axios.get(api).then(res => {
        // console.log(res.data)
        this.addressList = res.data
      }).catch(error => {
        console.log('error:', error.message)
      })
    },
    onSelected(data) {
      // alert(data.province + ' | ' + data.city + ' | ' + data.area)
      console.log(data)

      this.form.address = data.province.value+','+data.city.value+','+data.area.value
    },
    changeFixMethod(){
      this.form.address = ''
    },
    // 改变手机品牌函数
    changeItem(index){
      this.Btype = []
      this.Mtype = []
      for(let i=0;i<this.list.length;i++){
        if(i==index){
            this.Btype.push(1)
          }else{
            this.Btype.push(0);
          }
      }
      this.brandName = this.list[index].b_name
      this.form.brandName = this.list[index].b_name
      this.form.breakName =''
      // console.log(this.brandName)
      this.getModelData(this.list[index].b_name)

    },
    changeOrderItem(){
      // console.log(this.form)
      let index;
      for(let i=0;i<this.list.length;i++){
        if(this.list[i].b_name==this.form.brandName){
           index = i;
        }
      }
      this.Btype = []
      this.Mtype = []
      for(let i=0;i<this.list.length;i++){
        if(i==index){
            this.Btype.push(1)
          }else{
            this.Btype.push(0);
          }
      }
       this.getModelData(this.form.brandName)
       this.form.breakName =''

    },
    changeBreakInf(breakInf,newMoney){
      this.breakName = breakInf
      this.form.breakName = breakInf
      this.form.brandName = this.brandName
      this.form.modelName = this.modelName
      this.form.newMoney = newMoney
    },

    // 改变故障类型函数
    changeFaults(index){
      
      this.Mtype = []
      for(let i=0;i<this.modelLists.length;i++){
        if(i==index){
            this.Mtype.push(1)
          }else{
            this.Mtype.push(0);
          }
      }
      this.modelName = this.modelLists[index].model_name
      this.form.modelName = this.modelLists[index].model_name
      this.getBreakData(this.modelLists[index].model_name)
    },
    changeOrderFaults(){
      this.getBreakData(this.form.modelName)
      console.log("test")
      console.log(this.form.modelName)
      let index;
      for(let i=0;i<this.modelLists.length;i++){
        if(this.modelLists[i].model_name==this.form.modelName){
           index = i;
        }
      }
      this.Mtype = []
      for(let i=0;i<this.modelLists.length;i++){
        if(i==index){
            this.Mtype.push(1)
          }else{
            this.Mtype.push(0);
          }
      }  
      this.form.breakName = ''
    },
  
    changeOrderMoney(){
      console.log(this.form.breakName)

      for(let i=0;i<this.breakList.length;i++){
        if(this.breakList[i].modelName == this.form.modelName && this.breakList[i].breakName == this.form.breakName){
          console.log(this.breakList[i])
          this.form.newMoney = this.breakList[i].newMoney
        }
      }
    },
    // 滚动监听函数
    handleScroll(){
      var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
      // console.log(scrollTop);
      if(scrollTop>0){
         this.isTransparent='opacity:0.8;';
         this.funcTransparent='opacity:1;'
      }
      if(scrollTop==0){
        this.isTransparent='opacity:1;';
        this.funcTransparent='opacity:0;'
      }
    },
    // 返回顶部函数
    backTop() {
        document.body.scrollTop = 0
        document.documentElement.scrollTop = 0
    },
    // 自动增加函数
    autoAdd(){
      for(let i=0;i<40000;i++){
        setTimeout(()=>this.mateNum = this.mateNum+1,'50');
        
      }
    },

    //获取手机品牌
    getBrandData(){
      var api = 'api/tp5/public/index.php/Index/Index/brandData'
      Axios.get(api).then(res => {
        // console.log(res.data)
        for(let i=0;i<res.data.length;i++){
          if(i==0){
            this.Btype.push(1)
          }else{
            this.Btype.push(0);
          }
        }
        this.list = res.data
        this.brandName = this.list[0].b_name
        this.form.brandName = this.list[0].b_name
        this.getModelData(this.list[0].b_name)
        this.getBreakData('iPhone 6'),
        this.fullscreenLoading = false
      }).catch(error => {
        console.log('error:', error.message)
      })
    },

      // 获取错误信息
    getBreakData(name){
      this.faultsL = [],
      this.faultsR = []
      var getBreakList = 'api/tp5/public/index.php/Index/Index/getBreak'
      Axios.post(getBreakList, {
        model: name
      }).then(res => {
        this.breakList = res.data
      
          for(let i=0;i<res.data.length;i++){
            if(i<7){
              this.faultsL.push(res.data[i])
            }else{
              this.faultsR.push(res.data[i])
            }
          }
       
        
        // console.log(this.breakList)
      })
    },


    // 获取对应手机型号
    getModelData(name){
      var getModelApi = 'api/tp5/public/index.php/Index/Index/getModel'
      Axios.post(getModelApi, {
        name: name
      }).then(res => {
         this.modelLists = res.data
         this.modelName = this.modelLists[0].model_name
         this.form.modelName = this.modelLists[0].model_name
        // console.log(res.data)
        for(let i=0;i<res.data.length;i++){
          if(i==0){
            this.Mtype.push(1)
          }else{
            this.Mtype.push(0);
          }
        }

        this.getBreakData(this.modelName)
       
     
        // console.log(this.modelLists);
      }).catch(error => {
        console.log('error', error.message)
      })
    },

    // 提交表单数据
    submitForm(){

      if(this.form.checked == false){
        this.$confirm('请提前阅读并同意维修服务协议, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });          
        });
      }else{
          console.log("提交表单数据")
          console.log(this.form)
          this.loading  = true
          var orderApi = 'api/tp5/public/index.php/Index/Index/submitOrder'
          Axios.post(orderApi, {
            brandName: this.form.brandName,
            modelName: this.form.modelName,
            breakName: this.form.breakName,
            oldMoney:this.form.oldMoney,
            newMoney:this.form.newMoney,
            fixMethod:this.form.fixMethod,
            name:this.form.name,
            phoneNum:this.form.phoneNum,
            address:this.form.address,
            content:this.form.content
          }).then(res => {
            console.log(res.data)
            if (res.data === 'success') {

              
              this.loading = false

              this.form.brandName = '苹果'
              this.form.modelName = ''
              this.form.breakName = ''
              this.form.oldMoney = ''
              this.form.newMoney = '0'
              this.form.fixMethod = '上门维修',
              this.form.name = '',
              this.form.phoneNum = '',
              this.form.content = '',
              this.form.checked  = true

              this.$message('提交成功');

            }else{
              this.$message.error('提交失败，请检查订单信息');
            }
          }).catch(error => {

            
            console.log('error', error.message)
          })
      }
      
    }
  
  }
}
</script>


