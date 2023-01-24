<script>
	import '../app.css';
	import { supabase } from '../supabase.js';
	import Auth from '../components/Auth.svelte';
	import { user } from '../stores/authStore.js';
	import { loadTodos } from '../stores/todoStore';
	import Navbar from '../components/Navbar.svelte';

	user.set(supabase.auth.getUser());

	supabase.auth.onAuthStateChange((event, session) => {
		user.set(session?.user ?? null);
		if (session?.user) {
			loadTodos();
		}
	});
</script>

<div class="container mx-auto my-6 max-w-lg">
	{#if $user}
		<Navbar />
		<slot />
	{:else}
		<Auth />
	{/if}
</div>
