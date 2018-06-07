<template>
  <div id="app">
    <div class="container">
      <KNav :isCollapsed="isCollapsed">
        <WorkspaceToggle
          slot="topNavAction"
          :isCollapsed="isCollapsed"/>
        <WorkspaceTitle
          slot="topNavTitle"
          title="Mac OS" />
        <div class="menu-container" slot="NavMenu">
          <SidebarMenu
            v-for="menu in menuList"
            :key="menu.id"
            :menu="menu" />
        </div>
        <CollapseToggle 
          slot="NavToggle"
          :handleToggleCollapse="handleToggleCollapse"/>
      </KNav>
    </div>
  </div>
</template>

<script>
import KNav from '@/components/KNav'
import WorkspaceToggle from '@/components/WorkspaceToggle'
import WorkspaceTitle from '@/components/WorkspaceTitle'
import SidebarMenu from '@/components/SidebarMenu'
import CollapseToggle from '@/components/CollapseToggle'

import menu from '@/menu'

export default {
  name: 'app',
  components: {
    KNav,
    WorkspaceToggle,
    WorkspaceTitle,
    SidebarMenu,
    CollapseToggle
  },

  data () {
    return {
      isCollapsed: true
    }
  },

  computed: {
    menuList () {
      return menu.sections
    }
  },

  methods: {
    handleToggleCollapse () {
      this.isCollapsed = !this.isCollapsed
    }
  }
}
</script>

<style lang='scss'>
/* Global Variables */
$blue: #003459;
$blue-light: #E6F2FA;
$blue-lightest: #1270B2;
$black45: rgba(0,0,0,.45);
$black70: rgba(0,0,0,.7);
$black85: rgba(0,0,0,.85);
$gry-bg: #FAFBFC;
$gry-bg2: #F5F6F7;
$gry-drk: #EBEFF2;
$border-gry: #E0E1E2;

/* Set Body Variables */
:root {
  --blue: #003459;
  --blue-light: #E6F2FA;
  --blue-lightest: #1270B2;
  --black45: rgba(0,0,0,.45);
  --black70: rgba(0,0,0,.7);
  --black85: rgba(0,0,0,.85);
  --gry-bg: #FAFBFC;
  --gry-bg2: #F5F6F7;
  --gry-drk: #EBEFF2;
  --border-gry: #E0E1E2;
}

body {
  margin: 0;
}

#app {
  font-family: 'Roboto';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container {
	display: flex;
}

.gry-bounding {
	display: flex;
	align-items: center;
	padding: 10px 20px;
	color: $black45;
	font-size: 14px;
	background-color: $gry-bg2;
	box-shadow: 0 1px 0 0 $border-gry;
	cursor: pointer;
	transition: all .2s ease;
	&:hover {
		background: darken($gry-bg2, 2%);
  }

  nav.closed & {
    box-shadow: none;
    background: none;
  }
}

.workspace-toggle,
.sidebar-toggle {
  @extend .gry-bounding;
}

</style>
