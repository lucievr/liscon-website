<template>
  <div class="events-list">
    <h2 class="title">{{ stage }}</h2>
    <div
      v-for="event in events"
      :key="event.fullSpeaker + event.title"
      class="row"
      :class="{ current: event.current }"
    >
      <div class="col">
        <p>{{ event.startTime }} - {{ event.endTime }}</p>
        <a
          class="link-calendar"
          :href="generateGoogleCalendarUrl(event)"
          target="_blank"
          >Add to calendar</a
        >
      </div>
      <p class="col">{{ event.fullSpeaker }}</p>
      <p class="col">{{ event.title }}</p>
      <div v-if="event.miniSummit" class="col categories">
        <p class="label" :class="{ current: event.current }">
          {{ event.miniSummit }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { generateGoogleCalendarUrl } from '../utils'

export default {
  props: {
    events: {
      type: Array,
      default: () => [],
    },
    stage: {
      type: String,
      default: '',
    },
  },
  methods: {
    generateGoogleCalendarUrl,
  },
}
</script>

<style scoped lang="scss">
.events-list {
  .title {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 1rem;
  }

  .row {
    display: grid;
    grid-template-columns: 285px 1fr minmax(150px, 1fr) 180px;
    padding: 24px;
    font-size: 18px;
    grid-column-gap: 34px;
    align-items: center;
    justify-items: baseline;
    border-bottom: 1px solid $grey;

    .col {
      display: flex;
      flex-wrap: wrap;
      flex-direction: column;

      .link-calendar {
        margin: 4px;
        font-size: 14px;
      }

      .label {
        border: 1px solid $black;
        width: max-content;
        padding: 4px 8px;
      }

      &.categories {
        justify-content: flex-end;
        width: 100%;
        .label {
          width: 100%;
          text-align: center;
          // font-size: 16px;
        }
      }

      .current {
        &.label {
          border: 1px solid $blue;
        }
      }
    }
  }
}

@media (max-width: 930px) {
  .events-list {
    .row {
      display: flex;
      flex-direction: column;

      .col {
        text-align: center;
        margin: 8px;

        &.categories {
          justify-content: center;
          margin-right: 0;
          margin-left: 0;
          width: initial;
          .label {
            width: initial;
          }
        }
      }
    }
  }
}
</style>
