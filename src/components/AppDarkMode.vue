<template>
     <div class="flex align-middle">
<div
      class="
        relative
        inline-block
        w-10
        mr-2
        align-middle
        select-none
        transition
        duration-200
        ease-in
      "
    >
      <input
        @click="toggleModo"
        type="checkbox"
        name="toggle"
        id="toggle"
        class="
          toggle-checkbox
          absolute
          block
          w-6
          h-6
          rounded-full
          bg-white
          border-4
          appearance-none
          cursor-pointer
        "
      />
      <label
        for="toggle"
        class="
          toggle-label
          block
          overflow-hidden
          h-6
          rounded-full
          bg-gray-300
          cursor-pointer
        "
      ></label>
    </div>
    <label for="toggle" class="mode-label text-xs text-white ">Modo Black</label>
     </div>
    
  
</template>
<script>
export default {
    data: ()=> {
        return {
            darkMode: false
        }
    },
    methods: {
        toggleModo() {
            this.darkMode = !this.darkMode
            if(this.darkMode) {
                document.documentElement.classList.add("dark")
            } else {
                document.documentElement.classList.remove("dark")
            }
            

        }
    }
}
</script>
<style>
/* CHECKBOX TOGGLE SWITCH */
/* @apply rules for documentation, these do not work as inline style */
.toggle-checkbox:checked {
  @apply: right-0 border-blue-500;
  right: 0;
  border-color: #5947ff;
}
.toggle-checkbox:checked + .toggle-label {
  @apply: bg-green-400;
  background-color: #5947ff; 
}
.mode-label {
    line-height: 2;
}

</style>
