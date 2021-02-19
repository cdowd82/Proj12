<script>

  // Imports
  import { FirebaseApp, User } from "sveltefire";
  import firebase from "firebase/app";
  import "firebase/firestore";
  import "firebase/auth";
  import "firebase/performance";
  import "firebase/analytics";
  import { fade, fly } from 'svelte/transition';
  import { onMount } from "svelte";
  
  // My imports
  import { currentUser } from '/Users/Chris/Projects/Proj12/src/user.js';
  import Navdata from '/Users/Chris/Projects/Proj12/src/Navdata.svelte';
  import Footer from '/Users/Chris/Projects/Proj12/src/Footer.svelte';

  // For Firebase JS SDK v7.20.0 and later, measurementId is optional
  const firebaseConfig = {
      apiKey: "AIzaSyCwYTjYpXgFjqVwuVhBbx9ZCFuj7HaMiTk",
      authDomain: "proj12-466f0.firebaseapp.com",
      projectId: "proj12-466f0",
      storageBucket: "proj12-466f0.appspot.com",
      messagingSenderId: "403330034066",
      appId: "1:403330034066:web:9e1ee557018e85a6bf394b",
      measurementId: "G-X6X7G9M4SY"
  };

  let email = '';
  let password = '';
  let showMobileMenu = false; // Show mobile icon and display menu

// List of navigation items
const navItems = [
  { label: "Profile", href: "#"},
  { label: "Admin", href: "#" },
  { label: "Contact", href: "#"},
  { label: "About", href: "#" },
  { label: currentUser, href: "#"}
];

// Mobile menu click event handler
const handleMobileIconClick = () => (showMobileMenu = !showMobileMenu);
// Media match query handler
const mediaQueryHandler = e => {
    // Reset mobile state
    if (!e.matches) {
    }
};

// Attach media query listener on mount hook
onMount(() => {
    const mediaListener = window.matchMedia("(max-width: 767px)");
    mediaListener.addListener(mediaQueryHandler);
});

  // Sign in auth
  function signIn() {
      firebase.auth().signInWithEmailAndPassword(email, password).then((user) => {
          // Signed in. Update login flag
          currentUser.set(email);
          navItems[4].label = $currentUser;
      })
      .catch((error) => {
          var errorCode = error.code;
          var errorMessage = error.message;
          alert('Incorrect email and / or password');
        });
  }

  firebase.initializeApp(firebaseConfig);

</script>



<main>
  <!-- Outside Wrapper Firebase App -->
  <FirebaseApp {firebase}>
    <!-- Get the current user -->
    <User let:user let:auth>
       
      <!-- Landing login -->
      <div in:fade="{{y:1000, duration: 2000}}" slot="signed-out">
        <div>
          <h1 style="strong">TAVR<sup>2</sup></h1>
          <input top-margin="0" type="email" bind:value={email} placeholder="Email">
          <br>
          <input type="password" bind:value={password} placeholder="Password">
          <br>
          <button on:click={signIn}>Login</button>
        </div>
      </div>

      <!-- Navbar -->
      <div transition:fly="{{y:1000, duration: 1200}}">
        <nav>
          <div class="inner">
            <div on:click={handleMobileIconClick} class={`mobile-icon${showMobileMenu ? ' active' : ''}`}>
              <div class="middle-line"></div>
            </div>
            <ul class={`navbar-list${showMobileMenu ? ' mobile' : ''}`}>
              <li><a href="/#/"> <div class="nav-tavr">Liverpool-TAVR<sup>2</sup>: 18</div></a></li>
              <li><a href={navItems[0].href}>{navItems[0].label}</a></li>
              <li><a href={navItems[1].href}>{navItems[1].label}</a></li>
              <li><a href={navItems[2].href}>{navItems[2].label}</a></li>
              <li><a href={navItems[3].href}>{navItems[3].label}</a></li>
              <li><a href={navItems[4].href} on:click={() => auth.signOut()}>
                 Logout: {navItems[4].label}</a></li>
            </ul>
          </div>
        </nav>
      </div>

      <!-- Content -->
      <Navdata/>
      <Footer/>

    </User>
  </FirebaseApp>
</main>



<!-- Styles -->
<style>

  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  h1 {
        font-size: 75px;
        font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
        color: hsla(0, 100%, 35%, 0.89);
        margin-top: 0;
    }

    /* Navbar*/
    .nav-tavr {
        color:hsla(0, 97%, 77%, 0.89);
        font-size: 14px;
        font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
    }

    .logout-Btn {
    background-color: #343436;
    font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
    border: none;
    color: white;
    padding-top: 1em
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  nav {
    background-color: rgba(0, 0, 0, 0.8);
    font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
    height: 50px;
  }

  .inner {
    max-width: 980px;
    padding-left: 20px;
    padding-right: 20px;
    margin: auto;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    height: 100%;
  }

  .mobile-icon {
    width: 25px;
    height: 14px;
    position: relative;
    cursor: pointer;
  }

  .mobile-icon:after,
  .mobile-icon:before,
  .middle-line {
    content: "";
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
    transition: all 0.4s;
    transform-origin: center;
  }

  .mobile-icon:before,
  .middle-line {
    top: 0;
  }

  .mobile-icon:after,
  .middle-line {
    bottom: 0;
  }

  .mobile-icon:before {
    width: 66%;
  }

  .mobile-icon:after {
    width: 33%;
  }

  .middle-line {
    margin: auto;
  }

  .mobile-icon:hover:before,
  .mobile-icon:hover:after,
  .mobile-icon.active:before,
  .mobile-icon.active:after,
  .mobile-icon.active .middle-line {
    width: 100%;
  }

  .mobile-icon.active:before,
  .mobile-icon.active:after {
    top: 50%;
    transform: rotate(-45deg);
  }

  .mobile-icon.active .middle-line {
    transform: rotate(45deg);
  }

  .navbar-list {
    display: none;
    width: 100%;
    justify-content: space-between;
    margin: 0;
    padding: 0 40px;
  }

  .navbar-list.mobile {
    background-color: rgba(0, 0, 0, 0.8);
    position: fixed;
    display: block;
    height: calc(100% - 45px);
    bottom: 0;
    left: 0;
  }

  .navbar-list li {
    list-style-type: none;
    position: relative;
  }

  .navbar-list li:before {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 1px;
    background-color: #424245;
  }

  .navbar-list a {
    color: #fff;
    text-decoration: none;
    display: flex;
    height: 45px;
    align-items: center;
    padding: 0 10px;
    font-size: 13px;
  }

  @media only screen and (min-width: 767px) {
    .mobile-icon {
      display: none;
    }

    .navbar-list {
      display: flex;
      padding: 0;
    }

    .navbar-list a {
      display: inline-flex;
    }

    .navbar-list a:hover {
      background-color: rgba(63, 62, 62, 0.986);
    }
  }

  .logout-Btn {
    background-color: transparent;
    font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
    border: none;
    color: white;
    padding-top: 1em
  }

</style>

