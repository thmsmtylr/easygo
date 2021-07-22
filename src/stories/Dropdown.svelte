<script>
  /**
   * TODO: Add @popperjs/core to enable positioning of the dropdown with positional props.
   * TODO: Use component `Button` as the dropdown trigger.
   */

  import './dropdown.css';
  import { onMount, onDestroy } from 'svelte';

  const noop = () => {};

  /**
   * Props
   */
  export let open = false;
  export let label = '';
  export let keyboard = true;
  export let insideClick = false;
  export let closeOnOutsideClick = true;
  export let items = [];
  export let onOpened = noop;
  export let onClosed = noop;

  /**
   * Internal vars
   */
  let trigger;
  let triggerEvent;
  let keyboardEvent;
  let outsideClickEvent;
  let menu;
  let menuItems = [];

  /**
   * Keyboard events
   */
  const ESCAPE_KEY = "Escape";
  const ARROW_UP_KEY = "ArrowUp";
  const ARROW_DOWN_KEY = "ArrowDown";
  const REGEXP_KEYDOWN = new RegExp(
    `${ARROW_UP_KEY}|${ARROW_DOWN_KEY}|${ESCAPE_KEY}`
  );

  /**
   * Menu item nodes
   */
  const MENU_LIST_ITEMS = ".easygo-dropdown-menu-item"

  $: {
    if (open) {
      onDropdownOpened();
    } else {
      onDropdownClosed();
    }
  }

  function onDropdownOpened() {
    getMenuItems();
    keyboardEvents();
    outsideEventAttacher();
    onOpened();
  }

  function onDropdownClosed() {
    cleanUp();
    onClosed();
  }

  function getMenuItems() {
    // NOTE: Unsure how to use `bind:this` in the context of `each`
    // TODO: Remove messy `querySelectorAll` use.
    const nodeList = document.querySelectorAll(MENU_LIST_ITEMS);
    menuItems = [...nodeList];
  }

  function keyboardEvents() {
    if (keyboard) {
      keyboardEvent = attachEvent(document, "keydown", (e) => {
        if (
          !/input|textarea/i.test(e.target.tagName) &&
          REGEXP_KEYDOWN.test(e.key)
        ) {
          e.preventDefault();
          e.stopPropagation();

          if (e.key === ESCAPE_KEY) open = false;

          if (!menuItems.length) return;

          let index = menuItems.indexOf(e.target);
          // Up
          if (e.key === ARROW_UP_KEY && index > 0) index--;
          // Down
          if (e.key === ARROW_DOWN_KEY && index < menuItems.length - 1) index++;
          // index is -1 if the first keydown is an ArrowUp
          index = index === -1 ? 0 : index;
          menuItems[index].focus();
        }
      });
    }
  }

  function outsideEventAttacher() {
    if (closeOnOutsideClick) {
      outsideClickEvent = attachEvent(document, "click", event => {
        if (event.target !== menu && !menu.contains(event.target)) {
          open = false;
        }
      });
    }
  }

  function menuClick() {
    if (!insideClick) open = false;
  }

  function attachEvent(target, ...args) {
    target.addEventListener(...args);
    return {
      remove: () => target.removeEventListener(...args)
    }
  }

  function cleanUp() {
    if (keyboardEvent) keyboardEvent.remove();
    if (outsideClickEvent) outsideClickEvent.remove();
  }

  onMount(() => {
    triggerEvent = attachEvent(trigger, "click", (e) => {
      e.stopPropagation();
      open = !open;
    });
  });

  onDestroy(() => {
    cleanUp();
    triggerEvent.remove();
  })
</script>

<div class="easgo-dropdown">
  <button
    class="
      easygo-button
      easygo-button--medium
      easygo-button--secondary
      easygo-button--outlined-secondary
      easygo-button--elevation-1
      easygo-button--dropdown-toggle
    "
    aria-haspopup="true"
    aria-expanded={open}
    type="button"
    bind:this={trigger}
  >
    {label}
  </button>
  <div
    class="easygo-dropown-menu"
    class:show={open}
    bind:this={menu}
    on:click={menuClick}
  >
    {#each items as item}
      <button
        class="easygo-dropdown-menu-item"
        type="button"
        on:click={noop}
      >
        {item.label}
      </button>
      {#if item.divider}
        <div class="easygo-dropdown-menu-item-divider" />
      {/if}
    {/each}
  </div>
</div>
