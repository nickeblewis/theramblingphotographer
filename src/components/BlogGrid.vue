<!-- <template>
  <div class="grid blog-grid">
    <div v-for="{node} in posts" :key="node.id"
      class="border-2 border-grey flex"
    >
      <g-image :src="node.coverImage" class="w-100 min-height object-cover object-center  lg:w-32 xl:w-48"/>
      <div class="p-4 sm:pr-6">
        <p class="text-xs uppercase">{{node.date | formatDate("dd.MMM")}}</p>
        <h3 class="font-bold leading-tight"><g-link :to="node.path">{{node.title}}</g-link></h3>
        <p v-if="showExcerpt" class="leading-tight pt-2">{{node.summary}}</p>
      </div>
    </div>
  </div>
</template>-->

<template>
  <main class="flex-1 w-full mx-auto container">
    <!-- <h2 class="text-2xl font-bold">Recent Blog Posts</h2> -->
    <ul class="flex flex-wrap -mx-4">
      <li v-for="{node} in posts" :key="node.id" class="flex w-full px-4 mt-4 md:w-1/2 lg:w-1/3">
        <div
          class="flex flex-col overflow-hidden bg-white rounded-lg shadow-lg relative transition-all ease-in-out duration-200 group transform hover:translate-y-px hover:shadow-md"
        >
          <div>
            <g-image :src="node.coverImage"/>
          </div>
          <div class="flex flex-col flex-1 p-6">
            <h3 class="text-xl font-bold text-gray-900">{{node.title}}</h3>
            <div class="flex items-center">
              <p class="text-sm text-gray-700">
                <span>Published {{node.date | formatDate("dd MMM Y")}}</span>
                <!-- <span>•</span>
                <span>2m read time</span> -->
              </p>
            </div>
            <div class="flex flex-col flex-1 mt-6 text-gray-900">
              <p class="flex-1">{{node.summary}}</p>
            </div>
            <ul class="flex flex-wrap items-center mt-6">
              <li v-for="tag in node.tags" 
                :tag="tag"
                class="relative inline-block p-2 mb-2 mr-2 text-sm bg-gray-200 rounded-lg z-10"
              >
                <a
                  href=""
                  class="flex items-end text-gray-900 hover:opacity-75"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    class="icon-tag block w-4 h-4 mr-1"
                  >
                    <path
                      d="M2.59 13.41A1.98 1.98 0 012 12V7a5 5 0 015-5h4.99c.53 0 1.04.2 1.42.59l8 8a2 2 0 010 2.82l-8 8a2 2 0 01-2.82 0l-8-8zM7 9a2 2 0 100-4 2 2 0 000 4z"
                      class="primary"
                    />
                    <path d="M12 18l6-6-4-4-6 6.01L12 18z" class="secondary" />
                  </svg>
                  {{tag}}
                </a>
              </li>
              
             
            </ul>
            
            <g-link :to="node.path">Read: {{node.title}}</g-link>
          </div>
        </div>
      </li>
      
    </ul>
  </main>
</template>

<script>
export default {
  name: "BlogGrid",
  props: {
    posts: {
      type: Array,
      required: true
    },
    showExcerpt: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style scoped>
.min-height {
  min-height: 6rem;
}
@screen lg {
  .min-height {
    min-height: 8rem;
  }
}
@screen xl {
  .min-height {
    min-height: 12rem;
  }
}
</style>
