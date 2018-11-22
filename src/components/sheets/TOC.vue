<template>
  <div id="toc">
    <slot />
  </div>
</template>

<style lang="scss">
#toc {
  background: #333333;
  display: block;
  position: fixed;
  margin-left: -0.5in;

  a {
    color: white;
    display: block;
    padding: 0.1in;
    text-decoration: none;

    &:hover {
      text-decoration: underline;
    }
  }
}
</style>