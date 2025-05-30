<script>
  import TasksForm from "./components/tasks-form.svelte";
  import TasksList from "./components/tasks-list.svelte";

  let tasks = $state([]);
  let totalDone = $derived(
    tasks.reduce((total, task) => total + Number(task.done), 0)
  );
  const addTask = (newTask) => {
    tasks.push({
      id: crypto.randomUUID(),
      title: newTask,
      done: false,
    });
  };

  const removeTask = (index) => {
    tasks.splice(index, 1);
  };

  const toggleDone = (task) => {
    task.done = !task.done;
  };
</script>

<main>
  <TasksForm {addTask} />
  {#if tasks.length}
    <p>{totalDone}/{tasks.length}</p>
  {:else}
    Add a task to get started
  {/if}
  <TasksList {tasks} {toggleDone} {removeTask} />
</main>

<style>
</style>
