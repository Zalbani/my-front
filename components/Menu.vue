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
    <div class="random">
      <p>Title</p>
    </div>
    <ul>
      <li>hello</li>
      <li>hello</li>
      <li>hello</li>
    </ul>
  </nav>
</template>
<style lang="sass" scoped>
$topDivHeight: 120px
$hamburgerBoxWidth: 40px
$hamburgerBoxHeight: 24px
$hamburgerBoxPadding: 15px
$hamburgerLineThickness: 2px
$hamburgerLineSpaceBetween: 10px
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
  top: 0
  right: calc((( #{$hamburgerBoxPadding} * 2 ) + #{$hamburgerBoxWidth}) * -1)
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
  background-color: lightblue
  position: fixed
  transition-duration: $navAnimationDuration
  transition-timing-function: $navAnimationTiming
  &.active
    transform: translateX(-200px)
  .random
    width: 100%
    height: $topDivHeight
    position: absolute
    display: flex
    justify-content: center
    align-items: center
    background-color: lightcoral
    color: white
  ul
    display: flex
    align-items: center
    margin: 20px
    height: calc(100vh - #{$topDivHeight})
    flex-direction: column
    justify-content: center
    li
      display: flex
      width: 100%
      padding: 20px 0
      color: white
</style>
<script>
export default {
  data () {
    return {
      isActive: false
    }
  },

  methods: {
    myFilter () {
      this.isActive = !this.isActive
      // some code to filter users
    }
  }
}
</script>
