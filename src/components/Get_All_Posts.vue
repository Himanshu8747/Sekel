<template>
  <div>
    <div v-if="selectedPostComment.length > 0">
      <h2>Comments</h2>
        <p>Your Comment for selected Post is : {{selectedPostComment}}</p>
    </div>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Title</th>
          <th>Body</th>
          <th>User ID</th>
          <th>View Comments</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="post in allPosts" :key="post.id">
          <td>{{ post.id }}</td>
          <td>{{ post.title }}</td>
          <td>{{ post.body }}</td>
          <td>{{ post.userId }}</td>
          <td>
            <button @click="fetchComments(post.id)">View Comments</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        allPosts: [],
        selectedPostComment:"",
      };
    },
    mounted() {
      this.fetchPosts();
    },
    methods: {
      fetchPosts() {
        axios.get('https://dummyjson.com/posts')
          .then(response => {
            this.allPosts = response.data.posts;
          })
          .catch(error => {
            console.error('Error fetching posts:', error);
          });
      },
      fetchComments (postId) {
        axios.get(`https://dummyjson.com/posts/${postId}/comments`)
        .then(response => {
          this.selectedPostComment = response.data.comments[0].body;
        })
        .catch(error => {
          alert('Error Fetching Comments due to:', error);
        });
      }
    }
  };
  </script>

<style scoped>
table {
  width: 90%;
  margin-left: 5%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #f2f2f2;
}
</style>
  