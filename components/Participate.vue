<template>
  <div class="participate">
    <p class="title">{{ $t('participate.title') }}</p>
    <div class="buttons">
      <a target="_blank">
        <Button class="button" type="disable">{{
          $t('participate.tickets_sold_out')
        }}</Button></a
      >
      <a target="_blank"
        ><Button type="disable">{{
          $t('participate.apply_to_speak')
        }}</Button></a
      >
      <a target="_blank">
        <Button class="button" type="disable">{{
          $t('participate.sponsor')
        }}</Button></a
      >
    </div>
  </div>
</template>

<style lang="scss" scoped>
.participate {
  width: 100%;
  text-align: center;
  display: flex;
  flex-direction: column;
  min-height: 400px;
  align-items: center;
  justify-content: center;
  background-image: url('@/assets/building.svg');
  background-repeat: no-repeat;
  background-position: center;
  margin: 4rem 0;

  .title {
    font-size: 3.5rem;
    margin-bottom: 2rem;
    color: $blue;
    font-family: 'RousseauDeco', sans-serif;
  }

  .buttons {
    display: flex;

    .button {
      margin-right: 1rem;
    }
  }
}

@media (max-width: 680px) {
  .participate {
    .title {
      font-size: 10vw;
    }

    .buttons {
      flex-direction: column;

      .button {
        margin-right: 0;
        margin-bottom: 0.5rem;
      }
    }
  }
}
</style>
