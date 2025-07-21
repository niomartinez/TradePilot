# Design Plan - CopyTrade V2 Frontend

## Table of Contents
1. [Design Philosophy](#design-philosophy)
2. [Visual Identity](#visual-identity)
3. [Design System](#design-system)
4. [Component Library](#component-library)
5. [Page Layouts](#page-layouts)
6. [Responsive Design](#responsive-design)
7. [Interaction Patterns](#interaction-patterns)
8. [Accessibility Guidelines](#accessibility-guidelines)
9. [Animation & Motion](#animation--motion)
10. [Implementation Guidelines](#implementation-guidelines)

## Design Philosophy

### Core Principles

#### 1. **Trust Through Transparency**
- Clear data visualization
- No hidden information
- Real-time updates visible
- Performance metrics prominent

#### 2. **Simplicity in Complexity**
- Progressive disclosure
- Smart defaults
- Guided experiences
- Context-aware help

#### 3. **Web3 Native**
- Modern crypto aesthetics
- Dark mode first
- Neon accents
- Glass morphism elements

#### 4. **Performance Focused**
- Data-dense displays
- Efficient layouts
- Quick actions
- Minimal clicks

#### 5. **Mobile Excellence**
- Touch-friendly targets
- Swipe gestures
- Bottom navigation
- Thumb-zone optimization

## Visual Identity

### Brand Personality
- **Professional**: Serious about trading
- **Modern**: Cutting-edge technology
- **Trustworthy**: Secure and reliable
- **Accessible**: Welcoming to beginners
- **Dynamic**: Real-time and responsive

### Logo Design
```
Primary Logo:
╔═══════════════════════════╗
║   [CT]  CopyTrade        ║
║   ████  ▀▀▀▀▀▀▀▀        ║
╚═══════════════════════════╝

Icon Only:
╔═════╗
║ [CT]║
║ ████║
╚═════╝
```

### Color Palette

#### Primary Colors
```scss
// Brand Colors
$primary-green: #00D4AA;      // Success, profits, long positions
$primary-red: #FF3B69;        // Losses, short positions, warnings
$primary-blue: #4A90FF;       // Links, CTAs, information
$primary-purple: #9B59FF;     // Premium features, achievements

// Neutral Colors
$gray-900: #0A0E17;           // Primary background
$gray-800: #141922;           // Card backgrounds
$gray-700: #1E2530;           // Borders, dividers
$gray-600: #2A3441;           // Hover states
$gray-500: #3E4A5C;           // Disabled states
$gray-400: #5A6779;           // Muted text
$gray-300: #7A8599;           // Secondary text
$gray-200: #9DA7B8;           // Primary text
$gray-100: #C5CDD9;           // High contrast text
$white: #FFFFFF;              // Pure white for emphasis

// Semantic Colors
$success: #00D4AA;
$warning: #FFB84D;
$error: #FF3B69;
$info: #4A90FF;

// Gradient Definitions
$gradient-profit: linear-gradient(135deg, #00D4AA 0%, #00A584 100%);
$gradient-loss: linear-gradient(135deg, #FF3B69 0%, #CC2E54 100%);
$gradient-premium: linear-gradient(135deg, #9B59FF 0%, #7B3FDB 100%);
$gradient-dark: linear-gradient(180deg, #0A0E17 0%, #141922 100%);
```

#### Dark Mode (Default)
```scss
// Backgrounds
$bg-primary: #0A0E17;
$bg-secondary: #141922;
$bg-tertiary: #1E2530;
$bg-overlay: rgba(10, 14, 23, 0.8);

// Glass Morphism
$glass-bg: rgba(20, 25, 34, 0.6);
$glass-border: rgba(255, 255, 255, 0.1);
$glass-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
```

#### Light Mode (Optional)
```scss
// Inverted color scheme for day traders
$light-bg-primary: #FFFFFF;
$light-bg-secondary: #F8F9FA;
$light-bg-tertiary: #E9ECEF;
$light-text-primary: #0A0E17;
```

### Typography

#### Font Stack
```scss
// Primary Font - Inter
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;900&display=swap');

// Monospace Font - JetBrains Mono
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600&display=swap');

// Font Variables
$font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
$font-mono: 'JetBrains Mono', 'Monaco', 'Courier New', monospace;
```

#### Type Scale
```scss
// Headings
$h1: 3rem;      // 48px - Page titles
$h2: 2.25rem;   // 36px - Section headers
$h3: 1.875rem;  // 30px - Card titles
$h4: 1.5rem;    // 24px - Subsections
$h5: 1.25rem;   // 20px - Labels
$h6: 1.125rem;  // 18px - Small headers

// Body
$body-lg: 1.125rem;  // 18px - Important text
$body-md: 1rem;      // 16px - Default
$body-sm: 0.875rem;  // 14px - Secondary
$body-xs: 0.75rem;   // 12px - Captions

// Line Heights
$line-height-tight: 1.2;
$line-height-normal: 1.5;
$line-height-relaxed: 1.75;

// Font Weights
$font-normal: 400;
$font-medium: 500;
$font-semibold: 600;
$font-bold: 700;
$font-black: 900;
```

### Spacing System
```scss
// Base unit: 4px
$space-0: 0;
$space-1: 0.25rem;   // 4px
$space-2: 0.5rem;    // 8px
$space-3: 0.75rem;   // 12px
$space-4: 1rem;      // 16px
$space-5: 1.25rem;   // 20px
$space-6: 1.5rem;    // 24px
$space-8: 2rem;      // 32px
$space-10: 2.5rem;   // 40px
$space-12: 3rem;     // 48px
$space-16: 4rem;     // 64px
$space-20: 5rem;     // 80px
```

## Design System

### Grid System
```scss
// Container Widths
$container-sm: 640px;
$container-md: 768px;
$container-lg: 1024px;
$container-xl: 1280px;
$container-2xl: 1536px;

// Grid Configuration
$grid-columns: 12;
$grid-gap: $space-4;
$grid-margin: $space-4;

// Breakpoints
$breakpoint-sm: 640px;
$breakpoint-md: 768px;
$breakpoint-lg: 1024px;
$breakpoint-xl: 1280px;
$breakpoint-2xl: 1536px;
```

### Component Principles

#### 1. **Glass Morphism Cards**
```scss
.glass-card {
  background: rgba(20, 25, 34, 0.6);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
}
```

#### 2. **Neon Accents**
```scss
.neon-glow {
  box-shadow: 
    0 0 20px rgba(0, 212, 170, 0.5),
    inset 0 0 20px rgba(0, 212, 170, 0.1);
}

.neon-text {
  text-shadow: 
    0 0 10px rgba(0, 212, 170, 0.8),
    0 0 20px rgba(0, 212, 170, 0.6),
    0 0 30px rgba(0, 212, 170, 0.4);
}
```

#### 3. **Gradient Borders**
```scss
.gradient-border {
  position: relative;
  background: $bg-secondary;
  border-radius: 12px;
  
  &::before {
    content: '';
    position: absolute;
    inset: -2px;
    border-radius: 12px;
    padding: 2px;
    background: $gradient-profit;
    -webkit-mask: 
      linear-gradient(#fff 0 0) content-box, 
      linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
  }
}
```

## Component Library

### 1. Buttons

#### Primary Button
```tsx
// Gradient background with hover effects
<Button variant="primary" size="lg">
  Start Copy Trading
</Button>

// CSS
.btn-primary {
  background: $gradient-profit;
  color: $white;
  padding: $space-3 $space-6;
  border-radius: 8px;
  font-weight: $font-semibold;
  transition: all 0.2s ease;
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 20px rgba(0, 212, 170, 0.4);
  }
}
```

#### Secondary Button
```tsx
<Button variant="secondary" size="md">
  View Details
</Button>

// CSS
.btn-secondary {
  background: transparent;
  color: $primary-blue;
  border: 1px solid $primary-blue;
  
  &:hover {
    background: rgba(74, 144, 255, 0.1);
    border-color: lighten($primary-blue, 10%);
  }
}
```

#### Icon Button
```tsx
<IconButton icon={<Settings />} label="Settings" />

// CSS
.btn-icon {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: $bg-tertiary;
  border-radius: 8px;
  
  svg {
    width: 20px;
    height: 20px;
    color: $gray-300;
  }
}
```

### 2. Cards

#### Trader Card
```tsx
<TraderCard
  avatar="/trader1.jpg"
  name="Alex Chen"
  winRate={68.5}
  monthlyReturn={24.3}
  copiers={1284}
  verified={true}
/>

// Layout
.trader-card {
  @extend .glass-card;
  padding: $space-5;
  display: grid;
  gap: $space-4;
  
  .header {
    display: flex;
    align-items: center;
    gap: $space-3;
    
    .avatar {
      width: 56px;
      height: 56px;
      border-radius: 12px;
      border: 2px solid $primary-green;
    }
    
    .info {
      flex: 1;
      
      .name {
        font-size: $h5;
        font-weight: $font-semibold;
        color: $gray-100;
      }
      
      .badge {
        display: inline-flex;
        align-items: center;
        gap: $space-1;
        padding: $space-1 $space-2;
        background: rgba(0, 212, 170, 0.2);
        color: $primary-green;
        border-radius: 4px;
        font-size: $body-xs;
      }
    }
  }
  
  .stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: $space-3;
    
    .stat {
      text-align: center;
      
      .value {
        font-size: $h4;
        font-weight: $font-bold;
        color: $gray-100;
      }
      
      .label {
        font-size: $body-sm;
        color: $gray-400;
        margin-top: $space-1;
      }
    }
  }
}
```

#### Position Card
```tsx
<PositionCard
  symbol="BTC/USDT"
  side="long"
  entryPrice={45230}
  currentPrice={46150}
  pnl={920}
  pnlPercent={2.03}
/>

// Layout
.position-card {
  @extend .glass-card;
  padding: $space-4;
  
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: $space-3;
    
    .symbol {
      font-size: $h5;
      font-weight: $font-semibold;
      color: $gray-100;
    }
    
    .side {
      padding: $space-1 $space-3;
      border-radius: 4px;
      font-size: $body-sm;
      font-weight: $font-medium;
      
      &.long {
        background: rgba(0, 212, 170, 0.2);
        color: $primary-green;
      }
      
      &.short {
        background: rgba(255, 59, 105, 0.2);
        color: $primary-red;
      }
    }
  }
  
  .metrics {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: $space-3;
    
    .metric {
      .label {
        font-size: $body-sm;
        color: $gray-400;
        margin-bottom: $space-1;
      }
      
      .value {
        font-size: $body-lg;
        font-weight: $font-semibold;
        color: $gray-100;
        font-family: $font-mono;
      }
    }
  }
  
  .pnl {
    margin-top: $space-3;
    padding-top: $space-3;
    border-top: 1px solid $gray-700;
    display: flex;
    justify-content: space-between;
    align-items: center;
    
    .label {
      font-size: $body-sm;
      color: $gray-400;
    }
    
    .value {
      font-size: $h5;
      font-weight: $font-bold;
      
      &.profit {
        color: $primary-green;
      }
      
      &.loss {
        color: $primary-red;
      }
    }
  }
}
```

### 3. Form Elements

#### Input Field
```tsx
<Input
  label="Email Address"
  type="email"
  placeholder="trader@example.com"
  icon={<Mail />}
/>

// CSS
.input-group {
  margin-bottom: $space-4;
  
  .label {
    display: block;
    font-size: $body-sm;
    color: $gray-300;
    margin-bottom: $space-2;
    font-weight: $font-medium;
  }
  
  .input-wrapper {
    position: relative;
    
    .icon {
      position: absolute;
      left: $space-3;
      top: 50%;
      transform: translateY(-50%);
      color: $gray-500;
    }
    
    input {
      width: 100%;
      padding: $space-3 $space-4;
      padding-left: $space-10;
      background: $bg-tertiary;
      border: 1px solid $gray-700;
      border-radius: 8px;
      color: $gray-100;
      font-size: $body-md;
      
      &:focus {
        outline: none;
        border-color: $primary-blue;
        box-shadow: 0 0 0 3px rgba(74, 144, 255, 0.1);
      }
      
      &::placeholder {
        color: $gray-500;
      }
    }
  }
}
```

#### Select Dropdown
```tsx
<Select
  label="Trading Pair"
  options={tradingPairs}
  value={selectedPair}
  onChange={setSelectedPair}
/>

// CSS
.select-group {
  .select-wrapper {
    position: relative;
    
    select {
      appearance: none;
      width: 100%;
      padding: $space-3 $space-12 $space-3 $space-4;
      background: $bg-tertiary;
      border: 1px solid $gray-700;
      border-radius: 8px;
      color: $gray-100;
      cursor: pointer;
      
      &:focus {
        outline: none;
        border-color: $primary-blue;
      }
    }
    
    .chevron {
      position: absolute;
      right: $space-3;
      top: 50%;
      transform: translateY(-50%);
      pointer-events: none;
      color: $gray-500;
    }
  }
}
```

#### Toggle Switch
```tsx
<Toggle
  label="Enable Notifications"
  checked={notificationsEnabled}
  onChange={setNotificationsEnabled}
/>

// CSS
.toggle {
  display: flex;
  align-items: center;
  gap: $space-3;
  
  .switch {
    position: relative;
    width: 48px;
    height: 24px;
    background: $gray-700;
    border-radius: 12px;
    cursor: pointer;
    transition: background 0.2s ease;
    
    &.checked {
      background: $primary-green;
    }
    
    .slider {
      position: absolute;
      top: 2px;
      left: 2px;
      width: 20px;
      height: 20px;
      background: $white;
      border-radius: 10px;
      transition: transform 0.2s ease;
      
      &.checked {
        transform: translateX(24px);
      }
    }
  }
  
  .label {
    font-size: $body-md;
    color: $gray-200;
  }
}
```

### 4. Data Display

#### Table Component
```tsx
<DataTable
  columns={[
    { key: 'symbol', label: 'Symbol', sortable: true },
    { key: 'side', label: 'Side', width: 100 },
    { key: 'entry', label: 'Entry Price', align: 'right' },
    { key: 'pnl', label: 'P&L', align: 'right', highlight: true }
  ]}
  data={positions}
/>

// CSS
.data-table {
  width: 100%;
  background: $bg-secondary;
  border-radius: 12px;
  overflow: hidden;
  
  thead {
    background: $bg-tertiary;
    
    th {
      padding: $space-3 $space-4;
      text-align: left;
      font-size: $body-sm;
      color: $gray-400;
      font-weight: $font-medium;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      
      &.sortable {
        cursor: pointer;
        
        &:hover {
          color: $gray-300;
        }
      }
    }
  }
  
  tbody {
    tr {
      border-bottom: 1px solid $gray-700;
      
      &:hover {
        background: rgba(255, 255, 255, 0.02);
      }
      
      td {
        padding: $space-4;
        font-size: $body-md;
        color: $gray-200;
        
        &.highlight {
          font-weight: $font-semibold;
          
          &.positive {
            color: $primary-green;
          }
          
          &.negative {
            color: $primary-red;
          }
        }
      }
    }
  }
}
```

#### Chart Component
```tsx
<LineChart
  data={performanceData}
  height={300}
  showGrid={true}
  gradient={true}
/>

// Configuration
.chart-container {
  background: $bg-secondary;
  border-radius: 12px;
  padding: $space-4;
  
  .chart-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: $space-4;
    
    .title {
      font-size: $h5;
      font-weight: $font-semibold;
      color: $gray-100;
    }
    
    .timeframe-selector {
      display: flex;
      gap: $space-2;
      
      button {
        padding: $space-1 $space-3;
        background: transparent;
        border: 1px solid $gray-700;
        border-radius: 4px;
        color: $gray-400;
        font-size: $body-sm;
        
        &.active {
          background: $primary-blue;
          border-color: $primary-blue;
          color: $white;
        }
      }
    }
  }
}
```

### 5. Navigation

#### Top Navigation
```tsx
<TopNav>
  <Logo />
  <NavLinks>
    <NavLink href="/dashboard" active>Dashboard</NavLink>
    <NavLink href="/traders">Traders</NavLink>
    <NavLink href="/portfolio">Portfolio</NavLink>
  </NavLinks>
  <UserMenu />
</TopNav>

// CSS
.top-nav {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(10, 14, 23, 0.8);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid $gray-700;
  
  .nav-container {
    max-width: $container-2xl;
    margin: 0 auto;
    padding: 0 $space-4;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .nav-links {
    display: flex;
    gap: $space-8;
    
    a {
      color: $gray-400;
      font-weight: $font-medium;
      transition: color 0.2s ease;
      
      &:hover {
        color: $gray-100;
      }
      
      &.active {
        color: $primary-blue;
      }
    }
  }
}
```

#### Mobile Bottom Navigation
```tsx
<BottomNav>
  <NavItem icon={<Home />} label="Home" active />
  <NavItem icon={<TrendingUp />} label="Traders" />
  <NavItem icon={<Briefcase />} label="Portfolio" />
  <NavItem icon={<User />} label="Profile" />
</BottomNav>

// CSS
.bottom-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: $bg-secondary;
  border-top: 1px solid $gray-700;
  padding: $space-2 0;
  z-index: 100;
  
  @media (min-width: $breakpoint-md) {
    display: none;
  }
  
  .nav-items {
    display: flex;
    justify-content: space-around;
    
    .nav-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: $space-1;
      padding: $space-2;
      color: $gray-500;
      
      &.active {
        color: $primary-blue;
      }
      
      .icon {
        width: 24px;
        height: 24px;
      }
      
      .label {
        font-size: $body-xs;
      }
    }
  }
}
```

## Page Layouts

### 1. Dashboard Layout
```
┌─────────────────────────────────────────────────┐
│                  Top Navigation                  │
├─────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌──────────────────────────┐ │
│  │   Welcome    │  │    Quick Stats Cards     │ │
│  │   Message    │  └──────────────────────────┘ │
│  └─────────────┘                                │
│  ┌─────────────────────┐  ┌──────────────────┐ │
│  │                     │  │                  │ │
│  │   P&L Chart        │  │  Active Trades   │ │
│  │                     │  │                  │ │
│  └─────────────────────┘  └──────────────────┘ │
│  ┌─────────────────────────────────────────────┐│
│  │           Recent Activity Feed              ││
│  └─────────────────────────────────────────────┘│
└─────────────────────────────────────────────────┘
```

### 2. Trader Profile Layout
```
┌─────────────────────────────────────────────────┐
│                  Top Navigation                  │
├─────────────────────────────────────────────────┤
│  ┌──────────────────┐  ┌────────────────────┐  │
│  │   Trader Header   │  │   Follow Button   │  │
│  │   Avatar + Info   │  │   Stats Overview  │  │
│  └──────────────────┘  └────────────────────┘  │
│  ┌─────────────────────────────────────────────┐│
│  │               Tab Navigation                 ││
│  │  Performance | Trades | About | Reviews      ││
│  └─────────────────────────────────────────────┘│
│  ┌─────────────────────────────────────────────┐│
│  │                Tab Content                   ││
│  │         (Charts, Tables, Text)              ││
│  └─────────────────────────────────────────────┘│
└─────────────────────────────────────────────────┘
```

### 3. Mobile Layout Adaptation
```
Mobile (< 768px)             Tablet (768px - 1024px)
┌─────────────────┐          ┌──────────────────────┐
│   Simplified    │          │   2-Column Layout    │
│   Navigation    │          │                      │
├─────────────────┤          ├──────────┬───────────┤
│                 │          │          │           │
│  Single Column  │          │  Main    │  Sidebar  │
│    Content      │          │  Content │  Content  │
│                 │          │          │           │
├─────────────────┤          └──────────┴───────────┘
│  Bottom Nav     │
└─────────────────┘
```

## Responsive Design

### Breakpoint Strategy
```scss
// Mobile First Approach
@mixin respond-to($breakpoint) {
  @if $breakpoint == 'sm' {
    @media (min-width: #{$breakpoint-sm}) { @content; }
  }
  @else if $breakpoint == 'md' {
    @media (min-width: #{$breakpoint-md}) { @content; }
  }
  @else if $breakpoint == 'lg' {
    @media (min-width: #{$breakpoint-lg}) { @content; }
  }
  @else if $breakpoint == 'xl' {
    @media (min-width: #{$breakpoint-xl}) { @content; }
  }
}
```

### Component Adaptations

#### Cards
```scss
.card-grid {
  display: grid;
  gap: $space-4;
  grid-template-columns: 1fr;
  
  @include respond-to('md') {
    grid-template-columns: repeat(2, 1fr);
  }
  
  @include respond-to('lg') {
    grid-template-columns: repeat(3, 1fr);
  }
  
  @include respond-to('xl') {
    grid-template-columns: repeat(4, 1fr);
  }
}
```

#### Tables
```scss
// Mobile: Card View
@media (max-width: #{$breakpoint-md - 1px}) {
  .data-table {
    thead {
      display: none;
    }
    
    tbody {
      tr {
        display: block;
        margin-bottom: $space-3;
        background: $bg-tertiary;
        border-radius: 8px;
        padding: $space-3;
        
        td {
          display: flex;
          justify-content: space-between;
          padding: $space-2 0;
          
          &:before {
            content: attr(data-label);
            font-weight: $font-medium;
            color: $gray-400;
          }
        }
      }
    }
  }
}
```

## Interaction Patterns

### Hover States
```scss
// Consistent hover feedback
@mixin hover-lift {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
  }
}

@mixin hover-glow($color) {
  transition: box-shadow 0.2s ease;
  
  &:hover {
    box-shadow: 0 0 20px rgba($color, 0.3);
  }
}
```

### Loading States
```tsx
// Skeleton Loading
<Skeleton height={200} />

// CSS
.skeleton {
  background: $bg-tertiary;
  border-radius: 8px;
  position: relative;
  overflow: hidden;
  
  &::after {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(255, 255, 255, 0.05),
      transparent
    );
    animation: shimmer 2s infinite;
  }
}

@keyframes shimmer {
  100% {
    left: 100%;
  }
}
```

### Transitions
```scss
// Page Transitions
.page-enter {
  opacity: 0;
  transform: translateY(20px);
}

.page-enter-active {
  opacity: 1;
  transform: translateY(0);
  transition: opacity 0.3s ease, transform 0.3s ease;
}

// Modal Transitions
.modal-backdrop {
  transition: opacity 0.2s ease;
}

.modal-content {
  transition: transform 0.2s ease, opacity 0.2s ease;
}
```

### Gesture Support
```tsx
// Swipe to refresh
const [refreshing, setRefreshing] = useState(false);

<SwipeableView
  onRefresh={() => {
    setRefreshing(true);
    fetchLatestData();
  }}
>
  {/* Content */}
</SwipeableView>

// Pull to close
<BottomSheet
  onSwipeDown={() => closeSheet()}
  snapPoints={[0, 300, 600]}
>
  {/* Sheet content */}
</BottomSheet>
```

## Accessibility Guidelines

### Color Contrast
- Text on background: minimum 4.5:1 ratio
- Large text: minimum 3:1 ratio
- Interactive elements: minimum 3:1 ratio
- Use color + icon/pattern for critical information

### Keyboard Navigation
```scss
// Focus indicators
:focus-visible {
  outline: 2px solid $primary-blue;
  outline-offset: 2px;
}

// Skip links
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: $primary-blue;
  color: $white;
  padding: $space-2 $space-4;
  z-index: 1000;
  
  &:focus {
    top: 0;
  }
}
```

### Screen Reader Support
```tsx
// Proper ARIA labels
<button aria-label="Follow trader Alex Chen">
  Follow
</button>

// Live regions for updates
<div aria-live="polite" aria-atomic="true">
  {tradeNotification}
</div>

// Form associations
<label htmlFor="email">Email Address</label>
<input id="email" type="email" />
```

### Touch Targets
- Minimum size: 44x44px
- Spacing between targets: 8px minimum
- Clear hit areas for all interactive elements

## Animation & Motion

### Animation Principles
1. **Purpose**: Every animation has meaning
2. **Performance**: 60fps on all devices
3. **Subtlety**: Enhance, don't distract
4. **Consistency**: Same easing functions

### Easing Functions
```scss
$ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
$ease-out: cubic-bezier(0.0, 0, 0.2, 1);
$ease-in: cubic-bezier(0.4, 0, 1, 1);
$spring: cubic-bezier(0.175, 0.885, 0.32, 1.275);
```

### Common Animations
```scss
// Fade In
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

// Scale In
@keyframes scaleIn {
  from { 
    opacity: 0;
    transform: scale(0.9);
  }
  to { 
    opacity: 1;
    transform: scale(1);
  }
}

// Slide Up
@keyframes slideUp {
  from { 
    opacity: 0;
    transform: translateY(20px);
  }
  to { 
    opacity: 1;
    transform: translateY(0);
  }
}

// Pulse (for notifications)
@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.05); }
  100% { transform: scale(1); }
}
```

### Micro-interactions
```scss
// Button press
.button {
  transition: all 0.1s ease;
  
  &:active {
    transform: scale(0.98);
  }
}

// Toggle switch
.toggle-slider {
  transition: transform 0.2s $ease-out;
}

// Tab indicator
.tab-indicator {
  transition: transform 0.3s $ease-out, width 0.3s $ease-out;
}
```

### Loading Animations
```tsx
// Spinner
<div className="spinner">
  <div className="spinner-blade" />
  <div className="spinner-blade" />
  <div className="spinner-blade" />
</div>

// CSS
.spinner {
  width: 40px;
  height: 40px;
  position: relative;
  animation: spin 1s linear infinite;
  
  .spinner-blade {
    position: absolute;
    width: 4px;
    height: 12px;
    background: $primary-blue;
    border-radius: 2px;
    transform-origin: center bottom;
    
    &:nth-child(1) { transform: rotate(0deg); }
    &:nth-child(2) { transform: rotate(120deg); }
    &:nth-child(3) { transform: rotate(240deg); }
  }
}
```

## Implementation Guidelines

### Component Structure
```tsx
// Example component structure
components/
  ├── ui/                    # Base UI components
  │   ├── Button/
  │   │   ├── Button.tsx
  │   │   ├── Button.module.scss
  │   │   └── Button.test.tsx
  │   ├── Card/
  │   ├── Input/
  │   └── Modal/
  ├── trading/              # Trading-specific components
  │   ├── TraderCard/
  │   ├── PositionCard/
  │   └── OrderBook/
  └── layout/              # Layout components
      ├── Header/
      ├── Sidebar/
      └── Footer/
```

### Styling Approach
```tsx
// CSS Modules for component styles
import styles from './Button.module.scss';

// Tailwind for utility classes
<div className="flex items-center gap-4">

// CSS-in-JS for dynamic styles
const dynamicStyles = {
  color: isProfitable ? '#00D4AA' : '#FF3B69',
  fontSize: `${scale}rem`
};
```

### Theme Implementation
```tsx
// Theme provider setup
<ThemeProvider theme={darkTheme}>
  <App />
</ThemeProvider>

// Theme object
const darkTheme = {
  colors: {
    background: {
      primary: '#0A0E17',
      secondary: '#141922',
      tertiary: '#1E2530'
    },
    text: {
      primary: '#C5CDD9',
      secondary: '#7A8599',
      muted: '#5A6779'
    },
    brand: {
      primary: '#00D4AA',
      secondary: '#4A90FF'
    }
  },
  spacing: {
    xs: '0.25rem',
    sm: '0.5rem',
    md: '1rem',
    lg: '1.5rem',
    xl: '2rem'
  }
};
```

### Performance Optimization
```tsx
// Lazy load heavy components
const TradingChart = lazy(() => import('./TradingChart'));

// Memoize expensive renders
const TraderList = memo(({ traders }) => {
  return traders.map(trader => (
    <TraderCard key={trader.id} {...trader} />
  ));
});

// Virtual scrolling for long lists
<VirtualList
  height={600}
  itemCount={trades.length}
  itemSize={80}
  renderItem={({ index }) => <TradeRow trade={trades[index]} />}
/>
```

### Design Tokens
```json
{
  "color": {
    "brand": {
      "primary": "#00D4AA",
      "primary-dark": "#00A584",
      "primary-light": "#33DDBB"
    },
    "semantic": {
      "success": "#00D4AA",
      "warning": "#FFB84D",
      "error": "#FF3B69",
      "info": "#4A90FF"
    }
  },
  "typography": {
    "fontFamily": {
      "sans": "Inter, -apple-system, sans-serif",
      "mono": "JetBrains Mono, monospace"
    },
    "fontSize": {
      "xs": "0.75rem",
      "sm": "0.875rem",
      "base": "1rem",
      "lg": "1.125rem",
      "xl": "1.25rem",
      "2xl": "1.5rem",
      "3xl": "1.875rem",
      "4xl": "2.25rem",
      "5xl": "3rem"
    }
  },
  "spacing": {
    "0": "0",
    "1": "0.25rem",
    "2": "0.5rem",
    "3": "0.75rem",
    "4": "1rem",
    "5": "1.25rem",
    "6": "1.5rem",
    "8": "2rem",
    "10": "2.5rem",
    "12": "3rem",
    "16": "4rem",
    "20": "5rem",
    "24": "6rem",
    "32": "8rem"
  },
  "borderRadius": {
    "none": "0",
    "sm": "0.25rem",
    "base": "0.5rem",
    "md": "0.75rem",
    "lg": "1rem",
    "xl": "1.5rem",
    "full": "9999px"
  },
  "shadow": {
    "sm": "0 1px 2px 0 rgba(0, 0, 0, 0.05)",
    "base": "0 1px 3px 0 rgba(0, 0, 0, 0.1)",
    "md": "0 4px 6px -1px rgba(0, 0, 0, 0.1)",
    "lg": "0 10px 15px -3px rgba(0, 0, 0, 0.1)",
    "xl": "0 20px 25px -5px rgba(0, 0, 0, 0.1)",
    "2xl": "0 25px 50px -12px rgba(0, 0, 0, 0.25)",
    "inner": "inset 0 2px 4px 0 rgba(0, 0, 0, 0.06)"
  }
}
```

---

This design plan provides a comprehensive guide for creating a modern, user-friendly, and visually appealing crypto trading platform. The dark theme with neon accents creates a professional yet exciting atmosphere, while the focus on usability ensures traders of all levels can navigate the platform effectively.