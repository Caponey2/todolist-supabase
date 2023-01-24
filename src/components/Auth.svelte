<script>
	import { supabase } from '../supabase.js';

	let loading = false;
	let email;

	const handleLogin = async () => {
		try {
			loading = true;
			const { data, error } = await supabase.auth.signInWithOtp({ email });
			if (error) alert(error.error_description | error.message);
			alert('Check your email for the login link!');
		} catch (error) {
			console.error(error);
			alert(error.error_description | error.message);
		} finally {
			loading = false;
		}

		loading = false;
	};
</script>

<h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">Log In</h1>
<p class="text-center mt-2">Sign in via magic link with your email below.</p>
<form on:submit|preventDefault={handleLogin}>
	<div class="flex flex-col text-sm mb-2">
		<label class="font-bold mb-2 text-grey-800" for="email">Email</label>
		<input
			type="email"
			placeholder="Your email"
			name="email"
			class="appearance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
			bind:value={email}
		/>
	</div>
	<button
		type="submit"
		class="w-full shadow-sm bg-blue-500 hover:bg-blue-600 text-white py-2 px-4 rounded"
		>Log In</button
	>
</form>
