
<script>
import Logo from './Logo.vue';


    export default {
      components:{
  Logo,
  
  },
  data(){
            return{
                scrolledNav:null,
                mobile:null,
                mobileNav:null,
                windowWidth:null,
            }
        },
        created(){
            window.addEventListener('resize',this.checkScreen)
            this.checkScreen()
        },

        mounted(){
            window.addEventListener('scroll',this.updateScroll)
        },
        methods: {
            toggleMobileNav(){
                this.mobileNav =!this.mobileNav;
                
            },

            updateScroll() {
                const scrollPosition = window.scrollY;
                if(scrollPosition > 460){
                    this.scrolledNav = true;
                    return
                }
                this.scrolledNav = false
            },

            checkScreen(){
                this.windowWidth =window.innerWidth;
                if(this.windowWidth <= 1000){
                    this.mobile = true
                    return
                }
                this.mobile = null;
                this.mobileNav = null;
                return;
            },
            scrollToTop(){
              window.scrollTo(0, 0);
            }
        },
    }
</script>
<template>
 
    <header class="header container justify-content-between p-3 " :class="{'scrolled-nav':scrolledNav}"> 
     
      <a class="navbar-brand text-white m-0  " href="/">SKINCARE AI</a>
      <nav class="navbar d-flex align-items-center   ">
        <div v-show="!mobile" >
            <div class="navbar1 d-flex ">
              <div>
                <ul class="navigation d-flex gap-4 p-0 m-0">
                  <router-link @click="scrollToTop"   class="nav-link  "  to="/">Home</router-link>
                  <router-link @click="scrollToTop"  class="nav-link "  to="/">About Us</router-link>
                  <router-link @click="scrollToTop"    class="nav-link "  to="/">Our Services</router-link>
                  <router-link @click="scrollToTop"    class="nav-link "  to="/">App Features</router-link>
                  <router-link @click="scrollToTop"    class="nav-link "  to="/">Shop</router-link>
                  <router-link @click="scrollToTop"    class="nav-link "  to="/">Help Center</router-link>
              </ul> 
              </div>
            </div>
          </div>
           <div class="icon ">
            <svg  @click="toggleMobileNav" v-if="mobile" :class="{'icon-active':mobileNav}" width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M5 11.6667H35" stroke="#fff4ea" stroke-width="1.5" stroke-linecap="round"/>
              <path d="M5 20H35" stroke="#fff4ea" stroke-width="1.5" stroke-linecap="round"/>
              <path d="M5 28.3333H35" stroke="#fff4ea" stroke-width="1.5" stroke-linecap="round"/>
              </svg>   
      </div>  
         </nav> 
        
     

     <transition name="mobile-nav">
      <ul  v-if="mobileNav" class="dropdown-nav " >
        <div class="d-flex  justify-content-end align-items-center w-100 ">
        
            

          <svg class="icon "  v-show="mobile" @click="toggleMobileNav" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M1.51611 22.4859L12.0021 11.9999L22.4881 22.4859M22.4881 1.51392L12.0001 11.9999L1.51611 1.51392" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </div>
        
        <svg class="icon "  v-show="!mobile" @click="toggleMobileNav" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M1.51611 22.4859L12.0021 11.9999L22.4881 22.4859M22.4881 1.51392L12.0001 11.9999L1.51611 1.51392" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          
          
        <router-link  @click="toggleMobileNav();"  class="nav-link "  to="/">Home</router-link>
        <router-link  @click="toggleMobileNav();"  class="nav-link"  to="/services">Services</router-link>
           <router-link  @click="toggleMobileNav()"  class="nav-link"  to="/portfolio">Portfolio</router-link>
           <router-link  @click="toggleMobileNav();"  class="nav-link"  to="/products">Products</router-link>
           <router-link  @click="toggleMobileNav()"  class="nav-link"  to="/about">About</router-link>
           <router-link  @click="toggleMobileNav()"  class="nav-link mb-5 "  to="/contact">Contact</router-link>


       </ul>   
     </transition>
       
     
   
      <div  v-show="!mobile">
        <div class="">
          <router-link  class="text-decoration-none  btn2" to="/">  Login</router-link>     
       </div>
      </div>
   </header>

