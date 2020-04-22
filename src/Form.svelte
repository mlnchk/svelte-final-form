<script>
  import { createForm } from 'final-form'
  export let onSubmit, validate, initialValues

  const form = createForm({
    initialValues,
    onSubmit,
    validate,
  })
</script>

<form {...$$restProps} on:submit|preventDefault={form.submit}>
  <slot {form}></slot>
</form>
