<script>
  let { tasks, toggleDone, removeTask } = $props();
</script>

<section>
  {#each tasks as task, index}
    <article class="task">
      <label
        ><input
          onchange={() => toggleDone(task)}
          checked={task.done}
          type="checkbox"
        />
        <span class:done={task.done}>{task.title}</span></label
      ><button onclick={() => removeTask(index)} class="outline">X</button>
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
