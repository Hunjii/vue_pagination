<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-8 m-auto pt-2">
          <nav aria-label="Page navigation example">
            <ul class="pagination">
              <li
                class="page-item"
                :class="currentPage === 0 ? 'disabled' : ''"
              >
                <a class="page-link" @click="setCPage(currentPage - 1)"
                  >Previous</a
                >
              </li>
              <li class="page-item">
                <a class="page-link" href="#" v-if="currentPage !== 0">{{
                  currentPage
                }}</a>
              </li>
              <li class="page-item active">
                <a class="page-link" href="#">{{ currentPage + 1 }}</a>
              </li>
              <li class="page-item">
                <a
                  class="page-link"
                  href="#"
                  v-if="
                    currentPage !== Math.ceil(allList.length / pageSize) - 1
                  "
                  >{{ currentPage + 2 }}</a
                >
              </li>
              <li
                class="page-item"
                :class="
                  currentPage === Math.ceil(allList.length / pageSize) - 1
                    ? 'disabled'
                    : ''
                "
              >
                <a class="page-link" @click="setCPage(currentPage + 1)">Next</a>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex';

export default {
  name: 'Pagination',
  data() {
    return {
      visibleList: '',
    };
  },
  computed: {
    ...mapGetters('home', ['currentPage', 'pageSize', 'allList']),
  },
  beforeMount() {
    this.updateVisibleList();
    this.setVisibleList(this.visibleList);
  },
  methods: {
    ...mapMutations('home', ['setVisibleList', 'setcurrentPage']),
    updateVisibleList() {
      this.visibleList = this.allList.slice(
        this.currentPage * this.pageSize,
        this.currentPage * this.pageSize + this.pageSize
      );
    },
    setCPage(cP) {
      this.setcurrentPage(cP);
      this.updateVisibleList();
      this.setVisibleList(this.visibleList);
    },
  },
};
</script>

<style></style>
