<template>
  <div>
    <nav class="navbar navbar-expand-lg bg-transparent fixed-top" data-bs-theme="dark">
      <div class="container-fluid">
        <a class="navbar-brand text-white" href="#">BootStrap</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <form class="d-flex" role="search">
            <input class="form-control me-2 bg-transparent border-light" type="search" placeholder="Search" aria-label="Search" />
            <button class="btn btn-outline-light" type="submit">Search</button>
          </form>
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active text-white" aria-current="page" href="/index.html">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-white" href="/about.html">About Us</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-white" href="/contact.html">Contact Us</a>
            </li>
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle text-white" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false"> </a>
              <ul class="dropdown-menu">
                <li><a class="dropdown-item" href="#">Technology</a></li>
                <li><a class="dropdown-item" href="#">Web Development</a></li>
                <li><hr class="dropdown-divider" /></li>
                <li><a class="dropdown-item" href="#">Support</a></li>
                <li><a class="dropdown-item" href="#">Write For Us</a></li>
              </ul>
            </li>
          </ul>

          <div class="mx-2">
            <i class="bi bi-person-circle text-white" style="font-size: 1.5em"></i>

            <!--  <button class="btn btn-danger mx-2" data-bs-toggle="modal" data-bs-target="#loginModal">LogIn</button>
            <button class="btn btn-danger" data-bs-toggle="modal" data-bs-target="#signupModal">SignUp</button> -->
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style scoped>
.navbar {
  /*   backdrop-filter: blur(10px); */
  position: absolute;
  width: 100%;
  z-index: 1000;
  border: none;
}

.text-white {
  color: white;
}
</style>
