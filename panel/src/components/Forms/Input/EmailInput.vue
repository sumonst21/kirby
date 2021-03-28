<script>
export const props = {
  props: {
    autocomplete: {
      type: String,
      default: "email"
    },
    placeholder: {
      type: String,
      default() {
        return this.$t("email.placeholder");
      }
    },
    type: {
      type: String,
      default: "email"
    }
  }
}

export default {
  extends: "k-text-input",
  mixins: [props]
}
</script>
