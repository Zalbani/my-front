<template>
  <nav :class="{active: isActive}">
    <div
      :class="{active: !isActive}"
      class="hamburger hamburger--emphatic"
      @click="myFilter"
    >
      <div class="hamburger-box">
        <div class="hamburger-inner" />
      </div>
    </div>
    <ul>
      <li>
        <nuxt-link to="/">
          <span class="icon-dev-dot-to" /> Home
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/style-guide">
          <span class="icon-google" /> Style guide
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/">
          <span class="icon-docker" /> -
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="/">
          <span class="icon-github" /> -
        </nuxt-link>
      </li>
      <hr>
      <p>Documentation</p>
      <li>
        <a href="">
          <span class="icon-github" /> -
        </a>
      </li>
      <li>
        <a href="">
          <span class="icon-github" /> -
        </a>
      </li>
      <li>
        <a href="">
          <span class="icon-github" /> -
        </a>
      </li>
    </ul>
  </nav>
</template>
<style lang="sass" scoped>
$topDivHeight: 0px
$hamburgerBoxWidth: 20px
$hamburgerBoxHeight: 20px
$hamburgerBoxPadding: 20px
$hamburgerLineThickness: 2px
$hamburgerLineSpaceBetween: 6px
$hamburgerLineBorderRadius: 4px

$navAnimationDuration: 0.7s
$navAnimationTiming: ease-out

/* Burger MENU */

.hamburger
  z-index: 1
  padding: $hamburgerBoxPadding
  display: inline-block
  cursor: pointer
  transition-property: opacity, filter
  transition-duration: 0.15s
  transition-timing-function: linear
  font: inherit
  color: inherit
  text-transform: none
  background-color: transparent
  border: 0
  margin: 0
  overflow: visible
  position: absolute
  top: 10px
  right: 0
  //right: calc((( #{$hamburgerBoxPadding} * 2 ) + #{$hamburgerBoxWidth}) * -1)
  &:hover
    opacity: 0.7
  &.active
    &:hover
      opacity: 0.7
    .hamburger-inner, .hamburger-inner::before, hamburger-inner::after
      background-color: #000

.hamburger-box
  width: $hamburgerBoxWidth
  height: $hamburgerBoxHeight
  display: inline-block
  position: relative

.hamburger-inner
  display: block
  top: 50%
  margin-top: -2px
.hamburger-inner, .hamburger-inner::before, .hamburger-inner::after
  width: $hamburgerBoxWidth
  height: $hamburgerLineThickness
  background-color: #000
  border-radius: $hamburgerLineBorderRadius
  position: absolute
  transition-property: transform
  transition-duration: 0.15s
  transition-timing-function: ease
.hamburger-inner::before, .hamburger-inner::after
  content: ""
  display: block
.hamburger-inner::before
  top: calc(#{$hamburgerLineSpaceBetween} * -1)
.hamburger-inner::after
  bottom: calc(#{$hamburgerLineSpaceBetween} * -1)

/* Emphatic Animation */
.hamburger--emphatic
  overflow: hidden
  .hamburger-inner
    transition: background-color 0.125s 0.175s ease-in
    &::before
      left: 0
      transition: transform 0.125s cubic-bezier(0.6, 0.04, 0.98, 0.335), top 0.05s 0.125s linear, left 0.125s 0.175s ease-in
    &::after
      top: $hamburgerLineSpaceBetween
      right: 0
      transition: transform 0.125s cubic-bezier(0.6, 0.04, 0.98, 0.335), top 0.05s 0.125s linear, right 0.125s 0.175s ease-in
  &.active
    .hamburger-inner
      transition-delay: 0s
      transition-timing-function: ease-out
      background-color: transparent !important
      &::before
        left: calc((#{$hamburgerBoxWidth} *2) * -1)
        top: calc((#{$hamburgerBoxWidth} *2) * -1)
        transform: translate3d(calc(#{$hamburgerBoxWidth} *2), calc(#{$hamburgerBoxWidth} *2), 0) rotate(45deg)
        transition: left 0.125s ease-out, top 0.05s 0.125s linear, transform 0.125s 0.175s cubic-bezier(0.075, 0.82, 0.165, 1)
      &::after
        right: calc((#{$hamburgerBoxWidth} *2) * -1)
        top: calc((#{$hamburgerBoxWidth} *2) * -1)
        transform: translate3d(calc((#{$hamburgerBoxWidth} *2) * -1), calc(#{$hamburgerBoxWidth} *2) , 0) rotate(-45deg)
        transition: right 0.125s ease-out, top 0.05s 0.125s linear, transform 0.125s 0.175s cubic-bezier(0.075, 0.82, 0.165, 1)

nav
  height: 100vh
  width: 200px
  position: fixed
  transition-duration: $navAnimationDuration
  transition-timing-function: $navAnimationTiming
  background-color: white
  box-shadow: 0 0 2rem 0 rgba(136,152,170,.15)
  border-color: rgba(0,0,0,.05)
  overflow: hidden
  z-index: 1
  &.active
    width: 60px
    ul li, ul li.selected, ul p
      color: white
  ul
    display: flex
    align-items: center
    margin: 10px
    height: calc(100vh - #{$topDivHeight})
    flex-direction: column
    justify-content: center
    padding: 0
    li
      display: flex
      width: 100%
      margin: 5px 0
      color: black
      position: relative
      background-color: white
      border-radius: 8px
      transition-duration: 0.5s
      transition-timing-function: ease
      font-size: .9375rem
      white-space: nowrap
      &:hover
        background-color: #F0F0F5
      a
        text-decoration: none
        color: inherit
        display: inherit
        width: 100%
        padding: 10px
        position: relative
        &:before
          content: ''
          position: absolute
          width: 0
          left: -10px
          top: 0
          border-radius: 1px
          height: 37px
          background-color: white
          transition-duration: 0.4s
          transition-timing-function: ease
        &.exact-active-link:before
          background-color: red
          width: 2px
      span
        color: black
        padding: 1px 20px 0 2px
        font-size: .9375rem
    hr
      border: none
      width: calc(100% - 28px)
      height: 1px
      background-color: rgba(0,0,0,0.1)
      margin: 10px 15px
    p
      color: #8898aa
      text-align: left
      text-transform: capitalize
      width: 100%
      padding-left: 14px
      transition-duration: 0.5s
      transition-timing-function: ease
      &::first-letter
        color: #8898aa
</style>
<script>
export default {
  data () {
    return {
      isActive: false,
      test: true
    }
  },
  methods: {
    myFilter () {
      this.isActive = !this.isActive
    }
  }
}
</script>
