<template>
    <div>
        <MyItem v-for='t in todos' :key='t.id' :todo='t' :checkChange='checkChange' :dItem='dItem'/>
    </div>
</template>

<script>
    import MyItem from './MyItem.vue'
     export default{
        name:'MyList',
        components:{
            MyItem
        },
        props:['todos','dItem','checkChange']
        }
</script>