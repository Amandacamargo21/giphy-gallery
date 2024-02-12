
<template>
    <input type="text" placeholder="What awesome giphy do you want to find today?" v-model="keyword" @input="onInput" class="m-3" >
</template>

<script>
export default {
    name: "Search",
    data() {
        return {
            keyword: '',
            timeout: null,
        }
    },
    methods: {
        onInput() {
            clearTimeout(this.timeout);
            this.timeout = setTimeout(() => {
                this.search();
            }, 200);
        },
        search() {
            if (this.keyword.trim() === '') {
                this.$emit('empty-input');
            } else {
                fetch(`https://api.giphy.com/v1/gifs/search?api_key=MOazGpFAidHLr2nDYwcGjAc7LrlRJiUg&q=${this.keyword}`)
                    .then(response => response.json())
                    .then(result => {
                        this.$emit('fetch-gifs', result.data);
                    })
                    .catch(error => {
                        console.error('Error fetching data:', error);
                    });
            }
        },
    }
}
// MOazGpFAidHLr2nDYwcGjAc7LrlRJiUg
</script>

<style scoped>
input {
  padding: 10px 16px;
  border-radius: 4px;
  font-size: 18px;
  border: 2px solid #5f5f5f;
  outline: 0;
  display: block;
  width: 50%;
}

input:focus {
  border-color: #009ad7;
}
</style>
