<template>
    <div class = "backdrop" >
        <div class = "modal" :class="{sale : value === 40}">
            <button style="position: fixed; right: 150px; border-radius: 10px; background-color: red;  " @click.self="closeModal">X</button> <br/>
            <h1> {{ value }}</h1>
           <p>{{ someArray }}</p>
           <slot>Content Unavailable</slot>
           <div class="links">
           <slot name="links"> Content Unavailable</slot>
        </div>
        </div>
        
    </div>
</template>

<script>

export default{
    data(){
        return {
            clicked: true,
        }
    },
    props: [ 'someArray', 'value', 'text'],
    methods: {
        closeModal() {
            this.$emit('close');
        }
    },
}

</script>

<style scoped>
.modal {
    width: 400px;
    height: 300px;
    padding: 10px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}

.backdrop {
    top: 0;
    position: fixed;
    background: rgb(0,0,0,0.5);
    width: 100%;
    height: 100%;
}

.modal.sale {
    background: white;
}





</style>