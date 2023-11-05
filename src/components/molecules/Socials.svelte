<script>
	import Social from '../atoms/Social.svelte';
	import { user } from '../../util/discord';
</script>

<div class="socials-container">
	<Social icon="github" tip="Aymenae" link="https://github.com/aymenae" />
	<Social icon="discord" tip={user.username} link={`https://discord.com/users/${user.id}`} />
	<Social icon="email" tip="aymenebrahim90@gmail.com" link="mailto:aymenebrahim90@gmail.com" />
	<Social icon="kofi" tip="Aymenae" link="https://ko-fi.com/aymenae" />
</div>

<style>
	.socials-container {
		display: flex;
		gap: 0.75rem;
	}
</style>
