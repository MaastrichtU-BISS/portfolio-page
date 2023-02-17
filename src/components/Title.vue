<template>
  <h1></h1>
</template>

<style scoped lang="scss">
@import 'src/assets/typed';

h1 {
  @include typed("Hey jij", "Ja, jij!", "Druk op het scherm en ontdek BISS*<[100]>", (pause-typed: 4), (caret-width: 4px));
}
</style>