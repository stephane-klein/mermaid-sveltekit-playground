<script>
    import { browser } from "$app/environment";
    import mermaid from "mermaid";

    let diagram = `\
flowchart LR
    id1[Node1]
    id2[Node2]
    id3[Node3]
    id4[Node 4 with <a href="https://github.com/stephane-klein/mermaid-sveltekit-playground">link</a>]
    id5[Node5]
    id1 --> id2
    id1 --> id3
    id2 --> id4 --> id5
    `;

    let container;

    async function renderDiagram() {
        if (browser) {
            const {svg} = await mermaid.render('mermaid', diagram)
            container.innerHTML=svg;
        }
    }

    $: diagram && renderDiagram()
</script>

<main>
    <pre
        contenteditable="true"
        bind:innerHTML={diagram}
    ></pre>
    <span bind:this={container}>
</main>
