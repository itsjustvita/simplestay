<script>
    export let onChange;
    export let label;
    export let name;
    export let className = '';
    export let errors = [];

    $: props = (({ onChange, label, name, className, errors, ...rest }) => rest)($$props);
</script>

<div class={className}>
    {#if label}
        <label class="block text-sm font-medium leading-6 text-gray-900 mb-2" for={name}>{label}</label>
    {/if}

    <input
        id={name}
        name={name}
        {...props}
        on:change={onChange}
        class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        class:error={errors && errors.length}
    />

    {#if errors && errors.length}
        <div class="form-error">{errors[0]}</div>
    {/if}
</div>
