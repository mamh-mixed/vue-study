<template>
    <div>
        <h1>当前求和为：{{sum}}</h1>
        <h3>当前求和放大10倍为：{{bigSum}}</h3>
        <h3>我在{{school}}学习{{subject}}</h3>
        <select v-model.number="n">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
        </select>
        <button @click="increment(n)">+</button>
        <button @click="decrement(n)">-</button>
        <button @click="incrementOdd(n)">当前求和为奇数再加</button>
        <button @click="incrementWait(n)">等一等再加</button>
    </div>
</template>

<script>
    import {mapState, mapGetters, mapMutations, mapActions} from 'vuex'
    export default {
        name:'Count',
        data() {
            return {
                n:1,
            }
        },
        computed:{
            // 借助mapState生成计算属性，从state中读取数据
            ...mapState(['sum', 'school', 'subject']),
            ...mapGetters(['bigSum'])
        },
        methods:{
            // 借助mapMutations生成对应的方法，方法中会调用commit取联系mutations（对象写法）
            ...mapMutations({increment:'JIA',decrement:'JIAN'}),
            // 数组写法
            // ...mapMutations(['JIA','JIAN']),

            // increment(){
            //     this.$store.commit('JIA',this.n)
            // },
            // decrement(){
            //     this.$store.commit('JIAN',this.n)
            // },

            ...mapActions({incrementOdd:'jiaOdd', incrementWait:'jiaWait'}),
            // incrementOdd(){
            //     this.$store.dispatch('jiaOdd',this.n)
            // },
            // incrementWait(){
            //     this.$store.dispatch('jiaWait',this.n)
            // }
        },
    }
</script>

<style>
    button {
        margin-left: 5px;
    }
</style>