<template>
  <div>
    <button
      @click="onSubmit()"
    >test</button>
    <NuxtWelcome />
  </div>
</template>

<script setup lang="ts">
  const { login } = useStrapiAuth()
  const router = useRouter()
  const onSubmit = async () => {
    try {
      await login({ identifier: 'test1@test.com', password: 'test1234' })
      const user = useStrapiUser()
      console.log('user :>> ', user);
      console.log('user :>> ', user.value.email);
      router.push('/authenticated-page')
    } catch (e) {}
  }
  </script>
