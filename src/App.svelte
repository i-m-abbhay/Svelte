<!-- <script>
  import TasksForm from "./components/tasks-form.svelte";
  import TasksList from "./components/tasks-list.svelte";

  let tasks = $state([]);
  let totalDone = $derived(
    tasks.reduce((total, task) => total + Number(task.done), 0)
  );
  let currentFilter = $state("all");

  const addTask = (newTask) => {
    tasks.push({
      id: crypto.randomUUID(),
      title: newTask,
      done: false,
    });
  };

  const removeTask = (id) => {
    const index = tasks.findIndex((task) => task.id === id);
    tasks.splice(index, 1);
  };

  const toggleDone = (task) => {
    task.done = !task.done;
  };

  let filteredTasks = $derived.by(() => {
    switch (currentFilter) {
      case "all": {
        return tasks;
      }
      case "done": {
        return tasks.filter((task) => task.done);
      }
      case "todo": {
        return tasks.filter((task) => !task.done);
      }
    }
    return tasks;
  });
</script>

{#snippet filterButton(filter)}
  <button
    class="secondary filterText"
    class:contrast={currentFilter == filter}
    onclick={() => (currentFilter = filter)}>{filter}</button
  >
{/snippet}

<main>
  <TasksForm {addTask} />
  {#if tasks.length}
    <p>{totalDone}/{tasks.length}</p>
    <div class="btn-container">
      {@render filterButton("all")}
      {@render filterButton("todo")}
      {@render filterButton("done")}
    </div>
  {:else}
    Add a task to get started
  {/if}

  <TasksList {filteredTasks} {toggleDone} {removeTask} />
</main>

<style>
  main {
    margin: 1rem auto;
    max-width: 800px;
  }

  .btn-container {
    display: flex;
    justify-content: end;
    margin-bottom: 1rem;
    gap: 0.5rem;
  }

  .filterText {
    text-transform: capitalize;
  }
</style> -->

<script>
  import Dog from "./components/dog.svelte";
  import { setContext } from "svelte";

  const someObject = { Hey: "Its me" };
  setContext("someKey", someObject);

  let nameOfDog = "Hira";

  let count = 0;
  const incrementCount = () => {
    count = count + 1;
  };
  $: console.log(count);
</script>

<Dog name={nameOfDog} />
{count} <button onclick={incrementCount}>Increase the count</button>
