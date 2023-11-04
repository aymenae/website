<script>
	import Social from '../atoms/Social.svelte';
	import { user } from '../../util/discord';
</script>

<div class="socials-container">
	<Social icon="github" tip="Aymen" link="https://github.com/aymenae" />
	<Social icon="discord" tip={user.username} link={`https://discord.com/users/${user.id}`} />
	<!-- <Social icon="kofi" tip="Tristanaa" link="https://ko-fi.com/tristanaa" /> -->
</div>

<style>
	.socials-container {
		display: flex;
		gap: 0.75rem;
	}
</style>
