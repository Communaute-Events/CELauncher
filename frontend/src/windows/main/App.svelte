<script lang="ts">
import {window as w, app, os} from '@neutralinojs/lib';
import nsLogo from '@/assets/ce.png';
import './app.css';
import { onMount } from 'svelte';
let uuid = '';

onMount(async()=>{
  w.setDraggableRegion("drag")
  os.showNotification("drag","e")
})
</script>

<main>
	<div class="custom-taskbar" id="drag">
		<button class="unselectable"
			on:click={() => {
				app.exit();
			}}>
			<img width="26" height="26" src="https://img.icons8.com/metro/26/000000/multiply.png" alt="multiply" class="unselectable"/>
		</button>
	</div>
	<div class="logo">
		<a href="https://svelte.dev" target="_blank" rel="noreferrer"> </a>
		<img src={nsLogo} class="logo svelte" alt="CELOGO" />
	</div>
	<div class="content">
		<p>Installeur de mods</p>
		<input bind:value={uuid} placeholder="id de l'évenement..." />
		<footer>
			<div class="text">
				<p>commu.events</p>
			</div>
		</footer>
	</div>
</main>

<style>
:global(body) {
	background: #33cfa6;
	border: none;
}
.custom-taskbar {
	display: flex;
	justify-content: flex-end;
	background-color: #1f846c;
	width: 100%;
	position: fixed;
	top: 0;
	left: 0;
}

.custom-taskbar button {
	all: unset;
}

.logo {
	height: 8em;
	padding: 2.5em;
	will-change: filter;
	transition: filter 300ms;
	opacity: 0;
	transform: translateY(20px);
	animation: fadeInUp 2s ease-out forwards;
}
.content {
	margin-top: 40px;
	opacity: 0;
	transform: translateY(20px);
	animation: fadeInUp 1s ease-out forwards 1s;
}
@keyframes fadeInUp {
	0% {
		opacity: 0;
		transform: translateY(20px);
	}
	100% {
		opacity: 1;
		transform: translateY(0);
	}
}
.content input {
	background-color: #1f846c;
	border: 1px solid #34bc97;
	color: white;
	padding: 10px;
	border-radius: 4px;
}
.content input::placeholder {
	color: rgb(240, 240, 240);
}

.content p {
	font-family: 'Minecraftia', sans-serif;
	font-weight: normal;
	font-style: normal;
}

@media (max-width: 600px) {
	.logo {
		height: 4em;
		padding: 1.5em;
	}
	.content {
		margin-top: 20px;
	}
	footer .text {
		font-style: oblique;
		margin-top: 16px;
		margin-bottom: 1px;
	}
}
</style>
