<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import './styles.css';

	// import Plyr from 'plyr';

	// const player = new Plyr('#player');
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
	<link rel="stylesheet" href="https://cdn.plyr.io/1.8.2/plyr.css">
	<script src="https://cdn.jsdelivr.net/hls.js/latest/hls.js"></script>
	<!-- <script src="https://cdn.plyr.io/1.8.2/plyr.js" on:load={() => {
		var video = document.querySelector('#player');

		if (Hls.isSupported()) {
			var hls = new Hls();
			hls.loadSource('https://nvr.pwisetthon.com/vod/event/1685287665.30394-fsaods/master.m3u8');
			hls.attachMedia(video);
			hls.on(Hls.Events.MANIFEST_PARSED,function() {
				video.play();
			});
		}

		plyr.setup(video);
	}}></script> -->
	<script src="https://cdn.plyr.io/1.8.2/plyr.js"></script>
</svelte:head>

<!-- events title -->
<h1 class="text-3xl font-bold text-white p-2">EVENTS</h1>

<!-- div camera arrow down after click have popup select camera -->
<div class="flex flex-row p-2">
	<div class="flex flex-col bg-gray-500 rounded-md p-2 w-1/5">
		<!-- Cameras -->
		<div class="flex justify-between">
			Cameras
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 cursor-pointer" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</div>
	</div>
	<div class="flex flex-col bg-gray-500 rounded-md ml-2 p-2 w-1/5">
		<!-- Labels -->
		<div class="flex justify-between">
			Labels
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 cursor-pointer" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</div>
	</div>
	<div class="flex flex-col bg-gray-500 rounded-md ml-2 p-2 w-1/5">
		<!-- Zones -->
		<div class="flex justify-between">
			Zones
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 cursor-pointer" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</div>
	</div>
</div>

<!-- <video id="player" playsinline controls>
	<source src="https://nvr.pwisetthon.com/vod/event/1685287665.30394-fsaods/master.m3u8" type="application/x-mpegURL" />
</video> -->

<!-- <video id="player" playsinline controls> -->
	<!-- <source src="https://nvr.pwisetthon.com/vod/event/1685287665.30394-fsaods/master.m3u8" type="application/x-mpegURL" /> -->
<!-- </video> -->

<!-- <button class="bg-blue-500 rounded-lg" on:click={() => {
	var video = document.querySelector('#player');

	if (Hls.isSupported()) {
		var hls = new Hls();
		hls.loadSource('https://nvr.pwisetthon.com/vod/event/1685287665.30394-fsaods/master.m3u8');
		hls.attachMedia(video);
		hls.on(Hls.Events.MANIFEST_PARSED,function() {
			video.play();
		});
	}

	plyr.setup(video);
}}>Play</button> -->

<!-- <section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>

		to your new<br />SvelteKit app
	</h1>

	<h2>
		try editing <strong>src/routes/+page.svelte</strong>
	</h2>

	<Counter />
</section> -->

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
