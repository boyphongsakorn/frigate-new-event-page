<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<div class="w-full h-16 bg-gray-800 text-white text-2xl flex items-center space-x-4 dark:bg-gray-900 dark:text-white absolute z-40">
		<img src="http://192.168.31.220:9000/assets/safari-pinned-tab-1264f127.svg" class="h-8 w-8 invert" />
		<span class="text-2xl font-semibold">FRIGATE</span>
	</div>
	<!-- <Header /> -->

	<div class="flex flex-row min-h-screen w-full bg-gray-900 text-gray-900 dark:text-white z-30">
		<div class="w-64 h-screen text-white flex flex-col space-y-4">
			<div class="flex items-center space-x-2 p-4">
				<img src="http://192.168.31.220:9000/assets/safari-pinned-tab-1264f127.svg" class="h-8 w-8 invert" />
				<span class="text-2xl font-semibold">FRIGATE</span>
			</div>
			<!-- a tag from camera menu -->
			<a href="/camera" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">Cameras</span>
			</a>
			<!-- a tag from bridseye menu -->
			<a href="/bridseye" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">Bridseye</span>
			</a>
			<!-- a tag from events menu -->
			<a href="/events" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">Events</span>
			</a>
			<!-- line -->
			<div class="border-b border-gray-700"></div>
			<!-- a tag from storage menu -->
			<a href="/storage" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<!-- storage icon -->
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">Storage</span>
			</a>
			<!-- a tag from System menu -->
			<a href="/system" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<!-- system icon -->
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">System</span>
			</a>
			<!-- a tag from Config menu -->
			<a href="/settings" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<!-- config icon -->
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">Config</span>
			</a>
			<!-- a tag from logs menu -->
			<a href="/logs" class="flex items-center space-x-2 p-4 hover:bg-gray-700">
				<!-- logs icon -->
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
				</svg>
				<span class="text-xl font-medium">Logs</span>
			</a>
		</div>
		<div class="flex flex-col flex-1 pt-16">
			<slot />
		</div>
		<!-- <div class="w-full h-16 bg-gray-800 text-white text-2xl flex items-center space-x-4">
			<img src="http://192.168.31.220:9000/assets/safari-pinned-tab-1264f127.svg" class="h-8 w-8 invert" />
			Frigate
		</div> -->
	</div>

	<!-- <main>
		<slot />
	</main> -->

	<!-- <footer>
		<p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p>
	</footer> -->
</div>

<style>
	/* .app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	} */

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
