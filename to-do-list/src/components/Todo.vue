<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    toggleCheckbox(e) {
      this.$emit('toggle-checkbox', {
        id: this.todo.id,
        checked: e.target.checked
      })
    },
    clickDelete(e) {
      this.$emit('click-delete', this.todo.id) //함수와 인자
    },
    clickModify(e) {
      this.$emit('click-modify', this.todo.id) //함수와 인자
    }
  }
}
</script>

<template>
  <div class="form-check d-flex justify-content-between" :data-id="todo.id">
    <div>
      <input class="form-check-input" type="checkbox" value="" :id="'input' + todo.id" @change="toggleCheckbox">
      <label class="form-check-label" :for="`input${todo.id}`"
        :style="todo.checked ? 'text-decoration:line-through' : ''">
        {{ todo.text }}
      </label>
    </div>
    <div>
      <button type="button" class="btn btn-sm btn-light modify-btn" @click="clickModify">Modify</button>
      <button type="button" class="btn btn-sm btn-light" @click="clickDelete">delete</button>
    </div>
  </div>
</template>

<style>
.btn-sm {
  margin-left: 8px;
  font-size: 12px
}

input[type="checkbox"]:checked+label {
  color: silver;
}

.modify-btn {
  --bs-btn-bg: #eaf5ff;
  --bs-btn-border-color: #e8f3ff;
  --bs-btn-hover-bg: #d6e9fb;
  --bs-btn-hover-border-color: #bbddff;
  --bs-btn-active-bg: #c7e2fa;
  --bs-btn-active-border-color: #bbddff;

}
</style>