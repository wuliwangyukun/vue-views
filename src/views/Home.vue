<template>
  <div class="home">
    <inline-tags-input v-model="tags"></inline-tags-input>
    <tags-input v-model="tags" style="margin-bottom=10px">
      <div class="tags-input" slot-scope="{ tags,removeTag,inputBindings,inputEventHandlers }">
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
import TagsInput from '@/components/TagsInput.vue';
import InlineTagsInput from '@/components/InlineTagsInput.vue'


export default {
  name: 'home',
  components: {
    TagsInput,
    InlineTagsInput
  },
  data() {
    return {
      tags:['abc']
    }
  },
}
</script>
