<script lang="ts">
  import type { Snippet } from 'svelte'

  type Message = string | { content: Snippet; href?: string; variant?: 'default' | 'dark' }

  let {
    class: className,
    messages,
    isSender = false
  }: { class?: string; messages: Message[]; isSender?: boolean } = $props()

  const SIZE = 40
</script>

<div class="flex flex-col gap-1 {isSender ? 'items-end' : 'items-start'}">
  {#each messages as message, index (index)}
    {@const variant = typeof message === 'object' ? message.variant : undefined}
    {@const href = typeof message === 'object' ? message.href : undefined}
    {@const fillClass =
      variant === 'dark' ? 'fill-black' : isSender ? 'fill-[#0094FF]' : 'fill-message'}
    {@const bgClass =
      variant === 'dark'
        ? 'bg-black text-white selection:bg-white/30'
        : isSender
          ? 'bg-[#0094FF] text-white selection:bg-white/30'
          : 'bg-message selection:bg-black/20'}
    <div class="flex">
      {#if isSender}
        <!-- Left rounded edge for sender -->
        <svg
          class="-mr-6"
          width={(SIZE / 121) * 93}
          height={SIZE}
          viewBox="0 0 93 121"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M38.2285 4.53223C52.5705 0.000102997 65.8942 0 92.541 0V121C65.8942 121 52.5705 121 38.2285 116.468C22.5696 110.772 10.2347 98.4442 4.53516 82.7949C0.000221252 71.3903 0 62.92 0 60.5C0 58.08 0.000221252 49.6097 4.53516 38.2051C10.2347 22.5559 22.5696 10.2282 38.2285 4.53223Z"
            class={fillClass}
          />
        </svg>
      {:else}
        <!-- Left edge with tail for receiver (last message) -->
        {#if index === messages.length - 1}
          <svg
            class="-mr-6"
            width={(SIZE / 121) * 93}
            height={(SIZE / 121) * 142}
            viewBox="0 0 93 142"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M66 121H92.541V0C65.8942 0 52.5705 0.000102997 38.2285 4.53223C22.5696 10.2282 10.2347 22.5559 4.53516 38.2051C0.000221252 49.6097 0 58.08 0 60.5C0 62.92 0.000219822 71.3903 4.53516 82.7949C9.02507 95.1229 18.2797 104.404 28.7402 111.976C31.7741 114.171 32.5953 118.94 32 124C31 132.5 23 137 27 141C30.7375 144.737 52.8316 121 66 121Z"
              class={fillClass}
            />
          </svg>
        {:else}
          <svg
            class="-mr-6"
            width={(SIZE / 121) * 93}
            height={SIZE}
            viewBox="0 0 93 121"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M38.2285 4.53223C52.5705 0.000102997 65.8942 0 92.541 0V121C65.8942 121 52.5705 121 38.2285 116.468C22.5696 110.772 10.2347 98.4442 4.53516 82.7949C0.000221252 71.3903 0 62.92 0 60.5C0 58.08 0.000221252 49.6097 4.53516 38.2051C10.2347 22.5559 22.5696 10.2282 38.2285 4.53223Z"
              class={fillClass}
            />
          </svg>
        {/if}
      {/if}

      {#if href}
        <a
          {href}
          target="_blank"
          rel="noopener noreferrer external"
          style:height={`${SIZE}px`}
          class="z-10 flex items-center rounded-2xl px-2 text-lg tracking-[-0.015rem] lg:text-xl {bgClass}"
        >
          {#if typeof message === 'string'}
            {message}
          {:else}
            {@render message.content()}
          {/if}
        </a>
      {:else}
        <p
          style:height={`${SIZE}px`}
          class="z-10 flex items-center rounded-2xl px-2 text-lg tracking-[-0.015rem] lg:text-xl {bgClass}"
        >
          {#if typeof message === 'string'}
            {message}
          {:else}
            {@render message.content()}
          {/if}
        </p>
      {/if}

      {#if isSender}
        <!-- Right edge with tail for sender (last message) -->
        {#if index === messages.length - 1}
          <svg
            class="-ml-6"
            width={(SIZE / 121) * 93}
            height={(SIZE / 121) * 142}
            viewBox="0 0 93 142"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M27 121H0.459V0C27.1058 0 40.4295 0.000102997 54.7715 4.53223C70.4304 10.2282 82.7653 22.5559 88.4648 38.2051C92.9998 49.6097 93 58.08 93 60.5C93 62.92 92.9998 71.3903 88.4648 82.7949C83.9749 95.1229 74.7203 104.404 64.2598 111.976C61.2259 114.171 60.4047 118.94 61 124C62 132.5 70 137 66 141C62.2625 144.737 40.1684 121 27 121Z"
              class={fillClass}
            />
          </svg>
        {:else}
          <svg
            class="-ml-6"
            width={(SIZE / 121) * 93}
            height={SIZE}
            viewBox="0 0 93 121"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M54.3125 4.53223C39.9705 0.000102997 26.6468 0 0 0V121C26.6468 121 39.9705 121 54.3125 116.468C69.9714 110.772 82.3064 98.4442 88.0059 82.7949C92.5408 71.3903 92.541 62.92 92.541 60.5C92.541 58.08 92.5408 49.6097 88.0059 38.2051C82.3064 22.5559 69.9714 10.2282 54.3125 4.53223Z"
              class={fillClass}
            />
          </svg>
        {/if}
      {:else}
        <!-- Right rounded edge for receiver -->
        <svg
          class="-ml-6"
          width={(SIZE / 121) * 93}
          height={SIZE}
          viewBox="0 0 93 121"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M54.3125 4.53223C39.9705 0.000102997 26.6468 0 0 0V121C26.6468 121 39.9705 121 54.3125 116.468C69.9714 110.772 82.3064 98.4442 88.0059 82.7949C92.5408 71.3903 92.541 62.92 92.541 60.5C92.541 58.08 92.5408 49.6097 88.0059 38.2051C82.3064 22.5559 69.9714 10.2282 54.3125 4.53223Z"
            class={fillClass}
          />
        </svg>
      {/if}
    </div>
  {/each}
</div>

{className}
