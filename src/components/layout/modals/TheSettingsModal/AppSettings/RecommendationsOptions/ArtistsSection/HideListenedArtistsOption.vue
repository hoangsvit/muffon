<template>
  <div class="main-settings-option-container">
    <div class="main-settings-option">
      <BaseSettingsOptionHeader
        :text="optionText"
      />

      <BaseToggle
        store-key="recommendationArtists.isHideListenedArtists"
        :is-checked="isRecommendationArtistsHideListenedArtists"
      />
    </div>
  </div>
</template>

<script>
import {
  mapState
} from 'pinia'
import recommendationArtistsStore from '@/stores/recommendationArtists'
import BaseSettingsOptionHeader
  from '@/components/headers/settings/BaseSettingsOptionHeader.vue'
import BaseToggle from '@/components/toggles/BaseToggle.vue'

export default {
  name: 'HideListenedArtistsOption',
  components: {
    BaseSettingsOptionHeader,
    BaseToggle
  },
  computed: {
    ...mapState(
      recommendationArtistsStore,
      {
        isRecommendationArtistsHideListenedArtists:
          'isHideListenedArtists'
      }
    ),
    optionText () {
      return this.$t(
        'settings.options.app.recommendations.hideListenedArtists'
      )
    }
  }
}
</script>

<style lang="sass" scoped></style>
