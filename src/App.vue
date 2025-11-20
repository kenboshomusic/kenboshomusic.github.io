<template>
  <div>
    <!-- Header her zaman görünsün -->
    <Headerr />

    <!-- Router içerikleri -->
    <keep-alive>
      <router-view></router-view>
    </keep-alive>

    <!-- Footer her zaman görünsün -->
    <Footerr />

    <notifications group="foo" position="bottom left" />
  </div>
</template>

<script>
import Headerr from "@/components/Header/Header.vue";
import Footerr from "@/components/Footer/Footer.vue";

export default {
  components: {
    Headerr,
    Footerr
  },

  created() {
    // Tema ayarı aynı kalsın
    if (localStorage.getItem("darkTheme") === "true") {
      document
        .getElementById("varSource")
        .setAttribute("href", "/css/var-dark.css");
      document.getElementById("adr-color").setAttribute("content", "#090b10");
    } else {
      document.getElementById("varSource").setAttribute("href", "/css/var.css");
      document.getElementById("adr-color").setAttribute("content", "#2a555b");
    }

    // ❗ Login ya da loading yönlendirmesi ARTIK YOK.
    // Site direkt içerik sayfasını açacak.
  }
};
</script>

<style>
.vue-notification {
  border-radius: 10px !important;
  color: var(--color-text) !important;
  background: var(--color3) !important;
  border-left: 5px solid var(--color5) !important;
}

.vue-notification-group {
  bottom: 80px !important;
  width: 230px !important;
}

.notification-title {
  max-width: 100% !important;
  overflow: hidden !important;
  white-space: nowrap !important;
  text-overflow: ellipsis !important;
}
</style>
