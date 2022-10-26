<template>
	<div class="p-5">			
		<h1 class="mb-4" v-html="title"></h1>
		
		<img class="ng-featured-img mb-4" :src="featuredImage" width="1320" height="400" />
		
		<article class="mb-4" v-html="content"></article>
	</div>
</template>

<script>
export default {
  data() {
    return {
		title: null,
		content: null,
		featuredImage: null,
    }
  },
	async created () {
		const contentFetch = await fetch("https://ui96v7g6.directus.app/items/pages/2")

    	const { data: contentData } = await contentFetch.json()

		const ngFeaturedImgCode = contentData.featured_image;

	    this.title = contentData.title;
	    this.content = contentData.content;

		if( ngFeaturedImgCode ){
			var ngFeaturedImgUrl = "";
			const featuredFetch = await fetch("https://ui96v7g6.directus.app/files/" + ngFeaturedImgCode);

			const { data: featuredData } = await featuredFetch.json()

			this.featuredImage = "https://ui96v7g6.directus.app/assets/" + featuredData.filename_disk;
		}
	},
}
</script>
