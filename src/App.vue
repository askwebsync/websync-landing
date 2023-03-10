<template>
  <div v-if="loading" class="h-screen flex items-center justify-center">
    <div class="spinner w-12 h-12 mx-auto text-gray-600 animate-spin"></div>
  </div>
  <div
    v-if="!loading"
    class="relative h-screen w-full flex flex-col background-banner bg-center bg-cover"
  >
    <div
      class="absolute top-0 right-0 bottom-0 left-0 bg-gray-800 opacity-75"
    ></div>
    <div class="px-2 py-2 z-10 my-2 md:my-4">
      <img src="../public/logo-1.png" alt="logo" class="w-16 h-16 object-fit" />
    </div>
    <div
      class="flex flex-col gap-12 md:gap-8 z-10 items-center justify-center text-center py-12 md:py-20"
    >
      <div
        class="mx-auto space-y-4 center animate__animated animate__bounce animate__slow"
      >
        <h1 class="text-4xl md:text-6xl text-white">
          Our Website Is Coming Soon
        </h1>
        <h2 class="text-gray-300 text-sm md:text-lg max-w-sm">
          We're Working hard to Finish The Development Of This Site. Check Our
          Instagram For More Information!
        </h2>
      </div>
      <hr />
      <div
        class="flex flex-wrap justify-center p-2 md:p-4 text-center gap-1 md:gap-12 shadow-custom"
      >
        <div class="flex flex-col w-20 md:w-auto md:mx-2 mb-4 md:mb-0">
          <h2 class="text-blue-400 text-3xl md:text-5xl">{{ day }}</h2>
          <p class="text-white text-base md:text-lg">D</p>
        </div>
        <div class="flex flex-col w-20 md:w-auto md:mx-2 mb-4 md:mb-0">
          <h2 class="text-blue-400 text-3xl md:text-5xl">{{ hours }}</h2>
          <p class="text-white text-base md:text-lg">H</p>
        </div>
        <div class="flex flex-col w-20 md:w-auto md:mx-2 mb-4 md:mb-0">
          <h2 class="text-blue-400 text-3xl md:text-5xl">{{ minutes }}</h2>
          <p class="text-white text-base md:text-lg">M</p>
        </div>
        <div class="flex flex-col w-20 md:w-auto md:mx-2">
          <h2 class="text-blue-400 text-3xl md:text-5xl">{{ seconds }}</h2>
          <p class="text-white text-base md:text-lg">S</p>
        </div>
      </div>
      <div class="flex justify-center z-10 mt-6">
        <a href="https://www.instagram.com/websync.id/">
          <button
            type="button"
            class="button mb-2 inline-block rounded-full p-3 md:p-4 text-xs md:text-base font-medium uppercase leading-normal text-white shadow-md transition duration-150 ease-in-out hover:shadow-lg hover:text-black focus:shadow-lg focus:outline-none focus:ring-0 active:shadow-lg"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-6 w-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"
              />
            </svg>
          </button>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
// import AppHeader from "@/components/Header.vue";

export default {
  name: "App",
  data() {
    return {
      day: "23",
      hours: "24",
      minutes: "12",
      seconds: "32",
      loading: true,
    };
  },
  mounted() {
    const targetDate = new Date("2023-03-31"); // set your target date here
    const intervalId = setInterval(() => {
      const now = new Date();
      const timeDiff = targetDate - now;
      if (timeDiff <= 0) {
        clearInterval(intervalId);
        return;
      }
      this.days = Math.floor(timeDiff / (1000 * 60 * 60 * 24));
      this.hours = Math.floor(
        (timeDiff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      this.minutes = Math.floor((timeDiff % (1000 * 60 * 60)) / (1000 * 60));
      this.seconds = Math.floor((timeDiff % (1000 * 60)) / 1000);
    }, 1000);
  },
  created() {
    setTimeout(() => {
      if (this.loading) {
        this.loading = false;
      }
    }, 3000);
  },
  // components: {
  //   AppHeader,
  // },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,400;0,500;0,700;1,400;1,500;1,700&family=Roboto:wght@400;500&family=Tinos:ital,wght@0,700;1,400;1,700&display=swap");

a {
  transition: 0.15s;
}

.center {
  text-align: -webkit-center;
}

.background-banner {
  background-image: url(/public/web-6.webp);
}

h1 {
  font-family: Tinos, serif;
  font-weight: 600;
  font-style: italic;
}

h2 {
  font-family: "DM Sans", sans-serif;
  font-weight: 500;
}

p {
  font-family: Roboto, sans-serif;
  font-weight: 400;
}

.shadow-custom {
  box-shadow: rgba(6, 24, 44, 0.4) 0 0 0 2px,
    rgba(6, 24, 44, 0.65) 0 4px 6px -1px,
    rgba(255, 255, 255, 0.275) 0 1px 0 inset;
}

.button {
  background-color: #c13584;
}

.button:hover {
  background-color: white;
  transform: scale(1.1);
  transition: transform 0.2s ease-in-out;
}

.spinner {
  border: 5px solid rgba(0, 0, 0, 0.1);
  border-left-color: #3490dc;
  border-radius: 50%;
  animation: 1s linear infinite spin;
}
</style>
