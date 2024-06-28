<script>
    import TextInput from '$lib/TextInput.svelte';
    import Button from '$lib/Button.svelte';
</script>


<div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
    <form class="space-y-6" action="#" method="POST">
        <TextInput label="E-Mail" name="email" type="email" autocomplete="email" required/>
        <TextInput label="Password" name="password" type="password" autocomplete="current-password" required/>

        <Button type="submit" loading={false} class="flex w-full justify-center rounded-md bg-primary px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-primary focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-primary">
            Login
        </Button>
    </form>
</div>

