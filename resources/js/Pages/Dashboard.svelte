<script>
    import {Calendar} from "bits-ui";
    import { onMount } from 'svelte';
    import { today,startOfYear, getLocalTimeZone } from "@internationalized/date";

    let placeholder = startOfYear(today());
    console.log(placeholder);
    function cycleYear(number) {
        placeholder = placeholder.cycle("year", number);
    }
    export let months;

    onMount(() => {
        console.log(months);
    });
</script>
<Calendar.Root
    class="pt-10"
    let:months
    let:weekdays
    weekdayFormat="short"
    fixedWeeks={false}
    numberOfMonths={12}
    locale="de"
    bind:placeholder
>


    <Calendar.Header class="flex items-center justify-between mb-10">
        <button on:click={() => cycleYear(-1)}>Prev Year</button>
        <Calendar.Heading class="text-[15px] font-medium"/>
        <button on:click={() => cycleYear(1)}>Next Year</button>
    </Calendar.Header>
    <div
        class="flex flex-wrap gap-5 justify-between sm:flex-row sm:space-y-0"
    >
        {#each months as month, i (i)}
            <div class="rounded-xl border border-dark-10 bg-background-alt p-2">
            <Calendar.Grid class="">
                <Calendar.GridHead>
                    <Calendar.GridRow class="mb-1 flex w-full justify-between">
                        {#each weekdays as day}
                            <Calendar.HeadCell
                                class="w-10 rounded-md text-xs !font-normal text-muted-foreground"
                            >
                                <div>{day.slice(0, 2)}</div>
                            </Calendar.HeadCell>
                        {/each}
                    </Calendar.GridRow>
                </Calendar.GridHead>
                <Calendar.GridBody>
                    {#each month.weeks as weekDates}
                        <Calendar.GridRow class="flex w-full">
                            {#each weekDates as date}
                                <Calendar.Cell
                                    {date}
                                    class="relative size-10 !p-0 text-center text-sm"
                                >
                                    <Calendar.Day
                                        {date}
                                        month={month.value}
                                        class="group relative inline-flex size-10 items-center justify-center whitespace-nowrap rounded-9px border border-transparent bg-transparent p-0 text-sm font-normal text-foreground hover:border-foreground data-[disabled]:pointer-events-none data-[outside-month]:pointer-events-none data-[selected]:bg-foreground data-[selected]:font-medium data-[disabled]:text-foreground/30 data-[selected]:text-background data-[unavailable]:text-muted-foreground data-[unavailable]:line-through"
                                    >
                                        <div
                                            class="absolute top-[5px] hidden size-1 rounded-full bg-foreground group-data-[today]:block group-data-[selected]:bg-background"
                                        />
                                        {date.day}
                                    </Calendar.Day>
                                </Calendar.Cell>
                            {/each}
                        </Calendar.GridRow>
                    {/each}
                </Calendar.GridBody>
            </Calendar.Grid>
            </div>
        {/each}
    </div>
</Calendar.Root>
<style>

</style>
