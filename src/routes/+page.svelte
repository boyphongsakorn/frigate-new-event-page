<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import './styles.css';

	import Plyr from 'plyr';

	//const player = new Plyr('#player');

	// array for event
	const fetchevent = (async () => {
		const response = await fetch('http://192.168.31.220:9000/api/events?cameras=all&labels=all&zones=all&sub_labels=all&favorites=0&include_thumbnails=0&limit=25');
		const data = await response.json();
		return data;
	})();

	function unixToDateTime(unixTimestamp) {
		var date = new Date(unixTimestamp * 1000);
		var year = date.getFullYear() + 543;
		var month = date.getMonth() + 1;
		month = month.toString();
		var day = "0" + date.getDate();
		var hours = "0" + date.getHours();
		var minutes = "0" + date.getMinutes();
		var seconds = "0" + date.getSeconds();
		var formattedTime = day.substr(-2) + '/' + month.substr(-2) + '/' + year + ' ' + hours.substr(-2) + ':' + minutes.substr(-2) + ':' + seconds.substr(-2);
		return formattedTime;
	}

	function calminfromunixtimetonow(unixTimestamp) {
		var date = new Date(unixTimestamp * 1000);
		var now = new Date();
		var diff = now - date;
		//convert to sec
		var sec = Math.floor(diff / 1000);
		var min = Math.floor(diff / 60000);
		// if sec < 60 return sec
		if (diff < 60000) {
			return sec + 's ago';
		}
		// if min > 60 return hour
		if (min > 60) {
			var hour = Math.floor(min / 60);
			return hour + 'h ago';
		} else {
			return min + 'm ago';
		}
	}

	function cameraname(camera_id) {
		//remove _ and Upper case first letter
		var name = camera_id.replace(/_/g, ' ');
		name = name.replace(/\w\S*/g, function(txt) {
			return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
		});
		return name;
	}
</script>

<svelte:head>
	<title>Frigate</title>
	<meta name="description" content="Svelte demo app" />
	<script src="https://cdn.plyr.io/1.8.2/plyr.js"></script>
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
</svelte:head>

<!-- events title -->
<h1 class="text-3xl font-bold text-white p-2">EVENTS</h1>

