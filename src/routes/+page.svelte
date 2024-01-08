<script>
import Cards from "../lib/components/Cards.svelte";
import Button from "../lib/components/Button.svelte";
import Title from "../lib/components/Title.svelte";

export let data;

</script>

<Cards {data}/>
<Title />
<Button />