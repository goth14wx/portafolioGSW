<template>
  <v-layout row>
    <v-flex lg12>
        <mainText :title="'hola'" />
        <overText/>
    </v-flex>
  </v-layout>
</template>

<script>
import mainText from "@/components/index/mainText"
import overText from "@/components/index/overText"
export default {
  components: {
    mainText,
    overText
    }
}
</script>
