<script>

export default {
    name: 'AppHeader',

};
</script>

<template>
    <header>
        <!-- navbar -->
        <nav class="navbar navbar-expand-lg">
            <div class="container-fluid">
                <a class="navbar-brand ms-2" href="#"><img src="../img/aimage-logo.webp" alt="logo" width="100px"></a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
                    aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <!-- home -->
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#">Home</a>
                        </li>
                        <!-- vantaggi -->
                        <li class="nav-item">
                            <a class="nav-link" href="#">Vantaggi</a>
                        </li>
                        <!-- dropdown -->
                        <li class="nav-item dropdown">
                            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                                aria-expanded="false">
                                Soluzioni
                            </a>
                            <ul class="dropdown-menu">
                                <li><a class="dropdown-item" href="#">Chatbot per Lead Generation</a></li>
                                <li><a class="dropdown-item" href="#">Chatbot per Customer Care
                                    </a></li>
                                <li>
                                    <a class="dropdown-item" href="#">Chatbot per Whatsapp
                                    </a>
                                </li>
                                <li><a class="dropdown-item" href="#">Chatbot per Facebook</a></li>
                            </ul>
                        </li>
                    </ul>
                    <!-- searchbar -->
                    <form class="d-flex" role="search">
                        <input class="form-control me-2" type="search" placeholder="Cerca" aria-label="Search">
                        <button class="btn btn-outline-success" type="submit"><i
                                class="fa-solid fa-magnifying-glass"></i></button>
                    </form>
                </div>
            </div>
        </nav>
    </header>

</template>

<style scoped>
.navbar {
    background-color: white;
}
</style>