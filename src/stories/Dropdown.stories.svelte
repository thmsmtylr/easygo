<script>
  import { Meta, Template, Story } from "@storybook/addon-svelte-csf";
  import Dropdown from "./Dropdown.svelte";

  const menuItems = [
    {
      label: "Edit",
      to: "/edit",
    },
    {
      label: "Duplicate",
      to: "/duplicate",
      divider: true,
    },
    {
      label: "Archive",
      to: "/archive",
    },
    {
      label: "Move",
      to: "/move",
      divider: true,
    },
    {
      label: "Share",
      to: "/share",
    },
    {
      label: "Add to favorites",
      to: "/add",
      divider: true,
    },
    {
      label: "Delete",
      to: "/delete",
    },
  ]
</script>

<Meta
  title="Components/Dropdown"
  component="Dropdown"
/>

<Template let:args>
  <Dropdown {...args}></Dropdown>
</Template>

<Story
  name="Primary"
  args={{
    label: "Options",
    items: menuItems,
    keyboard: true,
    closedOnOuterClick: true,
    insideClick: false,
    onOpened: () => {},
    onClosed: () => {},
  }}
/>
