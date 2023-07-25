<!-- common-page.vue -->
<template>
  <div class="slidev-layout common-page">
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

::v-deep(h3) {
  font-size:  1.4rem;
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
  padding-left: 1rem;
}

::v-deep(table) {
  margin-top: 2rem;
  margin-left: 2.2rem;
  border: 1px solid #ccc;
  border-collapse: collapse;
  width: 96.5%;
}

::v-deep(table th) {
  border: 1px solid #ccc;
  background-color: rgb(203, 225, 225);
  padding: 0.4rem;
  width: 7rem;
}

::v-deep(table td) {
  border: 1px solid #ccc;
  padding: 0.4rem 0.7rem;
}

::v-deep(.support) {
  display: flex;
  gap: 0.8rem;
  margin-top: 0.8rem;
}

::v-deep(.support li) {
  margin: 0;
  background-color: #d73030;
  color: white;
  border-radius: 8px;
  flex: 1;
  text-align: center;
  font-size: 0.8rem;
  text-indent: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  line-height: 1.4;
  padding: 0.3rem;
}

::v-deep(.support li.support__supported) {
  background-color: #41B883;
}

::v-deep(.support li::before) {
  content: none;
}
</style>