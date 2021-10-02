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
    <HeaderNavItem href="/" text="Order Hien Co" />
    <HeaderNavItem href="/finishOrder" text="Order Da Xong" />
    <HeaderNavItem href="/yesterdayOrder" text="Order Hom Qua" />
    <HeaderNavItem href="/openOrClose" text="Dong/Mo Cua Tiem" />
    <HeaderNavItem href="/dst" text="Daylight Saving Time" />
    <HeaderNavItem href="/reasonToClose" text="Ly Do Dong Cua Tiem" />
    <HeaderNavItem href="/announcement" text="Thong Bao" />
    <HeaderNavItem href="/removeCategory" text="Xoa Mon An" />
    <HeaderNavItem href="/addBackCategory" text="Them Lai Mon An" />
    <HeaderNavItem href="/getRemovedCategory" text="Mon An Da Xoa" />
  </HeaderNav>
</Header>

<SideNav bind:isOpen={isSideNavOpen}>
  <SideNavItems>
    <SideNavLink href="/" text="Order Hien Co" />
    <SideNavLink href="/finishOrder" text="Order Da Xong" />
    <SideNavLink href="/yesterdayOrder" text="Order Hom Qua" />
    <SideNavLink href="/openOrClose" text="Dong/Mo Cua Tiem" />
    <SideNavLink href="/dst" text="Daylight Saving Time" />
    <SideNavLink href="/reasonToClose" text="Ly Do Dong Cua Tiem" />
    <SideNavLink href="/announcement" text="Thong Bao" />
    <SideNavLink href="/removeCategory" text="Xoa Mon An" />
    <SideNavLink href="/addBackCategory" text="Them Lai Mon An" />
    <SideNavLink href="/getRemovedCategory" text="Mon An Da Xoa" />
  </SideNavItems>
</SideNav>

