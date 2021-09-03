<template>
  <div>
    {{ data }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: null
    };
  },
  mounted() {
    const RSS_URL = `https://cors-anywhere.herokuapp.com/koreatimes.co.kr/www/rss/entertainment.xml`;

    var parseString = require("xml2js").parseString;

    this.$axios.get(RSS_URL).then(response => {
      var self = this;
      parseString(response.data, function(err, result) {
        self.data = result;
        console.log(result);
      });
    });
  }
};
</script>

<style lang="scss" scoped></style>
