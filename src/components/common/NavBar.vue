<!-- App.vue -->
<template>
  <BApp>
    <BNavbar toggleable="lg" class="fixed-top custom-navbar">
      <BNavbarBrand :to="{name: 'home'}" class="links">
        <div class="logo-container">
          <img
            id ="logo"
            :src="logo"
            alt="NexusHR Logo"
            height="30"
            class="logo-image"
          />
        </div>
      </BNavbarBrand>
      <BNavbarToggle target="nav-collapse" />
      <BCollapse id="nav-collapse" is-nav>
        <BNavbarNav class="ms-auto mb-2 mb-lg-0">
          <BNavItem class="links" :to="{name: 'login'}">
            Login
          </BNavItem>
        </BNavbarNav>
      </BCollapse>
    </BNavbar>
  </BApp>
</template>
<script setup>
import {
  BApp,
  BNavbar,
  BNavbarBrand,
  BNavbarToggle,
  BCollapse,
  BNavbarNav,
  BNavItem,
  // BNavItemDropdown,
  // BDropdownItem,
  // BNavForm,
  // BFormInput,
  // BButton,
} from 'bootstrap-vue-next'

const logo = new URL('@/assets/NexusLogo.png', import.meta.url).href
</script>

<style>
.links a {
  color: white !important;
  font-weight: 550;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
.custom-navbar {
  background-color: black !important;
}
#logo{
  width: 100px;
  height: 40px;
}
</style>
