<template>
  <CourseTemplate :contents="contents" where="advanced_react_course">
    <Video
      src="https://www.youtube.com/embed/WfCxdlkFzFk?list=PLn8_GKQGufjklqoAHsBgyfeX0jedV0Uo7"
    />
  </CourseTemplate>
</template>

<script>
import CourseTemplate from "@/views/Courses/CourseTemplate.vue";
import Video from "@/views/Courses/Video.vue";

export default {
  async created() {
    this.contents = await this.getcartoonUrl();
  },
  components: { CourseTemplate, Video },
  data() {
    return {
      contents: [],
    };
  },
  methods: {
    async getcartoonUrl() {
      const index = Number(this.$route.query.index);
      this.index = index;
      const query = `{
        advancedReactCollection(where: {AND: [{index: ${index} }]}) {
          items {
            title
            index
            description
            illustration{
              url
            }
            content
          }
        }
      }
      `;
      const fetchUrl = `https://graphql.contentful.com/content/v1/spaces/${process.env.VUE_APP_CONTENTFUL_SPACE_ID}/`;

      const fetchOptions = {
        method: "POST",
        headers: {
          Authorization: `Bearer ${process.env.VUE_APP_CONTENTFUL_ACCESS_TOKEN}`,
          "Content-Type": "application/json",
        },
        body: JSON.stringify({ query }),
      };

      try {
        const response = await fetch(fetchUrl, fetchOptions).then((response) =>
          response.json()
        );
        return response.data.advancedReactCollection.items;
      } catch (error) {
        throw new Error("Could not receive the data from Contentful!");
      }
    },
  },
};
</script>
