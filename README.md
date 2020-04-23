# 🏁 svelte-final-form

## Usage

```html
<script>
  import { Form, Field } from 'svelte-final-form'
</script>

<Form let:form let:handleSubmit {initialValues} {onSubmit} {validate}>
  <form on:submit|preventDefault|stopPropagation={handleSubmit}>
    <Field let:input let:meta name="name" {form}>
      <input
        type="tel"
        placeholder="Phone number"
        name={input.name}
        value={input.value}
        on:input={input.onChange}
        on:focus={input.onFocus}
        on:blur={input.onBlur}
      />
      {#if meta.touched && meta.error}
        <div>{meta.error}</div>
      {/if}
    </Field>
  </form>
</Form>

```

## TODO

* [ ] `FieldProps`
* [ ] Perfomance checks
* [ ] `component` prop
* [ ] Actions
* [ ] More docs
* [ ] CodeSandbox example
* [ ] SSR?
* [ ] Store data in svelte stores?
