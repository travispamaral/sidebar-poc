<template>
  <div
    class="workspace-toggle"
    @click="handleClick">
    <div v-if="isCollapsed">
     <svg class="icon-collapsed" xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="-4 -4 32 32">
        <path fill="#A3BBCC" fill-rule="evenodd" d="M2 0h6a2 2 0 0 1 2 2v6a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V2a2 2 0 0 1 2-2zm0 2v6h6V2H2zm0 10h6a2 2 0 0 1 2 2v6a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2v-6a2 2 0 0 1 2-2zm0 2v6h6v-6H2zM14 0h6a2 2 0 0 1 2 2v6a2 2 0 0 1-2 2h-6a2 2 0 0 1-2-2V2a2 2 0 0 1 2-2zm0 2v6h6V2h-6zm1 10l5 5-5 5V12z"/>
      </svg>
    </div>
    <div v-else>
      <svg class="icon" xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 16 16">
        <path fill="#A3BBCC" fill-rule="evenodd" d="M1 0h5c.55228 0 1 .44772 1 1v5c0 .55228-.44772 1-1 1H1c-.55228 0-1-.44772-1-1V1c0-.55228.44772-1 1-1zm1 2v3h3V2H2zM1 9h5c.55228 0 1 .44772 1 1v5c0 .55228-.44772 1-1 1H1c-.55228 0-1-.44772-1-1v-5c0-.55228.44772-1 1-1zm1 2v3h3v-3H2zm8-11h5c.55228 0 1 .44772 1 1v5c0 .55228-.44772 1-1 1h-5c-.55228 0-1-.44772-1-1V1c0-.55228.44772-1 1-1zm1 2v3h3V2h-3zm-1 7h5c.55228 0 1 .44772 1 1v5c0 .55228-.44772 1-1 1h-5c-.55228 0-1-.44772-1-1v-5c0-.55228.44772-1 1-1zm1 2v3h3v-3h-3z"/>
      </svg>
    </div>
    <span>
      <slot name="toggle-text">Change Workspace</slot>
    </span>
  </div>
</template>

<script>
  export default {
    name: 'WorkspaceToggle',
    props: {
      isCollapsed: {
        type: Boolean,
        default: false
      },
      handleClick: {
        type: Function,
        default: () => {}
      }
    }
  }
</script>

<style lang='scss' scoped>
  .workspace-toggle {
    .icon {
      margin-right: 20px;
    }
    span {
      white-space: nowrap;
    }

    nav.closed & {
      span {
        display: none;
      }
    }
  }
</style>
 