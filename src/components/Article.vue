<template>
    <div>
        <h3>{{article.title}}</h3>
        <p>{{article.content}}</p>
    </div>
</template>
<script>
export default {
    props: ['article'],
    data() {
        return {
            
        }
    } 
}
</script>
<style lang="stylus" scoped>

</style>