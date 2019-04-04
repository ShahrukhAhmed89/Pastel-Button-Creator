<template>
  <div class="wrapper">
    <Editor 
      :buttonStyle="buttonStyle" 
      :buttonBorderStyle="buttonBorderStyle"
      :buttonAnimations="buttonAnimations"
      @buttonAnimationChange="buttonAnimations=$event" 
    />
    <Display 
      :buttonStyle="buttonStyle" 
      :borderStyle="buttonBorderStyle"
      :buttonAnimations="buttonAnimations"
    />
  </div>
</template>

<script>
import Editor from './Editor'
import Display from './Display'

export default {
  data(){
    return {
      buttonStyle : {
        'borderRadius' : 0,
        'hue': 0,
        'saturation' : 80,
        'light' : 80
      },
      buttonBorderStyle:{
        'boxShadowX'  : 0,
        'boxShadowY'  : 0,
        'blurRadius'  : 0,
        'spreadRadius': 0,
        'shadowHue'   : 0,
        'saturation'  : 0 
      },
    }
  },
  components : {
    Editor,
    Display
  }
}
</script>
