# svelte-tutorial-notes
Notes taken from a svelte tutorial. No actual code. 

I took this [Svelte.js - The Complete Guide (incl. Sapper.js)](https://www.udemy.com/course/sveltejs-the-complete-guide/) tutorial on Udemy and these are my cheatsheet notes. 

1. `$: variable = something relying on some other variable` is essentially a memoize function
1. `class:className={bool}` optional class
1. arrays: never mutate, always recreate
1. `export let` is for external props
1. `{#if}...{:else if}...{:else}...{/if}`
1. `on:event` event forwarding, for using an event passed down from above OR for getting dispatched events from below
1. `dispatch('eventName', data)` from `createEventDispatcher()` for passing data up
1. slots can be default unnamed, or named, filled with default html, or empty.
1. `<h1 slot="title"/>` targets `<slot name="title"/>`
1. `<Component let:myVar>` gets `myVar` from `<Component><slot myVar={myVar}/></Component>`
1. Lifecycle `onMount` `beforeUpdate` `afterUpdate` `tick`(promise) `onDestroy`
1. `<input bind:value>` varies by input type. `bind:group` is cool.
1. `<Component bind:myVar={localVar}/>` IF and ONLY IF `type` is not set on downstream `<input/>` its binding to
1. `bind:this={myRef}` is ref to html element. For read.
1. Use store when data shared outside of parent/child relationship

          store = writeable(defaultValue)
          unsubscribe = store.subscribe(storeData => {}) //must unsubscribe on destroy!
          store.set(newVal)
          store.update(storeData => {})
          {#each $store as item} //auto handles subscriptions
          <p>{$store}</p>` //auto handles subscriptions
1.           
        readableStore = readable(storeData, set => { 
          do some repeatable/automatic stuff; 
          set(newStoreData); 
          return unsubscribe fn
        })    
        unsubscibe = readableStore.subscribe(storeData => {})
1. `animatedValue = tweened(value, {delay, duration, easing})` from motion
1. `physicsAnimatedValue = spring(value, {siffness, damping, precision})` from motion
1. `<div transition:fade={{delay, duration, easing, ...etc}} />` etc from transition or `<div in:fade out:fly />` if you want different
