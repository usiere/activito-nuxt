<template>
    <div>
            <h1>This is an app that suggests activities</h1>
            <p>This is the description of the application</p>
    </div>
</template>


<script>
export default {
    head() {
        return {
            title: 'About The App',
            meta: [
                {
                    hid: "description",
                    name: "description",
                    content: "This is where we suggest activities to you"
                }
            ]
        }
    }
    
}
</script>

<style lang="sass" scoped>

</style>