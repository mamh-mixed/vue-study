<template>
    <ul>
        <li :style="{opacity}">欢迎学习vue</li>
        <li>news001 <input type="text"/></li> 
        <li>news002 <input type="text"/></li> 
        <li>news003 <input type="text"/></li> 
    </ul>
</template>

<script>
    export default {
        name:'News',
        data(){
            return {
                opacity:1
            }
        },
        // 组件激活时调用
        activated(){
            this.timer = setInterval(()=>{
                this.opacity -= 0.01
                if (this.opacity <= 0)  this.opacity = 1
            }, 16)
        },
        // 组件取消激活时调用
        deactivated(){
            clearInterval(this.timer)
        },
    }
</script>