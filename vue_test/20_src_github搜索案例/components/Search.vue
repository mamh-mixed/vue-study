<template>
    <section class="jumbotron">
        <h3 class="jumbotron-heading">Search Github Users</h3>
        <div>
            <input type="text" placeholder="enter the name you search" v-model="keyWord"/>&nbsp;
            <button @click="searchUsers">Search</button>
        </div>
    </section>
</template>

<script>
    import axios from 'axios'
    export default {
        name:'Search',
        data() {
            return {
                keyWord:''
            }
        },
        methods: {
            searchUsers(){
                // 请求前更新List的数据
                this.$bus.$emit('updateListData',{isFirst:false,isLoading:true,errMsg:'',users:[]})
                axios.get(`https://api.github.com/search/users?q=${this.keyword}`).then(
                    // 请求成功
                    response => {
                        this.$bus.$emit('updateListData',{isLoading:false,errMsg:'',users:response.data.items})
                    },
                    // 请求失败
                    error => {
                        this.$bus.$emit('updateListData',{isLoading:false,errMsg:error.message,users:[]})
                    }
                )
            }
        }
    }
</script>

<style>

</style>