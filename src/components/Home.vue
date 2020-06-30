<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-md-8 m-auto">
          <ul class="list-group">
            <li
              class="list-group-item"
              v-for="item in visibleList"
              :key="item.id"
            >
              {{ item.title }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';
export default {
  name: 'Home',
  computed: mapGetters('home', ['allList', 'visibleList']),
};
</script>

<style></style>
