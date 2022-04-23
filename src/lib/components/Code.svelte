<script lang="ts">
    import { onMount } from "svelte";
    import { highlight, setCustomPattern, init } from "../static/prism";

    export let lang: string | undefined = undefined,
        code: string | undefined = "",
        match: Record<string, unknown> | undefined = undefined;

    let container: HTMLElement | undefined = undefined;
    $: $$props.string && update();

    function update() {
        init();
        match !== undefined && setCustomPattern(match);
        lang && highlight(container, false, undefined);
    }

    // component made possible by Prism.js

    // in future, build
    // 1. plain english regex builder, then
    // 2. code highlighter from scratch
    onMount(() => update());
</script>

<pre bind:this={container} class={`language-${lang}`}>
    <code class={`language-${lang}`}>
        {code}
        <slot />
    </code>
</pre>
