<template>
  <div id="app" class="id">
    <nav class="navbar navbar-expand-lg navbar-dark bg-success">
      <div class="container-fluid">
        <a class="navbar-brand" href="/">Auth Vue+Mysql</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav">
            <a class="nav-link" aria-current="page" href="/">Home</a>
            <a class="nav-link" href="/sign-up">Register</a>
          </div>
        </div>
      </div>
    </nav>
    <div class="container mt-3">
      <router-view/>
    </div>
  </div>
</template>