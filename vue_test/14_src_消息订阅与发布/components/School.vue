<template>
	<div class="school">
		<h2>学校名称：{{name}}</h2>
		<h2>学校地址：{{address}}</h2>
	</div>
</template>

<script>
	import pubsub from 'pubsub-js'
	export default {
		name:'School',
		props:['getSchoolName'],
		data() {
			return {
				name:'尚硅谷',
				address:'北京',
			}
		},
		mounted(){
			// this.$bus.$on('hello',(data)=>{
			// 	console.log(data)
			// })
			this.pubId = pubsub.subscribe('hello', (msgName, data)=>{
				console.log(this)
			})
		},
		beforeDestroy() {
			// this.$bus.$off('hello')
			pubsub.unsubscribe(this.pubId)
		}
	}
</script>

<style scoped>
    .school{
        background-color:skyblue;
    }
</style>