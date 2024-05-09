<template>
  <div class="vue3-read-more" :style="styles">
    <p><slot></slot></p>
    <label>
      <input type="checkbox" />
      {{ moreText }}
    </label>
  </div>
</template>

<script>
export default {
  name: 'read-more',
  props: {
    moreText: {
      type: String,
      default: 'Read more',
    },
    rows: {
      type: Number,
      default: 4,
    },
  },
  setup(props) {
    const styles = {
      '--rows': props.rows,
      '--gradient-from' : ((props.rows - 2) / props.rows) * 100 + "%",
      '--gradient-to' : ((props.rows - 1) / props.rows) * 100 + "%",
    };
    return {
      styles,
    }
  },
  mounted() {
    const textContents = this.$el.querySelector('.vue3-read-more p')
    const textHeight = textContents.scrollHeight
    let lineHeight = getComputedStyle(textContents).getPropertyValue('line-height');
    lineHeight = lineHeight.replace('px', '');

    if (textHeight < lineHeight * this.rows) {
      this.$el.querySelector('label input').checked = true
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.vue3-read-more {
    position: relative;
}

.vue3-read-more p {
    display: -webkit-box;
    position: relative;
    margin-bottom: 10px;
    overflow: hidden;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: var(--rows);
    mask-image: linear-gradient(rgba(0,0,0,1) var(--gradient-from), transparent var(--gradient-to));
}

.vue3-read-more:has(:checked) p {
    display: block;
    mask-image: none;
}

.vue3-read-more p::after {
    display: block;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 60px;
    content: '';
}

.vue3-read-more:has(:checked) p::after {
    content: none;
}

.vue3-read-more label {
    display: flex;
    align-items: center;
    gap: 0 4px;
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    padding: .4em 1.2em;
    border-radius: 1px;
    font-size: .8em;
}

.vue3-read-more label:hover {
    cursor: pointer;
}

.vue3-read-more:has(:checked) label {
    display: none;
}

.vue3-read-more input {
    display: none;
}

</style>
