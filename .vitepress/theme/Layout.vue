<script setup lang="ts">
import { useData, useRoute } from 'vitepress'

// https://vitepress.dev/reference/runtime-api#usedata
const { site, frontmatter } = useData()



const route = useRoute()

type NavItem = {
  href: string,
  name: string
}

const navItems: NavItem[] = [
  {
    href:'/',
    name: 'Home'
  },
  {
    href:'/markdown-examples.html',
    name: 'Markdown Examples'
  },
  {
    href: '/api-examples.html',
    name: 'API Examples'
  }
]

const isActiveRoute = (url: string) => {
  return route.path === url
}


</script>

<template>
    <ul v-for='({ href, name  }) of navItems'>
      <li>
        <a :href="href" :class="{'link--active': isActiveRoute(href)}">{{isActiveRoute(href)? 'active': 'inactive'}}: {{name}}</a>
      </li>
    </ul>
    <Content />
</template>

<style>
  .link--active {
    font-weight: bold;
  }
</style>
