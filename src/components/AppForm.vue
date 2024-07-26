    <script>
    export default {
        name: 'AppForm',
        data() {
            return {

                username: '',
                password: '',


                form: {
                    firstname: '',
                    lastname: '',
                    username: '',
                    password: '',
                    phone: '',
                    email: '',
                    interest: ''
                }
            };

        },
        methods: {
            // REGISTRAZIONE
            async handleSubmit(event) {

                event.preventDefault();
                try {
                    // ENDPOINT
                    const response = await fetch('http://localhost:8000/api/auth/register', {
                        // METODO
                        method: 'POST',
                        // FORMATO JSON
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(this.form)
                    });

                    const data = await response.json();

                    if (response.ok) {
                        alert('Registrazione completata con successo!');

                        this.form = {
                            firstname: '',
                            lastname: '',
                            username: '',
                            password: '',
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
            },
            // ACCESSO
            async login() {
                this.error = null;
                try {
                    // ENDPOINT
                    const response = await fetch('http://localhost:8000/api/auth/login', {
                        // METODO
                        method: 'POST',
                        // FORMATO JSON
                        headers: {
                            'Content-Type': 'application/json',
                        },
                        body: JSON.stringify({
                            username: this.username,
                            password: this.password
                        }),
                    });
                    // DATI PASSATI IN JSON
                    const data = await response.json();
                    // TOKEN
                    localStorage.setItem('token', data.access_token);


                    // ALERT CON IL TOKEN
                    const token = data.access_token;
                    alert("Benvenuto! il tuo token e' = " + token);

                    if (!response.ok) {
                        throw new Error('Invalid credentials');
                    }


                } catch (error) {
                    this.error = error.message;
                }
            },
        }

    };

</script>

    <template>
        <div class="container">
            <!-- REGISTRAZIONE -->
            <h1 class="mb-3">Registrazione</h1>

            <form @submit="handleSubmit">
                <div class="row row-cols-1 row-cols-md-2">
                    <div class="col">
                        <!-- First Name -->
                        <div class="mb-5">
                            <label for="firstname" class="form-label">Nome</label>
                            <input type="text" class="form-control" id="firstName" v-model="form.firstname"
                                placeholder="Mario">
                        </div>
                    </div>
                    <div class="col">
                        <!-- Last Name -->
                        <div class="mb-5">
                            <label for="lastname" class="form-label">Cognome</label>
                            <input type="text" class="form-control" id="lastName" v-model="form.lastname"
                                placeholder="Rossi">
                        </div>
                    </div>
                    <div class="col">
                        <!-- Last Name -->
                        <div class="mb-5">
                            <label for="username" class="form-label">Username</label>
                            <input type="text" class="form-control" id="username" v-model="form.username"
                                placeholder="mrss98">
                        </div>
                    </div>
                    <div class="col">
                        <!-- Last Name -->
                        <div class="mb-5">
                            <label for="password" class="form-label">Password</label>
                            <input type="password" class="form-control" id="password" v-model="form.password">
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
                            <input type="tel" class="form-control" id="phone" v-model="form.phone"
                                placeholder="3920393202">
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

            <!-- login -->
            <h1 class="my-3">Login</h1>
            <form @submit.prevent="login">
                <div class="row flex-column justify-content-aroud align-items-center">
                    <!-- username -->
                    <div class="col">
                        <label class="form-label" for="username">Username:</label>
                        <input class="form-control" type="text" v-model="username" id="username" required />
                    </div>
                    <!-- password -->
                    <div class="col">
                        <label class="form-label" for="password">Password:</label>
                        <input class="form-control" type="password" v-model="password" id="password" required />
                    </div>
                    <!-- button login -->
                    <div class="col mt-3">

                        <button class="btn btn-success" type="submit">Login</button>
                    </div>
                    <div v-if="error" class="error">{{ error }}</div>
                </div>
            </form>


        </div>

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
