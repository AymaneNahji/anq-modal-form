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
  <div>
    <q-btn 
      label="Open Form" 
      color="primary" 
      @click="modalRef?.show()" 
    />
    
    <AnqModalForm
      ref="modalRef"
      title="Form Title"
      @submit="onSubmit"
      @hide="onModalHide"
    >
      <template #content>
        <div class="q-pa-md">
          <q-form @submit="onSubmit" class="q-gutter-md">
            <q-input
              v-model="formData.field1"
              label="Field 1"
              :rules="[val => !!val || 'Field is required']"
              outlined
            />
            <!-- Add more form fields as needed -->
          </q-form>
        </div>
      </template>
    </AnqModalForm>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';
import { AnqModalForm } from 'anq-modal-form';

const modalRef = ref<InstanceType<typeof AnqModalForm> | null>(null);

const formData = reactive({
  field1: ''
});

const onSubmit = () => {
  console.log('Form submitted:', formData);
  modalRef.value?.hide();
};

const onModalHide = () => {
  console.log('Modal hidden');
};
</script>
```

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| isLoading | Boolean | false | Shows loading state on the submit button |
| formIsLoading | Boolean | false | Shows loading state on the form |
| okLabel | String | 'Ok' | Label for the submit button |
| cancelLabel | String | 'Cancel' | Label for the cancel button |
| title | String | 'Title' | Modal title |
| btnsColor | QBtnProps['color'] | 'primary' | Color for the buttons |
| modalCardProps | { class?: string; style?: string } & QCard['$props'] | undefined | Additional props for the q-card component |

## Events

| Event | Parameters | Description |
|-------|------------|-------------|
| submit | () | Emitted when form is submitted |
| hide | () | Emitted when modal is hidden |

## Slots

| Slot | Props | Description |
|------|-------|-------------|
| content | - | Main content of the modal |
| close-icon-btn | color, disable | Custom close button |
| cancel-btn | color, disable, label | Custom cancel button |
| ok-btn | color, label, disable, loading | Custom submit button |

## Examples

### Basic Form with Validation
```vue
<template>
  <AnqModalForm
    ref="modalRef"
    title="User Registration"
    @submit="onSubmit"
  >
    <template #content>
      <div class="q-pa-md">
        <q-form @submit="onSubmit" class="q-gutter-md">
          <q-input
            v-model="formData.email"
            label="Email"
            type="email"
            :rules="[
              val => !!val || 'Email is required',
              val => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(val) || 'Invalid email format'
            ]"
            outlined
          />
        </q-form>
      </div>
    </template>
  </AnqModalForm>
</template>
```

### Form with Custom Buttons
```vue
<template>
  <AnqModalForm
    ref="modalRef"
    title="Custom Form"
    @submit="onSubmit"
  >
    <template #ok-btn="{ color, label, disable, loading }">
      <q-btn
        :color="color"
        :label="label"
        :disable="disable"
        :loading="loading"
        icon="check"
      />
    </template>
  </AnqModalForm>
</template>
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