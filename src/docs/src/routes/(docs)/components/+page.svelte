<script>
  import { page } from "$app/stores"
  import SEO from "$components/SEO.svelte"
  import Translate from "$components/Translate.svelte"
  import Ads from "$components/Ads.svelte"
  export let data
  let { components } = data
</script>

<SEO title="Components" desc="Tailwind CSS component examples by daisyUI" />
<div class="flex flex-col-reverse justify-between gap-6 xl:flex-row">
  <div class="flex flex-col gap-6 ps-6 pt-10">
    <div class="prose max-w-4xl flex-grow">
      <h1><Translate text="All daisyUI components" /></h1>
      <p>{Object.keys(components).length} <Translate text="components" /></p>
    </div>
    <div
      class="not-prose grid grid-cols-1 gap-x-6 gap-y-12 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-4">
      {#each components as { slug, title, desc }}
        <a
          class="card card-compact hover:bg-base-200 transition-all duration-200 hover:-translate-y-1"
          href={`${$page.url.pathname.replace(/\/$/, "")}/${slug}`}>
          <figure class="px-4 pt-4">
            <img
              loading="lazy"
              src={`/images/components/${slug}.jpg`}
              class="border-base-content bg-base-300 rounded-lg border border-opacity-5"
              alt={title} />
          </figure>
          <div class="card-body">
            <h2 class="card-title"><Translate text={title} /></h2>
            <p class="text-xs opacity-60"><Translate text={desc || ""} /></p>
          </div>
        </a>
      {/each}
    </div>
  </div>
  <Ads slot="carbon2" />
</div>
