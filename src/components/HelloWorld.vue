<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
import Echo from "laravel-echo";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  created() {
    window.io = require('socket.io-client');

    var token = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI5MmMzMTVhZS02YmRkLTQ3MjYtOGY0Mi1jODY3MjEzMzA0NDMiLCJqdGkiOiJmZWUyYTZlMjg1ZTVhNDc4MDFkNzM3MDk1ZmZhZDM3MjVjYzBiZGRiODZlOWU1MDBiYzQwY2IxZjU0MWUyNTRhOWRlZjdiZDQ5OTRlY2RiOCIsImlhdCI6IjE2MTM2NjU4MDAuMzEwODUwIiwibmJmIjoiMTYxMzY2NTgwMC4zMTA4NTIiLCJleHAiOiIxNjQ1MjAxODAwLjMwNjYwMyIsInN1YiI6IjAwMDAwMDAwLTAwMDAtMDAwMC0wMDAwLTAwMDAwMDAwMDAwMCIsInNjb3BlcyI6W119.GW7Fa-uUpRwvDuLykJUqI8a0shA_0P_GKLXyBJN7-WzxhjPzGdZwqxCngPzWvrlZ951Zaq8pRnFBSEDC4rM6Ok5v4wdhWA25q1YWUbIZP9lTzTcy39wTXW7097w6VrAefvpy3mgcLtWBAGhAwVNEBLUeVUPL-qUFWU82ICSSjn2MtTruE84TCNYafQJzKAdtEztUH8ZW7am3gfEMmYzBBnodN9aoQDcY8cXMmLHct_3UHWefU8AnJs5irN7YkhlMhGwKXdGsbmtpQOPfFdcmmV7rkEYnm6gVIw1c7bQl8YPQcHGpGrQduzhTWqdqfFly1XPSWCx-o4HpDrNxeKvpmp2bPwnOFbUhafPVNyiedUt9Jy8dZuBW3OqK7CuKI9hfL2UVPPB8vkXsFUeq7M4PcZQCk0c_wEBfiNgQkaY157u1kZcuz2ULFId0RMME6UhNOrB0jKDeISma492tLN7QUOzNdNzF1Y4X_L1TM1KqlMfY3ocyXkHAY8xADLzcUsOQcNelq8kTZdDriIF8MHKtf0gf9IMu_j0rh62hVwANwqBuOeDELA7Uy703AFESyukmvCOB2Nge3hmn7WNF2r82UN7t3M_5iF1nX55gxp9n9AOsMC2hd2hMr2MCi2eCfc69bVwUlPJJ4BRF8eRGWBYj2zNJfDHa8lBcSnnfxAsAxNE';

    window.Echo = new Echo({
      broadcaster: 'socket.io',
      host: 'http://localhost:6001',
      auth: {
        headers: {
          Authorization: 'Bearer ' + token,
        },
      },
      namespace: 'App.Events.Notifications'
    });

    window.Echo.channel('e2g.private-notification.user.00000000-0000-0000-0000-000000000000')
        .listen('NotificationEvent', (e => {
          console.log(e)
        }))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