</template>
<style scoped>
*{
  font-family: 'Jost', sans-serif;
}
.btn2{
  background: rgba( 255, 255, 255, 0.15 );
  backdrop-filter: blur( 15.5px );
  -webkit-backdrop-filter: blur( 15.5px );
  border: 1px solid rgba( 255, 255, 255, 0.18 );
  padding: 5px 10px;
  color: white;
  border-radius: 5px;
  font-family: 'Jost', sans-serif;
  font-size: 13px;
  font-weight: 400;

}
.scrolled-nav{
  background-color: rgb(141, 132, 132,0);
  box-shadow: 0 20px 50px rgb(0 0 0 / 46%);
  height: 50px;
  transition: .3s ease;
}

.scrolled-nav header{
  padding: 3px 10%;
}

.scrolled-nav .logo img{


}

.scrolled-nav .navbar a{
  font-size: 12px;
  color: rgb(255, 255, 255);
}

 .nav-link{
  padding-right:20px ;
  color: #FFFFFF !important;

 }
 
 
 .mobile-nav-enter-active,.mobile-nav-leave-active{
 transition: 1s ease all;
 }
 
 .mobile-nav-enter-from,.mobile-nav-leave-to{
  transform: translateX(550px);
 }

 .mobile-nav-enter-to{
  transform: translateX(0);
 }

 .header{
  display: flex;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  right: 0;
  background:#0b3229;
  z-index: 9999;
  border-bottom: 1px solid #3a5950;
}
nav.navbar{
  display: flex;
  flex-wrap: nowrap;
  align-items: center;
  justify-content: center;
}

.navbar-brand {
  margin-left: 40px;
}

.icon{
  cursor: pointer;
}


.dropdown-nav{
  display: flex;
  flex-direction: column;
  position: fixed;
  width: 25%;
  height: 100vh;
  background: #05021A;
  top: 0px;
  right: 0;
  gap: 5px;
  padding: 30px;
  font-size: 40px; 
  color: #FFFFFF;
  z-index: 100;
  align-items: flex-end;
 
 } 

.dropdown-nav li{
   margin-left: 0;
   list-style: none;
   
}

.dropdown-nav a{
  color: #FFFFFF;
  text-decoration: none;
  padding: 5px;
}

nav.navbar a{
  box-shadow: inset 0 0 0 0 #4e5051;
  color: #2E00E4; 
  padding: 4px;
  font-size: 13px;
  font-weight: 200;
  transition: color .3s ease-in-out, box-shadow .3s ease-in-out ;
  text-decoration: none;
}

@media (max-width:1124px){
  
   .header{
    padding: 10px;
   }
  
   .header .nav-links.active{
      position: fixed;
      height: 100vh;
      width: 100%;
      top: 0;
      left: 0;
      display: flex;
      flex-direction: column ;
      justify-content: center;
      align-items: center;
      background: white;
      
   }
  

  
   .dropdown-nav {
    display: flex;
    flex-direction: column;
    position: fixed;
    width: 100% !important;
    height: 100vh !important;
    background:  #0b3229;
    top: 0!important;
    right: 0 !important;
    gap: 20px;
    
    padding: 30px;
    font-size: 40px;
    color: #FFFFFF;
    z-index: 100;
    align-items: flex-end;
}
   header nav.navbar a{
      box-shadow: inset 0 0 0 0 #54b3d6;
      color: #383850;
      font-weight:bold;
      padding: 4px;
      font-size: 14px;
      transition: color .3s ease-in-out, box-shadow .3s ease-in-out ;
      font-family: 'Jost', sans-serif;
  }
  .navbar-brand {
    margin-left: 0px;
  }
  
  
}

@media (max-width:495px) {
.dropdown-nav{
  display: flex;
  flex-direction: column;
  position: fixed;
  width: 100% !important;
  height: 100vh !important;
  background: #0b3229;
  top: 0px;
  right: 0;
  gap: 20px;
  padding: 30px;
  font-size: 40px;
  color: #FFFFFF;
  z-index: 100;
  align-items: flex-end;
}
.navbar-brand a {
  height: 20px;
}
.header{
  padding-top: 5px !important;
  padding-bottom: 5px !important;
}

.navbar-brand {
  margin-left: 0px;
}
}
</style>