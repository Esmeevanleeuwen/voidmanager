<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    laravelVersion: String,
    phpVersion: String,
});


</script>

<template>
    <Head title="Welcome" />

    <nav class="bg-white shadow-lg">
  <div class="container mx-auto px-6 py-3 md:flex md:justify-between md:items-center">
    <div class="flex items-center justify-between">
      <div>
        <a class="text-xl font-bold text-gray-800 dark:text-dark md:text-2xl hover:text-gray-700 dark:hover:text-gray-300" href="#">
          <img class="h-10 w-auto" src="../../images/logo.png" alt="">
        </a>
      </div>

      <!-- Mobile menu button -->
      <div class="flex md:hidden">
        <button
            type="button"
            class="text-gray-500 hover:text-gray-600 focus:outline-none focus:text-gray-600"
            aria-label="toggle menu"
            @click="toggleMenu"
            >
            <svg viewBox="0 0 24 24" class="h-6 w-6 fill-current">
                <path
                fill-rule="evenodd"
                d="M3 5a1 1 0 0 0 0 2h18a1 1 0 1 0 0-2H3zm0 5a1 1 0 0 0 0 2h18a1 1 0 1 0 0-2H3zm0 5a1 1 0 0 0 0 2h18a1 1 0 1 0 0-2H3z"
                ></path>
            </svg>
         </button>
      </div>
    </div>

    <!-- Mobile Menu open: "block", Menu closed: "hidden" -->
    <div   class="md:flex items-center"
    :class="{ hidden: !isMenuOpen }">
      <div class="flex flex-col md:flex-row md:mx-6">
        <a class="my-1 text-gray-700   hover:text-indigo-500 md:mx-4 md:my-0" href="#">Home</a>
        <a class="my-1 text-gray-700 hover:text-indigo-500 md:mx-4 md:my-0" href="#">Features</a>
        <a class="my-1 text-gray-700  hover:text-indigo-500 md:mx-4 md:my-0" href="#">Pricing</a>
      </div>

      <div class="flex items-center py-2 -mx-1 md:mx-0">
        <a class="btn login-btn block px-3 py-2 rounded-md text-base font-medium text-white bg-indigo-500 hover:bg-indigo-600 md:mx-4"  href="/login">Login</a>
      </div>
    </div>
  </div>
</nav>


<!-- Header Section -->
<header class="header-section">
    <div class="container mx-5">
  <div class="md:w-2/3 md:mr-8">
    <h1 class="titel text-4xl md:text-5xl lg:text-6xl leading-tight mb-6">
      Lorem ipsum dolor<br/> sit amet.
    </h1>
    <p class="text text-lg md:text-xl mb-8">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Aspernatur, velit. Minus id aliquid possimus aliquam cum nihil pariatur laboriosam ut.
    </p>
    <!-- Add the two buttons -->
    <a class="btn btn-outline mr-2" href="#">Button 1</a>
    <a class="btn btn-filled" href="#">Log In <i class="bi bi-arrow-right"></i></a>
  </div>
  <div class="md:w-1/3">
    <img src="../../images/undraw_programmer_re_owql.svg" alt="">
  </div>
</div>

</header>

<section class="content-section my-5">
  <div class="container p-5 features ">
    <div class="flex flex-col md:flex-row">
      <div class="md:w-1/2">
        <h1 class="titel2 text-3xl font-bold mb-4">Lorem ipsum <span class="text-indigo-500">dolor</span><br> sit amet.</h1>
        <p class="text2 text-gray-700 mb-8">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptas molestias fugiat, quod quisquam id reprehenderit possimus atque. Tempore fuga voluptatum odio. Recusandae aspernatur molestiae eligendi natus amet iste culpa ea molestias saepe aliquid. Provident mollitia, fugiat vero, laborum rem, eaque facilis error reprehenderit adipisci blanditiis quidem odit? Aliquam, maiores placeat!</p>
        <a href="#" class="btn login-btn py-2 px-4 rounded-lg bg-indigo-500 text-white text-base hover:bg-indigo-600">Login</a>
      </div>
      <div class="md:w-1/2">
        <img src="../../images/undraw_business_decisions_re_84ag.svg" alt="Your Image Description" class="w-full h-auto">
      </div>
    </div>
  </div>
</section>
 

