<script setup>
import AnalyticsAward from '@/views/dashboards/analytics/AnalyticsAward.vue'
import AnalyticsBarCharts from '@/views/dashboards/analytics/AnalyticsBarCharts.vue'
import AnalyticsDatatable from '@/views/dashboards/analytics/AnalyticsDatatable.vue'
import AnalyticsDepositWithdraw from '@/views/dashboards/analytics/AnalyticsDepositWithdraw.vue'
import AnalyticsSalesByCountries from '@/views/dashboards/analytics/AnalyticsSalesByCountries.vue'
import AnalyticsTotalEarning from '@/views/dashboards/analytics/AnalyticsTotalEarning.vue'
import AnalyticsTotalProfitLineCharts from '@/views/dashboards/analytics/AnalyticsTotalProfitLineCharts.vue'
import AnalyticsTransactions from '@/views/dashboards/analytics/AnalyticsTransactions.vue'
import AnalyticsWeeklyOverview from '@/views/dashboards/analytics/AnalyticsWeeklyOverview.vue'
import CardStatisticsVertical from '@core/components/CardStatisticsVertical.vue'
import Router from '@/router'

const totalProfit = {
  title: 'Total Profit',
  color: 'secondary',
  icon: 'mdi-poll',
  stats: '$25.6k',
  change: 42,
  subtitle: 'Weekly Project',
}
const newProject = {
  title: 'New Project',
  color: 'primary',
  icon: 'mdi-briefcase-variant-outline',
  stats: '862',
  change: -18,
  subtitle: 'Yearly Project',
}


onMounted(()=>{
  let tourStarted = sessionStorage.getItem('tour')
  if(!tourStarted){
    introJs().setOptions({
      tooltipClass: 'welcometooltip',
      doneLabel:'Explore',
      hidePrev:true,
      steps:[
        {
          title: 'Guided tour',
          intro: `<div class="logo"><img src="assets/baxter.png"></div>
        <iframe title="vimeo-player" src="https://player.vimeo.com/video/80318319?h=5ab7d6bd9e" width="360" height="200" frameborder="0"    allowfullscreen></iframe>
        <div class="welcome-text"><b>Welcome to baxter</b></div>
        `,
        },
        {
          title: 'Guided tour',
          intro:'<div class="welcome-text">we will guide you through this application to make your experience better.</div>',
        },

        // {
        //   element:document.querySelector('.v-avatar'),
        //   title:'profile section',
        // },

      ],
    }).onexit(function(){
      introJs().setOptions({
        tooltipClass: 'profileSection',
        showProgress:false,
        showBullets:false,
        doneLabel:'Next',
        steps:[
          {
            element:document.querySelector('.v-avatar'),
            intro: `<div class="profile_avatar"><img src="assets/60111.jpg"/></div>
        <div class="text">Here is the profile section of the app where you can update your personal info.</div>`,
          },
        ],
      }).onexit(function(){
        introJs().setOptions({
          tooltipClass: 'profileSection',
          showProgress:false,
          showBullets:false,
          doneLabel:'Jump to Account Settings',
          steps:[
            {
              element:document.querySelector('#accountSetting'),
              intro: `<div class="profile_avatar"><img src="assets/23389494.jpg"/></div>
        <h2 class="mainTitle">Setup Your Account</h2>
        <p class="subtitle">Make it more secure</p>`,
              position: 'right',
            },
          ],
        }).onexit(function(){
          Router.push('/account-settings')
        }).start()}).start()

    }).start()
  }else{
    introJs().setOptions({
      tooltipClass: 'profileSection',
      showProgress:false,
      showBullets:false,
      doneLabel:'Okey',
      steps:[
        {
          element :document.querySelector('#awardTile'),
          intro: `<div class="profile_avatar"><img src="assets/trophy.gif"/></div>
        <p class="subtitle" style="padding:15px">This tile will update you about the best performer of the month</p>`,
          position: 'right',
        },
      ],
    }).onexit(function(){
      Router.push('/')
    }).start()
  }
  
})
</script>

<template>
  <VRow
    class="match-height"
  >
    <VCol
    
      cols="12"
      md="4"
    >
      <AnalyticsAward />
    </VCol>

    <VCol
     
      cols="12"
      md="8"
    >
      <AnalyticsTransactions />
    </VCol>

    <VCol
      cols="12"
      md="4"
    >
      <AnalyticsWeeklyOverview />
    </VCol>

    <VCol
      cols="12"
      md="4"
    >
      <AnalyticsTotalEarning />
    </VCol>

    <VCol
      cols="12"
      md="4"
    >
      <VRow class="match-height">
        <VCol
          cols="12"
          sm="6"
        >
          <AnalyticsTotalProfitLineCharts />
        </VCol>

        <VCol
          cols="12"
          sm="6"
        >
          <CardStatisticsVertical v-bind="totalProfit" />
        </VCol>

        <VCol
          cols="12"
          sm="6"
        >
          <CardStatisticsVertical v-bind="newProject" />
        </VCol>

        <VCol
          cols="12"
          sm="6"
        >
          <AnalyticsBarCharts />
        </VCol>
      </VRow>
    </VCol>

    <VCol
      cols="12"
      md="4"
    >
      <AnalyticsSalesByCountries />
    </VCol>

    <VCol
      cols="12"
      md="8"
    >
      <AnalyticsDepositWithdraw />
    </VCol>

    <VCol cols="12">
      <AnalyticsDatatable />
    </VCol>
  </VRow>
</template>

<style>
.logo img{
  height:80px;
  width:300px;
  text-align: center;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 20px;
}
.introjs-tooltip-header{
background-color:#9155FD;
color:white;
border-top-left-radius:10px;
    border-top-right-radius:10px;

}

.welcome-text{
  text-align: center;
  margin-top: 20px;
}

.welcometooltip{
  min-width: 400px;
  border-radius:10px;
}

.introjs-tooltip-title{
  padding-bottom:10px;
}

 .introjs-nextbutton.introjs-button, .introjs-nextbutton.introjs-button:focus, .introjs-nextbutton.introjs-button:active{
    border:none;
    box-shadow:none;
    background-color:#9155FD;
    color:white;
    border-radius:10px;
    text-shadow: none;
  }

   .introjs-prevbutton.introjs-button, .introjs-prevbutton.introjs-button:focus, .introjs-prevbutton.introjs-button:active{
    border:none;
    box-shadow:none;
    background-color:#F0F0F0;
    color:black;
    border-radius:10px;
    text-shadow: none;
  }

  .profileSection .introjs-tooltip-header{
    display:none;
  }

  .profileSection .introjs-tooltiptext{
    padding:0;
  }

  .profileSection{
    min-width: 250px;
    border-radius: 5px;
  }

  .profileSection .text{
    padding:10px;
    text-align:center;
  }

  .profileSection .introjs-tooltipbuttons{
    display:flex;
    align-items: center;
    justify-content: center;
  }

  .profileSection .subtitle,.profileSection .mainTitle{
    text-align: center;
  }
  

  .profile_avatar img{
    display:block;
    width:100%;
    height:50%;
  }
</style>
