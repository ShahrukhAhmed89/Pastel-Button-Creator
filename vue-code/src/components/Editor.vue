<template>
    <div class="editor-wrapper">
        <div class="editor">
            <div class="editor-sections">
                <h2>Button Design</h2>
                <div class="form-container">
                    <label class="slider-label" for="border-radius">Change Border Radius</label>
                    <input
                        class="slider" 
                        type="range"
                        name="border-radius"  
                        min="0" 
                        max="30" 
                        value="0"
                        @input="$emit('buttonStyle', buttonStyleValues.borderRadius = $event.target.value)"
                    >
                </div>
                <div class="form-container">
                    <label class="slider-label" for="hue">Change Background Color</label>
                    <input
                        class="slider color-slider"  
                        type="range"
                        name="hue"  
                        min="0" 
                        max="360" 
                        value="0"
                        @input="$emit('hueChange', buttonStyleValues.hue = $event.target.value)"
                    >
                </div>
            </div>
            <div class="editor-sections">
                <h2>Button Shadow Settings</h2>
                <div id="button-borders" class="sm-form-container">
                    <div class="form-item">
                        <label>X</label>
                        <input type="number" name="quantity" min="-50" max="50" :value="buttonBorderValues.boxShadowX"
                            @input="$emit('x', buttonBorderValues.boxShadowX = $event.target.value)"
                        >
                    </div>
                    <div class="form-item">
                        <label>Y</label>
                        <input type="number" name="quantity" min="-50" max="50" :value=" buttonBorderValues.boxShadowY"
                            @input="$emit('y', buttonBorderValues.boxShadowY = $event.target.value)"
                        >
                    </div>
                    <div class="form-item">
                        <label>Blur</label>
                        <input type="number" name="quantity" min="1" max="50" :value="buttonBorderValues.blurRadius"
                            @input="$emit('blur', buttonBorderValues.blurRadius = $event.target.value)"
                        >
                    </div>
                    <div class="form-item">
                        <label>Spread</label>
                        <input type="number" name="quantity" min="1" max="50" :value="buttonBorderValues.spreadRadius"
                            @input="$emit('spread', buttonBorderValues.spreadRadius = $event.target.value)"
                        >
                    </div>
                </div>
                <div class="form-container">
                    <label class="slider-label" for="shadowHue">Change Shadow Hue</label>
                    <input
                        class="slider color-slider"  
                        type="range"
                        name="hue"  
                        min="0" 
                        max="360" 
                        value="0"
                        @input="$emit('ShadowHueChange', buttonBorderValues.shadowHue = $event.target.value)"
                    >
                </div>
                <div class="form-container">
                    <label class="slider-label" for="shadowSaturation">Change Shadow Saturation</label>
                    <input
                        class="slider sautration-slider"  
                        type="range"
                        name="hue"  
                        min="0" 
                        max="360" 
                        value="0"
                        @input="$emit('ShadowSatuChange', buttonBorderValues.saturation = $event.target.value)"
                        
                    >
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props : ['buttonStyle', 'buttonBorderStyle', 'buttonAnimations'],
    data(){
        return {
            buttonStyleValues : this.buttonStyle,
            buttonBorderValues  : this.buttonBorderStyle,
            buttonAnimatedSelect : this.buttonAnimations
        }
    },
    methods : {
        transmitFloat(){
            let buttonAnimation = 'btn-float'
            this.$emit('buttonAnimationChange', buttonAnimation)
        },
        transmitDarken(){
            let buttonAnimation = 'btn-darken'
            this.$emit('buttonAnimationChange', buttonAnimation)
        },        
        transmitDropShadow(){
            let buttonAnimation = 'btn-shadow'
            this.$emit('buttonAnimationChange', buttonAnimation)
        },        
        transmitFloatShadow(){
            let buttonAnimation = 'btn-float-shadow'
            this.$emit('buttonAnimationChange', buttonAnimation)
        }
    }
}
</script>


