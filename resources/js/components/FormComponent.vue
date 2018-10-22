<template>
    <div class="card">
        <div class="card-header">¿En que estas pensando ahora?</div>

        <div class="card-body">
            <form action="" v-on:submit.prevent="newThought()">
                <div class="form-group">
                    <label for="thought">Ahora estoy pensando en:</label>
                    <input type="text" class="form-control" name="thought" id="thought" v-model="description">
                </div>
                <button type="submit" class="btn btn-primary">Enviar pensamiento</button>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "FormComponent",
        data(){
            return {
                description: '',
            }
        },
        methods: {
            newThought(){
                const params = {
                    description: this.description,
                };
                this.description = '';
                axios.post('/thoughts',params)
                    .then((response) => {
                        const thought = response.data;
                        this.$emit('new',thought);
                    });

            }
        },
    }
</script>

<style scoped>

</style>