<template>
  <!-- note list -->
  <div class="notes">
    <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index">
      <div class="note-header">
        <p>{{ note.title }}</p>
        <p @click="removeNote(index)" style="cursor:pointer">x</p>
      </div>
      <div class="note-body">
        <p>{{note.descr}}</p>
        <span>{{note.date}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    notes: {
      type: Array,
      required: true,
    },
    grid: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      console.log(`${index}`);
      this.$emit('remove', index);
    },
  },
};
</script>

<style lang="scss">
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}

.note {
  width: 46%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #fff;
  &.full {
    width: 100%;
  }
}

.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  h1 {
    font-size: 32px;
  }
  p {
    font-size: 22px;
    color: rgb(16, 3, 129);
    font-weight: bold;
  }
  svg {
    color: #999;
    margin-right: 12px;
    &.active {
      color: rgb(16, 3, 129);
    }
    &:last-child {
      margin-right: 0;
    }
  }
}

.note-body {
  p {
    margin: 20px 0;
  }
  span {
    font-size: 14px;
    color: #999;
  }
}
</style>