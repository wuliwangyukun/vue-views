<template>
    <tags-input :tags="value" @update="(newTags)=>{$emit('input',newTags)}">
      <div class="tags-input" slot-scope="{ tags,removeTag,inputBindings,inputEventHandlers }">
        <span class="tags-input-tag" v-for="tag in tags">
        {{tag}}
        <button type="button" class="tags-input-remove" @click="removeTag(tag)">&times;</button>
        </span>
        <input id="tags-input-text" placeholder="add tags......"
          v-bind="inputBindings"
          v-on="inputEventHandlers"
        >
      </div>
    </tags-input>
</template>

<script>
import TagsInput from '@/components/TagsInput.vue'

    export default {
        name:'InlineTagsInput',
        props:['value'],
        components: {
            TagsInput
        },
    }
</script>

<style scoped>

</style>