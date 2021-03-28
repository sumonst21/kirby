<script>
export const props = {
  props: {
    autocomplete: {
      type: String,
      default: "tel"
    },
    type: {
      type: String,
      default: "tel"
    }
  }
}

export default {
  extends: "k-text-input",
  mixins: [props]
}
</script>
