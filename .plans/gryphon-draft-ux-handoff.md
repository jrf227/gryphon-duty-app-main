# UX Handoff: Gryphon Draft

## Design Tool Mode
**Pencil** (in-repo `.pen` files via Pencil MCP)

## Design Files
- Pencil: `design/mockup-1.pen`
- Theme: Dark mode default, Light mode available via `theme: { Mode: "Light" }`
- Canvas: 10 desktop screens (1440x900) + 10 mobile screens (393x852) + Lunaris design system component library

## User Stories
`.plans/user-stories/gryphon-draft.md`
- **Total stories:** 23
- **Total acceptance criteria:** 78
- **Consumed by:** `/project:userstorytest-coordinator` for e2e test generation

## Flow Diagrams
`.plans/gryphon-draft-flows.md` (Mermaid diagrams)
- Overall feature map
- Authentication flow
- Draft lifecycle state machine
- Live draft turn flow
- Draft board cell states
- Trade lifecycle state machine
- Trade terminal flow (mobile)
- Sheet import & parsing flow
- Mobile navigation structure
- Desktop navigation structure
- Real-time WebSocket architecture (sequence diagram)

## Design Variable Source
- **Source of truth:** `design/mockup-1.pen` → `get_variables()`
- **Token map:** `.plans/design-token-map.md` (design variable → Tailwind class mapping)
- **Variables used:** Colors (38 variables with Light/Dark themes), Typography (2 font families), Border Radius (3 tokens), Spacing (derived from component analysis)
- **Gaps (fallbacks needed):** None — all required tokens are defined in the Lunaris design system

---

## Component Inventory (TitleCase — matches code names)

### Atoms (existing in Lunaris — reuse all)

| Name | Variants | Pencil ID(s) |
|------|----------|-------------|
| Button | Default, Secondary, Destructive, Outline, Ghost (regular + large) | `ZETEA`, `U83R7`, `ftEoU`, `4x7RU`, `Svd9t`, `ZGI9Z`, `89sf2`, `HXajN`, `EAwax`, `zIDRN` |
| IconButton | Default, Secondary, Destructive, Outline, Ghost (regular + large) | `pEY1B`, `HWbHA`, `ai6BP`, `xQWwZ`, `eNU2w`, `o27Xt`, `vv6Lu`, `o49Ro`, `tzDL1`, `ubB6W` |
| Input | Default, Filled (with group/label variants) | `gKpi4`, `z6HCm`, `592AB`, `URXVp` |
| Select | Default, Filled | `XhJWF`, `mTHMq` |
| Textarea | Default, Filled (with group variant) | `QFzE8`, `oiT6B`, `nvIIa` |
| InputOTP | Default, Filled | `M5Mgn`, `JFrjZ` |
| SearchBox | Default, Filled | `T5yK2`, `Zksub` |
| Avatar | Text, Image | `90SQo`, `4AN1p` |
| Label | Secondary, Success, Violet, Orange (with/without icon) | `it00G`, `7KC5U`, `rjvI1`, `L8Rgv`, `XYdcn`, `Ffti9`, `A58oI`, `7Fif0` |
| Checkbox | Default, Checked (with/without description) | `Wxq1C`, `r91nP`, `VYDf7`, `8zOyn`, `YIw6B`, `5Wp4y` |
| Radio | Default, Selected (with/without description) | `Ao9E1`, `u61z6`, `yoahP`, `20Ebu`, `t3kqz`, `hMm4B` |
| Switch | Default, Checked | `wk1O8`, `zdFKu` |
| Progress | — | `W4YFH` |
| Tooltip | — | `xCEfn` |
| BreadcrumbItem | Default, Active, Separator, Ellipsis | `nW26m`, `mErlM`, `axCNF`, `xzG1l` |
| TabItem | Active, Inactive | `KbyBJ`, `BdBJJ` |
| PaginationItem | Active, Default, Ellipsis | `oT0d2`, `Doslm`, `Irk3I` |
| ListItem | Checked, Unchecked, Title, Divider | `5RtqD`, `Nb9Jh`, `IAQUJ`, `ZIXiw` |
| Alert | Info, Success, Warning, Error | `ITZkn`, `nIj3a`, `vbyqV`, `YZjRF` |
| TableColumnHeader | — | `tbrR4` |
| TableCell | — | `uKYIj` |
| TableRow | — | `T73Cd` |

### Molecules (existing in Lunaris — reuse all)

| Name | Composed Of | Pencil ID(s) |
|------|-------------|-------------|
| Tabs | TabItem/Active + TabItem/Inactive | `Kbr4h` |
| Pagination | PaginationItem[] | `9PVw5` |
| Accordion | Open, Closed | `3bQzF`, `DFcCn` |
| Dropdown | ListItem[], SearchBox, Divider | `cH4wO` |
| SidebarItem | Active, Default | `dOLzc`, `X6nwq` |
| SidebarSectionTitle | — | `h12kK` |

