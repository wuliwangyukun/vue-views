<template>
    <div class="tags-input">
        <slot
            :tags="tags"
            :removeTag="removeTag"
            :input-bindings="{
                value: newTag
            }"
            :input-event-handlers="{
                input:(e)=>{newTag=e.target.value},
                keydown:(e)=>{
                    if(e.keyCode===8){
                        this.handleTagBackspace();
                    }
                    if(e.keyCode===13){
                        this.addTag();
                    }
                }
            }"
        >
        </slot>
    </div>
</template>

<script>
// <slot name="tag">

// <slot/>
// <slot name="input">
    
// <slot/> 
    export default {
        name:'TagsInput',
        model:{
            prop:'tags',
            event:'update'
        },
        props:['tags'],
        data() {
            return {
                newTag:''
            }
        },
        methods: {
            handleTagBackspace(e){
                if(this.newTag.length===0){
                    this.$emit('update',this.tags.slice(0,-1));
                }
            },
            addTag(){
                if(this.newTag.trim().length===0||this.tags.includes(this.newTag)) {
                    return;
                }
                this.$emit('update',[...this.tags,this.newTag]);
                this.newTag = '';
            },
            removeTag(tag) {
                this.$emit('update',this.tags.filter(t=>t!==tag));
            }
        },
    }
</script>

<style scoped lang="scss">
    .tags-input{
        display: block;
        padding: 4px 6px;
        max-width: 100%;
        background-color: #fff;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);   
        line-height: 22px;
        color: #515151;
        text-align: left;
        cursor: text;
        .tags-input-tag {
            position: relative;
            display: inline-block;
            vertical-align: middle;
            padding: 2px 4px;
            padding-right: 18px;
            margin: 4px 0;
            max-width: 50%;
            margin-right: 4px;
            border-radius: 2px;
            color: #fff;
            font-size: 12px;
            font-weight: 700;
            text-align: center;
            background-color: rgba(86,95,223,0.6);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            .tags-input-remove {
                position: absolute;
                top: 0;
                bottom: 0;
                right: 4px;
                padding: 0;
                border: none;
                outline: none;
                background-color: transparent;
                color: #fff;
                line-height: 1;
                font-size: 14px;
                cursor: pointer;
            }       
        }
        #tags-input-text {
            width: auto;
            max-width: inherit;
            margin: 0;
            padding: 6px;
            border: none;
            box-shadow: none;
            outline: none;
            background-color: transparent;
        }
    }
</style>