<!-- div camera arrow down after click have popup select camera -->
<div class="flex flex-row p-2">
	<div class="flex flex-col bg-gray-500 rounded-md p-2 w-1/5">
		<!-- Cameras -->
		<div class="flex justify-between">
			Cameras
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</div>
	</div>
	<div class="flex flex-col bg-gray-500 rounded-md ml-2 p-2 w-1/5">
		<!-- Labels -->
		<div class="flex justify-between">
			Labels
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</div>
	</div>
	<div class="flex flex-col bg-gray-500 rounded-md ml-2 p-2 w-1/5">
		<!-- Zones -->
		<div class="flex justify-between">
			Zones
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
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
<!-- card for event -->
{#await fetchevent}
{:then event}
	{#each event as item}
	<div class="flex flex-row m-1 bg-gray-500 rounded-lg" on:click={() => {
		//hide all video tag
		var allvideo = document.querySelectorAll('video');
		allvideo.forEach((item) => {
			// item.pause();
			// item.classList.add('hidden');
			// item.classList.add('hidden');
			// const player = new Plyr(item);
			// player.pause();
			// player.toggleControls(false);
			// player.destroy();
			item.pause();
			try {
				var plyrtest = document.querySelector('.plyr');
				plyrtest.classList.add('hidden');
			} catch (error) {
				console.log(error);
			}
		});
		//hide all detail-* element
		var alldetail = document.querySelectorAll('.detail');
		alldetail.forEach((item) => {
			item.classList.add('hidden');
		});
		// var video = document.querySelector('#' + item.id);
		var video = document.getElementById(item.id);
		//if not hidden class then add hidden class
		if (!video.classList.contains('hidden')) {
			// alert('not hidden');
			// video.classList.add('hidden');
			//unloaded video
			// video.pause();
			// video.destroy();
			// video.toggleControls(false);
			//const player = new Plyr(video);
			//video.classList.add('hidden');
			setTimeout(() => {
				// player.destroy();
				video.classList.add('hidden');
				// const player = new Plyr(video);
				video.pause();
				// player.pause();
				// player.toggleControls(false);
				// player.destroy();
				//find class plyr and add hidden class
				var plyrtest = document.querySelector('.plyr');
				plyrtest.classList.add('hidden');
			}, 1000);
		} else {
			var detail = document.getElementById('detail-' + item.id);
				detail.classList.remove('hidden');
			if(item.has_clip){
				//remove hidden class
				video.classList.remove('hidden');
			
				if (Hls.isSupported()) {
					var hls = new Hls();
					hls.loadSource('https://nvr.pwisetthon.com/vod/event/'+item.id+'/master.m3u8');
					hls.attachMedia(video);
					hls.on(Hls.Events.MANIFEST_PARSED,function() {
						video.play();
					});
				}

				// const player = new Plyr(document.getElementById(item.id));

				// player.setup(video);

				// player.setup(video);
			
				plyr.setup(video);

				// setTimeout(() => {
				// 	var test2 = document.getElementById(item.id);
				// 	test2.plyr.pause();
				// }, 5000);
			}
		}
		// document.querySelector('#' + item.id).classList.remove('hidden');
	}}>
		<div class="relative rounded-l flex-initial min-w-[125px] h-[125px] bg-contain bg-no-repeat bg-center" style="background-image: url('http://192.168.31.220:9000/api/events/{item.id}/thumbnail.jpg'); background-size: cover; background-position: center;">
			<!-- bar on bottom say in progress -->
			{#if item.end_time == null}
				<div class="absolute bottom-0 left-0 w-full h-1/4 bg-gradient-to-t from-black text-center text-white">IN PROGRESS</div>
			{/if}
		</div>
		<div class="flex flex-col bg-gray-500">
			<span class="pl-2 pt-2 text-white text-lg font-bold">Person({(item.top_score*100).toFixed(0)}%)</span>
			<div class="inline-flex">
				<svg xmlns="http://www.w3.org/2000/svg" class="h-6 text-white pl-2" viewBox="0 0 20 20" fill="currentColor">
					<path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9 4a1 1 0 112 0v5.243l2.445 2.445a1 1 0 11-1.414 1.414L10 10.414l-1.031 1.03a1 1 0 01-1.414-1.414L9 9.243V4z" clip-rule="evenodd" />
				</svg>
				<span class="text-white pl-2"> {unixToDateTime(item.start_time)} - {calminfromunixtimetonow(item.start_time)}</span>
			</div>
			<div class="inline-flex">
				<!-- camera icon -->
				<img src="https://flaticons.net/icon.php?slug_category=science-technology&slug_icon=cctv-camera" class="h-6 text-white pl-2" />
				<span class="text-white pl-2"> {cameraname(item.camera)}</span>
			</div>
			<div class="inline-flex">
				<!-- location icon -->
				<img src="https://cdn.iconscout.com/icon/free/png-256/free-location-1361-439490.png" class="h-6 text-white pl-2 invert" />
				<span class="text-white pl-2"> {item.area ? item.area : ""}</span>
			</div>
		</div>
	</div>
	<!-- video player -->
	<div id="detail-{item.id}" class="text-center w-full rounded-r hidden detail">
		{#if item.has_clip}
			<button class="rounded-lg bg-white text-black p-2 mb-2">Clip</button>
		{:else}
			<button class="rounded-lg bg-gray-500 text-black p-2 mb-2">Clip</button>
		{/if}
		<button class="rounded-lg bg-white text-black p-2 mb-2">Snapshot</button>
		<video id={item.id} playsinline controls class="hidden">
		</video>
	</div>
	{/each}
{/await}

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
