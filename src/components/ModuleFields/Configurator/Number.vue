<template>
  <div>
    <b-form-group>
      <label class="d-block">{{ $t('kind.number.prefixLabel') }}</label>
      <b-form-input
        v-model="f.options.prefix"
        :placeholder="$t('kind.number.prefixPlaceholder')"
      />
    </b-form-group>
    <b-form-group>
      <label class="d-block">{{ $t('kind.number.suffixLabel') }}</label>
      <b-form-input
        v-model="f.options.suffix"
        :placeholder="$t('kind.number.suffixPlaceholder')"
      />
    </b-form-group>
    <b-form-group>
      <label class="d-block">{{ $t('kind.number.precisionLabel') }}</label>
      <b-form-input
        v-model="f.options.precision"
        :placeholder="$t('kind.number.precisionPlaceholder')"
        type="number"
        min="0"
        max="6"
      />
    </b-form-group>
    <b-form-group>
      <label class="d-block">{{ $t('kind.number.formatLabel') }}</label>
      <b-form-input
        v-model="f.options.format"
        :placeholder="$t('kind.number.formatPlaceholder')"
      />
    </b-form-group>
    <div>
      <p>{{ $t('kind.number.liveExample') }}</p>
      <div class="d-flex align-items-center">
        <b-form-input
          v-model="liveExample"
          class="w-25"
        />
        <span class="ml-3">{{ mockField }}</span>
      </div>
      <p class="mt-3">
        {{ $t('kind.number.examplesLabel') }}
      </p>
      <table style="width: 100%;">
        <tr>
          <th>{{ $t('kind.number.exampleInput') }}</th>
          <th>{{ $t('kind.number.exampleFormat') }}</th>
          <th>{{ $t('kind.number.exampleResult') }}</th>
        </tr>
        <tr>
          <td>10000.234</td>
          <td>$0.00</td>
          <td>$10000.23</td>
        </tr>
        <tr>
          <td>0.974878234</td>
          <td>0.000%</td>
          <td>97.488%</td>
        </tr>
        <tr>
          <td>1</td>
          <td>0%</td>
          <td>100%</td>
        </tr>
        <tr>
          <td>238</td>
          <td>00:00:00</td>
          <td>0:03:58</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import base from './base'
import { compose } from '@cortezaproject/corteza-js'

export default {
  i18nOptions: {
    namespaces: 'field',
  },

  extends: base,
  data () {
    return {
      liveExample: 101070,
    }
  },
  computed: {

    mockField () {
      const mockField = new compose.ModuleFieldNumber({
        options: {
          format: this.f.options.format,
          prefix: this.f.options.prefix,
          suffix: this.f.options.suffix,
          precision: this.f.options.precision,
          multiDelimiter: '\n',
        },
      })
      return mockField.formatValue(this.liveExample)
    },
  },
}
</script>
