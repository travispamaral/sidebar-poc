<template>
  <nav :class="{ closed: isCollapsed }">
    <slot name="topNavAction"></slot>
    <slot name="topNavTitle"></slot>
    <slot name="NavMenu"></slot>
    <slot name="NavToggle"></slot>
  </nav>
</template>

<script>
  export default {
    name: 'KNav',
    props: {
      isCollapsed: {
        type: Boolean,
        required: true
      }
    }
  }
</script>

<style lang='scss' scoped>
nav {
  display: flex;
	flex-direction: column;
	width: 240px;
	min-height: 100vh;
	overflow-x: hidden;
	overflow-y: auto;
	border-right: 1px solid #E6E7E8;
	background: #f9f9f9;
	transition: all .175s ease-in-out;
	&.closed {
		width: 63px;
	}
}
</style>
