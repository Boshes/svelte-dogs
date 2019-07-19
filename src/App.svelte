<script>
import Dog from './Dog.svelte'
</script>

<style>
:global(body) {
	min-height: 100vh;
	width: 100%;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	background: rgb(147, 183, 229);
	border: 5px rgb(169, 209, 223) solid;
}
</style>

<Dog/>


