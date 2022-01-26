# Errors
## vue/require-v-for-key
Require v-bind:key with v-for directives

⚙️ This rule is included in all of "plugin:vue/vue3-essential", "plugin:vue/essential", "plugin:vue/vue3-strongly-recommended", "plugin:vue/strongly-recommended", "plugin:vue/vue3-recommended" and "plugin:vue/recommended".
# 📖 Rule Details
This rule reports the elements which have v-for and do not have v-bind:key with exception to custom components.
## Examples Good/Bad
```
<template>
  <!-- ✓ GOOD -->
  <div
    v-for="todo in todos"
    :key="todo.id"
  />
  <!-- ✗ BAD -->
  <div v-for="todo in todos"/>
</template>
```
