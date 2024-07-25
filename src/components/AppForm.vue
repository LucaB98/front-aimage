<script>
export default {
    name: 'AppForm',
    data() {
        return {
            form: {
                firstname: '',
                lastname: '',
                phone: '',
                email: '',
                interest: ''
            }
        };
    },
    methods: {
        // Function for data submission
        async handleSubmit(event) {
            // Prevent default form submission behavior
            event.preventDefault();
            try {
                // Endpoint
                const response = await fetch('http://localhost:8000/api/register', {
                    method: 'POST',
                    // JSON format
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(this.form)
                });

                const data = await response.json();
                // Successful operation
                if (response.ok) {
                    alert('Registrazione completata con successo!');
                    // Clear the form data
                    this.form = {
                        firstname: '',
                        lastname: '',
                        phone: '',
                        email: '',
                        interest: ''
                    };
                } else {
                    alert('Errore: ' + (data.message || 'Si è verificato un errore sconosciuto.'));
                }
            } catch (error) {
                console.error('Error:', error);
                alert('Si è verificato un errore durante la registrazione. Riprova più tardi.');
            }
        }
    }
};
</script>

<template>
    <!-- Form -->
    <form class="container" @submit="handleSubmit">
        <div class="row row-cols-1 row-cols-md-2">
            <div class="col">
                <!-- First Name -->
                <div class="mb-5">
                    <label for="firstname" class="form-label">Nome</label>
                    <input type="text" class="form-control" id="firstName" v-model="form.firstname" placeholder="Mario">
                </div>
            </div>
            <div class="col">
                <!-- Last Name -->
                <div class="mb-5">
                    <label for="lastname" class="form-label">Cognome</label>
                    <input type="text" class="form-control" id="lastName" v-model="form.lastname" placeholder="Rossi">
                </div>
            </div>
            <div class="col">
                <!-- Email -->
                <div class="mb-5">
                    <label for="email" class="form-label">Email</label>
                    <input type="email" class="form-control" id="email" v-model="form.email"
                        placeholder="name@example.com">
                </div>
            </div>
            <div class="col">
                <!-- Phone -->
                <div class="mb-5">
                    <label for="phone" class="form-label">Telefono</label>
                    <input type="tel" class="form-control" id="phone" v-model="form.phone" placeholder="3920393202">
                </div>
            </div>
            <div class="col">
                <!-- Course Selection -->
                <div class="mb-5">
                    <label for="interest" class="form-label">Corso</label>
                    <select class="form-select" id="interest" v-model="form.interest">
                        <option selected value="">Seleziona un corso</option>
                        <option value="React">React</option>
                        <option value="Vue">Vue</option>
                        <option value="Nodejs">Nodejs</option>
                        <option value="MongoDB">MongoDB</option>
                    </select>
                </div>
            </div>
            <div class="col">
                <!-- Submit Button -->
                <div class="mb-3 d-flex justify-content-end">
                    <button type="submit" class="btn btn-success"> Registrati</button>
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
