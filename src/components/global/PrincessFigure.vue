<template>
  <v-card
    :href="link"
  >
    <v-img
      :src="src"
      :alt="name"
      :style="style"
    />
    <v-row
      class="d-flex justify-center align-center"
      no-gutters
    >
      <v-col>
        <v-btn
          small
          block
          :color="this.princess.status.atk_type === 1 ? 'pink' : 'indigo'"
          class="pa-0 font-weight-light white--text"
          v-text="name"
        />
      </v-col>
      <slot name="add" />
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: 'PrincessFigure',
  props: {
    princess: {
      type: Object,
      required: true
    },
    zoomRatio: {
      type: String,
      default: '1'
    }
  },
  data () {
    return {
      origHeight: 180,
      origWidth: 180
    }
  },
  computed: {
    name () {
      return this.princess.status.unit_name
    },
    link () {
      return `/princess/detail/${this.name}`
    },
    src () {
      return `${this.$store.state.CDNBaseURL}/image/character_favicons/fav_push_notif_${this.princess.id}.png`
    },
    style () {
      return {
        height: `${this.origHeight * parseFloat(this.zoomRatio)}px`,
        width: `${this.origWidth * parseFloat(this.zoomRatio)}px`
      }
    }
  }
}
</script>
