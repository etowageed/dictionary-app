<script>
export default {
    name: 'Toggle',

    inject: ['toggleBtn']
}
</script>





<template>
    <div>
        <label class="switch">
            <input type="checkbox" @change="toggleBtn">
            <span class="slider"></span>
        </label>

        <img src="/src/assets/moonicon.svg" alt="moon icon" class="w-7 h-7 inline ml-5">


    </div>
</template>






<style>
/* The switch - the container */
.switch {

    position: relative;
    display: inline-block;
    width: 50px;
    height: 28px;
}

/* Hide the default HTML checkbox */
.switch input {
    opacity: 0;
    width: 0;
    height: 0;
}

/* The slider */
.slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    transition: 0.4s;
    border-radius: 24px;
}

/* The circle inside the slider */
.slider:before {
    position: absolute;
    content: "";
    height: 20px;
    width: 20px;
    left: 4px;
    bottom: 4px;
    top: 4px;
    /* right: 4px; */
    background-color: white;
    transition: 0.4s;
    border-radius: 50%;
}

/* When the checkbox is checked, move the slider */
input:checked+.slider {
    background-color: #5D5FEF;
}

input:checked+.slider:before {
    transform: translateX(24px);
}
</style>