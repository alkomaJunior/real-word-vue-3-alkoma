<template>
  <EventDetailsLayout :event="event"></EventDetailsLayout>
</template>

<script>
import EventDetailsLayout from '@/components/EventDetailsLayout'
import EventService from '@/services/EventService'

export default {
  name: 'EventDetails',
  components: {
    EventDetailsLayout,
  },
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data
      })
      .catch((error) => {
        console.log(error)
      })
  },
}
</script>

<style scoped></style>
