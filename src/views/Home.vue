<template>
  <div class="home">
    <tags-input v-model="tags">
      <div slot-scope="{ tag,removeTag,inputBindings,inputEventHandlers }">
        <input id="tags-input-text" placeholder="add tags..."
          v-bind="inputBindings"
          v-on="inputEventHandlers"
        >

        <div>
          <span class="tags-input-tag" v-for="tag in tags">
            {{tag}}
            <button type="button" class="tags-input-remove" @click="removeTag(tag)">&times;</button>
          </span>
        </div>
      </div>
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
