<template>
  <PanelItem :field="field">
    <template #value>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div v-for="(permissions, group) in field.options" :key="group">
          <h1 class='font-normal mb-1 mt-2'>
            {{ __(group) }}
          </h1>
          <div class="grid gap-4">
            <div v-for="(permission, option) in permissions" :key="option">
              <Icon
                viewBox="0 0 24 24"
                width="24"
                height="24"
                :type="hasPermission(permission.option) ? 'check-circle' : 'x-circle'"
                :class="hasPermission(permission.option) ? 'text-green-500' : 'text-red-500'"
              />
              <span class="ml-1">{{ permission.label }}</span>
            </div>
          </div>
        </div>
      </div>
    </template>
  </PanelItem>
</template>

<script>
export default {
  props: [
    'resource',
    'resourceName',
    'resourceId',
    'field'
  ],
  methods: {
    hasPermission(value) {
      return this.field.value && this.field.value.includes(value)
    }
  },
}
</script>
