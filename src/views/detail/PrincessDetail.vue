<template>
  <v-container
    fluid
    class="pa-1"
  >
    <v-row>
      <v-col class="pr-1">
        <PrincessBanner
          :princess="princess"
        />
      </v-col>
    </v-row>
    
    <v-row>
      <v-col
        class="col-12 col-lg-8 pr-1"
      >
        <PrincessCard
          :princess="princess"
        />
      </v-col>
      <v-col
        class="col-12 col-lg-2 px-1"
      >
        <PrincessProfile
          :princess="princess"
        />
      </v-col>
      <v-col
        class="col-12 col-lg-2 px-1"
      >
        <PrincessStoryBonus
          :princess="princess"
        />
      </v-col>
    </v-row>
    <v-row>
      <v-col
        class="pr-3 col-12 col-lg-auto"
      >
        <PrincessAP
          :princess="princess"
        />
      </v-col>
    </v-row>
    <v-row>
      <v-col
        class="col-12 col-lg-6"
      >
        <PrincessEquipment
          :princess="princess"
        />
      </v-col>
      <v-col
        class="col-12 col-lg-6 pr-1"
      >
        <PrincessStatus
          :princess="princess"
        />
      </v-col>
    </v-row>
    <v-row
      v-if="Object.prototype.hasOwnProperty.call(princess, 'unique_equipment')"
    >
      <v-col class="col-12 pr-1">
        <PrincessUniqueEquipment
          :princess="princess"
        />
      </v-col>
    </v-row>
    <v-row>
      <v-col class="col-12 pr-1">
        <PrincessSkill
          :princess="princess"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import PrincessEquipment from '@/components/princesses/PrincessEquipment'
import PrincessBanner from '@/components/princesses/PrincessBanner'
import PrincessProfile from '@/components/princesses/PrincessProfile'
import PrincessCard from '@/components/princesses/PrincessCard'
import PrincessAP from '@/components/princesses/PrincessAP'
import PrincessStatus from '@/components/princesses/PrincessStatus'
import PrincessUniqueEquipment from '@/components/princesses/PrincessUniqueEquipment'
import PrincessSkill from '@/components/princesses/PrincessSkill'
import PrincessStoryBonus from '@/components/princesses/PrincessStoryBonus'

export default {
  name: 'PrincessDetail',
  components: {
    PrincessEquipment,
    PrincessBanner,
    PrincessProfile,
    PrincessCard,
    PrincessAP,
    PrincessStatus,
    PrincessUniqueEquipment,
    PrincessSkill,
    PrincessStoryBonus
  },
  computed: {
    princess () {
      return this.$store.getters.getPrincessByName(this.name)
    },
    name () {
      return this.$route.params.princessName
    }
  },
  mounted () {
    console.log(this.princess)
  }
}
</script>
