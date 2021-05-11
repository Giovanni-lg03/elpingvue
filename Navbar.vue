<template>
  <nav class="navbar navbar-expand-lg light bg-dark-custom navbar-dark">
    <div class="container mt-2">
      <!-- Brand -->
      <router-link class="navbar-brand" to="/">
        <h3 class="text-white" style="font-weight:600">
          <span style="font-weight:400" class="text-orange">El</span>P<span
            class="text-orange"
            >in</span
          >G
        </h3>
      </router-link>

      <!-- Toggler -->
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarCollapse"
        aria-controls="navbarCollapse"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Collapse -->
      <div class="collapse navbar-collapse text-center" id="navbarCollapse">
        <!-- Navigation -->
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <router-link
              class="nav-link text-weight-300 text-light"
              style="opacity: .8;"
              to="smartphone"
              >Smartphone</router-link
            >
          </li>
          <li class="nav-item">
            <router-link
              class="nav-link text-weight-300 text-light"
              style="opacity: .8;"
              to="watch"
              >Watch</router-link
            >
          </li>
          <li class="nav-item">
            <router-link
              class="nav-link text-weight-300 text-light"
              style="opacity: .8;"
              to="tablet"
              >Tablet</router-link
            >
          </li>
          <li class="nav-item">
            <router-link
              class="nav-link text-weight-300 text-light mr-2"
              style="opacity: .8;"
              to="about"
              >Chi siamo</router-link
            >
          </li>
          <li class="nav-item">
            <a
              class="nav-link text-weight-300 text-light btn btn-primary bg-orange"
              href="https://shop.elping.it"
            >
              Shop
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
