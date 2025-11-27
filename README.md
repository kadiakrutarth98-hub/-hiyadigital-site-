import React, { useState } from "react";

// Hiyadigital - Single File React Component (Tailwind CSS)
// Default export: HiyadigitalWebsite
// This file is a complete single-page application layout you can paste into a React project.

export default function HiyadigitalWebsite() {
  const [nav, setNav] = useState("home");
  const [formData, setFormData] = useState({
    businessName: "",
    contactName: "",
    phone: "",
    email: "",
    website: "",
    industry: "",
    goals: [],
    package: "",
    message: "",
  });

  const handleNav = (id) => setNav(id);
  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    if (type === "checkbox") {
      setFormData((s) => ({
        ...s,
        goals: checked ? [...s.goals, value] : s.goals.filter((g) => g !== value),
      }));
      return;
    }
    setFormData((s) => ({ ...s, [name]: value }));
  };

  const submitForm = (e) => {
    e.preventDefault();
    // In production, send to your API or email service
    alert("Form submitted. Check console for data.");
    console.log("Onboarding form data:", formData);
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-slate-50 to-white text-slate-800">
      <header className="max-w-6xl mx-auto p-6 flex items-center justify-between">
        <div className="flex items-center gap-3">
          <div className="w-12 h-12 rounded-lg bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center text-white font-bold">HI</div>
          <div>
            <h1 className="text-xl font-semibold">Hiyadigital</h1>
            <p className="text-xs text-slate-500">Growth-focused digital marketing agency</p>
          </div>
        </div>
        <nav className="hidden md:flex gap-4 items-center text-sm">
          <button onClick={() => handleNav('home')} className="hover:text-blue-600">Home</button>
          <button onClick={() => handleNav('services')} className="hover:text-blue-600">Services</button>
          <button onClick={() => handleNav('packages')} className="hover:text-blue-600">Packages</button>
          <button onClick={() => handleNav('workflow')} className="hover:text-blue-600">Workflow</button>
          <button onClick={() => handleNav('sop')} className="hover:text-blue-600">SOPs</button>
          <button onClick={() => handleNav('onboarding')} className="hover:text-blue-600">Onboarding</button>
          <button onClick={() => handleNav('contact')} className="bg-blue-600 text-white px-4 py-2 rounded-lg text-sm hover:opacity-95">Get Started</button>
        </nav>
        <div className="md:hidden">
          <select onChange={(e) => handleNav(e.target.value)} value={nav} className="border rounded p-2 text-sm">
            <option value="home">Home</option>
            <option value="services">Services</option>
            <option value="packages">Packages</option>
            <option value="workflow">Workflow</option>
            <option value="sop">SOPs</option>
            <option value="onboarding">Onboarding</option>
            <option value="contact">Contact</option>
          </select>
        </div>
      </header>

      <main className="max-w-6xl mx-auto px-6 py-8">
        {/* HERO */}
        {nav === 'home' && (
          <section className="grid md:grid-cols-2 gap-8 items-center py-12">
            <div>
              <h2 className="text-4xl font-extrabold leading-tight">Hiyadigital — Digital Marketing That Delivers Customers</h2>
              <p className="mt-4 text-slate-600">We combine strategic SEO, high-converting websites, cinematic video, paid campaigns and social media management to grow local & niche businesses. Specialised packages for wellness coaches, reiki healers, gyms and restaurants.</p>

              <div className="mt-6 flex gap-3">
                <button onClick={() => handleNav('onboarding')} className="bg-blue-600 text-white px-5 py-3 rounded-lg font-medium">Start Onboarding</button>
                <button onClick={() => handleNav('packages')} className="border border-slate-200 px-5 py-3 rounded-lg">See Packages</button>
              </div>

              <div className="mt-8 grid grid-cols-2 gap-4">
                <div className="p-4 bg-white rounded-lg shadow-sm">
                  <h4 className="text-sm font-semibold">Monthly Retainers</h4>
                  <p className="text-xs text-slate-500">Predictable growth & performance</p>
                </div>
                <div className="p-4 bg-white rounded-lg shadow-sm">
                  <h4 className="text-sm font-semibold">Specialised Niches</h4>
                  <p className="text-xs text-slate-500">Wellness, Fitness, Food & Local businesses</p>
                </div>
              </div>
            </div>

            <div className="rounded-xl bg-gradient-to-br from-cyan-50 to-white p-6 shadow-md">
              <div className="h-56 bg-slate-100 rounded-lg flex items-center justify-center text-slate-400">Hero Visual / Video Placeholder</div>
              <ul className="mt-6 text-sm space-y-2">
                <li>✅ Free audit on first month</li>
                <li>✅ Transparent reporting</li>
                <li>✅ 30-day measurable improvements</li>
              </ul>
            </div>
          </section>
        )}

        {/* SERVICES */}
        {nav === 'services' && (
          <section className="py-10">
            <h3 className="text-2xl font-bold">Services — What We Do</h3>
            <p className="text-slate-600 mt-2">End-to-end digital marketing services designed to scale revenue and customer acquisition.</p>

            <div className="grid md:grid-cols-3 gap-6 mt-6">
              <ServiceCard title="Social Media Management" desc="Strategy, content calendar, reels, captions, posting & analytics" / >
              <ServiceCard title="Website Development" desc="High-converting WordPress/Shopify sites with on-page SEO" />
              <ServiceCard title="Video Production" desc="Concept, shoot, edit, color-grade, and platform-optimised cuts" />
              <ServiceCard title="Paid Campaigns" desc="Facebook, Instagram & Google — setup, optimisation, A/B tests" />
              <ServiceCard title="SEO" desc="Technical + on-page + off-page with content and local SEO" />
              <ServiceCard title="Consulting & Strategy" desc="Brand strategy, funnels, pricing, and growth plans" />
            </div>
          </section>
        )}

        {/* PACKAGES */}
        {nav === 'packages' && (
          <section className="py-10">
            <h3 className="text-2xl font-bold">Packages (Industry Tailored)</h3>
            <p className="text-slate-600 mt-2">Ready-made retainer packages for wellness coaches, reiki healers, gyms and restaurants. SEO add-ons available.</p>

            <div className="mt-6 grid md:grid-cols-3 gap-6">
              <PackageCard title="Wellness Coach - Basic" price="₹12,000 / month" bullets={["12 posts","4 reels","Basic branding","Monthly report"]} />
              <PackageCard title="Gym - Standard" price="₹28,000 / month" bullets={["16 posts","8 reels","Local ads","GMB optimization"]} />
              <PackageCard title="Restaurant - Premium" price="₹60,000 / month" bullets={["15 reels","Influencer collab","Google Ads","High-quality shoots"]} />
            </div>

            <div className="mt-8 bg-white p-6 rounded-lg shadow-sm">
              <h4 className="font-semibold">SEO Packages (Add-on)</h4>
              <div className="mt-4 grid md:grid-cols-3 gap-4">
                <SEOBox title="Basic SEO" price="₹8k–12k / month" list={["Audit","On-page","3–5 backlinks","GMB"]} />
                <SEOBox title="Standard SEO" price="₹18k–28k / month" list={["8–10 backlinks","2 blogs / month","Competitor analysis"]} />
                <SEOBox title="Premium SEO" price="₹30k–45k / month" list={["15–20 backlinks","Technical SEO","4 blogs / month"]} />
              </div>
            </div>

          </section>
        )}

        {/* WORKFLOW */}
        {nav === 'workflow' && (
          <section className="py-10">
            <h3 className="text-2xl font-bold">Company Workflow</h3>
            <p className="text-slate-600 mt-2">How Hiyadigital runs client projects — efficient, transparent and repeatable.</p>

            <div className="mt-6 space-y-6">
              <WorkflowBox title="Onboarding" content={[
                'Discovery call & goals',
                'Proposal & contract',
                'Collect brand assets & access',
                'Kickoff meeting'
              ]} />

              <WorkflowBox title="Monthly Cycle" content={[
                'Week 1 — Strategy & calendar',
                'Week 2 — Content creation & shoots',
                'Week 3 — Posting & ads',
                'Week 4 — Reporting & optimisation'
              ]} />

              <WorkflowBox title="SOPs & Quality Control" content={[
                'Content QA checklist',
                'Ad pre-launch checklist',
                'Website deploy checklist'
              ]} />
            </div>
          </section>
        )}

        {/* SOPs */}
        {nav === 'sop' && (
          <section className="py-10">
            <h3 className="text-2xl font-bold">SOP Checklists</h3>
            <p className="text-slate-600 mt-2">Operational checklists to ensure consistent delivery and quality.</p>

            <div className="mt-6 grid md:grid-cols-2 gap-6">
              <SOPCard title="Social Media Content" bullets={["Research competitors","Create monthly themes","Design & reels","Client approval","Scheduling"]} />
              <SOPCard title="Paid Ads" bullets={["Define objective","Audience","Ad creative","Install pixel","Monitor & optimise"]} />
              <SOPCard title="SEO Monthly" bullets={["Audit","Fix speed","On-page","Backlinks","Blogs"]} />
              <SOPCard title="Website Development" bullets={["Wireframe","Design approval","Responsive dev","Testing","Deployment"]} />
            </div>
          </section>
        )}

        {/* ONBOARDING FORM */}
        {nav === 'onboarding' && (
          <section className="py-10">
            <h3 className="text-2xl font-bold">Client Onboarding Form</h3>
            <p className="text-slate-600 mt-2">Fill this form to start your growth plan with Hiyadigital.</p>

            <form onSubmit={submitForm} className="mt-6 grid md:grid-cols-2 gap-4">
              <Input label="Business Name" name="businessName" value={formData.businessName} onChange={handleChange} />
              <Input label="Contact Name" name="contactName" value={formData.contactName} onChange={handleChange} />
              <Input label="Phone" name="phone" value={formData.phone} onChange={handleChange} />
              <Input label="Email" name="email" value={formData.email} onChange={handleChange} type="email" />
              <Input label="Website (if any)" name="website" value={formData.website} onChange={handleChange} />
              <Input label="Industry / Category" name="industry" value={formData.industry} onChange={handleChange} />

              <div className="md:col-span-2 bg-white p-4 rounded-lg shadow-sm">
                <label className="text-sm font-medium">Primary Goals (select any)</label>
                <div className="mt-2 grid grid-cols-2 gap-2 text-sm">
                  {['Increase brand awareness','Increase leads','Improve SEO','Increase footfall','Build personal brand'].map((g) => (
                    <label key={g} className="flex items-center gap-2"><input type="checkbox" value={g} onChange={handleChange} /> {g}</label>
                  ))}
                </div>
              </div>

              <div className="md:col-span-2">
                <label className="block text-sm font-medium">Preferred Package</label>
                <select name="package" value={formData.package} onChange={handleChange} className="mt-2 w-full border rounded p-2">
                  <option value="">Select a package</option>
                  <option value="basic">Basic</option>
                  <option value="standard">Standard</option>
                  <option value="premium">Premium</option>
                </select>
              </div>

              <div className="md:col-span-2">
                <label className="block text-sm font-medium">Message / Requirements</label>
                <textarea name="message" value={formData.message} onChange={handleChange} rows={4} className="mt-2 w-full border rounded p-2"></textarea>
              </div>

              <div className="md:col-span-2 flex gap-3">
                <button type="submit" className="bg-blue-600 text-white px-6 py-3 rounded-lg">Submit & Start Audit</button>
                <button type="button" onClick={() => { setFormData({ businessName:'', contactName:'', phone:'', email:'', website:'', industry:'', goals:[], package:'', message:'' }) }} className="border px-6 py-3 rounded-lg">Reset</button>
              </div>
            </form>

          </section>
        )}

        {/* CONTACT */}
        {nav === 'contact' && (
          <section className="py-10">
            <h3 className="text-2xl font-bold">Contact & Next Steps</h3>
            <p className="text-slate-600 mt-2">Ready to grow? Here's how we work and how to start.</p>

            <div className="mt-6 grid md:grid-cols-2 gap-6">
              <div className="bg-white p-6 rounded-lg shadow-sm">
                <h4 className="font-semibold">How we start</h4>
                <ol className="mt-3 list-decimal list-inside text-sm space-y-2">
                  <li>Free audit & discovery call</li>
                  <li>Proposal & package selection</li>
                  <li>Onboarding & kickoff</li>
                  <li>Month 1 – strategy & implementation</li>
                </ol>

                <div className="mt-6">
                  <p className="text-sm">Email: hello@hiyadigital.com</p>
                  <p className="text-sm">Phone: +91 99999 99999</p>
                </div>
              </div>

              <div className="bg-white p-6 rounded-lg shadow-sm">
                <h4 className="font-semibold">Quick FAQ</h4>
                <div className="mt-3 text-sm space-y-2">
                  <p><strong>Q:</strong> Minimum contract?<br /> <strong>A:</strong> 1 month for retainers, 50% advance for websites.</p>
                  <p><strong>Q:</strong> How do you report?<br /> <strong>A:</strong> Monthly analytics + weekly WhatsApp updates.</p>
                </div>
              </div>
            </div>

          </section>
        )}

        {/* FOOTER */}
        <footer className="mt-12 py-8 border-t">
          <div className="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4">
            <div>
              <h4 className="font-bold">Hiyadigital</h4>
              <p className="text-xs text-slate-500">Full-service digital marketing — SEO, websites, video, ads & social.</p>
            </div>
            <div className="text-sm text-slate-500">© {new Date().getFullYear()} Hiyadigital. All rights reserved.</div>
          </div>
        </footer>

      </main>
    </div>
  );
}


