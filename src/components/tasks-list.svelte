<script>
  import { fade } from "svelte/transition";
  let { filteredTasks, toggleDone, removeTask } = $props();
</script>

<section>
  {#each filteredTasks as task}
    <article class="task" transition:fade>
      <label
        ><input
          onchange={() => toggleDone(task)}
          checked={task.done}
          type="checkbox"
        />
        <span class:done={task.done}>{task.title}</span></label
      ><button onclick={() => removeTask(task.id)} class="outline">X</button>
    </article>
  {/each}
</section>

<style>
  .task {
    display: flex;
    justify-content: space-between;
  }
  .done {
    text-decoration: line-through;
  }
</style>
