# Inline editing component for Svelte 3 [demo](https://svelte.dev/repl/5f9e842face0479fb0cdac814a2f7d23?version=3.18.0)

[![NPM version](https://img.shields.io/npm/v/svelte-inline-edit.svg?style=flat)](https://www.npmjs.com/package/svelte-inline-edit) [![NPM downloads](https://img.shields.io/npm/dm/svelte-inline-edit.svg?style=flat)](https://www.npmjs.com/package/svelte-inline-edit)

## Features

- Simple
- Cancelable
- Different positioning of controls
- `edit`, `save`, `cancel` events

## Install

```bash
npm i svelte-inline-edit --save-dev
```

```bash
yarn add svelte-inline-edit
```

CDN: [UNPKG](https://unpkg.com/svelte-inline-edit/) | [jsDelivr](https://cdn.jsdelivr.net/npm/svelte-inline-edit/) (available as `window.InlineEdit`)

## Usage

```html
<InlineEdit bind:value />

<script>
    import InlineEdit from './InlineEdit.svelte';

    let value;
</script>
```

### Using events

```html
<InlineEdit type="email" {value} on:save={save} on:cancel={cancel} on:edit={edit} />

<script>
    import InlineEdit from './InlineEdit.svelte';

    let value;

    function save({ detail: input }) {
        if (input.checkValidity()) {
            value = input.value;
        }
    }

    function edit() {
        console.log('Start editing');
    }

    function cancel() {
        console.log('Cancel editing');
    }
</script>
```

If you are **not** using using es6, instead of importing add 

```html
<script src="/path/to/svelte-inline-edit/index.js"></script>
```

just before closing body tag.

## API

## Props

| Name | Type | Description | Required | Default |
| --- | --- | --- | --- | --- |
| `value` | `String or Number` | Editable value | No | `empty string` |
| `options` | `Array` | A list of permissible or recommended options of value | No | `empty array` |
| `rows` | `Number` | Define number of rows for editable. | No | `1` |
| `position` | `String` | Position of controls: left, right, top-left, top-right, bottom-left, bottom-right | No | `right` |

## Slots

- `save` - element to be placed as save control
- `cancel` - element to be placed as cancel control

## Events

- `edit` - on start editing
- `save` - on save
- `cancel` - on cancel editing

You can use direct access to input element via `event.detail`.

## License

MIT &copy; [PaulMaly](https://github.com/PaulMaly)
