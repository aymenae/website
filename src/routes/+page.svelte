<script>
	import NavHost from '../components/molecules/NavHost.svelte';
	import Hero from '../components/organisms/Hero.svelte';
	import About from '../components/organisms/About.svelte';
	import Repos from '../components/organisms/Repos.svelte';
	import Supporters from '../components/organisms/Supporters.svelte';
	import Footer from '../components/molecules/Footer.svelte';
	import Experiences from '../components/organisms/Experiences.svelte';
	import Monday from '../components/organisms/Monday.svelte';
	import { toZonedTime } from 'date-fns-tz';
	import { onMount } from 'svelte';

	let isMonday = false;

	onMount(() => {
		// Only run this code on the client
		const amsterdamTimeZone = 'Europe/Amsterdam';
		const currentDate = new Date();
		const zonedDate = toZonedTime(currentDate, amsterdamTimeZone);

		// Check if today is Monday (0 = Sunday, 1 = Monday, ..., 6 = Saturday)
		isMonday = zonedDate.getDay() === 1;
	});
</script>

{#if isMonday}
	<Monday />
{:else}
	<main>
		<Hero />
		<About />
		<Repos />
		<Experiences />
		<Supporters />
		<Footer />
	</main>
{/if}
