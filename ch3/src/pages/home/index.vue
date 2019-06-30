<template>
    <div>
        <div>{{msg}}</div>
        <router-link to="/list">跳转到List</router-link>
    </div>
</template>
<script>
export default {
    name: 'Home',
    data(){
        return {
            msg:'hello Home'
        }
    }

}
</script>

