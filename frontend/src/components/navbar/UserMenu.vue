<script setup lang="ts">
import {useUserStore} from "@/stores/user.ts";
import UserSpaceicon from "@/components/navbar/icons/UserSpaceicon.vue";
import UserProfileicon from "@/components/navbar/icons/UserProfileicon.vue";

const user = useUserStore()

function closeMenu() {
  const element = document.activeElement
  if (element && element instanceof HTMLElement) element.blur()
}

</script>

<template>
  <div class="dropdown dropdown-end">
    <div tabindex="0" role="button" class="avatar btn btn-circle w-8 h-8 mr-6">
      <div class="w-8 rounded-full">
        <img :src="user.photo" alt="">
      </div>
    </div>
    <ul tabindex="-1" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-lg">
      <li>
        <RouterLink @click="closeMenu" :to="{name: 'user-space-index',params: {user_id: user.id}}">
          <div class="avatar">
            <div class="w-10 rounded-full">
              <img :src="user.photo" alt="">
            </div>
          </div>
          <span class="text-base font-bold line-clamp-1">{{user.username}}</span>
        </RouterLink>
      </li>
      <li>
        <router-link @click="closeMenu" :to="{name: 'user-space-index',params: {user_id: user.id}}" class="text-sm font-bold py-3">
          <UserSpaceicon />
          <div>
            个人空间
          </div>
        </router-link>
      </li>
      <li>
        <router-link @click="closeMenu" :to="{name: 'user-profile-index',params: {user_id: user.id}}" class="text-sm font-bold py-3">
          <UserProfileicon />
          <div>
            编辑资料
          </div>
        </router-link>
      </li>
      <li></li>
      <li>
        <a @click="closeMenu" class="text-sm font-bold py-3">
          <UserProfileicon />
          <div>
            退出登录
          </div>
        </a>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>