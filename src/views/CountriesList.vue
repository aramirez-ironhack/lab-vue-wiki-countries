<template>
	<div class="column is-4" style="overflow: auto">
		<div v-for="country in countries">
			<router-link
				:to="{ name: 'details', params: { code: country.alpha3Code } }"
			>
				<a class="media is-clickable">
					<figure class="media-left">
						<p class="image is-64x64">
							<img
								:src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`"
							/>
						</p>
					</figure>
					<div class="media-content">
						<div class="content">
							<p>
								<strong>{{ country.name.common }}</strong>
							</p>
						</div>
					</div>
				</a>
			</router-link>
		</div>
	</div>
	<RouterView></RouterView>
</template>
<script setup>
import countries from "../assets/countries.json";
</script>
<style scoped>
template {
	display: flex;
}
</style>