### Organisms (existing in Lunaris — reuse all)

| Name | Composed Of | Pencil ID(s) |
|------|-------------|-------------|
| Card | Header (title + subtitle) + Content + Footer (actions) | `ERkuB` |
| CardImage | Card with image header | `ksvfk` |
| CardAction | Card with action button footer | `wg5F3` |
| CardPlain | Card with stat content, no footer | `eBwLd` |
| Dialog | Card variant with confirm/cancel buttons | `cYAuh` |
| ModalLeft | Left-aligned modal | `izigX` |
| ModalCenter | Center-aligned modal | `5JUG0` |
| ModalCenterIcon | Center modal with icon | `DBtsv` |
| Sidebar | Logo + SectionTitle + SidebarItem[] + user info | `d5ZTS` |
| Table | TableRow[] (slot container) | `pPOgy` |
| DataTable | DataTableHeader + Table + DataTableFooter | `yLiVX` |
| DataTableHeader | SearchBox + actions | `VnGc5` |
| DataTableFooter | Pagination + row count | `j9N2Y` |

### Templates (composed in screen frames)

| Name | Layout | Pencil Screen ID(s) |
|------|--------|-------------------|
| SidebarPageTemplate | 280px Sidebar + fill Content area | `ZsB2h`, `yH6gH`, `uXhCD`, `3T3wC`, `za2G0`, `qZnpu` |
| TopBarPageTemplate | 64px TopBar + fill Content area | `pRa46`, `sj3oL`, `HM809` |
| CenteredCardTemplate | Full-screen background + centered card | `ORirA` |
| MobileTabTemplate | 56px Header + fill Content + 72px TabBar | `zjV2P`, `r8Wt9` |
| MobileHeaderTemplate | 56px Header + fill Content (no tab bar) | `92XvV`, `jui8b`, `KbfS9`, `52jQq`, `bnktV`, `kpEC7` |
| MobileOverlayTemplate | Full-screen with floating reaction bar | `X0qaU` |

### Pages (with state variants — all designed)

| Name | States Designed | Platform | Pencil ID |
|------|----------------|----------|-----------|
| LoginPage | default (dark mode) | Desktop | `ORirA` |
| AdminUserManagement | loaded | Desktop | `ZsB2h` |
| HeadGryphonDashboard | loaded (schedule + quotas) | Desktop | `yH6gH` |
| GryphonDashboard | loaded (stats + upcoming + draft alert) | Desktop | `uXhCD` |
| DraftsListPage | list view with create | Desktop | `3T3wC` |
| DraftLobbyPage | waiting, participants listed | Desktop | `pRa46` |
| LiveDraftPage | active draft with board + reactions | Desktop | `sj3oL` |
| DraftResultsPage | summary + full table | Desktop | `HM809` |
| TradeCenterPage | open/completed tabs | Desktop | `za2G0` |
| ProfilePage | loaded | Desktop | `qZnpu` |
| MobileDashboard | loaded (on-duty, upcoming, draft) | Mobile | `zjV2P` |
| MobileMyShifts | loaded (quotas + stats) | Mobile | `r8Wt9` |
| MobileCommenceDraft | config form | Mobile | `92XvV` |
| MobileDraftLobby | countdown + participants | Mobile | `jui8b` |
| MobileDraftPortal | live (picker + timer + reactions) | Mobile | `KbfS9` |
| MobileLiveDraftGrid | calendar grid + floating reactions | Mobile | `X0qaU` |
| MobileMyShiftsTrade | shift cards with trade buttons | Mobile | `z1RRi` |
| MobileTradeTerminalStep1 | select shift (radio) | Mobile | `52jQq` |
| MobileTradeTerminalStep2 | choose method (broadcast/direct) | Mobile | `bnktV` |
| MobileTradeBoard | open trades + proposals | Mobile | `kpEC7` |

---

## Design-to-Code Mapping (ready for view-coordinator)

These TitleCase names map 1:1 to code components. The view-coordinator reads designs via `batch_get` (Pencil):

### Atoms → `src/components/atoms/`

