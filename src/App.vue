<template>
  <header class="header" ref="top">
    <div class="header-name-container">
      <router-link to="/">
        <img class="header-logo" src='./assets/headerLogo.png' alt="logo">
      </router-link>
      <nav>
        <router-link to="/">Hem</router-link>
        <router-link to="/about">Om mig</router-link>
        <router-link to="/projects">Projekt</router-link>
        <router-link to="/contact">Kontakt</router-link>
      </nav>
      <button class="mobile-menu-button" v-if="!mobileMenu" @click="mobileMenu = true">
        <div class="hamburger-container">
          <div class="row1"></div>
          <div class="row2"></div>
          <div class="row3"></div>
        </div>
      </button>
      <button class="mobile-menu-button" v-if="mobileMenu" @click="mobileMenu = false">
        <div class="cross-container">
          <div class="cross1"></div>
          <div class="cross2"></div>
          <div class="cross3"></div>
        </div>
      </button>
      <div @click="mobileMenu = false" v-if="mobileMenu" class="mobile-nav-container">
        <router-link to="/">Hem</router-link>
        <router-link to="/about">Om mig</router-link>
        <router-link to="/projects">Projekt</router-link>
        <router-link to="/contact">Kontakt</router-link>
      </div>
    </div>
  </header>
  <router-view />
  <footer class="footer-container">
    <div class="footer-content">
      <div class="about">
        <h2>Om mig</h2>
        <p>Mitt namn är william ali, 29 årig utvecklare från sverige Här kommer ni hitta information om mig och
          projekten jag har jobbat med och även projekt jag aktuellt jobbar på!</p>
      </div>
      <div class="links">
        <h2>Snabb länkar</h2>
        <router-link to="/" @click="scrollToTop('top')">hem</router-link>
        <router-link to="/about">Om mig</router-link>
        <router-link to="/projects">Projekt</router-link>
        <router-link to="/contact">Kontakt</router-link>
      </div>
      <div class="contact-details">
        <h2>Kontakta mig</h2>
        <p>William ali</p>
        <a href="tel: 072-90 22 198">Telefonnummer: 072-90 22 198</a>
        <a href="mailto:william.ali@hotmail.se">Email: william.ali@hotmail.se</a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      mobileMenu: false,
    }
  },
  methods: {
    scrollToTop(refname) {
      const el = this.$refs[refname]
      el.scrollIntoView({behavior: 'smooth'})
    },
  }
}
</script>


<style>
:root
{
  --clr-hover-link: rgba(135, 206, 250, 0.7);
  --clr-hover-link-Bright: rgba(135, 206, 250, 0.9);
  --clr-standard-link-color: rgb(155, 106, 106);
}

html
{
  overflow-y: scroll;
}

#app
{
  font-family: monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: black;
  margin: 20px 300px;
}

body
{
  background: white;
}

header
{
  width: 100%;
}

.mobile-menu-button
{
  display: none;
}

nav
{
  display: flex;
  margin-right: 20px;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  font-weight: bold;
  width: 100%;
}

nav a
{
  margin: 0px 20px;
  color: black;
}

nav a.router-link-exact-active
{
  color: var(--clr-standard-link-color);
}

.header
{
  box-shadow: 1px 1px 6px 1px black;
  width: 100%;
}

.header-name-container
{
  display: flex;
}

.header-name-text
{
  margin: 0;
  font-weight: normal;
  font-family: monospace;
  font-size: x-large;
  width: 100%;
}

.header-logo
{
  margin-top: 10px;
  padding-bottom: 10px;
  margin-left: 5px;
  width: 200px;
  height: 40px;
}

a
{
  text-decoration: none;
}

a:hover
{
  color: var(--clr-hover-link);
}


.footer-container
{
  bottom: 0;
  width: 100%;
  margin-top: 10px;
  background: #f2f2f2;
  height: fit-content;
  border-radius: 5px;
  text-align: left;
  box-shadow: 1px 1px 4px 2px;
}

.footer-content
{
  display: flex;
  justify-content: center;
  height: 100%;
  gap: 0.3em;
}

.about
{
  display:flex;
  flex-direction: column;
  width: 40%;
  margin-left: 5px;
}

.about p
{
  margin-top:20px;
  font-size: 14px;
  width: 80%;
}

