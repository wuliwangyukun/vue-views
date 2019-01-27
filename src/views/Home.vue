<template>
  <div class="home">
    <tags-input v-model="tags">
      <span slot="tag" slot-scope="{ tag,removeTag }" class="tags-input-tag">
        {{tag}}
        <button type="button" class="tags-input-remove" @click="removeTag(tag)">&times;</button>
      </span>

      <input slot="input" slot-scope="{bindings,eventHandlers}" id="tags-input-text" placeholder="add tags..."
          v-bind="bindings"
          v-on="eventHandlers"
      >
      <!-- <input slot="input" slot-scope="{newTag,onInput,handleTagBackspace,addTag}" id="tags-input-text"
          placeholder="add tags..."
          :value="newTag"
          @input="onInput"
          @keydown.backspace="handleTagBackspace"
          @keydown.enter.prevent="addTag"
      > -->
    </tags-input>
  </div>
</template>

<script>
// @ is an alias to /src
import TagsInput from '@/components/TagsInput.vue'

export default {
  name: 'home',
  components: {
    TagsInput
  },
  data() {
    return {
      tags:['abc']
    }
  },
}
</script>
