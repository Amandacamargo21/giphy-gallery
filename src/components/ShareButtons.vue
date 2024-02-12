<template>
    <div class="share-buttons">
        <button @click="shareWhatsApp" class="share-button">
            <img src="@/assets/css/images/icons8-whatsapp.svg" alt="WhatsApp" />
        </button>
        <button @click="shareInstagram" class="share-button">
            <img src="@/assets/css/images/icons8-instagram.svg" alt="WhatsApp" />
        </button>
        <button @click="shareFacebook" class="share-button">
            <img src="@/assets/css/images/icons8-facebook.svg" alt="WhatsApp" />
        </button>
        <button @click="copyLink" class="share-button">
            <img src="@/assets/css/images/icons8-copy-50.png" alt="WhatsApp" />
        </button>
    </div>
</template>
  
<script>
export default {
    name: "ShareButtons",
    props: {
        gifUrl: String
    },
    methods: {
        shareWhatsApp() {
            console.log(this.gifUrl);
            const url = 'https://api.whatsapp.com/send?text=' + encodeURIComponent(this.gifUrl);
            window.open(url, '_blank');
        },
        shareInstagram() {
            const url = 'https://www.instagram.com/create/story/';
            const message = 'Confira este GIF incrível!';
            const hashtags = 'giphy, gif, instagood'; 
            const shareUrl = `${url}?text=${encodeURIComponent(message)}&hashtags=${hashtags}`;
        
            window.open(shareUrl, '_blank');
        },
        shareFacebook() {
            const url = 'https://www.facebook.com/sharer/sharer.php?u=' + encodeURIComponent(this.gifUrl);
            window.open(url, '_blank');
        },
        copyLink() {
            const gifUrl = this.gifUrl;
            const tempInput = document.createElement('textarea');
            tempInput.value = gifUrl;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);
            alert('Link copiado para a área de transferência!');
        }
    }
}
</script>
  
<style scoped>
.share-buttons {
    position: absolute;
    bottom: 35px;
    background: #f2f5f491;
    display: flex;
    justify-content: space-evenly;
    width: -webkit-fill-available;
}

.share-button {
    background: none;
    border: none;
    color: #000;
    cursor: pointer;
    width: 1.5em;

}
</style>
  