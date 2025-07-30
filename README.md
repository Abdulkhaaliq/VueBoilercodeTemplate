# Modern Vue.js Landing Page Template

# Please Note
- When starting off a new project. Clone this repository and change the dummy name and delete the git folder as you would not want to commit to this repo
- I Will update when necessary this project to keep it up to date with packages and best practices

## Features

- 🎨 **Modern Design**: Clean, professional design with smooth animations
- 📱 **Fully Responsive**: Optimized for all devices and screen sizes
- 🌊 **Parallax Hero**: Eye-catching hero section with parallax scrolling effect
- 🧭 **Smooth Navigation**: Auto-scrolling navigation with active section highlighting
- 📋 **Services Section**: Comprehensive services showcase with hover effects
- 📞 **Contact Form**: Functional contact form with validation
- 🍔 **Mobile Menu**: Collapsible hamburger menu for mobile devices
- ⚡ **Performance**: Built with Vite for fast development and optimized builds

## Tech Stack

- **Vue.js 3** - Progressive JavaScript framework
- **Vite** - Fast build tool and dev server
- **CSS3** - Modern styling with CSS variables and animations
- **@vueuse/core** - Vue composition utilities

## Getting Started

### Prerequisites

- Node.js (version 16 or higher)
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd vue-landing-page
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:3000`

### Building for Production

```bash
npm run build
```

The built files will be in the `dist` directory.

### Preview Production Build

```bash
npm run preview
```

## Project Structure

```
src/
├── components/          # Vue components
│   ├── Navbar.vue      # Navigation bar with mobile menu
│   ├── HeroSection.vue # Hero section with parallax effect
│   ├── ServicesSection.vue # Services showcase
│   └── ContactSection.vue  # Contact form and info
├── styles/
│   └── global.css      # Global styles and CSS variables
├── App.vue             # Main app component
└── main.js            # App entry point
```

## Customization

### Colors
Update the CSS variables in `src/styles/global.css`:

```css
:root {
  --primary-color: #3b82f6;
  --secondary-color: #10b981;
  --accent-color: #f59e0b;
  /* ... other variables */
}
```

### Content
- Update the hero content in `HeroSection.vue`
- Modify services in `ServicesSection.vue`
- Change contact information in `ContactSection.vue`

### Styling
- All styles use CSS variables for easy customization
- Responsive breakpoints are defined in the global CSS
- Component-specific styles are scoped to each component

## Features in Detail

### Navigation
- Fixed navbar with smooth scrolling
- Active section highlighting
- Mobile hamburger menu
- Backdrop blur effect

### Hero Section
- Parallax background effect
- Animated gradient background
- Statistics display
- Call-to-action buttons

### Services Section
- Grid layout with hover effects
- Service cards with icons
- Feature lists for each service
- Call-to-action section

### Contact Section
- Contact form with validation
- Contact information display
- Social media links
- Responsive layout

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

This project is licensed under the MIT License.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
