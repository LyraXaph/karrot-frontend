<template>
  <div>
    <q-card class="no-shadow grey-border">
      <q-card-title>{{ $t('USERDATA.PROFILE_TITLE') }}</q-card-title>
      <q-card-main>
        <ChangePhoto
          :value="user"
          :status="profileEditStatus"
          @save="saveUser"
        />
        <q-card-separator />
        <ProfileEdit
          :value="user"
          :status="profileEditStatus"
          @save="saveUser"
        />
      </q-card-main>
    </q-card>
    <q-card class="no-shadow grey-border">
      <q-card-title>{{ $t('USERDATA.EMAIL') }}</q-card-title>
      <q-card-main>
        <ChangeEmail
          :user="user"
          :status="changeEmailStatus"
          @save="changeEmail"
        />
      </q-card-main>
    </q-card>
    <q-card class="no-shadow grey-border">
      <q-card-title>{{ $t('USERDATA.PASSWORD') }}</q-card-title>
      <q-card-main>
        <ChangePassword
          :status="changePasswordStatus"
          @save="changePassword"
        />
      </q-card-main>
    </q-card>
  </div>
</template>

<script>
import { QCard, QCardTitle, QCardMain, QCardSeparator } from 'quasar'
import ProfileEdit from '@/components/Settings/ProfileEdit'
import ChangePassword from '@/components/Settings/ChangePassword'
import ChangeEmail from '@/components/Settings/ChangeEmail'
import ChangePhoto from '@/components/Settings/ChangePhoto'

import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'Settings',
  components: { QCard, QCardTitle, QCardMain, QCardSeparator, ProfileEdit, ChangePassword, ChangeEmail, ChangePhoto },
  computed: {
    ...mapGetters({
      user: 'auth/user',
      profileEditStatus: 'auth/saveStatus',
      changePasswordStatus: 'auth/changePasswordStatus',
      changeEmailStatus: 'auth/changeEmailStatus',
    }),
  },
  methods: {
    ...mapActions({
      saveUser: 'auth/save',
      changePassword: 'auth/changePassword',
      changeEmail: 'auth/changeEmail',
    }),
  },
}
</script>

<style scoped lang="stylus">
</style>
