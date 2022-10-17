<template>
	<div class="column is-8">
		<section class="section">
			<figure class="image is-128x128">
				<img :src="imageSrc" />
			</figure>
			<div class="title">{{ countryName }}</div>
			<table class="table is-fullwidth">
				<tbody>
					<tr>
						<td>Capital</td>
						<td>{{ capital }}</td>
					</tr>
					<tr>
						<td>Area</td>
						<td>{{ area }} km <sup>2</sup></td>
					</tr>
					<tr>
						<td>Borders</td>
						<td>
							<ul>
								{{
									borders
								}}
							</ul>
						</td>
					</tr>
				</tbody>
			</table>
		</section>
	</div>
</template>
<script setup>
import countries from "../assets/countries.json";
import { useRoute } from "vue-router";
import { ref, onMounted, watch } from "vue";
const route = useRoute();

let imageSrc = ref();
let countryName = ref();
let capital = ref();
let area = ref();
let borders = ref();

watch(
	() => route.params.code,
	(newValue) => {
		console.log(route.params.code);
		// isLoading.value = true;
		findDetail();
	}
);

const findDetail = () => {
	countries.filter((country) => {
		if (country.alpha3Code === route.params.code) {
			return (
				(imageSrc.value = `https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`),
				(countryName.value = country.name.common),
				(area.value = country.area),
				(capital.value = country.capital),
				(borders.value = country.borders)
			);
		}
	});
};
//console.log(countries);
</script>
<style scoped></style>
