<html lang="en" class="scroll-smooth">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>MyLink - Personal Link Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/@preline/preline@2.0.0/dist/preline.min.js"></script>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
    <script>
      tailwind.config = {
        darkMode: "class",
        theme: {
          extend: {
            colors: {
              primary: {
                50: "#f0f9ff",
                100: "#e0f2fe",
                200: "#bae6fd",
                300: "#7dd3fc",
                400: "#38bdf8",
                500: "#0ea5e9",
                600: "#0284c7",
                700: "#0369a1",
                800: "#075985",
                900: "#0c4a6e",
              },
            },
          },
        },
      };
    </script>
    <style>
      @import url("https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap");
      body {
        font-family: "Inter", sans-serif;
        transition: background-color 0.3s ease;
      }
      .link-card {
        transition: all 0.3s ease;
      }
      .link-card:hover {
        transform: translateY(-2px);
      }
      .avatar {
        transition: transform 0.3s ease;
      }
      .avatar:hover {
        transform: scale(1.05);
      }
    </style>
  </head>
  <body class="bg-gray-50 dark:bg-gray-900 min-h-screen">
    <div class="container mx-auto px-4 py-8 max-w-md">
      <!-- Profile Section -->
      <div class="text-center mb-8">
        <div
          class="avatar mx-auto mb-4 w-24 h-24 rounded-full overflow-hidden border-4 border-primary-500 shadow-lg"
        >
          <img
            src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=880&q=80"
            alt="Profile"
            class="w-full h-full object-cover"
          />
        </div>
        <h1 class="text-2xl font-bold text-gray-800 dark:text-white">
          Aidil Koto
        </h1>
        <p class="text-gray-600 dark:text-gray-300 mt-1">
          Digital Creator & Web Developer
        </p>
        <div class="flex justify-center space-x-4 mt-3">
          <button
            class="text-gray-500 hover:text-primary-500 dark:hover:text-primary-400 transition-colors"
          >
            <i class="fab fa-instagram text-xl"></i>
          </button>
          <button
            class="text-gray-500 hover:text-primary-500 dark:hover:text-primary-400 transition-colors"
          >
            <i class="fab fa-twitter text-xl"></i>
          </button>
          <button
            class="text-gray-500 hover:text-primary-500 dark:hover:text-primary-400 transition-colors"
          >
            <i class="fab fa-github text-xl"></i>
          </button>
        </div>
      </div>

      <!-- Links Section -->
      <div class="space-y-4 mb-8" id="links-container">
        <!-- Links will be dynamically inserted here -->
      </div>

      <!-- Add New Link Button -->
      <div class="fixed bottom-6 right-6">
        <button
          id="add-link-btn"
          class="bg-primary-500 hover:bg-primary-600 text-white w-14 h-14 rounded-full shadow-lg flex items-center justify-center transition-all"
        >
          <i class="fas fa-plus text-xl"></i>
        </button>
      </div>

      <!-- Theme Toggle -->
      <div class="fixed bottom-6 left-6">
        <button
          id="theme-toggle"
          class="bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 w-14 h-14 rounded-full shadow-lg flex items-center justify-center transition-all"
        >
          <i class="fas fa-moon dark:hidden"></i>
          <i class="fas fa-sun hidden dark:block"></i>
        </button>
      </div>

      <!-- Add Link Modal -->
      <div
        id="add-link-modal"
        class="hs-overlay hidden size-full fixed top-0 start-0 z-[80] overflow-x-hidden overflow-y-auto"
      >
        <div
          class="hs-overlay-open:mt-7 hs-overlay-open:opacity-100 hs-overlay-open:duration-500 mt-0 opacity-0 ease-out transition-all sm:max-w-lg sm:w-full m-3 sm:mx-auto"
        >
          <div
            class="relative flex flex-col bg-white border shadow-sm rounded-xl dark:bg-gray-800 dark:border-gray-700"
          >
            <div
              class="flex justify-between items-center py-3 px-4 border-b dark:border-gray-700"
            >
              <h3 class="font-bold text-gray-800 dark:text-white">
                Add New Link
              </h3>
              <button
                type="button"
                class="hs-dropup-toggle flex justify-center items-center size-7 text-sm font-semibold rounded-full border border-transparent text-gray-800 hover:bg-gray-100 disabled:opacity-50 disabled:pointer-events-none dark:text-white dark:hover:bg-gray-700"
                data-hs-overlay="#add-link-modal"
              >
                <span class="sr-only">Close</span>
                <svg
                  class="flex-shrink-0 size-4"
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M18 6 6 18" />
                  <path d="m6 6 12 12" />
                </svg>
              </button>
            </div>
            <div class="p-4 overflow-y-auto">
              <form id="link-form" class="space-y-4">
                <div>
                  <label
                    for="link-title"
                    class="block text-sm font-medium mb-2 dark:text-white"
                    >Title</label
                  >
                  <input
                    type="text"
                    id="link-title"
                    name="title"
                    class="py-3 px-4 block w-full border-gray-200 rounded-lg text-sm focus:border-primary-500 focus:ring-primary-500 disabled:opacity-50 disabled:pointer-events-none dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400 dark:focus:ring-gray-600"
                    required
                  />
                </div>
                <div>
                  <label
                    for="link-url"
                    class="block text-sm font-medium mb-2 dark:text-white"
                    >URL</label
                  >
                  <input
                    type="url"
                    id="link-url"
                    name="url"
                    class="py-3 px-4 block w-full border-gray-200 rounded-lg text-sm focus:border-primary-500 focus:ring-primary-500 disabled:opacity-50 disabled:pointer-events-none dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400 dark:focus:ring-gray-600"
                    placeholder="https://example.com"
                    required
                  />
                </div>
                <div>
                  <label
                    for="link-icon"
                    class="block text-sm font-medium mb-2 dark:text-white"
                    >Icon</label
                  >
                  <select
                    id="link-icon"
                    name="icon"
                    class="py-3 px-4 block w-full border-gray-200 rounded-lg text-sm focus:border-primary-500 focus:ring-primary-500 disabled:opacity-50 disabled:pointer-events-none dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400 dark:focus:ring-gray-600"
                  >
                    <option value="fas fa-globe">Website</option>
                    <option value="fab fa-youtube">YouTube</option>
                    <option value="fab fa-instagram">Instagram</option>
                    <option value="fab fa-twitter">Twitter</option>
                    <option value="fab fa-github">GitHub</option>
                    <option value="fab fa-linkedin">LinkedIn</option>
                    <option value="fab fa-tiktok">TikTok</option>
                    <option value="fas fa-envelope">Email</option>
                    <option value="fas fa-shopping-bag">Shop</option>
                  </select>
                </div>
              </form>
            </div>
            <div
              class="flex justify-end items-center gap-x-2 py-3 px-4 border-t dark:border-gray-700"
            >
              <button
                type="button"
                class="hs-dropup-toggle py-2 px-3 inline-flex items-center gap-x-2 text-sm font-medium rounded-lg border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-slate-900 dark:border-gray-700 dark:text-white dark:hover:bg-gray-800"
                data-hs-overlay="#add-link-modal"
              >
                Cancel
              </button>
              <button
                type="button"
                id="save-link-btn"
                class="py-2 px-3 inline-flex items-center gap-x-2 text-sm font-semibold rounded-lg border border-transparent bg-primary-500 text-white hover:bg-primary-600 disabled:opacity-50 disabled:pointer-events-none"
              >
                Save Link
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <script>
      // Sample link data
      let links = [
        {
          id: 1,
          title: "My Whatsapp",
          url: "https://wa.me/+6282125053345",
          icon: "fas fa-globe",
        },
        {
          id: 2,
          title: "YouTube Channel",
          url: "https://www.youtube.com/@fanny.Sepuh87",
          icon: "fab fa-youtube",
        },
        {
          id: 3,
          title: "GitHub Profile",
          url: "https://github.com/aidilkoto87",
          icon: "fab fa-github",
        },
        {
          id: 4,
          title: "Online Store",
          url: "https://www.tiktok.com/@dill_store04",
          icon: "fas fa-shopping-bag",
        },
      ];

      // DOM elements
      const linksContainer = document.getElementById("links-container");
      const addLinkBtn = document.getElementById("add-link-btn");
      const themeToggle = document.getElementById("theme-toggle");
      const saveLinkBtn = document.getElementById("save-link-btn");
      const linkForm = document.getElementById("link-form");

      // Initialize the app
      function init() {
        renderLinks();
        setupEventListeners();
        checkTheme();
      }

      // Render all links
      function renderLinks() {
        linksContainer.innerHTML = "";

        links.forEach((link) => {
          const linkElement = document.createElement("a");
          linkElement.href = link.url;
          linkElement.target = "_blank";
          linkElement.rel = "noopener noreferrer";
          linkElement.className =
            "link-card block bg-white dark:bg-gray-800 rounded-xl p-4 shadow-sm hover:shadow-md border border-gray-200 dark:border-gray-700";
          linkElement.innerHTML = `
                    <div class="flex items-center space-x-3">
                        <div class="flex-shrink-0 w-10 h-10 rounded-full bg-primary-50 dark:bg-gray-700 flex items-center justify-center text-primary-500 dark:text-primary-400">
                            <i class="${link.icon} text-lg"></i>
                        </div>
                        <div class="min-w-0 flex-1">
                            <p class="text-sm font-medium text-gray-900 dark:text-white truncate">${
                              link.title
                            }</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400 truncate">${
                              new URL(link.url).hostname
                            }</p>
                        </div>
                        <div class="flex-shrink-0">
                            <i class="fas fa-external-link-alt text-gray-400"></i>
                        </div>
                    </div>
                `;
          linksContainer.appendChild(linkElement);
        });
      }

      // Set up event listeners
      function setupEventListeners() {
        // Add new link button
        addLinkBtn.addEventListener("click", () => {
          const modal = document.getElementById("add-link-modal");
          HSOverlay.open(modal);
        });

        // Theme toggle
        themeToggle.addEventListener("click", toggleTheme);

        // Save new link
        saveLinkBtn.addEventListener("click", saveLink);
      }

      // Save new link
      function saveLink() {
        const title = document.getElementById("link-title").value;
        const url = document.getElementById("link-url").value;
        const icon = document.getElementById("link-icon").value;

        // Basic validation
        if (!title || !url) {
          alert("Please fill in all fields");
          return;
        }

        // Create new link object
        const newLink = {
          id: links.length + 1,
          title,
          url,
          icon,
        };

        // Add to links array
        links.push(newLink);

        // Re-render links
        renderLinks();

        // Close modal and reset form
        const modal = document.getElementById("add-link-modal");
        HSOverlay.close(modal);
        linkForm.reset();
      }

      // Theme functions
      function checkTheme() {
        if (
          localStorage.getItem("color-theme") === "dark" ||
          (!("color-theme" in localStorage) &&
            window.matchMedia("(prefers-color-scheme: dark)").matches)
        ) {
          document.documentElement.classList.add("dark");
        } else {
          document.documentElement.classList.remove("dark");
        }
      }

      function toggleTheme() {
        if (document.documentElement.classList.contains("dark")) {
          document.documentElement.classList.remove("dark");
          localStorage.setItem("color-theme", "light");
        } else {
          document.documentElement.classList.add("dark");
          localStorage.setItem("color-theme", "dark");
        }
      }

      // Initialize the app
      document.addEventListener("DOMContentLoaded", init);
    </script>
  </body>
</html>
