
<script lang="ts">
  let value = '';
  let todos = ['test name', 'test description'];

  // Добавить элемент
  const onAddTodo = () => {
    todos = [...todos, value];
    value = '';
  };

  // Удалить элемент
  const onDeleteTodo = (idx) => {
    const delItem = todos[idx];
    todos = todos.filter((x) => x !== delItem);
  };
</script>


<h2>Todo list</h2>

<div class="flex mt-2 gap-2 items-center">
  <input bind:value class="rounded-md p-1" type="text" />
  <button on:click={onAddTodo} class="block px-2 py-1 text-sm"> Add </button>
</div>

<!-- Маппинг данных -->
<div class="flex mt-2 flex-col">
  {#each todos as item, i}
    <span class="flex justify-between border-zinc-700 border-solid border px-2 py-1 rounded-md items-center gap-2 mt-1">
      <div>
        title: <span class="text-blue-400"> {item}</span>
        id: <span class="text-blue-400">{i + 1}</span>
      </div>
      <button on:click={() => onDeleteTodo(i)} class="leading-none px-1 py-1 ml-2 rounded-md">del</button>
    </span>
  {/each}
</div>
