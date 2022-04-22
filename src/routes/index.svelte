<script lang="ts">
    import Code from "$lib/Code.svelte";
    import DemoBlock from "../components/DemoBlock.svelte";
</script>

<h1>Demo</h1>
<DemoBlock title="custom">
    <Code>
        <span>npm install <span class="token important">sadforms</span> </span>
    </Code>
</DemoBlock>
<DemoBlock title="Svelte">
    <Code
        lang="svelte"
        code={`  
        \<script lang\=\"ts\"\>
            import Form from \"sadforms\"\;
            const data = {
                uid: "8310f3b8-f4ba-484e-a3fd-ea1eb3fc8fba",
                title: "Sample Form v2",
                fields: {
                    "8310f3b8-f4ba-484e-a3fd-ea1eb3fc8fba": {
                        "name": "First Name",
                        "uid": "8310f3b8-f4ba-484e-a3fd-ea1eb3fc8fba",
                        "type": "text",
                        "required": true,
                        "spellcheck": false,
                        "autocomplete": "name"
                    },
                    "a0b21c64-e6c1-476e-89dc-4ac7a5778720": {
                        "name": "Last Name",
                        "uid": "a0b21c64-e6c1-476e-89dc-4ac7a5778720",
                        "type": "text",
                        "spellcheck": false,
                        "autocomplete": "family-name"
                    },
                }
            }
        \<\/script\>
        <Form {...data} />
            `}
    />
</DemoBlock>
<DemoBlock title="TS">
    <Code
        lang="typescript"
        code={`
        function afterFormLoad(refresh: function): void {
            // your code goes here
        }

        function refresh(clean: boolean): void {
            // if clean === "true" will reset the form after form load
            // otherwise form will reload without resetting the form 

            // *note: if refresh is called, 
            // ensure there is a breaking condition
            // otherwise the form will be trapped in a loop
        }
    `}
    />
</DemoBlock>
<DemoBlock title="JS">
    <Code
        lang="javascript"
        code={`
        typeof value === "string"
        
        textarea: {
            uid: "textarea",        // (required) unique identifier
            name: "textarea",       // (required) human-readable title
            type: "textarea",       // (required) input field type
            tooltip:                // description on how to use field
            "any character, number, and line breaks. Also preserves spaces!",
            onInput: undefined,     // custom function runs whenever the field changes
            hide: {                 // hide certain features from the user
            label: false            // hide field label
            },
            placeholder:            // really short description on how to use field
            "most versitile field, can accept...",
            defaultValue: undefined,// pre-filled field that the user can change
            disabled: false,        // prevent user from accessing field
            required: false,        // check if field is empty
            redact: false,          // hide data when field is inactive
            dontSave: true,         // do not save data to localStorage
            validity: undefined,    // custom function checks the input value
            spellcheck: false,      // toggle browser spellcheck
            autocomplete: "off",    // instruct browser to autofill if available
        },
    `}
    />
</DemoBlock>
<DemoBlock title="HTML">
    <Code
        lang="html"
        code={`
        <html>
            <body>
                <div class="modal-open">activate modal</div>
                <div role="dialog">
                    <button class="modal-close">x</button>
                    <a href="https://www.instagram.com/byjackli">ok</a>
                </div>
                <div class="modal-backdrop"/>
            </body>
        </html>
    `}
    />
