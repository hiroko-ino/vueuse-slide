<!-- index-page.vue -->
<template>
    <div class="slidev-layout index-page">
      <slot />
    </div>
  </template>
  
  <style scoped>
  .slidev-layout {
    padding: 2rem 2rem 2rem 0;
  }

  ::v-deep(h1) {
    font-size: 2.8rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    line-height: 1;
  }

  ::v-deep(h1::before) {
    content: "";
    width: 1.5rem;
    height: 3px;
    background-color: #ddd;
    position: relative;
    top: 2px;
    margin-right: 0.5rem;
  }

  ::v-deep(ul) {
    margin-top: 1.48rem;
    padding-left: 2.2rem;
  }

  ::v-deep(li) {
    font-size: 1.7rem;
    line-height: 1.7;
    padding-left: 1rem;
  }

  ::v-deep(li:has(strong)) {
    background-color: #41B883;
    color: white;
  }

  ::v-deep(li > ul) {
    margin-top: 0;
    padding-left: 1rem;
  }

  ::v-deep(li > ul > li::before) {
    content: "・";
  }
  </style>