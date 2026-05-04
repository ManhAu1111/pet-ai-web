<script setup>
import { RouterLink } from 'vue-router'
import { Home, BookOpen, PawPrint } from 'lucide-vue-next'
</script>

<template>
  <!-- Mobile Bottom Navigation - hidden on md and above -->
  <nav class="mobile-bottom-nav md:hidden" aria-label="Mobile Navigation">
    <div class="nav-pill">
      <RouterLink to="/" class="nav-item" active-class="nav-item--active" exact>
        <div class="nav-icon-wrap">
          <Home class="nav-icon" />
        </div>
        <span class="nav-label">Trang chủ</span>
      </RouterLink>

      <RouterLink to="/category" class="nav-item" active-class="nav-item--active">
        <div class="nav-icon-wrap">
          <BookOpen class="nav-icon" />
        </div>
        <span class="nav-label">Thư viện</span>
      </RouterLink>

      <RouterLink to="/matching" class="nav-item" active-class="nav-item--active">
        <div class="nav-icon-wrap">
          <PawPrint class="nav-icon" />
        </div>
        <span class="nav-label">Tìm nuôi</span>
      </RouterLink>
    </div>
  </nav>
</template>

<style scoped>
.mobile-bottom-nav {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 100;
  width: calc(100% - 32px);
  max-width: 380px;
}

.nav-pill {
  display: flex;
  align-items: center;
  justify-content: space-around;
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(226, 232, 240, 0.8);
  border-radius: 9999px;
  padding: 10px 16px;
  box-shadow:
    0 8px 32px rgba(0, 0, 0, 0.1),
    0 2px 8px rgba(0, 0, 0, 0.06);
  gap: 8px;
}

.nav-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
  flex: 1;
  text-decoration: none;
  color: #94a3b8;
  transition: color 0.2s ease, transform 0.15s ease;
  padding: 4px 8px;
  border-radius: 9999px;
}

.nav-item:active {
  transform: scale(0.92);
}

.nav-icon-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  transition: background 0.2s ease;
}

.nav-icon {
  width: 22px;
  height: 22px;
  stroke-width: 1.8;
  transition: transform 0.2s ease;
}

.nav-label {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.02em;
  line-height: 1;
}

/* Active state */
.nav-item--active {
  color: #0d9488; /* teal-600 */
}

.nav-item--active .nav-icon-wrap {
  background: rgba(13, 148, 136, 0.1);
}

.nav-item--active .nav-icon {
  transform: scale(1.1);
}

/* Hover on devices that support it */
@media (hover: hover) {
  .nav-item:hover {
    color: #0d9488;
  }

  .nav-item:hover .nav-icon-wrap {
    background: rgba(13, 148, 136, 0.08);
  }
}

/* Safe area support for iPhone notch/home bar */
@supports (padding-bottom: env(safe-area-inset-bottom)) {
  .mobile-bottom-nav {
    bottom: calc(12px + env(safe-area-inset-bottom));
  }
}
</style>
