<template>
    <header class="header">

        <div class="header-item">
            <a href="mailto:amandacamargo2102@gmail.com" target="_blank">
                <img src="@/assets/css/images/envelope.png" alt="WhatsApp" />
            </a>
        </div>
        <div class="header-item">
            <a href="https://github.com/amandacamargo21" target="_blank">
                <img src="@/assets/css/images/github.png" alt="github" />
            </a>
        </div>
        <div class="header-item">
            <a href="https://wa.me/41995509912" target="_blank">
                <img src="@/assets/css/images/whatsapp.png" alt="WhatsApp" />
            </a>
        </div>
        <div class="header-item">
            <a href="https:www.linkedin.com/in/amandacamargo21/" target="_blank">
                <img src="@/assets/css/images/linkedin.png" alt="linkedin" />
            </a>
        </div>
    </header>
</template>
  
  
<script>
export default {
    name: "Header"
};
</script>
  
<style scoped>
.header {
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 1rem;
    background-color: #333;
    color: white;
    gap: 2rem;
}

.header-item a {
    color: white;
    text-decoration: none;
}

.header-item a:hover {
    text-decoration: underline;
}
</style>
  