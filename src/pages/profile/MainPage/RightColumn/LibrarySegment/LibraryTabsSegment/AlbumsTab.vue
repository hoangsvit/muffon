<template>
  <BaseProfileLibraryTabContainer
    :profile-id="profileId"
    :scope="scope"
    :limit="limit"
    :is-active="isActive"
    @focus="handleFocus"
  >
    <template
      #default="slotProps"
    >
      <BaseAlbumsTableList
        :[scope]="slotProps[scope]"
        :items-in-row="itemsInRow"
        :profile-id="profileId"
        :is-with-library-option="!isSelf"
        :is-with-delete-option="isSelf"
        is-with-image
        is-with-artist-name
        is-with-source
        is-with-created
        is-with-library
        is-link-to-library
        is-with-page-option
        is-with-favorite-option
        is-with-bookmark-option
        is-with-listened-option
        is-with-share-option
        is-with-external-link-option
      />
    </template>
  </BaseProfileLibraryTabContainer>
</template>

<script>
import BaseProfileLibraryTabContainer
  from '@/components/containers/tabs/profile/library/BaseProfileLibraryTabContainer.vue'
import BaseAlbumsTableList
  from '@/components/lists/albums/BaseAlbumsTableList.vue'
import {
  isCurrentProfile
} from '@/helpers/utils'
import {
  albums as albumsLimits
} from '@/helpers/data/limits'

export default {
  name: 'AlbumsTab',
  components: {
    BaseProfileLibraryTabContainer,
    BaseAlbumsTableList
  },
  props: {
    profileId: {
      type: Number,
      required: true
    },
    isActive: Boolean
  },
  emits: [
    'focus'
  ],
  data () {
    return {
      scope: 'albums',
      limit:
        albumsLimits.table.extrasmall,
      itemsInRow:
        albumsLimits.table.extrasmall
    }
  },
  computed: {
    isSelf () {
      return isCurrentProfile(
        this.profileId
      )
    }
  },
  methods: {
    handleFocus () {
      this.$emit(
        'focus'
      )
    }
  }
}
</script>

<style lang="sass" scoped></style>
