<script lang="ts">
  import MessageBubbles from '$lib/components/MessageBubbles.svelte'
</script>

{#snippet quiroMessage()}
  currently building
  <img src="/quiro.png" alt="quiro" class="mr-1 ml-2 h-6 -rotate-3 drop-shadow-sm" />
  <span class="font-semibold">quiro</span>
{/snippet}

{#snippet likeActually()}
  (like, <i class="ml-1">actually</i>)
{/snippet}

{#snippet xLink()}
  <svg height="15" viewBox="0 0 1200 1227" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path
      d="M362.59 -10L365.57 -5.66309L668.024 434.521L1047.45 -6.52148L1050.44 -10H1182.68L1168.47 6.52148L726.751 519.984L1208.24 1220.71L1219 1236.37H837.41L834.431 1232.03L514.603 766.583L113.447 1232.89L110.454 1236.37H-21.7949L-7.58105 1219.85L455.888 681.137L-8.24219 5.66309L-19.0039 -10H362.59ZM529.893 614.204L577.36 682.098L579.165 684.679V684.705L897.687 1140.3H1035.89L650.685 589.309L603.217 521.415H603.216L301.404 89.6943H163.204L529.893 614.204Z"
      fill="white"
      stroke="white"
      stroke-width="20"
    />
  </svg>
  <span class="ml-1">@simplygandan</span>
{/snippet}

{#snippet githubLink()}
  <svg width="19" viewBox="0 0 1024 1024" fill="none">
    <path
      fill-rule="evenodd"
      clip-rule="evenodd"
      d="M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z"
      transform="scale(64)"
      fill="white"
    />
  </svg>
  <span class="ml-1">@gandandev</span>
{/snippet}

{#snippet mail()}
  <span class="text-blue-500 underline underline-offset-4">hey@gandan.dev</span>
{/snippet}

<div class="mx-auto my-12 w-full max-w-xl space-y-5 px-4">
  <MessageBubbles messages={["hey! i'm gandan", "i'm 14 y/o dev and designer from 🇰🇷"]} />

  <MessageBubbles
    messages={[
      { content: quiroMessage },
      "it's an ai study app that actually teaches you",
      { content: likeActually },
      'think duolingo but for any textbook 😎'
    ]}
  />

  <img src="/quiro-screenshot.png" alt="screenshot of quiro" class="w-48 rotate-2" />

  <MessageBubbles
    messages={[
      'follow my journey:',
      { content: xLink, href: 'https://x.com/simplygandan', variant: 'dark' },
      { content: githubLink, href: 'https://github.com/gandandev', variant: 'dark' }
    ]}
  />

  <MessageBubbles messages={['mail me at:', { content: mail, href: 'mailto:hey@gandan.dev' }]} />

  <p class="mt-10 mb-8 text-center text-sm text-balance text-zinc-400">
    if you've noticed the custom message bubbles, you're an amazing person
  </p>
</div>