| Design Component | Code Path | Pencil Ref |
|------------------|-----------|------------|
| Button | `src/components/atoms/Button/` | `ZETEA` (+ variants) |
| IconButton | `src/components/atoms/IconButton/` | `pEY1B` (+ variants) |
| Input | `src/components/atoms/Input/` | `gKpi4` |
| Select | `src/components/atoms/Select/` | `XhJWF` |
| Textarea | `src/components/atoms/Textarea/` | `QFzE8` |
| SearchBox | `src/components/atoms/SearchBox/` | `T5yK2` |
| Avatar | `src/components/atoms/Avatar/` | `90SQo` |
| Label | `src/components/atoms/Label/` | `it00G` (+ variants) |
| Checkbox | `src/components/atoms/Checkbox/` | `Wxq1C` |
| Radio | `src/components/atoms/Radio/` | `Ao9E1` |
| Switch | `src/components/atoms/Switch/` | `wk1O8` |
| Progress | `src/components/atoms/Progress/` | `W4YFH` |
| Tooltip | `src/components/atoms/Tooltip/` | `xCEfn` |
| Alert | `src/components/atoms/Alert/` | `ITZkn` (+ variants) |
| TabItem | `src/components/atoms/TabItem/` | `KbyBJ` |
| PaginationItem | `src/components/atoms/PaginationItem/` | `oT0d2` |

### Molecules → `src/components/molecules/`

| Design Component | Code Path | Pencil Ref |
|------------------|-----------|------------|
| Tabs | `src/components/molecules/Tabs/` | `Kbr4h` |
| Pagination | `src/components/molecules/Pagination/` | `9PVw5` |
| Accordion | `src/components/molecules/Accordion/` | `3bQzF` |
| Dropdown | `src/components/molecules/Dropdown/` | `cH4wO` |
| SidebarItem | `src/components/molecules/SidebarItem/` | `dOLzc` |
| BreadcrumbItem | `src/components/molecules/BreadcrumbItem/` | `nW26m` |

### Organisms → `src/components/organisms/`

| Design Component | Code Path | Pencil Ref |
|------------------|-----------|------------|
| Card | `src/components/organisms/Card/` | `ERkuB` |
| Dialog | `src/components/organisms/Dialog/` | `cYAuh` |
| Modal | `src/components/organisms/Modal/` | `izigX` |
| Sidebar | `src/components/organisms/Sidebar/` | `d5ZTS` |
| DataTable | `src/components/organisms/DataTable/` | `yLiVX` |
| Table | `src/components/organisms/Table/` | `pPOgy` |

### Feature Components (custom — not in design system)

| Design Component | Code Path | Description |
|------------------|-----------|-------------|
| DraftBoard | `src/features/draft/DraftBoard/` | 9-column shift grid with cell states |
| DraftTopBar | `src/features/draft/DraftTopBar/` | Turn indicator, timer, progress, pause |
| QuotaSidebar | `src/features/draft/QuotaSidebar/` | Weekday/weekend progress per Gryphon |
| ReactionBar | `src/features/draft/ReactionBar/` | Emoji picker + floating animations |
| DraftCell | `src/features/draft/DraftCell/` | Available/picked/pre-filled/selected states |
| ShiftCard | `src/features/shifts/ShiftCard/` | Mobile shift display with trade button |
| TradeCard | `src/features/trades/TradeCard/` | Trade proposal display with accept/decline |
| StatCard | `src/features/dashboard/StatCard/` | Dashboard stat (CardPlain pattern) |
| ScheduleCalendar | `src/features/schedule/ScheduleCalendar/` | Week-by-week calendar view |
| MobileTabBar | `src/components/organisms/MobileTabBar/` | Bottom 4-tab navigation |

---

## Open Design Questions

- [ ] **Auto-pick behavior:** What happens when the timer expires? Random available shift? Skip turn? Best available by preference?
- [ ] **Trade expiry window:** 24h? 48h? Configurable by Head Gryphon?
- [ ] **Loading states:** Only "loaded" states are designed in the mockup. Loading skeletons, empty states, and error states need design iteration.
- [ ] **Responsive breakpoints:** The PRD mentions tablet (768px) but no tablet mockups exist. Need design for tablet breakpoints.
- [ ] **Dark/Light toggle:** The mockup defaults to Dark theme. Where is the theme toggle exposed in the UI? Profile settings? System preference?
- [ ] **Accessibility audit:** Color contrast ratios need verification for both themes, particularly `--muted-foreground` (#666666 on #F2F3F0 in Light mode).
- [ ] **Empty states:** No "no data" illustrations or messages are designed for: empty drafts list, no trades, no shifts, no users.
- [ ] **Confirmation dialogs:** The Dialog component exists but specific confirmation flows (delete user, cancel draft, accept trade) need content design.
- [ ] **Draft board scroll behavior:** How does the 9-column x 17-week grid scroll on mobile (393px wide)? Horizontal scroll? Pinch-zoom?
- [ ] **Notification bell behavior:** Mobile dashboard shows notification bell icon — what's the notification panel design?

---

## Prototype Location
- **Design file:** `design/mockup-1.pen` (open in Pencil desktop app)
- **Handoff document:** `.plans/gryphon-draft-ux-handoff.md` (this file)
- **Token map:** `.plans/design-token-map.md`
- **User stories:** `.plans/user-stories/gryphon-draft.md`
- **Flow diagrams:** `.plans/gryphon-draft-flows.md`
