<!-- common-page-has-image.vue -->
<template>
    <div class="slidev-layout common-page-has-image">
      <slot />
    </div>
  </template>
  
  <style scoped>
  .slidev-layout {
    padding: 1.4rem 2rem 2rem 0;
  }

  ::v-deep(h1) {
    font-size: 2.4rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    line-height: 1.3;
    padding-right: 5rem;
  }

  ::v-deep(h2) {
    font-size:  1.8rem;
    font-weight: 700;
    margin-top: 1.48rem;
    padding-left: 2.2rem;
  }

  ::v-deep(h1::before) {
    content: "";
    width: 1.5rem;
    height: 3px;
    background-color: #333;
    position: relative;
    top: 2px;
    margin-right: 0.5rem;
  }

  ::v-deep(p) {
    padding-left: 2.2rem;
    font-size: 2rem;
    margin-top: 2.5rem;
    font-weight: 700;
  }

  ::v-deep(p span) {
    color: #41B883;
  }

  ::v-deep(ul) {
    margin-top: 1.48rem;
    padding-left: 2.2rem;
    width: 74%;
  }

  ::v-deep(li) {
    font-size: 1.6rem;
    line-height: 1.7;
    text-indent: -1.7rem;
    margin-left: 1.7rem;
  }

  ::v-deep(li span) {
    color: #41B883;
    font-weight: 700;
  }

  ::v-deep(li::before) {
    content: "・";
  }

  ::v-deep(li ul) {
    margin: 0;
    width: auto;
    padding-left: 1rem;
  }

  ::v-deep(img) {
    position: absolute;
    bottom: 2rem;
    right: 2rem;
    width: 13rem;
    height: auto;
  }
  </style>