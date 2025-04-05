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
