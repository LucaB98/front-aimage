<script>

export default {
    name: 'AppForm',
    data() {
        return {
            form: {
                firstName: '',
                lastName: '',
                phone: '',
                email: '',
                interest: ''
            }
        };
    },
    methods: {
        // funzione per l'invio dei dati
        async handleSubmit() {
            try {
                // endpoint
                const response = await fetch('http://localhost:8000/api/register', {
                    method: 'POST',
                    // formato json
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(this.form)
                });
                const data = await response.json();
                // operazione riuscita
                if (response.ok) {
                    alert('Registrazione completata con successo!');
                    // operazione fallita
                } else {
                    alert('Errore: ' + data.message);
                }
                // errori
            } catch (error) {
                console.error('Error:', error);
            }
        }
    }
};
</script>

<template>
    <!-- Form -->
    <form class="container">
        <div class="row row-cols-1 row-cols-md-2">

            <div class="col">
                <!-- Nome -->
                <div class="mb-5">
                    <label for="name" class="form-label">Nome</label>
                    <input type="text" class="form-control" id="name" placeholder="Mario">
                </div>
            </div>
            <div class="col">
                <!-- cognome -->
                <div class="mb-5">
                    <label for="lastname" class="form-label">Cognome</label>
                    <input type="text" class="form-control" id="lastname" placeholder="Rossi">
                </div>
            </div>
            <div class="col">
                <!-- email -->
                <div class="mb-5">
                    <label for="email" class="form-label">Email</label>
                    <input type="email" class="form-control" id="email" placeholder="name@example.com">
                </div>
            </div>
            <div class="col">
                <!-- Telefono -->
                <div class="mb-5">
                    <label for="phone" class="form-label">Telefono</label>
                    <input type="tel" class="form-control" id="phone" placeholder="3920393202">
                </div>
            </div>
            <div class="col">
                <!-- Corso -->
                <div class="mb-5">
                    <select class="form-select" aria-label="Default select example">
                        <option selected>Seleziona un corso</option>
                        <option value="1">React</option>
                        <option value="2">Vue</option>
                        <option value="3">Nodejs</option>
                        <option value="3">MongoDB</option>
                    </select>
                </div>

            </div>
            <div class="col">
                <!-- Corso -->
                <div class="mb-3 d-flex justify-content-end">
                    <button class="btn btn-success"> Registrati</button>
                </div>

            </div>
        </div>
    </form>




</template>

<style scoped>
.btn-success {
    background-color: #007A89;
    font-weight: bold;

}

.btn-success:hover {
    background-color: #00464b;


}

form {
    background-color: #0E1C44;
    border-radius: 10px;
    padding: 20px;
    color: white;
}
</style>