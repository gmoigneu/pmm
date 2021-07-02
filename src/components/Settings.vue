<template>
  <div class="flex flex-col">
    <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
        <div
          class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg"
        >
          <table class="min-w-full divide-y divide-gray-200">
            <thead class="bg-gray-50">
              <tr>
                <th
                  scope="col"
                  class="
                    px-6
                    py-3
                    text-xs
                    font-medium
                    text-gray-500
                    uppercase
                    tracking-wider
                  "
                >
                  Aperture
                </th>
                <th
                  scope="col"
                  class="
                    px-6
                    py-3
                    text-base
                    font-medium
                    text-gray-500
                    uppercase
                    tracking-wider
                  "
                >
                  Speed
                </th>
              </tr>
            </thead>
            <tbody>
              <!-- Even row bg-gray-50 -->
              <tr class="bg-white" v-for="(setting, index) in settings" :key="index">
                <td
                  class="
                    px-6
                    py-2
                    whitespace-nowrap
                    text-base
                    font-medium
                    text-gray-900
                  "
                >
                  f/{{ setting.aperture }}
                </td>
                <td class="px-6 py-2 whitespace-nowrap text-sm text-gray-500">
                  {{ setting.speed }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Settings",
  props: {
    settings: Array,
  },
};
</script>
