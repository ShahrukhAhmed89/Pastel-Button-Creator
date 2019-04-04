<template>
    <div class="display-wrapper">
        <div class="display_button">
            <button id="button_design" 
                :class="buttonAnimations"
                :style="{ 
                    borderRadius: buttonStyle.borderRadius + 'px', 
                    backgroundColor : `hsla( ${buttonStyle.hue},  ${buttonStyle.saturation}%, ${buttonStyle.light}%, 1)`,
                    color : `hsla( ${buttonStyle.hue}, 25%, 25%, 1)`,
                    boxShadow: `${borderStyle.boxShadowX}px ${borderStyle.boxShadowY}px ${borderStyle.blurRadius}px ${borderStyle.spreadRadius}px hsla( ${borderStyle.shadowHue},  ${borderStyle.saturation}%, ${buttonStyle.light}%, 1)`
                }">
               my btn
            </button>
        </div>
        <div class="display_code">
            <!-- <div class="code_button-wrapper"><button class="code_copyButton" @click="copyCode">copy</button></div> -->
            <transition  mode="out-in">
                <div key=1 v-if="copied" class="code_button-wrapper" ><button class="code_copied" >copied</button></div>
                <div key=2 v-else class="code_button-wrapper" @click="copyCode"><button class="code_copied" >copy</button></div>
            </transition>
            <div class="code_css">
                <pre class="language-css">
                    <code v-html="codeDisplay" id="code">
                       
                    </code>
                </pre>
             </div>
        </div>
    </div>
</template>

<script>
export default {
    props : ['buttonStyle', 'borderStyle', 'buttonAnimations'],
    data(){
        return {copied : false}
    },
    computed : {
        codeDisplay(){
            return `
<span class="token selector">.btn</span> <span class="token punctuation">{</span>
    <span class="token property">border-radius</span><span class="token punctuation">: </span>${this.buttonStyle.borderRadius}px<span class="token punctuation">;</span>
    <span class="token property">color</span><span class="token punctuation">: </span>hsla(${this.buttonStyle.hue}, 25%, 25%, 1)<span class="token punctuation">;</span>
    <span class="token property">background-color</span><span class="token punctuation">: </span>hsla(${this.buttonStyle.hue}, ${this.buttonStyle.saturation}%, ${this.buttonStyle.light}%, 1)<span class="token punctuation">;</span>
    <span class="token property">box-shadow</span><span class="token punctuation">: </span>${this.borderStyle.boxShadowX}px ${this.borderStyle.boxShadowY}px ${this.borderStyle.blurRadius}px ${this.borderStyle.spreadRadius}px hsla( ${this.borderStyle.shadowHue},  ${this.borderStyle.saturation}%, ${this.buttonStyle.light}%, 1)<span class="token punctuation">;</span>
    <span class="token property">font-size</span><span class="token punctuation">: </span>1rem<span class="token punctuation">;</span>
    <span class="token property">border</span><span class="token punctuation">: </span>0<span class="token punctuation">;</span>
    <span class="token property">padding</span><span class="token punctuation">: </span>16px 32px<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
`
        }
    },
    methods : {
        copyCode(){
            var temptext= document.createElement('textarea')
            temptext.id = 'temparea'
            document.body.appendChild(temptext)
            document.getElementById(temptext)
            temptext.value =document.getElementById('code').innerText
            var selector = document.querySelector('#temparea')
            selector.select()
            document.execCommand('copy')
            document.body.removeChild(temptext)
            
            this.copied = !this.copied
            let that = this
            setTimeout(function() {
                debugger;
                that.copied = false;
            }, 750); 
           
        }
    }

}
</script>

