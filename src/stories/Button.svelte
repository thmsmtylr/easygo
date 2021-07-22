<script>
  import './button.css';

  const noop = () => {};

  /**
   * Props
   */
  export let size = 'medium';
  export let label = ''
  export let mode = '';
  export let outlined = false;
  export let disabled = false;
  export let elevation = '';
  export let onClick = noop;
</script>

<button
  type="button"
  class={[
    'easygo-button',
    `easygo-button--${size}`,
    `easygo-button--${elevation}`,
    outlined ? `easygo-button--outlined-${mode}` : `easygo-button--${mode}`,
  ].join(' ')}
  disabled={disabled}
  on:click={onClick}
 >
  {label}
</button>
