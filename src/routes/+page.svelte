<script>
import Cards from "../lib/components/Cards.svelte";
import Button from "../lib/components/Button.svelte";
import Title from "../lib/components/Title.svelte";
import Start from "../lib/components/Start.svelte";
import Sketches from "../lib/components/Sketches.svelte";

export let data;

</script>

<Sketches />
<Title />
<Start />
<Cards {data}/>
<Button />