<section class="bg-gray-100 py-12">
  <div class="container mx-auto">
    <h1 class="text-4xl font-bold mb-8 text-center">Ons aanbod</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
      <!-- Free Package -->
      <div class="bg-white p-6 rounded shadow-md">
        <p class="text-gray-700 uppercase">Basis</p>
        <h2 class="text-2xl text-gray-900 font-bold mt-4 mb-2  ">Gratis versie</h2>
        <a href="basis.html" class="inline-block login-btn bg-blue-500 hover:bg-blue-700 text-white   py-2 px-4 rounded-full text-center mt-4">Download</a>
        <ul class="features-list">
          <li>Maximaal 50 sparingen</li> 
          <li>Cloud based</li>
          <li>Opmerkingen bijhouden</li>
        </ul>
      </div>

      <!-- Pro Package -->
      <div class="bg-white p-6 rounded shadow-md">
        <p class="text-gray-700   uppercase">PRO</p>
        <h2 class="text-2xl text-gray-900 font-bold mt-4 mb-2  ">€40 P/M</h2>
        <a href="#" class="inline-block login-btn bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full  mt-4">Download</a>
        <ul class="features-list">
          <li>3 projecten</li>
          <li>Onbeperkt aantal sparingen</li>
          <li>Cloud based</li>
          <li>Goedkeuringsproces</li>
          <li>Opmerkingingen bijhouden</li>
          <li>Cooordinaten voor inmeten</li>
          <li>Fair use policy</li>
        </ul>
      </div>

      <!-- Pro Plus Package -->
      <div class="bg-white p-6 rounded shadow-md">
        <p class="text-gray-700 uppercase">PRO-plus</p>
        <h2 class="text-2xl text-gray-900 font-bold mt-4 mb-2  ">€75 P/M</h2>
        <a href="#" class="inline-block login-btn bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full   mt-4">Download</a>
        <ul class="features-list">
          <li>8 projecten</li>
          <li>Onbeperkt aantal sparingen</li>
          <li>Cloud based</li>
          <li>Goedkeuringsproces</li>
          <li>Opmerkingingen bijhouden</li>
          <li>Cooordinaten voor inmeten</li>
          <li>Fair use policy</li>
        </ul>
      </div>

      <!-- Custom Package -->
      <div class="bg-white p-6 rounded shadow-md">
        <p class="text-gray-700  uppercase">MAATWERK</p>
        <h2 class="text-2xl text-gray-900 font-bold mt-4 mb-2  ">Offerte</h2>
       
        <a href="#" class="inline-block login-btn bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full text-center mt-4">Download</a>
        <ul class="features-list">
      <li>Ongelimiteerd aantal projecten</li>
      <li>Onbeperkt aantal sparingen</li>
      <li>Cloud based</li>
      <li>Goedkeuringsproces</li>
      <li>Opmerkingingen bijhouden</li>
      <li>Project support</li>
      <li>Cooordinaten voor inmeten</li>
      <li>Fair use policy</li>
    </ul>
  </div>
</div>
</div>
</section>


<section class="bg-white py-12">
  <div class="container mx-auto">
    <div class="flex flex-wrap">
      <div class="w-full md:w-1/2 px-4">
        <h2 class="text-3xl mb-4 font-bold">Contact Us</h2>
        <form id="contact-form" method="post" action="your-action-url" class="mb-8">
          <div class="mb-4">
            <label for="name" class="block text-gray-700 font-bold mb-2">Name</label>
            <input type="text" class="border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="name" name="name" placeholder="Enter your name" required>
          </div>
          <div class="mb-4">
            <label for="email" class="block text-gray-700 font-bold mb-2">Email</label>
            <input type="email" class="border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="email" name="email" placeholder="Enter your email" required>
          </div>
          <div class="mb-4">
            <label for="message" class="block text-gray-700 font-bold mb-2">Message</label>
            <textarea class="border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="message" name="message" rows="5" placeholder="Enter your message here" required></textarea>
          </div>
          <button type="submit" class="inline-block bg-indigo-500 hover:bg-indigo-600 text-white font-bold py-2 px-4 rounded-full text-center">Send Message</button>
        </form>
      </div>
      <div class="w-full md:w-1/2 px-4">
        <div class="mb-4">
          <div class="flex items-center">
            <span class="mr-2"><i class="fas fa-envelope"></i></span>
            <p class="text-gray-700">Email: example@example.com</p>
          </div>
        </div>
        <div class="mb-4">
          <div class="flex items-center">
            <span class="mr-2"><i class="fas fa-phone"></i></span>
            <p class="text-gray-700">Phone: +1 (555) 123-4567</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

</template>

<style>

</style>

<script>
export default {
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<style>
.features-list li::before {
  content: '✓';
  display: inline-block;
  margin-right: 8px;
  color: green; 
  margin-top: 5px;
} 
.features-list  {
 
  margin-top: 10px;
} 
</style>