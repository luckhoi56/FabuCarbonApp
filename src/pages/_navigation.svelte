<script>
  import {
    Header,
    HeaderNav,
    HeaderNavItem,
    HeaderNavMenu,
    SideNav,
    SideNavItems,
    SideNavMenu,
    SideNavMenuItem,
    SideNavLink,
    SkipToContent,
    Content,
    Grid,
    Row,
    Column,
  } from "carbon-components-svelte";

  let isSideNavOpen = false;
</script>

<Header company="IBM" platformName="Carbon Svelte" bind:isSideNavOpen>
  <div slot="skip-to-content">
    <SkipToContent />
  </div>

  <HeaderNav>
    <HeaderNavItem href="/announcement" text="Announcement" />
    <HeaderNavItem href="/calendar" text="Booking Calendar" />
  </HeaderNav>
</Header>

<SideNav bind:isOpen={isSideNavOpen}>
  <SideNavItems>
    <SideNavLink href="/announcement" text="Announcement" />
    <SideNavLink href="/calendar" text="Booking Calendar" />
  </SideNavItems>
</SideNav>

