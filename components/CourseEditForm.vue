<template>
  <v-form v-model="valid">
    <v-text-field v-model="course.name" label="Course Name" />
    <v-select :items="['course', 'chapter', 'standalone_chapter']"
              v-model="course.series_type"
              label="Series Type" />
    <v-select :items="['beginner', 'intermediate', 'advanced', 'beginner to advanced']"
              v-model="course.difficulty"
              label="Difficulty" />
    <S3FileUpload :obj="course"
                  fieldName="image_url"
                  directory="thumbnails"
                  label="Course Thumbnail Image" />
    <MarkdownEditor :markdown="course.description">
      <v-textarea v-model="course.description" 
                  label="Description" 
                  counter=true
                  rows="9" />
    </MarkdownEditor>

    <v-btn @click="saveCourse" :disabled="!valid">Save Course</v-btn>
  </v-form>
</template>

<script>
  import S3FileUpload from '@/components/S3FileUpload'
  import MarkdownEditor from '@/components/MarkdownEditor'

  export default {
    data(){
      return {
        valid: false
      }
    },
    components: {
      S3FileUpload,
      MarkdownEditor
    },
    props: {
      course: {
        type: Object,
        required: true
      },
      saveCourse: {
        type: Function,
        required: true
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>