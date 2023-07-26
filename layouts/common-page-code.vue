<!-- common-page-code.vue -->
<template>
    <div class="slidev-layout common-page-code">
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

  ::v-deep(h1::before) {
    content: "";
    width: 1.5rem;
    height: 3px;
    background-color: #ddd;
    position: relative;
    top: 2px;
    margin-right: 0.5rem;
  }

  ::v-deep(.slidev-code-wrapper) {
    margin-left: 1.2rem !important;
    margin-top: 1rem !important;
  }

  ::v-deep(.slidev-code) {
    font-size: 1rem !important;
    line-height: 1.5 !important;
  }
  </style>