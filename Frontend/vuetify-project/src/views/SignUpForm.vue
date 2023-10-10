<template>
    <div class="main">
        <v-card
        class="mx-auto pa-12 pb-8"
        elevation="8"
        width="448"
        rounded="lg"
        >

            <v-img
            class="mx-auto my-2"
            max-width="334"
            src="@/assets/MyNoteHub.png"
            >
            </v-img>

            <v-form
                v-model="form"
                @submit.prevent="onSubmit"
            >

                <div class="text-h5 text-medium-emphasis font-weight-bold mb-10">Olá, seja bem-vindo(a) &#128075</div>

                <v-text-field
                v-model="name"
                :readonly="loading"
                :rules="[required]"
                class="mb-3"
                clearable
                density="compact"
                placeholder="Digite um nome de usuário"
                prepend-inner-icon="mdi-account-outline"
                variant="outlined"
                ></v-text-field>

                <v-text-field
                v-model="email"
                :readonly="loading"
                :rules="[required]"
                class="mb-3"
                clearable
                density="compact"
                placeholder="Digite um endereço de e-mail"
                prepend-inner-icon="mdi-email-outline"
                variant="outlined"
                ></v-text-field> 

                <v-text-field
                :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
                :type="visible ? 'text' : 'password'"
                density="compact"
                placeholder="Digite uma senha"
                prepend-inner-icon="mdi-lock-outline"
                variant="outlined"
                @click:append-inner="visible = !visible"
                ></v-text-field>

                <br>

                <v-btn
                block
                class="mb-4"
                color="blue"
                size="large"
                variant="tonal"
                >
                Criar nova conta
                </v-btn>

                <v-card-text class="text-center">
                <a
                class="text-blue text-decoration-none"
                href="/login"
                rel="noopener noreferrer"
                target="_self"
                >
                Já possui uma conta? Logue aqui <v-icon icon="mdi-chevron-right"></v-icon>
                </a>
                </v-card-text>
            </v-form>
        </v-card>
    </div>
</template>
  
<script>
export default {
    name: 'SignUpForm',
    data: () => ({
    visible: false,
    }),
}
</script>

<style scoped>
.main {
    text-align: center;
    height: 100vh;
    margin: 0;          
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.main .text-h5 {
    margin-bottom: 20px;
    margin-top: 30px;
}
.text-subtitle-1 {
    text-align: left;
}
</style>