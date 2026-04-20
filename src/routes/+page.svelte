<script>
  import SlideGallery from '$lib/components/MultimediaGallery/SlideGallery.svelte';
  import TitleSlide from '$lib/components/MultimediaGallery/TitleSlide.svelte';
  import PhotoSlide from '$lib/components/MultimediaGallery/PhotoSlide.svelte';
  import TextSlide from '$lib/components/MultimediaGallery/TextSlide.svelte';
  import CreditsSlide from '$lib/components/MultimediaGallery/CreditsSlide.svelte';


  let { data } = $props();
</script>

<SlideGallery>
  <TitleSlide
    headline="From Trolleys to Express Trains"
    smallHeadline="A Brief History History of New York City's Public Transit"
    intro="As plans for new transit lines advance, from the Second Avenue Subway to the Interborough Express, a brief look back at how far New York City public transit has come"
  />

  {#each data.story as slide (slide.id)}
    {#if slide.type === 'photo'}
      <PhotoSlide photo={slide} />
    {:else if slide.type === 'text'}
      <TextSlide {slide} />
    {/if}
  {/each}

  <CreditsSlide>
    <h2>About These Photographs</h2>
    <p>
      All images are sourced from the New York Public Library Digital Collection, Library of Congress, Wikimedia Commons and public domain images on Flickr. For more historical photos of New York City transit, check out the
      <a href="https://digitalcollections.nypl.org/" target="_blank">
        New York Public Library</a>'s digital collection.
    </p>
    <br>
    <h2>Credits</h2>
    <p>History101.nyc, the Bard Graduate Center, nycsubway.org, NYPL records, NYC Department of Records and Information Services and the Village Preservation Blog.</p>
    <br>
    <h2>Icons</h2>
    <p>Icons used in this presentation are from the Noun Project and are used under a Creative Commons Attribution 3.0 Unported License. Icons by visual language, Vektorify, Bakunetsu Kaito, Firza Alamsyah, Adrien Coquet and Daniel.</p>
  </CreditsSlide>
</SlideGallery>