</DemoBlock>
<DemoBlock title="CSS">
    <Code
        lang="css"
        code={`
        /*  FORM  */
        .sf { }                     /* form container */
        .sf h2 { }                  /* form title */
        .sf p { }                   /* form description */
        .sf form { }                /* form element */
        .sf .trailingButtons { }    /* form buttons (reset, submit) */


        /*  FIELD & GROUP CONTAINERS  */
        .sf .form-block { }         /* field container */
        .sf .form-group { }         /* group container */


        /*  FIELD  */
        .sf .field { }              /* FIELD  */
        .sf .disabled .field { }    /* FIELD: disabled */
        .sf .items .field { }       /* FIELD: within a group  */


        /*  FIELD - label  */
        .sf label, .sf legend { }
        .sf label *, .sf legend * { }


        /*  FIELD:placeholder  */
        .sf input::placeholder, .sf textarea::placeholder,
        .sf .dropdown-container .option-empty:not(.redact) { }


        /*  FIELD - switch  */
        .sf .switch-container { }                                                   /* switch: container */
        .sf .switch-container span { }                                              /* switch: on & off icon */
        .sf .switch[aria-checked="false"] .switch-container span:first-of-type { }  /* switch: off icon - off state */
        .sf .switch[aria-checked="true"] .switch-container span:last-of-type { }    /* switch: on icon - on state */
        .sf .switch .switch-state { }                                               /* switch: background & off state */
        .sf .switch[aria-checked="true"] .switch-state { }                          /* switch: background - on state */


        /*  FIELD - dropdown  */
        .sf .dropdown-container { }                     /* dropdown: container */
        .sf .dropdown-container.active { }              /* dropdown: container - active */
        .sf .dropdown > span:first-of-type { }          /* dropdown: preview of selected */
        .sf .option-container { }                       /* dropdown - option: container */
        .sf .option-container > div, .sf .option { }    /* dropdown - option */
        .sf .option > span { }                          /* dropdown - option: label */
        .sf .option.active,
        .sf input.option.active ~ .edit-details * { }   /* dropdown - option - active */


        /*  FIELD - dropdown - EDITING FEATURE  */
        .sf .option.adding-container { }                /* dropdown - option: add container */
        .sf .option.adding-container .edit-details { }  /* dropdown - option: add container: edit details */
        .sf div.option input { }                        /* dropdown - option: add */
        .sf div.option input::placeholder { }           /* dropdown - option: add: placeholder */
        .sf div.option input.active::placeholder { }    /* dropdown - option: add: placeholder - active */
        .sf .option-actions { }                         /* dropdown - option: add - actions */
        .sf .option-actions span { }                    /* dropdown - option: add - actions: icons */
        .sf .option-del { }                             /* dropdown - option: add - actions: delete */


        /*  FIELD - divider  */
        .sf .divider { }                            /* divider: container */
        .sf .divider span:first-of-type { }         /* divider: icon */
        .sf .divider span:last-of-type { }          /* divider: title */
        .sf .divider hr { }                         /* divider: line */


        /*  FIELD - feedback  */
        .sf .container-tooltip { }                  /* feedback: tooltip */

        .sf .container-validity { }                 /* feedback: validity */
        .sf .container-validity.active { }          /* feedback: validity - active */
        .sf .condition-true { }                     /* feedback: validity - condition true */
        .sf .condition-false { }                    /* feedback: validity - condition false */

        .sf .container-preview { }                  /* feedback: preview container */
        .sf .container-preview.active { }           /* feedback: preview - active */
        .sf .preview { }                            /* feedback: preview */

        .sf .container-preview.redact::after { }    /* feedback: redact preview */
        .sf .field.redact::after { }                /* feedback: redact checkbox */

        .sf .field.redact:hover::after, 
        .sf .field.redact:focus::after, 
        .sf .container-preview:hover::after,    
        .sf .container-preview:focus::after { } 


        .sf .form-block.warn .field { }             /* feedback: warn - field */
        .sf .form-group.warn .items { }             /* feedback: warn - group */
        .sf .warn label, .sf .warn legend,          
        .sf .warn label *, .sf .warn legend * { }   /* feedback: warn - labels */


        /*  FORM - hide aria  */
        .sf .for-aria { 
            max-width: 0;
            max-height: 0;
            margin: 0;
            padding: 0;
            position: fixed;
            top: 0;
            left: 0;
            overflow: hidden;
        }

`}
    />
</DemoBlock>
