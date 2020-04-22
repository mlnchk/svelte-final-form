<script>
  export let name, form

  let meta = {}
  let input = {}

  if (form) {
    form.registerField(
      name,
      (fieldState) => {
        const { blur, change, focus, value, ...fieldMeta } = fieldState

        meta = fieldMeta

        input = {
          name,
          onBlur: blur,
          onChange: change,
          onFocus: focus,
          value,
        }
      },
      {
        touched: true,
        value: true,
        error: true,
      },
    )
  }

  const register = (node, form) => form.registerField(
    name,
    (fieldState) => {
      const { blur, change, focus, value, ...fieldMeta } = fieldState
      node.addEventListener('blur', () => blur())
      node.addEventListener('input', (e) => {
        change(
          node.type === 'checkbox'
            ? event.target.checked
            : event.target.value
        )
      })
      node.addEventListener('focus', () => focus())
      if (node.type === 'checkbox') node.checked = value
      else node.value = value === undefined ? '' : value

      meta = fieldMeta

      input = {
        name,
        onBlur: blur,
        onChange: change,
        onFocus: focus,
        value,
      }
    },
    {
      touched: true,
      value: true,
      error: true,
    },
  )
</script>

<slot {register} {meta} {input}></slot>
