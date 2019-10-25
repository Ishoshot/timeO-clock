<template>
  <div class="hello">
    <div class="ion-page">
      
      <ion-content class="ion-padding" overflow-scroll="true" scroll-y="true">

      <!-- <button class="toggle" @click="modeChanger()">Dark mode</button> -->
        
        <div class="clock-container" v-show="analog">
          <div class="clock">
            <div class="needle hour"></div>
            <div class="needle minute"></div>
            <div class="needle second"></div>
            <div class="center-point"></div>
          </div>
          <div id="date_two" class="date"></div>
          <ion-button @click="goDigital()" class="goto" shape="round">
            GO DIGITAL
            <i class="fa fa-chevron-right" style="margin-left:5px;"></i>
          </ion-button>
        </div>

        <div v-show="digital" class="digital">
          <div class="time"></div>
          <div id="date" class="date"></div>
          <ion-button @click="goAnalog()" class="goto" shape="round">
            <i class="fa fa-chevron-left" style="margin-right:5px;"></i>
            GO ANALOG
          </ion-button>
        </div>

<!--  -->
        <ion-fab vertical="bottom" horizontal="start" slot="fixed">
          
          <ion-fab-button>
            <i class="fa fa-plus"></i>            
          </ion-fab-button>

          <ion-fab-list side="top">

            <ion-fab-button>
              <i class="fa fa-bell"></i>            
            </ion-fab-button>

            <ion-fab-button>
              <i class="fa fa-star"></i>            
            </ion-fab-button>

          </ion-fab-list>

        </ion-fab>
<!--  -->

      </ion-content>
    </div>
  </div>
</template>

<script>

export default {
  
  name: 'Clock',
  
  props: {
    msg: String
  },

  data(){
    return{
      analog:true,
      digital:false,
    }
  },
  
  mounted(){
    this.driveAnalog();
  },

  methods:{

    goDigital(){
      this.analog = !this.analog;
      this.digital = !this.digital;
      this.driveDigital();
    },

    goAnalog(){
      this.analog = !this.analog;
      this.digital = !this.digital;
      // this.driveDigital();
    },

    driveDigital(){

        const time = new Date();
        const date = time.getDate();
        const day = time.getDay();
        const month = time.getMonth();
        const hours = time.getHours();
        const minutes = time.getMinutes();
        const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
        const months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
        const timeEl = document.querySelector('.time');
        const dateEl = document.querySelector('#date');
        timeEl.innerHTML = `${hours < 10 ? `0${hours}` : hours}:${minutes < 10 ? `0${minutes}` : minutes}`;
        dateEl.innerHTML = `${days[day]}, ${months[month]} <span class="circle">${date}</span>`;
    },

    driveAnalog(){
      setInterval(()=>{
        const time = new Date();
        const date = time.getDate();
        const day = time.getDay();
        const month = time.getMonth();
        const hours = time.getHours();
        const hoursForClock = hours % 12;
        const minutes = time.getMinutes();
        const seconds = time.getSeconds();
        const dateEl = document.querySelector('#date_two');
        const hourEl = document.querySelector('.hour');
        const minuteEl = document.querySelector('.minute');
        const secondEl = document.querySelector('.second');
        const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
        const months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
        const scale = (num, in_min, in_max, out_min, out_max) => {
          return (num - in_min) * (out_max - out_min) / (in_max - in_min) + out_min;
        };
        
        hourEl.style.transform = `translate(-50%, -100%) rotate(${scale(hoursForClock, 0, 11, 0, 360)}deg)`;
        minuteEl.style.transform = `translate(-50%, -100%) rotate(${scale(minutes, 0, 59, 0, 360)}deg)`;
        secondEl.style.transform = `translate(-50%, -100%) rotate(${scale(seconds, 0, 59, 0, 360)}deg)`;
        dateEl.innerHTML = `${days[day]}, ${months[month]} <span class="circle">${date}</span>`;
        
      }
      ,1000);
    },
    
    modeChanger(){
      const html = document.querySelector('html');
      const toggle = document.querySelector('toggle');
      if(html.classList.contains('dark'))
      {
        html.classList.remove('dark');
        toggle.target.innerHTML = 'Dark mode';
      } 
      else
      {
        html.classList.add('dark');
        toggle.target.innerHTML = 'Light mode';
      }
    },

  },//Methods
  

}; //export default
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