.links
{
  display: flex;
  flex-direction: column;
  row-gap: 10px;
  margin-bottom: 20px;
  width: 30%;
  padding-left: 20px;
}

.links a
{
  font-size: 16px;
  color: var(--clr-standard-link-color);
  text-decoration: underline;
}

.links a:hover
{
  color: var(--clr-hover-link);
}

.contact-details
{
  display: flex;
  flex-direction: column;
  padding-right: 5px;
}

.contact-details p
{
  font-size: 16px;
}

.contact-details a
{
  font-size: 16px;
  color: var(--clr-standard-link-color);
  margin: 0;
  padding: 5px 0px;
}

.contact-details a:hover
{
  color: var(--clr-hover-link);
}

@media screen and (max-width:4000px) and (min-width: 2880px)
{
  .footer-content p
  {
    font-size: 30px;
  }

  .footer-content h2
  {
    font-size: 35px;
  }

  .links a
  {
    font-size: 30px;
  }

  nav
  {
    display: flex;
    align-items: center;
    text-align: center;
    width: 100%;
    font-size: 30px;
  }

  .header
  {
    box-shadow: 1px 1px 6px 1px black;
    padding: 5px;
    width: 100%;
    height: 65px;
  }

  .header-name-container
  {
    width: 100%;
    display: flex;
    gap: 1000px;

  }

  .header-logo
  {
    width: 200px;
    height: 70px;
  }
}

@media screen and (max-width:768px) and (min-width: 500px)
{
  #app
  {
    font-family: monospace;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: black;
    margin: auto;
  }

  nav
  {
    display: flex;
    align-items: center;
    text-align: center;
    font-size: 18px;
  }


  .header
  {
    box-shadow: 1px 1px 6px 1px black;
    padding: 5px;
  }

  .header-name-container
  {
    display: flex;
    gap: 40px;
  }

  .header-name-text
  {
    margin: 0;
    font-weight: normal;
    font-family: monospace;
    font-size: x-large;
  }
}

@media (max-width: 425px)
{

  #app
  {
    margin: auto;
  }

  nav
  {
    display: none;
  }

  .mobile-menu-button
  {
    display: block;
  }

  .row1,
  .row2,
  .row3
  {
    width: 35px;
    height: 5px;
    background-color: black;
    margin: 6px 0;
  }

  .cross1
  {
    width: 35px;
    height: 5px;
    background-color: black;
    margin: 6px 0;
    -webkit-transform: rotate(-45deg) translate(-9px, 6px);
    transform: rotate(-45deg) translate(0px, 6px);
  }

  .cross2
  {
    opacity: 0;
  }

  .cross3
  {
    width: 35px;
    height: 5px;

    background-color: black;
    -webkit-transform: rotate(45deg) translate(-8px, -8px);
    transform: rotate(45deg) translate(0px, -8px);
  }

  header
  {
    margin: 0;
    padding: 0;
    width: 100;
  }

  .header-name-container
  {
    width: 100%;
    margin: 0;
    padding: 0;
    justify-content: space-between;
  }

  .hamburger-container
  {
    margin-top: 10px;
  }

  .footer-content
  {
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100%;
    margin: 0;
    padding: 0;
    text-align: center;
  }

  .about
  {
    align-items: center;
    width: 100%;
    margin: 0;
  }

  .about p
  {
    margin: 0;
    font-size: 14px;
  }

  .links
  {
    display: flex;
    flex-direction: column;
    row-gap: 10px;
    margin-bottom: 20px;
    width: 100%;
    padding-left: 0;
  }

  .links a
  {
    font-size: 16px;
  }

  .contact-details
  {
    display: flex;
    width: 100%;
    flex-direction: column;
    padding-right: 0px;
  }

  .mobile-nav-container
  {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 50px;
    width: 409px;
    height: 300px;
    border-radius: 10px;
    background-color: rgba(0, 0, 0, 0.77);
    color: wheat;
    position: absolute;
    top: 7em;
  }

  .mobile-nav-container a
  {
    color: white;
    font-size: 20px;
    text-decoration: underline;
  }

  .mobile-nav-container a:hover
  {
    color: rgba(135, 206, 250, 0.7)
  }
}
</style>
