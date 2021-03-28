<script>
export const props = {
  props: {
    autocomplete: {
      type: String,
      default: "new-password"
    },
    type: {
      type: String,
      default: "password"
    }
  }
}

export default {
  extends: "k-text-input",
  mixins: [props]
}
</script>
