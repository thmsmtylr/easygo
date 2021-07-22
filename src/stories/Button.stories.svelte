<script>
  import { Meta, Template, Story } from "@storybook/addon-svelte-csf";
  import Button from "./Button.svelte";
</script>

<Meta
  title="Components/Button"
  component={Button}
  argTypes={{
    label: { control: "text" },
    mode: {
      control: { type: "select", options: ["primary", "secondary", "success", "danger", "warning"] },
    },
    outlined: {
      control: "boolean",
      defaultValue: false,
    },
    size: {
      control: { type: "select", options: ["small", "medium", "large"] },
    },
    disabled: {
      control: "boolean",
      defaultValue: false,
    },
    elevation: {
      control: { type: "select", options: ["elevation-0", "elevation-1", "elevation-2", "elevation-3"] },
      defaultValue: "elevation-0",
    },
    onClick: { action: "onClick" },
  }}
/>

<Template let:args>
  <Button {...args} on:click={args.onClick} />
</Template>

<Story
  name="Primary"
  args={{
    mode: "primary",
    label: "Primary",
  }}
/>

<Story
  name="Primary Outlined"
  args={{
    mode: "primary",
    label: "Primary Outlined",
    outlined: true,
  }}
/>

<Story
  name="Secondary"
  args={{
    mode: "secondary",
    label: "Secondary",
  }}
/>

<Story
  name="Secondary Outlined"
  args={{
    mode: "secondary",
    label: "Secondary Outlined",
    outlined: true,
  }}
/>

<Story
  name="Success"
  args={{
    mode: "success",
    label: "Success",
  }}
/>

<Story
  name="Success Outlined"
  args={{
    mode: "success",
    label: "Success Outlined",
    outlined: true,
  }}
/>

<Story
  name="Danger"
  args={{
    mode: "danger",
    label: "Danger",
  }}
/>

<Story
  name="Danger Outlined"
  args={{
    mode: "danger",
    label: "Danger Outlined",
    outlined: true,
  }}
/>

<Story
  name="Warning"
  args={{
    mode: "warning",
    label: "Warning",
  }}
/>

<Story
  name="Warning Outlined"
  args={{
    mode: "warning",
    label: "Warning Outlined",
    outlined: true,
  }}
/>

<Story
  name="Large"
  args={{
    size: "large",
    label: "Button",
  }}
/>

<Story
  name="Small"
  args={{
    size: "small",
    label: "Button",
  }}
/>
