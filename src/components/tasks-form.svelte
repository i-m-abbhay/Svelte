<script lang="js">
  let newTask = $state("");

  let { addTask } = $props();

  const formSubmitted = (e) => {
    e.preventDefault();
    if (newTask !== "") addTask(newTask);
    newTask = "";
  };
</script>

<form onsubmit={formSubmitted}>
  <label>
    Task
    <input type="newTask" bind:value={newTask} />
  </label>
  <div class="button-container"><button>Add</button></div>
</form>

<style>
  .button-container {
    display: flex;
    justify-content: end;
  }
  form {
    margin-bottom: 1rem;
  }
</style>
