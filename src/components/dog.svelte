<script>
  import { username } from "../store/store";
  import { get } from "svelte/store";
  import { getContext } from "svelte";
  const someObject = getContext("someKey");
  export let name;

  import Button, { changeColor } from "./button.svelte";
</script>

<h1>
  The dog name is {name}! I am {get(username)}'s dog
  <Button />
  {someObject.Hey}
</h1>

<style>
  h1 {
    color: purple;
  }
</style>
