<script>
export const props = {
  props: {
    autocomplete: {
      type: String,
      default: "url"
    },
    type: {
      type: String,
      default: "url"
    }
  }
}

export default {
  extends: "k-text-input",
  mixins: [props]
}
</script>
