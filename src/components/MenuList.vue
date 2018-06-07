<template>
  <ul class="menu-list">
    <li
      v-for="item in menuItems"
      :key="item.name"
      :class="{ 'menu-title' : item.title }">
      <a :href="item.link">{{ item.name }}</a>
    </li>
  </ul>
</template>

<script>
  export default {
    name: 'MenuList',
    props: {
      menuItems: {
        type: Array,
        required: true
      }
    }
  }
</script>

<style lang='scss' scoped>
.menu-list {
  display: block;
  list-style: none;
  padding: 0;
  margin: 0;
  width: 100%;
  white-space: nowrap;
  // Add margin if icon sibling
  .item-wrapper & {
    .icon ~ & {
      margin-left: 1rem;
    }
  }
  li {
    line-height: 36px;
    cursor: pointer;
    &.menu-title a {
      font-weight: 500;
      color: var(--blue);
    }
    a {
      display: block;
      text-decoration: none;
      color: var(--black70);
      transition: all 300ms ease;
    }
    &:not(.menu-title):hover a {
      color: #000;
    }
  }

  nav.closed & {
    display: none;
    li {
      padding: 0 1rem;
      transition: all .3s ease;
      &:not(.menu-title):hover {
        background: var(--blue-light);
        a {color: var(--blue-lightest);}
      }
    }
  }
}
</style>
