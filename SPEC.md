# Shopee Reseller AI - Spesifikasi Aplikasi

## 1. Concept & Vision

**ShopeeReseller AI** - Aplikasi asisten AI untuk para reseller Shopee Indonesia. Memberikan pengalaman "jualan smarter, bukan harder" dengan fitur-fitur yang membantu menemukan produk profitable, membuat listing menarik, dan mengelola toko dengan efisien. Desainnya playful tapi profesional - orange Shopee meets modern fintech aesthetic dengan sentuhan playful yang membuat jualan terasa fun.

## 2. Design Language

### Aesthetic Direction
**"Playful Profit"** - Kombinasi energi marketplace Shopee dengan keseriusan tools bisnis. Bold, vibrant, tapi tetap clean dan organized. Terinspirasi dari fintech apps yang successful dengan sentuhan playfulness.

### Color Palette
- **Primary**: `#EE4D2D` (Shopee Orange)
- **Secondary**: `#F5A623` (Warm Gold)
- **Accent**: `#2D3436` (Dark Charcoal)
- **Background**: `#FFF9F5` (Warm Cream)
- **Card BG**: `#FFFFFF` (Pure White)
- **Success**: `#00C853` (Profit Green)
- **Text Primary**: `#2D3436`
- **Text Secondary**: `#636E72`

### Typography
- **Headlines**: "Plus Jakarta Sans" (800 weight) - Bold, modern, distinctive
- **Body**: "Plus Jakarta Sans" (400, 500 weight)
- **Accent/Numbers**: "Space Grotesk" (700) - Untuk profit numbers dan metrics

### Spatial System
- Base unit: 8px
- Container max-width: 1200px
- Card padding: 24px
- Gap between cards: 16px
- Border radius: 16px (cards), 12px (buttons), 8px (inputs)

### Motion Philosophy
- Entrance animations: fade-up dengan stagger 50ms
- Hover: scale(1.02) dengan shadow elevation
- Loading: skeleton pulse animation
- Success states: confetti burst effect
- Transitions: 300ms cubic-bezier(0.4, 0, 0.2, 1)

### Visual Assets
- Icons: Lucide icons
- Decorative: Gradient blobs, subtle grid pattern background
- Product images: Placeholder dengan gradient backgrounds

## 3. Layout & Structure

### Page Structure
```
┌─────────────────────────────────────────────────────────────┐
│  HEADER: Logo + Navigation + Profile                        │
├─────────────────────────────────────────────────────────────┤
│  HERO: Tagline + Quick Stats (Profit today, Products)       │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │  PRODUCT FINDER  │  │  PRICE CALCULATOR │                  │
│  │  AI-powered     │  │  Margin analyzer  │                  │
│  └─────────────────┘  └─────────────────┘                  │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │  DESC GENERATOR │  │  STOCK MANAGER    │                  │
│  │  Auto-listing   │  │  Inventory track  │                  │
│  └─────────────────┘  └─────────────────┘                  │
├─────────────────────────────────────────────────────────────┤
│  CHAT ASSISTANT: AI Chatbot for selling tips                │
├─────────────────────────────────────────────────────────────┤
│  FOOTER: Tips & Tricks                                       │
└─────────────────────────────────────────────────────────────┘
```

### Responsive Strategy
- Desktop (>1024px): 2-column grid for feature cards
- Tablet (768-1024px): 2-column with smaller cards
- Mobile (<768px): Single column stack

## 4. Features & Interactions

### A. Product Finder (AI)
- Input: Kategori, budget, target margin
- Output: Rekomendasi produk profitable dari database
- Interaction: Click card → Detail modal dengan supplier info
- States: Empty (prompts user), Loading (skeleton), Results (cards)

### B. Price Calculator
- Input: Harga modal, biaya tambahan, target margin
- Output: Harga jual recommended + profit breakdown
- Formula: `Harga Jual = (Harga Modal + Biaya Kirim + Fee Platform) / (1 - Margin - Fee Shopee%)`
- Real-time calculation dengan animated number transition

### C. Description Generator
- Input: Nama produk, fitur utama, keyword
- Output: Deskripsi produk Shopee-ready dengan emoji dan hashtag
- Features: Copy to clipboard, regenerate, edit inline

### D. Stock Manager
- Simple table untuk track inventory
- Input: Product name, stock, harga modal, harga jual
- Visual: Profit margin indicator (green/yellow/red)
- Actions: Add, Edit, Delete stock items

### E. Chat Assistant
- AI chatbot untuk tips jualan
- Pre-built prompts: "Tips naikin penjualan", "Cara handling complaint", dll
- Typing indicator animation
- Message bubbles dengan timestamp

## 5. Component Inventory

### Navigation Bar
- Logo (ShopeeReseller AI)
- Nav items: Dashboard, Products, Calculator, Tips
- Profile dropdown
- States: Default, Active tab indicator

### Stat Card
- Icon + Label + Value
- Subtle gradient background
- Hover: slight lift with shadow

### Feature Card
- Icon header
- Title + Description
- CTA button
- States: Default, Hover (scale + shadow), Active

### Product Card (Finder Results)
- Product image placeholder
- Product name
- Harga modal + Estimated profit
- Supplier badge
- Action: Lihat Detail

### Input Fields
- Label + Input + Helper text
- States: Default, Focus (border color change), Error (red border + message)

### Button
- Primary: Orange gradient, white text
- Secondary: White, orange border
- States: Default, Hover (darken), Active (scale down), Disabled (opacity 0.5)

### Chat Bubble
- User: Right-aligned, orange bg
- AI: Left-aligned, white bg with shadow
- Timestamp below
- Loading: Typing indicator dots

### Modal
- Backdrop blur
- Centered card
- Close button top-right
- Entrance: fade + scale up

## 6. Technical Approach

### Stack
- Single HTML file dengan embedded CSS dan JavaScript
- Vanilla JS untuk interaktivitas
- LocalStorage untuk persistensi data (stock manager)
- CSS Variables untuk theming
- No external frameworks

### Data Model
```javascript
// Stock Item
{
  id: string,
  nama: string,
  stock: number,
  hargaModal: number,
  hargaJual: number,
  kategori: string
}

// Chat Message
{
  id: string,
  role: 'user' | 'ai',
  content: string,
  timestamp: Date
}
```

### AI Responses (Simulated)
- Predefined response patterns untuk common questions
- Template-based generation untuk description generator
- Randomized tips untuk variety

### State Management
- Global state object
- Event-driven updates
- LocalStorage sync on changes