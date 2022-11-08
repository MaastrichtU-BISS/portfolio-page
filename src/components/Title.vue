<template>
  <h1></h1>
</template>

<style scoped lang="scss">
@import 'src/assets/typed';

h1 {
  @include typed("Hey you", "Yeah, you!", "Come checkout BISS*<[100]>", (pause-typed: 4), (caret-width: 4px));
}
</style>