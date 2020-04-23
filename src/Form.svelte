<script>
  import { createForm } from 'final-form'
  export let onSubmit, validate, initialValues

  const form = createForm({
    initialValues,
    onSubmit,
    validate,
  })
</script>

<slot {form} handleSubmit={form.submit}></slot>
