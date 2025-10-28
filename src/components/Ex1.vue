<script>
    //import component
    import SoundIcon from './subcomponents/SoundIcon.vue';


    
    export default { 
         components: {SoundIcon}
        ,
        data() {
            return {
                soundLevel: 0
            }
        }
    }
</script>

<template>

   Sound level
    <input type="number" min="0" max="3" v-model="soundLevel"> 
    <SoundIcon :level="soundLevel"></SoundIcon>
    <!-- TODO: Add Code Here to make use of the component -->
     <!-- {{ soundIcon[soundemoji] }}
     <soundIcon
     @click="increment">
     </soundIcon>

    <soundIcon
     @click="decrement">
     </soundIcon> -->

    

</template>

