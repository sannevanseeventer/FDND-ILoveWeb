<script>
import Cards from "../lib/components/Cards.svelte";
import Button from "../lib/components/Button.svelte";
import Title from "../lib/components/Title.svelte";
import Start from "../lib/components/Start.svelte";

export let data;

</script>

<Start />
<Cards {data}/>
<Title />
<Button />