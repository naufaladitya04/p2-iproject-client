<template>
  <section class="h-100 w-100 bg-white" style="box-sizing: border-box">
    <nav class="navbar-1-2 navbar navbar-expand-lg navbar-light p-4 px-md-4 mb-3 bg-body" style="font-family: Poppins, sans-serif">
      <div class="container">
        <a class="navbar-brand" href="#">
          <svg width="42" height="42" viewBox="0 0 42 42" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M3.5 15.75C3.5 8.98451 8.98451 3.5 15.75 3.5H29.75C30.7165 3.5 31.5 4.2835 31.5 5.25C31.5 6.2165 30.7165 7 29.75 7H15.75C10.9175 7 7 10.9175 7 15.75V29.75C7 30.7165 6.2165 31.5 5.25 31.5C4.2835 31.5 3.5 30.7165 3.5 29.75V15.75Z"
              fill="#391484"
            />
            <path d="M10.5 17.5C10.5 13.634 13.634 10.5 17.5 10.5H31.5C35.366 10.5 38.5 13.634 38.5 17.5V31.5C38.5 35.366 35.366 38.5 31.5 38.5H17.5C13.634 38.5 10.5 35.366 10.5 31.5V17.5Z" fill="#391484" />
          </svg>
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo02" aria-controls="navbarTogglerDemo02" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0" style="margin-right: 50%">
            <li class="nav-item">
              <a class="nav-link px-md-4 active" aria-current="page" href="#">YOURS</a>
            </li>
          </ul>
          <div class="d-flex" style="margin-left: 10%">
            <a class="btn btn-get-started btn-get-started-yellow" @click.prevent="toLogin" v-if="!isLogin">Login</a>
          </div>
          <div class="d-flex" style="margin-left: 1%">
            <a class="btn btn-get-started btn-get-started-yellow" @click.prevent="toRegister" v-if="!isLogin">Register</a>
          </div>
          <div class="d-flex" style="margin-left: 10%">
            <a class="btn btn-get-started btn-get-started-yellow" @click.prevent="toHome" v-if="isLogin">Home</a>
          </div>
          <div class="d-flex" style="margin-left: 1%">
            <a class="btn btn-get-started btn-get-started-yellow" @click.prevent="doLogout" v-if="isLogin">Logout</a>
          </div>
        </div>
      </div>
    </nav>
  </section>
</template>

<script>
export default {
  name: "Navbar",
  methods: {
    toLogin() {
      this.$router.push("/login");
    },
    toRegister() {
      this.$router.push("/register");
    },
    toHome() {
      this.$router.push("/home");
    },
    doLogout() {
      localStorage.removeItem("access_token");
      this.$store.commit("IS_LOGIN", false);
      this.$router.push("/");
    },
  },
  computed: {
    // access_token() {
    //   return localStorage.getItem("access_token");
    // },
    isLogin() {
      return this.$store.state.isLogin;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

.navbar-1-2.navbar-light .navbar-nav .nav-link {
  color: #092a33;
  transition: 0.3s;
}

.navbar-1-2.navbar-light .navbar-nav .nav-link.active {
  font-weight: 500;
}

.navbar-1-2 .btn-get-started {
  border-radius: 20px;
  padding: 12px 30px;
  font-weight: 500;
}

.navbar-1-2 .btn-get-started-yellow {
  background-color: #ffdda9;
  color: #372642;
  transition: 0.3s;
}

.navbar-1-2 .btn-get-started-yellow:hover {
  background-color: #fcd396;
  color: #372642;
  transition: 0.3s;
}
</style>
