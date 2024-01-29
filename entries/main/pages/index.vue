<template lang="pug">
.home.page
    //- Title based on window size. If SSR, this will prevent cumulative layout shift.
    client-only
      h1 {{ title }}
      h1(slot="placeholder") Loading...
    p Lucas ipsum dolor sit amet coruscant anakin jar obi-wan darth darth organa hoth antilles chewbacca. Sebulba han obi-wan antilles obi-wan. C-3po zabrak padmé gonk ackbar yavin solo. Darth alderaan palpatine dagobah grievous dooku twi'lek maul moff. Mara tusken raider kamino skywalker hutt mothma wedge greedo vader. Yavin kamino ben kenobi sidious lando. Kenobi calrissian organa ventress k-3po yoda darth jinn. Darth binks boba ben wedge. Lando twi'lek mace ewok solo. Skywalker kenobi coruscant kessel droid.
    p Solo c-3p0 watto hutt chewbacca r2-d2 windu. Grievous obi-wan jade organa calamari jinn aayla. Windu yavin boba amidala darth secura mara boba ben. Solo greedo hutt fett padmé antilles kamino. Mara zabrak obi-wan binks gamorrean mon. Binks twi'lek dooku moff. Jango leia binks calrissian luuke wedge wampa. Darth sidious binks biggs. Yoda lars antilles darth calamari skywalker antilles dagobah. Qui-gonn darth kessel fisto kessel organa darth. Organa maul vader darth moff ben obi-wan. Yoda kamino fett darth.
    .button-wrapper
      button(@click="causeError") Cause Error
      nuxt-link.btn(to="/sample") Sample Page
      ButtonCounter
</template>

<script>
import ButtonCounter from '~~/components/ButtonCount.vue'

export default {
  name: 'Home',
  components: {
    ButtonCounter,
  },
  computed: {
    title() {
      if (this.$store.state.isMobile) {
        return 'Home - Mobile'
      } else if (this.$store.state.isTablet) {
        return 'Home - Tablet'
      } else {
        return 'Home - Desktop'
      }
    },
  },
  methods: {
    causeError() {
      throw new Error('ERROR')
    },
  },
}
</script>

<style lang="scss" scoped>
// .home {
// }
.button-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 2rem;

  button,
  .btn {
    margin: 0.5rem 0;
  }

  @include media-breakpoint-up(md) {
    flex-direction: row;

    button,
    .btn {
      margin: 0 0.5rem;
    }
  }
}
</style>
