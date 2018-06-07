<template>
  <div class="menu-wrapper">
    <div class="icon">	
      <svg width="24" height="24" viewBox="0 0 24 24">
        <path fill="#A3BBCC" fill-rule="evenodd" d="M20 11V9l4 3-4 3v-2H0v-2h20zm-4 9v-2l4 3-4 3v-2h-5.3620499l-6.00000004-5H0v-2h5.36204994l5.99999996 5H16zm0-18V0l4 3-4 3V4h-4.6379501L5.36204994 9H0V7h4.63795006l6.00000004-5H16z"/>
      </svg>
    </div>
    <div class="item-wrapper">
      <MenuList :menuItems="menu.items" />
    </div>
  </div>
</template>

<script>
import MenuList from '@/components/MenuList'
export default {
  name: 'SidebarMenu',
  components: {
    MenuList
  },
  props: {
    menu: {
      type: Object,
      required: true
    }
  },

  methods: {
    handleMouseEnter (e) {
      console.log('entered', e.target, e.target.parentNode)
      if (e.target.parentNode.classList.contains('menu-list-wrapper')) {
        e.target.classList.add('active')
      }
    },
    handleMouseLeave (e) {
      if (e.target.parentNode.classList.contains('menu-list-wrapper')) {
        e.target.parentNode.classList.remove('active')
      }
    }
  }
}
</script>

<style lang='scss' scoped>
  .menu-wrapper {
		margin-bottom: 1.5rem;
    display: flex;
    .menu-container & {
      margin: 0 20px;
    }
		.icon {
			font-size: 32px;
			color: #DCDDDE;
			svg path {
				transition: all .2s ease;
			}
    }
    .item-wrapper {
      width: 0%;
    }

    nav.closed & {
      margin: 0;
      .icon {
        width: 100%;
        text-align: center;
        padding: 1rem;
        cursor: pointer;
      }
      &:hover {
        .item-wrapper {
          position: absolute;
          display: inline-block;
          left: 63px;
          width: auto;
          .icon {
            display: inline-block;
            background: var(--gry-drk);
          }
          .menu-list {
            display: block;
            width: 160px;
            padding: 1rem 0;
            margin-left: 1rem;
            border-radius: 4px;
            box-shadow: 0 2px 12px rgba(0,0,0,.08);
            border: 1px solid rgba(0,0,0,.12);
            background: white;
            z-index: 100;
          }
        }
      }
    }
  }
</style>
