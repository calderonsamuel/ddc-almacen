<script lang="ts">
    import { base } from '$app/paths';
</script>

<nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand fs-3" href="{base}/">
        <img src="logo-almacen.svg" alt="logo" width="30px" height="40px">
        Almacén DDC
      </a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse justify-content-end" id="navbarSupportedContent">
        <ul class="navbar-nav mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link" href="{base}/about"><i class="bi bi-info-circle pe-1 fs-5"></i>Info</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="https://github.com/calderonsamuel/ddc-almacen"><i class="bi bi-github pe-1 fs-5"></i>Repo</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>