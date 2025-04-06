<script lang="ts">
    import * as Accordion from "$lib/components/ui/accordion/index.js";

    const accordionContent = [
        {
            q: "Why did you make this?",
            a: "Cause I can and I didn't wanna do homework",
        },
        {
            q: "Can you add X or Y feature?",
            a: "Sure, holler at with an email at dck003@ucsd.edu I'll see what I can do."
        },
        {
            q: "Do you collect or store my Data?",
            a: "No, and I don't really plan to because theres not much I can do with it with this project and managing accounts is tedious. The only thing I record will be how many people use the service which is obviously anonymous.\n\nI also don't really have the money to keep podcasts downloaded on a server so lol\n\nI COULD reencode videos with AV1 and try acting as a host once I have my homeserver up but thats a bit of a pipe dream."
        }
    ]


  </script>


<h1 class="text-3xl font-semibold text-center m-5">About</h1>

<h2 class="text-2xl font-semibold text-center m-5">Contacts</h2>
<div class="flex justify-center my-4">
  <a href="https://github.com/davidk003" target="_blank" rel="noopener noreferrer" aria-label="GitHub Profile">
    <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36" viewBox="0 0 24 24" class="dark:invert mx-4">
      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
    </svg>
  </a>
  
  <a href="mailto:dck003@ucsd.edu" aria-label="Email Contact">
  <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36" viewBox="0 0 24 24" class="dark:invert mx-4">
    <path xmlns="http://www.w3.org/2000/svg" d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/>
  </svg>
  </a>


</div>

<h2 class="text-2xl font-semibold text-center m-5">Frequently Asked Questions</h2>
   
  <Accordion.Root class="mx-auto w-full max-w-4xl">
  {#each accordionContent as item}
    <Accordion.Item value={item.q} class="border-b">
      <Accordion.Trigger class="flex w-full items-center justify-between py-3 text-left font-medium text-gray-900 dark:text-gray-100">
        {item.q}
      </Accordion.Trigger>
      <Accordion.Content class="text-md text-gray-700 dark:text-gray-400">
        <pre>{item.a}</pre>
      </Accordion.Content>
    </Accordion.Item>
  {/each}
  </Accordion.Root>
