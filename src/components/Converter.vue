<template>
  <v-container>
    <v-row class="text-center">


      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          Private key converter
        </h2>

        <v-row justify="center">
<v-col cols="12" sm="6" md="6">
<v-text-field
            v-model="mnemonic"
            type="text"
            name="input-10-1"
            label="Mnemonic"
            hint="Mnemonic"
          ></v-text-field>
        </v-col>
<div class="my-2">
        <v-btn text large color="primary" @click="click">Convert</v-btn>
      </div>
</v-row>
   <v-row v-if='converted' justify="center">
<v-col cols="12" sm="6" md="6">
          <v-text-field
            v-model="pkey"
            :append-icon="show2 ? 'mdi-eye' : 'mdi-eye-off'"
            :type="show2 ? 'text' : 'password'"
            readonly
            label="Nem private key"
            @click:append="show2 = !show2"
          ></v-text-field>
        </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import xor from 'buffer-xor'
const bip39 = require('bip39')

const fromMnemonic = (mnemonic) => {
    const original = bip39.mnemonicToSeedSync(mnemonic).toString('hex')
    const part1 = Buffer.from(original.substr(0, 64), 'hex')
    const part2 = Buffer.from(original.substr(64, 64), 'hex')
    const hex = xor(part1, part2).toString('hex')
    return hex
  }

  export default {
    name: 'Coverter',

    data: () => ({
     mnemonic: '',
     pkey: '',
     converted: false,
     show1: false,
     show2: false
    }),
    methods: {
      click() {
        this.pkey = fromMnemonic(this.mnemonic)
        this.converted = true
      }
    }
  }
</script>
