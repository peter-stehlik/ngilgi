<template>
    <div class="px-5 pt-5 pb-0">		
        <div class="alert alert-warning text-center" role="alert" v-html="alert">
            
        </div>
    
        <ul class="nav justify-content-end">
            <li class="nav-item">
        <NuxtLink to="/" class="nav-link active" aria-current="page">Home</NuxtLink>
            </li>
        
            <li class="nav-item">
        <NuxtLink to="/history" class="nav-link">History</NuxtLink>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  data() {
    return {
    	alert: null,
    }
  },
	async created () {

    	const alertFetch = await fetch("https://vkjgzl0l.directus.app/items/alert")

    	const { data: alertData } = await alertFetch.json()

	    this.alert = alertData.alert;
	},
}
</script>
