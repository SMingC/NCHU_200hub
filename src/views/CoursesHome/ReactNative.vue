<template>
  <div>
    <CoursehomeTemplate
      query="reactNativeCollection"
      where="react_native_course"
    />
  </div>
</template>

<script>
import CoursehomeTemplate from "@/views/CoursesHome/CoursehomeTemplate.vue";
export default {
  components: {
    CoursehomeTemplate,
  },
};
</script>
