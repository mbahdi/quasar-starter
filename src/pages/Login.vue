<template>
  <div class="absolute-center text-white bg-black mainbox">
    <div class="q-px-lg q-pt-xl q-mb-md q-mb-xs">
      <div class="text-h3 margin-bottom-20">Sign In</div>
      <div class="row margin-bottom-10">
        <q-input
          type="text"
          v-model="email"
          class="col"
          filled
          bg-color="grey-7"
          dense
          label="Email or phone number"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Please enter a valid email or phone number.']">
        </q-input>
      </div>

      <div class="row margin-bottom-20">
        <q-input
          type="password"
          v-model="password"
          class="col"
          filled
          bg-color="grey-7"
          dense
          label="Password"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Your password must contain between 4 and 60 characters.']">
        </q-input>
      </div>

      <div class="row margin-bottom-20">
        <q-btn
          class="col"
          color="primary"
          dense="dense"
          size="lg">
          Sign In
        </q-btn>
      </div>
      <div class="row box-remember margin-bottom-20">
        <div class="item" style="margin-left:-8px;">
          <q-checkbox
            size="xs"
            keep-color
            v-model="val"
            label="Remember me"
            color="red" />
        </div>
        <div class="item text-right">
          <q-btn
            to="/help"
            flat
            no-caps
            label="Need help?"
            size="sm" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      val: true
    }
  }
}
</script>

<style lang="scss">
.mainbox {
  opacity: 0.9;
  min-width: 350px;
}
.margin-bottom-10 {
  margin-bottom: 10px;
}
.margin-bottom-20 {
  margin-bottom: 20px;
}
.box {
  padding: 20px;
}
.box-remember {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
}
.box-remember
.item {
  width: 50%;
  font-size: 12px;
}
</style>
