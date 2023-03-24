<template>
    <div >
        <navbar/>

        <main>
            <!-- // çözünürlük küçülse bile resimler yan yana ve okunur boyutta olur  -->
            <div class="max-w-[1200px] mx-auto"><router-view/></div>
        </main>
    </div>
</template>


<script setup>
import Navbar from '../components/Navbar.vue';

</script>