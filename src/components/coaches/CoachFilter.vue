<template>
  <base-card>
    <h2>Find Your Coach</h2>
    <div class="container">
      <span class="filter-option">
        <input type="checkbox" id="ai" checked @change="setFilter" />
        <label for="ai">AI</label>
      </span>
      <span class="filter-option">
        <input type="checkbox" id="backend" checked @change="setFilter" />
        <label for="backend">Backend</label>
      </span>
      <span class="filter-option">
        <input type="checkbox" id="career" checked @change="setFilter" />
        <label for="career">Career</label>
      </span>
      <span class="filter-option">
        <input type="checkbox" id="frontend" checked @change="setFilter" />
        <label for="frontend">Frontend</label>
      </span>
      <span class="filter-option">
        <input type="checkbox" id="mobile" checked @change="setFilter" />
        <label for="mobile">Mobile</label>
      </span>
    </div>
  </base-card>
</template>

<script>
export default {
  emits: ["change-filter"],
  data() {
    return {
      filters: {
        ai: true,
        backend: true,
        career: true,
        frontend: true,
        mobile: true,
      },
    };
  },
  methods: {
    setFilter(event) {
      const inputId = event.target.id;
      const isActive = event.target.checked;
      const updatedFilters = {
        ...this.filters,
        [inputId]: isActive,
      };
      this.filters = updatedFilters;
      this.$emit("change-filter", updatedFilters);
    },
  },
};
</script>

<style scoped>
h2 {
  margin: 0.5rem 0 1rem 0;
  text-align: center;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.filter-option {
  margin-right: 1rem;
}

.filter-option label,
.filter-option input {
  vertical-align: middle;
}

.filter-option label {
  margin-left: 0.25rem;
}

.filter-option.active label {
  font-weight: bold;
}
</style>
