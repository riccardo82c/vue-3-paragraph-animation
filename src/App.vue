<template>
	<div class="container">
		<div class="block"></div>
		<button>Animate</button>
	</div>
	<base-modal
		@close="hideDialog"
		v-if="dialogIsVisible"
	>
		<p>This is a test dialog!</p>
		<button @click="hideDialog">Close it!</button>
	</base-modal>
	<div class="container">
		<button @click="showDialog">Show Dialog</button>
	</div>
	<div class="container--p">
		<transition mode="out-in">
			<p v-if="selected === 1">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eos, optio officia maiores recusandae molestiae exercitationem aperiam praesentium harum possimus minima sunt ipsam. Tempore consequuntur iste officia exercitationem quia quam quos!</p>
			<p v-else-if="selected === 2">Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem distinctio temporibus aliquam sit ipsum vitae aspernatur tempora consequuntur, itaque totam. Itaque soluta mollitia hic asperiores cupiditate natus eius alias atque! </p>
			<p v-else> Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatum debitis aliquid earum quaerat fugiat corporis voluptatem repellendus placeat alias at error obcaecati, architecto totam expedita voluptatibus in, accusamus aliquam optio.</p>
		</transition>
	</div>
	<button @click="select1">select 1</button>
	<button @click="select2">select 2</button>
	<button @click="select3">select 3</button>
</template>  

<script>
	export default {
		data() {
			return { dialogIsVisible: false, selected: 1 };
		},
		methods: {
			showDialog() {
				this.dialogIsVisible = true;
			},
			hideDialog() {
				this.dialogIsVisible = false;
			},
			select1() {
				this.selected = 1;
			},
			select2() {
				this.selected = 2;
			},
			select3() {
				this.selected = 3;
			},
		},
	};
</script>

<style>
	.container--p {
		height: 100px;
	}

	.container--p p {
		background: grey;
	}

	.v-enter-from {
		transform: translateY(-5px);
		opacity: 0;
	}
	.v-enter-active {
		transition: all ease-in 0.2s;
	}

	.v-enter-to,
	.v-leave-from {
		opacity: 1;
		transform: translateY(0px);
	}

	.v-leave-active {
		transition: all ease-out 0.2s;
	}
	.v-leave-to {
		opacity: 0;
		transform: translateY(+5px);
	}

	* {
		box-sizing: border-box;
	}
	html {
		font-family: sans-serif;
	}
	body {
		margin: 0;
	}
	button {
		font: inherit;
		padding: 0.5rem 2rem;
		border: 1px solid #810032;
		border-radius: 30px;
		background-color: #810032;
		color: white;
		cursor: pointer;
	}
	button:hover,
	button:active {
		background-color: #a80b48;
		border-color: #a80b48;
	}
	.block {
		width: 8rem;
		height: 8rem;
		background-color: #290033;
		margin-bottom: 2rem;
	}
	.container {
		max-width: 40rem;
		margin: 2rem auto;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		padding: 2rem;
		border: 2px solid #ccc;
		border-radius: 12px;
	}
</style>