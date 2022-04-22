<script lang="ts">
    import { onMount } from "svelte";
    import { highlight, setCustomPattern } from "./prism";

    export let lang: string | undefined = undefined,
        code: string | undefined = "",
        match: Record<string, unknown> | undefined = undefined;

    let container: HTMLElement | undefined = undefined;
    $: $$props.string && update();

    async function addCSS() {
        const style = document.createElement("style"),
            content = document.createTextNode(`${await import("./code.css")}`);

        style.setAttribute("id", "highlighter-css");

        style.appendChild(content);
        document.appendChild(style);
    }
    function update() {
        match !== undefined && setCustomPattern(match);
        lang && highlight(container, false, undefined);
        if (!document.getElementById("highliter-css")) addCSS();
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
