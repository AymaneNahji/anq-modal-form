# ANQ Modal Form

A powerful, customizable modal form component for Quasar Framework and Vue 3 applications. This component provides a seamless way to handle forms within modals, featuring dynamic form generation, validation, and smooth animations.

## Features

- 🎯 Dynamic form generation
- ✅ Built-in form validation
- 🎨 Seamless Quasar UI integration
- 📱 Responsive design
- ⚡ Vue 3 Composition API support
- 🔒 TypeScript support
- 🎭 Customizable animations
- 🎨 Theme support
- 🔄 Form state management
- 📦 Easy to integrate

## Installation

```bash
# Using npm
npm install anq-modal-form

# Using yarn
yarn add anq-modal-form

# Using pnpm
pnpm add anq-modal-form
```

## Quick Start

```vue
<template>
  <anq-modal-form
    v-model="isOpen"
    :form-schema="formSchema"
    @submit="handleSubmit"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { AnqModalForm } from 'anq-modal-form'

const isOpen = ref(false)

const formSchema = {
  fields: [
    {
      name: 'username',
      label: 'Username',
      type: 'text',
      required: true
    },
    {
      name: 'email',
      label: 'Email',
      type: 'email',
      required: true
    }
  ]
}

const handleSubmit = (formData) => {
  console.log('Form submitted:', formData)
}
</script>
```

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| modelValue | Boolean | false | Controls modal visibility |
| formSchema | Object | {} | Form configuration object |
| title | String | 'Form' | Modal title |
| width | String | '500px' | Modal width |
| persistent | Boolean | false | Prevents closing on outside click |
| noEscDismiss | Boolean | false | Prevents closing on ESC key |
| noBackdropDismiss | Boolean | false | Prevents closing on backdrop click |

## Events

| Event | Parameters | Description |
|-------|------------|-------------|
| submit | (formData: Object) | Emitted when form is submitted |
| cancel | () | Emitted when form is cancelled |
| update:modelValue | (value: Boolean) | Emitted when modal visibility changes |

## Form Schema

The form schema is an object that defines the structure and behavior of your form:

```typescript
interface FormSchema {
  fields: Array<{
    name: string
    label: string
    type: string
    required?: boolean
    validation?: Object
    options?: Array<{ label: string, value: any }>
    // ... other field properties
  }>
  // ... other form properties
}
```

## Examples

### Basic Form
```vue
<template>
  <anq-modal-form
    v-model="isOpen"
    :form-schema="basicForm"
    @submit="handleSubmit"
  />
</template>

<script setup>
const basicForm = {
  fields: [
    {
      name: 'name',
      label: 'Name',
      type: 'text',
      required: true
    }
  ]
}
</script>
```

### Form with Validation
```vue
<template>
  <anq-modal-form
    v-model="isOpen"
    :form-schema="validatedForm"
    @submit="handleSubmit"
  />
</template>

<script setup>
const validatedForm = {
  fields: [
    {
      name: 'email',
      label: 'Email',
      type: 'email',
      required: true,
      validation: {
        pattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
        message: 'Please enter a valid email'
      }
    }
  ]
}
</script>
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

- **Aymane Nahji** - [GitHub](https://github.com/AymaneNahji)

## Support

If you find this project helpful, please give it a ⭐️ on GitHub! 