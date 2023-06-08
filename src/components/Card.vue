<template>
    <div class="card">
        <h3 class="title">
            <slot name="title"></slot>
        </h3>
        
        <slot name="slogan"></slot>
        <slot></slot>
        <button>確認</button>
    </div>
</template>