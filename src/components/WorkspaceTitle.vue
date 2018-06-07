<template>
  <div class="workspace-title">
    <div class="workspace-icon">{{ workspaceAbbreviation }}</div>
    <div class="workspace-name">{{ title }}</div>
  </div>
</template>

<script>
  export default {
    name: 'WorkspaceTitle',
    props: {
      title: {
        type: String,
        required: true
      }
    },

    computed: {
      workspaceAbbreviation () {
        // Get first character each word
        return this.title
          .split(' ')
          .slice(0, 2)
          .map(x => x[0])
          .join('')
      }
    },
  }
</script>

<style lang='scss' scoped>
  .workspace-title {
		display: flex;
		align-items: center;
		padding: 24px 0;
		margin: 0 1rem 1rem;
    border-bottom: 1px solid var(--border-gry);
    white-space: nowrap;
		.workspace-icon {
      position: relative;
      display: flex;
      flex-shrink: 0;
			align-items: center;
			justify-content: center;
			width: 32px;
      height: 32px;
			font-size: 14px;
			font-weight: 500;
			color: #fff;
			background-color: #3894F0;
      border-radius: 2px;
		}
		.workspace-name {
      margin-left: 12px;
			font-weight: 500;
			color: var(--black85);
      white-space: nowrap;
    }
    
    nav.closed & {
      .workspace-name {
        display: none;
        width: 0;
        margin: 0;
      }
    }
  }
  
  @keyframes fadeIn {
    0% {opacity: 0; width: 0}
    100% {opacity: 1; width: 100%;}
  }
  @keyframes fadeOut {
    0% {opacity: 1; width: 100%; }
    100% {opacity: 0; width: 0 }
  }
</style>
