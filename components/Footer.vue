<template>
  	<div>				
		<footer class="p-5 bg-dark text-white">
			<div class="row">
				<div class="col-12 col-lg-3">
					<a class="" href="https://www.capesfoundation.org.au/" target="_blank" v-html="logo">

					</a>
				</div>

				<div class="col-12 col-lg-4 mt-4 mt-lg-0" v-html="footer_1">

				</div>

				<div class="col-12 col-lg-4 offset-lg-1 mt-4 mt-lg-0" v-html="footer_2">

				</div>
			</div>			
		</footer>
		
		<div class="copy px-5 py-2 bg-secondary text-white" v-html="copy"> </div>
	</div>
</template>

<script>
export default {
  data() {
    return {
		logo: null,
		footer_1: null,
		footer_2: null,
		copy: null,
    }
  },
	async created () {
    	const footerFetch = await fetch("https://vkjgzl0l.directus.app/items/footer")

    	const { data: footerData } = await footerFetch.json()

	    this.logo = footerData.logo_svg;
	    this.footer_1 = footerData.footer_content_1;
	    this.footer_2 = footerData.footer_content_2;
	    this.copy = footerData.copyright;
	},
}
</script>
