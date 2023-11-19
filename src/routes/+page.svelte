<script>
	import NavHost from '../components/molecules/NavHost.svelte';
	import Hero from '../components/organisms/Hero.svelte';
	import About from '../components/organisms/About.svelte';
	import Repos from '../components/organisms/Repos.svelte';
	import Supporters from '../components/organisms/Supporters.svelte';
	import Footer from '../components/molecules/Footer.svelte';
	import Experiences from '../components/organisms/Experiences.svelte';
</script>

<NavHost />
<main>
	<Hero />
	<About />
	<Repos />
	<Experiences />
	<Supporters />
	<Footer />
</main>
