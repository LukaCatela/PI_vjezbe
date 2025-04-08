<template>
        <div class="bg-slate-700 p-2 text-white flex justify-center ">
            <slot></slot> - {{ new Date().getFullYear() }}
        </div>
</template>