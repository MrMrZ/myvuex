<template>
    <div>
        <h2>{{msg}}</h2>
        <hr/>

        <h3>{{$store.state.count}}======={{count}}</h3>

        <hr/>
        
        <button @click="add(10)">+</button>
        <button @click="reduce()">-</button>

        <br>
        <button @click="addAction">+</button>
        <button @click="reduceAction">-</button>
    </div>
</template>

<script>

import store from '@/vuex/store';
import {mapState,mapMutations, mapGetters,mapActions} from 'vuex';

export default {
    data(){
        return{
            msg:'Hello Vuex',
        }
    },
    // computed:{
    //     count(){
    //         return this.$store.state.count  //第一种方法
    //     }
    // },
    // computed:mapState({
    //    count:state=>state.count   //第二种方法
    // }),
    // computed:mapState(['count']), //第三种方法
    computed:{
        ...mapState(['count']),
        // count(){
        //    return this.$store.getters.count
        // }
        ...mapGetters(['count'])  //简写
    },
    methods:{
        ...mapMutations(['add','reduce']),
        ...mapActions(['addAction','reduceAction'])
    },

    store
}
</script>
