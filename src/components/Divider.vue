 <template>
  <div class="divider"></div>
</template>

<script>
export default {
  name: 'divider',

  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.divider {
  height: 6px;
  background: {
    image: url(../assets/img/dash.png);
    size: 30px 6px;
  }
}
</style>