/* ---------------------- Reusable UI components ---------------------- */

function ServiceCard({ title, desc }) {
  return (
    <div className="bg-white p-6 rounded-lg shadow-sm">
      <h4 className="font-semibold">{title}</h4>
      <p className="text-sm text-slate-500 mt-2">{desc}</p>
    </div>
  );
}

function PackageCard({ title, price, bullets = [] }) {
  return (
    <div className="bg-gradient-to-br from-white to-cyan-50 p-6 rounded-xl shadow-lg">
      <h4 className="font-bold">{title}</h4>
      <div className="text-sm text-slate-600 mt-2">{price}</div>
      <ul className="mt-3 text-sm space-y-1">
        {bullets.map((b) => (<li key={b}>• {b}</li>))}
      </ul>
      <div className="mt-4">
        <button className="bg-blue-600 text-white px-4 py-2 rounded">Start with this</button>
      </div>
    </div>
  );
}

function SEOBox({ title, price, list = [] }) {
  return (
    <div className="p-4 bg-white rounded-lg border">
      <h5 className="font-semibold">{title}</h5>
      <div className="text-sm text-slate-600 mt-1">{price}</div>
      <ul className="mt-2 text-sm space-y-1">
        {list.map((l) => (<li key={l}>• {l}</li>))}
      </ul>
    </div>
  );
}

function WorkflowBox({ title, content = [] }) {
  return (
    <div className="bg-white p-4 rounded-lg shadow-sm">
      <h5 className="font-semibold">{title}</h5>
      <ul className="mt-2 text-sm space-y-1">
        {content.map((c) => (<li key={c}>• {c}</li>))}
      </ul>
    </div>
  );
}

function SOPCard({ title, bullets = [] }) {
  return (
    <div className="bg-white p-4 rounded-lg shadow-sm">
      <h5 className="font-semibold">{title}</h5>
      <ul className="mt-2 text-sm space-y-1">
        {bullets.map((b) => (<li key={b}>• {b}</li>))}
      </ul>
    </div>
  );
}

function Input({ label, name, value, onChange, type = 'text' }) {
  return (
    <label className="block">
      <div className="text-sm font-medium">{label}</div>
      <input name={name} value={value} onChange={onChange} type={type} className="mt-2 w-full border rounded p-2" />
    </label>
  );
}
