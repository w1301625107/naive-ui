# Inline Form
```html
<n-form
  inline
  :label-width="80"
  :model="formValue"
  :rules="rules"
  ref="form"
>
  <n-form-item label="Name" path="user.name">
    <n-input v-model="formValue.user.name" placeholder="Input Name" />
  </n-form-item>
  <n-form-item label="Age" path="user.age">
    <n-input placeholder="Input Age" v-model="formValue.user.age"/>
  </n-form-item>
  <n-form-item label="Phone" path="phone">
    <n-input placeholder="Phone Number" v-model="formValue.phone"/>
  </n-form-item>
  <n-form-item v-model="formValue.phone">
    <n-button @click="handleValidateClick">Validate</n-button>
  </n-form-item>
</n-form>

<pre>
{{  JSON.stringify(formValue, 0, 2) }}
</pre>
```
```js
export default {
  data () {
    return {
      formValue: {
        user: {
          name: '',
          age: ''
        },
        phone: ''
      },
      rules: {
        user: {
          name: {
            required: true,
            message: 'Please input your name',
            trigger: 'blur'
          },
          age: {
            required: true,
            message: 'Please input your age',
            trigger: 'input'
          }
        },
        phone: {
          required: true,
          message: 'Please input your number',
          trigger: ['input']
        }
      }
    }
  },
  methods: {
    handleValidateClick (e) {
      e.preventDefault()
      this.$refs.form.validate()
    }
  }
}
```