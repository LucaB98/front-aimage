<script>
export default {
    name: 'AppForm'
};
</script>

<template>
    <div class="container">
        <div class="row row-cols-sm-1 row-cols-md-2">
            <div class="col">

                <div class="mb-3">
                    <label for="exampleFormControlInput1" class="form-label">Nome</label>
                    <input type="text" class="form-control" id="exampleFormControlInput1"
                        placeholder="name@example.com">
                </div>
            </div>
            <div class="col">

                <div class="mb-3">
                    <label for="exampleFormControlInput1" class="form-label">Cognome</label>
                    <input type="text" class="form-control" id="exampleFormControlInput1"
                        placeholder="name@example.com">
                </div>
            </div>
            <div class="col">

                <div class="mb-3">
                    <label for="exampleFormControlInput1" class="form-label">Email</label>
                    <input type="email" class="form-control" id="exampleFormControlInput1"
                        placeholder="name@example.com">
                </div>
            </div>
            <div class="col">

                <div class="mb-3">
                    <label for="exampleFormControlInput1" class="form-label">Telefono</label>
                    <input type="number" class="form-control" id="exampleFormControlInput1"
                        placeholder="name@example.com">
                </div>
            </div>
            <div class="col">


                <div class="mb-3">
                    <select class="form-select" aria-label="Default select example">
                        <option selected>Open this select menu</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>

            </div>
        </div>
    </div>




</template>

<style scoped></style>