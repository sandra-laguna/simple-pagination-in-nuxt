<template>
  <div class="relative w-full h-full">

    <app-main>
      <transition mode="out-in">
        <nuxt :key="$route.fullPath" />
      </transition>
    </app-main>

  </div>
</template>
