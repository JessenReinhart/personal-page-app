<script>
  import { slide } from "svelte/transition";
  import { quintOut } from "svelte/easing";

  let name = "Jessen Reinhart";
  let position = "Frontend Software Engineer";
  let location = "Banten, Indonesia";
  let summary = `Hello! My name is ${name}. I am a ${position} based in ${location}. I mainly use ReactJS as my primary tool, but can also work with VueJS and Svelte. My life motto is "Stay Curious" because there are a lot of things in this world that we don't know, and the more we learn, the more we discover that knowledge is endless.`;
  let linkedinUrl = "https://www.linkedin.com/in/jessenreinhart/";
  let githubUrl = "https://github.com/JessenReinhart";

  let experiences = [
    {
      company: "Inspigo",
      position: "Frontend Engineer",
      duration: "December 2022 - Present (8 months)",
      responsibilities: [
        "Develops a Web CMS using ReactJS, Typescript, and NextJS",
        "Develops a dashboard app using ReactJS, TypeScript, and NextJS",
      ],
    },
    {
      company: "SIRCLO",
      position: "Frontend Engineer",
      duration: "November 2019 - November 2022 (3 years 1 month)",
      responsibilities: [
        "Developing a ReactJS based CMS for managing webstore contents.",
        "Developing a SSR web frontend for online shop webstore using NextJS and TailwindCSS.",
        "Developing a ReactJS based frontend for payment page.",
      ],
    },
    {
      company: "Aksaramaya",
      position: "UI Developer",
      duration: "March 2019 - November 2019 (9 months)",
      responsibilities: [
        "Designing and developing UI for web dashboards and apps.",
        "Using ReactJS and React-Admin to build a CMS & Dashboard app.",
        "Using Chart.js to display graphs from the database.",
        "Fetching data from APIs and displaying the data on the app.",
        "Using Figma and Adobe XD to design UI and interactive mockup.",
      ],
    },
    {
      company: "Darshana Design Studio",
      position: "Image Specialist",
      duration: "December 2018 - February 2019 (3 months)",
      responsibilities: [
        "Editing member's images (creative editing, background replacement, beauty editing, GIF animation).",
      ],
    },
    {
      company: "Laboratory of Informatics Engineering, Gunadarma University",
      position: "Laboratory Assistant",
      duration: "February 2018 - November 2018 (10 months)",
      responsibilities: [
        "Guided students during lab sessions.",
        "Tutored students during lab sessions.",
        "Graded laboratory workbook and reports regarding content and accuracy in technical writing.",
      ],
    },
    {
      company: "Code Margonda",
      position: "Graphic Designer / Assistant / Developer",
      duration: "August 2016 - March 2018 (1 year 8 months)",
      responsibilities: [
        "Tutored workshop sessions about basic web development.",
        "Tutored workshop sessions about basic game development using Construct 2.",
        "Taught junior high school students in IT.",
        "Designed posters and Instagram feeds about upcoming events.",
      ],
    },
  ];

  let education = {
    institution: "Gunadarma University",
    degree: "Bachelor's degree in Informatics Engineering",
    duration: "2014 - 2018",
  };

  let activeTab = "summary";
</script>

<main class="container mx-auto px-4 py-8">
  <header class="shadow-lg bg-gray-50 text-gray-600 rounded py-4">
    <div class="container mx-auto px-4">
      <h1 class="text-2xl font-bold">{name}</h1>
      <p class="text-lg">{position}</p>
      <p class="text-lg">{location}</p>
    </div>
    <div class="flex items-center space-x-4 p-4 opacity-50">
      <a href={linkedinUrl} target="_blank" rel="noopener noreferrer">
        <img
          src="https://sguru.org/wp-content/uploads/2018/02/linkedin-png-linkedin-icon-1600.png"
          alt="LinkedIn"
          class="w-6 h-6 hover:opacity-75"
        />
      </a>
      <a href={githubUrl} target="_blank" rel="noopener noreferrer">
        <img
          src="https://www.pngarts.com/files/8/Black-Github-Logo-PNG-Image.png"
          alt="GitHub"
          class="w-6 h-6 hover:opacity-75"
        />
      </a>
    </div>
  </header>

  <nav
    class="flex space-x-2 mt-8 w-full justify-center md:relative md:bg-white md:p-0 md:border-0 fixed bottom-0 left-0 p-6 bg-gray-50 border z-50"
  >
    <button
      class="py-2 px-4 rounded-md border-0 cursor-pointer hover:shadow-lg focus:shadow-inner focus:bg-gray-100 transition"
      class:selected={activeTab === "summary"}
      class:shadow-inner={activeTab === "summary"}
      on:click={() => (activeTab = "summary")}
    >
      Summary
    </button>
    <button
      class="py-2 px-4 rounded-md border-0 cursor-pointer hover:shadow-lg focus:shadow-inner focus:bg-gray-100 transition"
      class:selected={activeTab === "experiences"}
      class:shadow-inner={activeTab === "experiences"}
      on:click={() => (activeTab = "experiences")}
    >
      Experiences
    </button>
    <button
      class="py-2 px-4 rounded-md border-0 cursor-pointer hover:shadow-lg focus:shadow-inner focus:bg-gray-100 transition"
      class:shadow-inner={activeTab === "education"}
      class:selected={activeTab === "education"}
      on:click={() => (activeTab = "education")}
    >
      Education
    </button>
  </nav>

  {#if activeTab === "summary"}
    <section
      class="mt-8 mb-20"
      transition:slide={{
        duration: 300,
        x: 100,
        y: 500,
        opacity: 0.5,
        easing: quintOut,
      }}
    >
      <h2 class="text-2xl font-bold">Summary</h2>
      <p class="mt-4">{summary}</p>
    </section>
  {/if}

  {#if activeTab === "experiences"}
    <section
      class="mt-8 mb-20"
      transition:slide={{
        duration: 300,
        x: 100,
        y: 500,
        opacity: 0.5,
        easing: quintOut,
      }}
    >
      <h2 class="text-2xl font-bold">Experiences</h2>
      {#each experiences as experience}
        <div class="mt-4">
          <h3 class="text-lg font-bold">
            {experience.position} - {experience.company}
          </h3>
          <p class="text-sm italic">{experience.duration}</p>
          <ul class="list-disc list-inside">
            {#each experience.responsibilities as responsibility}
              <li>{responsibility}</li>
            {/each}
          </ul>
        </div>
      {/each}
    </section>
  {/if}

  {#if activeTab === "education"}
    <section
      class="mt-8 mb-20"
      transition:slide={{
        duration: 300,
        x: 100,
        y: 500,
        opacity: 0.5,
        easing: quintOut,
      }}
    >
      <h2 class="text-2xl font-bold">Education</h2>
      <div class="mt-4">
        <h3 class="text-lg font-bold">{education.institution}</h3>
        <p class="text-sm italic">{education.degree} ({education.duration})</p>
      </div>
    </section>
  {/if}
</main>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://unpkg.com/tailwindcss@2.2.19/dist/tailwind.min.css"
  />
  <title>Jessen Reinhart's Personal Page</title>
</svelte:head>

<style>
  .selected {
    background-color: #e5e7eb;
    color: #000000;
    font-weight: bold;
  }
</style>
