<template>
  <div 
    class="sidebar-toggle" 
    @click="handleToggleCollapse">
    <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 16 16">
      <path fill="#A3BBCC" fill-rule="evenodd" d="M0 0h2v16H0V0zm16 7v2H9v3L4 8l5-4v3h7z"/>
    </svg>
    <span>
      <slot name="toggle-text">Collapse Sidebar</slot>
    </span>
  </div>
</template>

<script>
  export default {
    name: 'CollapseToggle',
    props: {
      isCollapsed: {
        type: Boolean,
        default: false
      },
      handleToggleCollapse: {
        type: Function,
        default: () => {}
      }
    }
  }
</script>

<style lang='scss' scoped>
  .sidebar-toggle {
    display: flex;
    align-items: center;
    margin-top: auto;
    cursor: pointer;
    svg {
      transition: all .2s ease;
    }
    span {
      width: 100%;
      margin-left: 1rem;
      white-space: nowrap;
    }

    nav.closed & {
      span { 
        display: none; 
      }
      svg {
        transform: rotate(180deg); 
      }
    }
  }
</style>
