import React, { useState } from "react";

/**
 * Irie Life Café - Single-file React component (modern Caribbean style)
 * - TailwindCSS utility classes assumed available in host project
 * - Uses no external images except a logo placeholder. Replace `logoSrc` with uploaded logo path.
 * - Includes: Home hero, About, Menu, Bakery, Tapas Nights, Events, Gallery, Shop placeholder,
 *   Reservations & Contact form, Newsletter, Footer with social links.
 *
 * How to use:
 * - Drop this file into a React app (Create React App / Vite / Next.js page)
 * - Ensure Tailwind CSS is configured in the project
 * - Replace placeholder images and links with real assets
 */

const logoSrc = "/logo-irie-life.png"; // <-- replace with path to your uploaded logo (e.g. /assets/logo.png)

const MenuItem = ({ name, price, desc }) => (
  <div className="flex justify-between items-start gap-4 py-3 border-b border-sand-200"> 
    <div>
      <h4 className="text-teal-700 font-semibold">{name}</h4>
      <p className="text-sm text-gray-600">{desc}</p>
    </div>
    <div className="text-right">
      <div className="text-teal-800 font-semibold">${price}</div>
    </div>
  </div>
);

export default function IrieLifeSite() {
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);
  const [reserve, setReserve] = useState({ name: "", email: "", date: "", time: "", people: 2 });
  const [newsletterEmail, setNewsletterEmail] = useState("");
  const submitReservation = (e) => { e.preventDefault(); alert(`Thanks ${reserve.name}! Reservation request received.`); };
  const submitNewsletter = (e) => { e.preventDefault(); alert(`Thanks! We'll keep ${newsletterEmail} posted.`); setNewsletterEmail(""); };

  return (
    <div className="min-h-screen font-sans text-gray-800 bg-[url('/parchment-bg.jpg')] bg-cover bg-center">
      {/* Header */}
      <header className="backdrop-blur-sm bg-white/40 border-b border-white/60">
        <div className="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
          <div className="flex items-center gap-4">
            <img src={logoSrc} alt="Irie Life Cafe logo" className="w-36 h-auto object-contain" />
            <div>
              <div className="text-sm text-gray-700">IRIE LIFE CAFÉ</div>
              <div className="text-xs text-amber-700 italic">Where Caribbean Flavor Meets Global Wellness</div>
            </div>
          </div>

          <nav className="hidden md:flex items-center gap-6 text-sm">
            <a href="#about" className="text-teal-700 hover:underline">About</a>
            <a href="#menu" className="text-teal-700 hover:underline">Menu</a>
            <a href="#bakery" className="text-teal-700 hover:underline">Bakery</a>
            <a href="#tapastime" className="text-teal-700 hover:underline">Tapas Nights</a>
            <a href="#events" className="text-teal-700 hover:underline">Events</a>
            <a href="#shop" className="text-teal-700 hover:underline">Shop</a>
            <a href="#contact" className="bg-amber-200 px-3 py-1 rounded text-teal-900 shadow">Contact & Reserve</a>
          </nav>

          <button
            className="md:hidden p-2 rounded bg-white/30"
            onClick={() => setMobileMenuOpen(!mobileMenuOpen)}
            aria-label="Toggle menu"
          >
            <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6 text-teal-700" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>

        {mobileMenuOpen && (
          <div className="md:hidden border-t border-white/60">
            <div className="px-6 py-4 flex flex-col gap-3">
              <a href="#about" onClick={() => setMobileMenuOpen(false)} className="text-teal-700">About</a>
              <a href="#menu" onClick={() => setMobileMenuOpen(false)} className="text-teal-700">Menu</a>
              <a href="#bakery" onClick={() => setMobileMenuOpen(false)} className="text-teal-700">Bakery</a>
              <a href="#tapastime" onClick={() => setMobileMenuOpen(false)} className="text-teal-700">Tapas Nights</a>
              <a href="#events" onClick={() => setMobileMenuOpen(false)} className="text-teal-700">Events</a>
              <a href="#shop" onClick={() => setMobileMenuOpen(false)} className="text-teal-700">Shop</a>
              <a href="#contact" onClick={() => setMobileMenuOpen(false)} className="bg-amber-200 px-3 py-1 rounded text-teal-900 shadow">Contact & Reserve</a>
            </div>
          </div>
        )}
      </header>

      {/* Hero */}
      <main className="max-w-6xl mx-auto px-6 py-12">
        <section className="grid md:grid-cols-2 gap-8 items-center py-8">
          <div>
            <h1 className="text-4xl md:text-5xl font-extrabold text-teal-800 leading-tight">Irie Life Café</h1>
            <p className="mt-4 text-lg text-gray-700">Where Caribbean Flavor Meets Global Wellness — fresh, sustainable, and soulful. Join us for handcrafted bites, island-inspired pastries, and warm hospitality.</p>

            <div className="mt-6 flex flex-wrap gap-3">
              <a href="#menu" className="px-5 py-3 bg-teal-700 text-white rounded shadow">View Menu</a>
              <a href="#contact" className="px-5 py-3 border border-teal-700 text-teal-700 rounded">Reserve a Table</a>
              <a href="#shop" className="px-5 py-3 bg-amber-200 text-teal-900 rounded">Shop Merch</a>
            </div>

            <div className="mt-8 grid grid-cols-2 gap-3">
              <div className="bg-white/70 rounded p-3">
                <div className="text-xs text-gray-500">Opening</div>
                <div className="font-semibold">Dominica (Flagship)</div>
              </div>
              <div className="bg-white/70 rounded p-3">
                <div className="text-xs text-gray-500">Funding Goal</div>
                <div className="font-semibold">USD $300,000</div>
              </div>
            </div>
          </div>

          <div className="rounded-lg overflow-hidden shadow-lg bg-white/50 p-6">
            <img src="/hero-dish.jpg" alt="Caribbean dish" className="w-full h-64 object-cover rounded" />
            <div className="mt-3 text-sm text-gray-600">Signature: Grass-fed Lamb Burger with island slaw</div>
          </div>
        </section>

        {/* Two-column sections start here - emulate magazine style */}
        <section id="about" className="mt-12">
          <div className="prose max-w-none">
            <h2 className="text-2xl text-teal-700 font-bold">About Irie Life Café</h2>
            <p className="text-gray-700">Irie Life Café celebrates the Caribbean’s culinary heritage with a modern, health-forward sensibility. We prioritize local produce, sustainable sourcing, and creative flavors that tell the story of the islands.</p>
          </div>

          <div className="mt-6 grid md:grid-cols-2 gap-6">
            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="text-teal-700 font-semibold">Founder</h3>
              <p className="text-gray-700">Chef Julian Broome — a Barbadian-born pastry chef with leadership experience at luxury resorts including Grace Bay Club, BodyHoliday, CuisinArt, Mandarin Oriental, Seven Stars, and Sandy Lane.</p>
              <a href="#founder" className="mt-3 inline-block text-teal-800 underline">Read Founder Profile</a>
            </div>

            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="text-teal-700 font-semibold">Our Promise</h3>
              <ul className="list-disc pl-5 text-gray-700">
                <li>Local sourcing & community partnerships</li>
                <li>Seasonal menus that reduce waste</li>
                <li>Mindful, flavorful food for all ages</li>
              </ul>
            </div>
          </div>
        </section>

        {/* Menu */}
        <section id="menu" className="mt-14">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Menu Highlights</h2>
          <div className="grid md:grid-cols-2 gap-6">
            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="text-teal-800 font-semibold">Burgers & Mains</h3>
              <MenuItem name="Grass-Fed Beef Burger" price="14.00" desc="Specialty bun, island slaw, cassava fries" />
              <MenuItem name="Goat Burger" price="15.00" desc="Island spice rub, mango chutney" />
              <MenuItem name="Seafood Burger" price="15.50" desc="Mahi-Mahi, tropical slaw" />
            </div>

            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="text-teal-800 font-semibold">Pizzas, Wraps & Salads</h3>
              <MenuItem name="Jerk Chicken Pizza" price="17.00" desc="Pineapple salsa, scotch bonnet glaze" />
              <MenuItem name="Callaloo & Plantain Pizza" price="16.00" desc="Vegetarian, island greens" />
              <MenuItem name="Tropical Kale Salad" price="12.50" desc="Papaya vinaigrette" />
            </div>
          </div>
        </section>

        {/* Bakery */}
        <section id="bakery" className="mt-14">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Bakery & Sweets</h2>
          <div className="grid md:grid-cols-3 gap-6">
            <div className="bg-white/70 rounded-lg p-6">
              <h4 className="font-semibold">Breads</h4>
              <p className="text-gray-700">Cassava buns, plantain loaf, coconut rolls.</p>
            </div>
            <div className="bg-white/70 rounded-lg p-6">
              <h4 className="font-semibold">Cakes & Donuts</h4>
              <p className="text-gray-700">Spiced rum cake, guava-filled donuts, tropical slices.</p>
            </div>
            <div className="bg-white/70 rounded-lg p-6">
              <h4 className="font-semibold">Pastries</h4>
              <p className="text-gray-700">Danishes, coconut turnovers, handmade petit fours.</p>
            </div>
          </div>
        </section>

        {/* Tapas Nights */}
        <section id="tapastime" className="mt-14">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Tapas Nights — Irie Evenings</h2>
          <div className="bg-white/70 rounded-lg p-6">
            <p className="text-gray-700">From 7pm we serve scaled-down portions for sharing — mini jerk sliders, seafood fritters, plantain skewers, and island-inspired cocktails. Perfect for groups, live music, and slow conversation.</p>
          </div>
        </section>

        {/* Events */}
        <section id="events" className="mt-14">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Events & Community</h2>
          <div className="grid md:grid-cols-2 gap-6">
            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="font-semibold">Weekly Events</h3>
              <ul className="list-disc pl-5 text-gray-700">
                <li>Sunday Chill Sessions – acoustic sets</li>
                <li>Market & Makers – local artisan pop-ups</li>
                <li>Young Chef Workshops – monthly culinary training</li>
              </ul>
            </div>
            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="font-semibold">Private Events</h3>
              <p className="text-gray-700">On-site catering, private tastings, and wedding dessert packages. Contact us for bespoke menus and team-building workshops.</p>
            </div>
          </div>
        </section>

        {/* Gallery */}
        <section id="gallery" className="mt-14">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Gallery</h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
            <img src="/gallery1.jpg" alt="gallery" className="w-full h-48 object-cover rounded shadow" />
            <img src="/gallery2.jpg" alt="gallery" className="w-full h-48 object-cover rounded shadow" />
            <img src="/gallery3.jpg" alt="gallery" className="w-full h-48 object-cover rounded shadow" />
          </div>
        </section>

        {/* Shop placeholder */}
        <section id="shop" className="mt-14">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Shop</h2>
          <div className="bg-white/70 rounded-lg p-6">
            <p className="text-gray-700">Coming soon: Irie Life merch, sauces, and small-batch island products. Sign up below to be the first to know.</p>
            <form onSubmit={submitNewsletter} className="mt-4 flex gap-2 flex-col sm:flex-row">
              <input value={newsletterEmail} onChange={(e)=>setNewsletterEmail(e.target.value)} placeholder="Email address" className="flex-1 p-2 rounded border" />
              <button className="px-4 py-2 bg-teal-700 text-white rounded">Join</button>
            </form>
          </div>
        </section>

        {/* Contact & Reservations */}
        <section id="contact" className="mt-14 pb-24">
          <h2 className="text-2xl text-teal-700 font-bold mb-4">Contact & Reservations</h2>
          <div className="grid md:grid-cols-2 gap-6">
            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="text-teal-800 font-semibold">Get in touch</h3>
              <p className="text-gray-700">Email: <a href="mailto:irielifecafe@gmail.com" className="text-teal-700">irielifecafe@gmail.com</a></p>
              <p className="text-gray-700">Phone/WhatsApp: <a href="tel:+16492325920" className="text-teal-700">+1 (649) 232-5920</a></p>
              <p className="text-gray-700">Follow: <a href="https://www.instagram.com/chefmoses246" target="_blank" rel="noreferrer" className="text-teal-700">@chefmoses246</a> | <a href="https://www.instagram.com/irielifecafe" target="_blank" rel="noreferrer" className="text-teal-700">@irielifecafe</a></p>

              <div className="mt-6">
                <h4 className="font-semibold">Location (Flagship)</h4>
                <p className="text-gray-700">Dominica — exact address coming soon</p>
                <div className="mt-3"/>
                <iframe title="map" src="https://www.google.com/maps?q=dominica&output=embed" className="w-full h-40 rounded border" />
              </div>
            </div>

            <div className="bg-white/70 rounded-lg p-6">
              <h3 className="text-teal-800 font-semibold">Reserve a table</h3>
              <form onSubmit={submitReservation} className="mt-3 grid gap-3">
                <input value={reserve.name} onChange={(e)=>setReserve({...reserve,name:e.target.value})} placeholder="Full name" className="p-2 rounded border" required />
                <input value={reserve.email} onChange={(e)=>setReserve({...reserve,email:e.target.value})} placeholder="Email" type="email" className="p-2 rounded border" required />
                <input value={reserve.date} onChange={(e)=>setReserve({...reserve,date:e.target.value})} placeholder="Date (YYYY-MM-DD)" className="p-2 rounded border" required />
                <input value={reserve.time} onChange={(e)=>setReserve({...reserve,time:e.target.value})} placeholder="Time (e.g. 19:00)" className="p-2 rounded border" required />
                <select value={reserve.people} onChange={(e)=>setReserve({...reserve,people:e.target.value})} className="p-2 rounded border">
                  <option value={2}>2 people</option>
                  <option value={3}>3 people</option>
                  <option value={4}>4 people</option>
                  <option value={5}>5 people</option>
                </select>
                <button className="px-4 py-2 bg-amber-200 text-teal-900 rounded">Request Reservation</button>
              </form>
            </div>
          </div>
        </section>

        {/* Footer */}
        <footer className="mt-12 bg-white/40 rounded p-6 text-center">
          <div className="max-w-4xl mx-auto">
            <div className="flex flex-col md:flex-row items-center justify-between gap-4">
              <div>
                <div className="text-sm text-gray-700">Irie Life Café</div>
                <div className="text-xs text-gray-500">Where Caribbean Flavor Meets Global Wellness</div>
              </div>
              <div className="text-sm text-gray-600">© {new Date().getFullYear()} Irie Life Café</div>
              <div className="flex items-center gap-3">
                <a href="https://www.instagram.com/irielifecafe" target="_blank" rel="noreferrer" className="text-teal-700">@irielifecafe</a>
                <a href="https://www.instagram.com/chefmoses246" target="_blank" rel="noreferrer" className="text-teal-700">@chefmoses246</a>
              </div>
            </div>
            <div className="mt-4 text-xs text-gray-500">Irie Life Café | Business Plan | Confidential</div>
          </div>
        </footer>
      </main>
    </div>
  );
}
