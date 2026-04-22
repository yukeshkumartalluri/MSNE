<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MSME Connect Prototype</title>
  <style>
    :root {
      --bg: #f5f7fb;
      --card: #ffffff;
      --text: #1f2937;
      --muted: #6b7280;
      --primary: #0f62fe;
      --primary-dark: #0b4ecc;
      --success: #16a34a;
      --warning: #f59e0b;
      --danger: #dc2626;
      --border: #e5e7eb;
      --chip: #eef2ff;
      --shadow: 0 10px 25px rgba(0,0,0,0.06);
      --radius: 16px;
    }

    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background: var(--bg);
      color: var(--text);
    }

    .app {
      display: grid;
      grid-template-columns: 260px 1fr;
      min-height: 100vh;
    }

    .sidebar {
      background: #0b1220;
      color: white;
      padding: 24px 18px;
      position: sticky;
      top: 0;
      height: 100vh;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 28px;
    }

    .logo {
      width: 42px;
      height: 42px;
      border-radius: 12px;
      background: linear-gradient(135deg, #2563eb, #06b6d4);
      display: grid;
      place-items: center;
      font-weight: 800;
      color: white;
    }

    .brand h1 {
      font-size: 18px;
      margin: 0;
    }

    .brand p {
      margin: 2px 0 0;
      font-size: 12px;
      color: #94a3b8;
    }

    .nav {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .nav button {
      all: unset;
      cursor: pointer;
      padding: 12px 14px;
      border-radius: 12px;
      color: #e5e7eb;
      font-size: 14px;
    }

    .nav button.active,
    .nav button:hover {
      background: rgba(255,255,255,0.08);
      color: white;
    }

    .main {
      padding: 24px;
    }

    .topbar {
      display: flex;
      justify-content: space-between;
      gap: 16px;
      align-items: center;
      margin-bottom: 24px;
      flex-wrap: wrap;
    }

    .searchbar {
      flex: 1;
      min-width: 260px;
      display: flex;
      gap: 12px;
    }

    .searchbar input {
      flex: 1;
      padding: 14px 16px;
      border-radius: 12px;
      border: 1px solid var(--border);
      outline: none;
      background: white;
    }

    .btn {
      border: none;
      border-radius: 12px;
      padding: 12px 16px;
      cursor: pointer;
      font-weight: 600;
    }

    .btn-primary {
      background: var(--primary);
      color: white;
    }

    .btn-primary:hover {
      background: var(--primary-dark);
    }

    .btn-light {
      background: white;
      border: 1px solid var(--border);
      color: var(--text);
    }

    .hero {
      background: linear-gradient(135deg, #e0ecff, #ecfeff);
      border-radius: var(--radius);
      padding: 28px;
      box-shadow: var(--shadow);
      margin-bottom: 22px;
    }

    .hero h2 {
      margin: 0 0 10px;
      font-size: 32px;
      line-height: 1.15;
    }

    .hero p {
      margin: 0 0 18px;
      max-width: 760px;
      color: #334155;
    }

    .chips {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    .chip {
      background: var(--chip);
      color: #3730a3;
      padding: 10px 12px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: 600;
    }

    .grid {
      display: grid;
      grid-template-columns: 2fr 1fr;
      gap: 20px;
    }

    .stack {
      display: grid;
      gap: 20px;
    }

    .cards {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 16px;
    }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 18px;
      box-shadow: var(--shadow);
    }

    .card h3, .card h4 {
      margin-top: 0;
      margin-bottom: 10px;
    }

    .muted {
      color: var(--muted);
      font-size: 14px;
    }

    .scheme-card {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .tag-row {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
    }

    .tag {
      font-size: 12px;
      padding: 6px 10px;
      border-radius: 999px;
      background: #f3f4f6;
      color: #374151;
    }

    .status {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 13px;
      font-weight: 700;
      padding: 8px 10px;
      border-radius: 999px;
    }

    .status.success { background: #dcfce7; color: #166534; }
    .status.warning { background: #fef3c7; color: #92400e; }
    .status.review { background: #dbeafe; color: #1d4ed8; }

    .list {
      display: grid;
      gap: 12px;
    }

    .list-item {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      align-items: start;
      padding: 14px 0;
      border-bottom: 1px solid var(--border);
    }

    .list-item:last-child { border-bottom: none; }

    .price {
      font-weight: 700;
    }

    .section-title {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      margin-bottom: 14px;
    }

    .section-title h3 {
      margin: 0;
    }

    .hidden {
      display: none !important;
    }

    .screen {
      display: none;
    }

    .screen.active {
      display: block;
    }

    .scheme-list {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 16px;
    }

    .detail-box {
      display: grid;
      grid-template-columns: 1.4fr 1fr;
      gap: 20px;
    }

    .timeline {
      display: grid;
      gap: 14px;
      margin-top: 12px;
    }

    .timeline-step {
      display: flex;
      gap: 12px;
      align-items: flex-start;
    }

    .dot {
      width: 14px;
      height: 14px;
      border-radius: 999px;
      margin-top: 4px;
      background: #cbd5e1;
      flex-shrink: 0;
    }

    .dot.done { background: var(--success); }
    .dot.current { background: var(--primary); }

    form {
      display: grid;
      gap: 14px;
    }

    label {
      display: grid;
      gap: 8px;
      font-size: 14px;
      font-weight: 600;
    }

    input, select, textarea {
      padding: 12px 14px;
      border-radius: 12px;
      border: 1px solid var(--border);
      font: inherit;
      background: white;
    }

    textarea { min-height: 100px; resize: vertical; }

    .two-col {
      display: grid;
      grid-template-columns: repeat(2, minmax(0,1fr));
      gap: 14px;
    }

    .kpi {
      display: grid;
      grid-template-columns: repeat(4, minmax(0,1fr));
      gap: 16px;
      margin-bottom: 20px;
    }

    .kpi .card h3 {
      margin: 6px 0 4px;
      font-size: 28px;
    }

    .small {
      font-size: 12px;
      color: var(--muted);
    }

    .footer-note {
      margin-top: 18px;
      color: var(--muted);
      font-size: 13px;
    }

    @media (max-width: 1100px) {
      .cards, .scheme-list, .detail-box, .grid, .kpi {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 820px) {
      .app {
        grid-template-columns: 1fr;
      }

      .sidebar {
        position: static;
        height: auto;
      }

      .nav {
        flex-direction: row;
        flex-wrap: wrap;
      }

      .two-col {
        grid-template-columns: 1fr;
      }

      .main {
        padding: 16px;
      }

      .hero h2 {
        font-size: 26px;
      }
    }
  </style>
</head>
<body>
  <div class="app">
    <aside class="sidebar">
      <div class="brand">
        <div class="logo">MC</div>
        <div>
          <h1>MSME Connect</h1>
          <p>Unified schemes & services</p>
        </div>
      </div>

      <nav class="nav">
        <button class="nav-link active" data-screen="home">Home</button>
        <button class="nav-link" data-screen="schemes">Schemes</button>
        <button class="nav-link" data-screen="apply">Apply</button>
        <button class="nav-link" data-screen="track">Track Applications</button>
        <button class="nav-link" data-screen="market">Market & Logistics</button>
        <button class="nav-link" data-screen="help">Help & FAQs</button>
      </nav>
    </aside>

    <main class="main">
      <div class="topbar">
        <div class="searchbar">
          <input id="globalSearch" type="text" placeholder="Search schemes, loans, subsidies, deadlines..." />
          <button class="btn btn-primary" id="searchBtn">Search</button>
        </div>
        <button class="btn btn-light">Login / Register</button>
      </div>

      <!-- HOME -->
      <section class="screen active" id="home">
        <div class="hero">
          <h2>Access government schemes, loans, and MSME services on one platform</h2>
          <p>
            Discover funding schemes, apply online, track approvals, compare market prices,
            and get training support through a single MSME-focused dashboard.
          </p>
          <div class="chips">
            <span class="chip">Fund Schemes</span>
            <span class="chip">Apply Now</span>
            <span class="chip">Track Status</span>
            <span class="chip">Technical Support</span>
            <span class="chip">Market Access</span>
          </div>
        </div>

        <div class="kpi">
          <div class="card">
            <div class="small">Eligible schemes</div>
            <h3>12</h3>
            <div class="muted">Matched to your business profile</div>
          </div>
          <div class="card">
            <div class="small">Applications</div>
            <h3>03</h3>
            <div class="muted">1 approved, 1 in review, 1 draft</div>
          </div>
          <div class="card">
            <div class="small">Training sessions</div>
            <h3>08</h3>
            <div class="muted">Available this month</div>
          </div>
          <div class="card">
            <div class="small">Market leads</div>
            <h3>24</h3>
            <div class="muted">Buyer and supplier opportunities</div>
          </div>
        </div>

        <div class="grid">
          <div class="stack">
            <div class="card">
              <div class="section-title">
                <h3>Featured Government Schemes</h3>
                <button class="btn btn-light" onclick="goToScreen('schemes')">View All</button>
              </div>
              <div class="cards">
                <div class="card scheme-card">
                  <span class="tag">Capital Support</span>
                  <h4>Subsidy for New Machines</h4>
                  <p class="muted">Support for equipment upgrades to improve productivity and manufacturing capacity.</p>
                  <div class="tag-row">
                    <span class="tag">Manufacturing</span>
                    <span class="tag">Upgradation</span>
                  </div>
                  <button class="btn btn-primary" onclick="openScheme('machines')">Apply Now</button>
                </div>

                <div class="card scheme-card">
                  <span class="tag">Credit Access</span>
                  <h4>Low-Interest MSME Loans</h4>
                  <p class="muted">Affordable financing for working capital, expansion, and business continuity needs.</p>
                  <div class="tag-row">
                    <span class="tag">Loans</span>
                    <span class="tag">Micro & Small</span>
                  </div>
                  <button class="btn btn-primary" onclick="openScheme('loans')">Apply Now</button>
                </div>

                <div class="card scheme-card">
                  <span class="tag">Startup Support</span>
                  <h4>First-Time Entrepreneur Assistance</h4>
                  <p class="muted">Support for new entrepreneurs with a focus on underserved categories and first-time founders.</p>
                  <div class="tag-row">
                    <span class="tag">Women</span>
                    <span class="tag">SC/ST</span>
                  </div>
                  <button class="btn btn-primary" onclick="openScheme('entrepreneur')">Apply Now</button>
                </div>
              </div>
            </div>

            <div class="card">
              <div class="section-title">
                <h3>Announcements & Deadlines</h3>
              </div>
              <div class="list">
                <div class="list-item">
                  <div>
                    <strong>Machine Subsidy Window</strong>
                    <div class="muted">Applications close on 30 April</div>
                  </div>
                  <span class="status warning">Closing Soon</span>
                </div>
                <div class="list-item">
                  <div>
                    <strong>Cluster Modernization Drive</strong>
                    <div class="muted">New intake expected in July 2026</div>
                  </div>
                  <span class="status review">Upcoming</span>
                </div>
                <div class="list-item">
                  <div>
                    <strong>Export Readiness Webinar</strong>
                    <div class="muted">Registration open for May 2026 batch</div>
                  </div>
                  <span class="status success">Open</span>
                </div>
              </div>
            </div>
          </div>

          <div class="stack">
            <div class="card">
              <div class="section-title">
                <h3>Market Prices</h3>
                <button class="btn btn-light" onclick="goToScreen('market')">View all</button>
              </div>
              <div class="list">
                <div class="list-item">
                  <div>Steel</div>
                  <div class="price">₹57/kg</div>
                </div>
                <div class="list-item">
                  <div>Copper</div>
                  <div class="price">₹813/kg</div>
                </div>
                <div class="list-item">
                  <div>Aluminium</div>
                  <div class="price">₹228/kg</div>
                </div>
              </div>
            </div>

            <div class="card">
              <div class="section-title">
                <h3>Technical Support & Trainings</h3>
              </div>
              <div class="list">
                <div class="list-item">
                  <div>
                    <strong>Chat with Experts</strong>
                    <div class="muted">Get scheme and documentation guidance</div>
                  </div>
                </div>
                <div class="list-item">
                  <div>
                    <strong>Video Tutorials</strong>
                    <div class="muted">Application walkthroughs and onboarding help</div>
                  </div>
                </div>
                <div class="list-item">
                  <div>
                    <strong>Consultation Booking</strong>
                    <div class="muted">Book a support call for your business case</div>
                  </div>
                </div>
              </div>
            </div>

            <div class="card">
              <div class="section-title">
                <h3>My Application Snapshot</h3>
              </div>
              <div>
                <h4 style="margin-bottom: 8px;">Subsidy for New Machines</h4>
                <span class="status review">In Review</span>
                <div class="timeline">
                  <div class="timeline-step">
                    <span class="dot done"></span>
                    <div><strong>Applied</strong><div class="muted">Application submitted successfully</div></div>
                  </div>
                  <div class="timeline-step">
                    <span class="dot done"></span>
                    <div><strong>Documents Submitted</strong><div class="muted">KYC and business proof verified</div></div>
                  </div>
                  <div class="timeline-step">
                    <span class="dot current"></span>
                    <div><strong>Approval Pending</strong><div class="muted">Expected update by July</div></div>
                  </div>
                </div>
                <div style="margin-top: 16px;">
                  <button class="btn btn-light" onclick="goToScreen('track')">View Full Status</button>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="footer-note">
          Prototype note: this is a front-end demo showing user journeys for discovery, application, and status tracking.
        </div>
      </section>

      <!-- SCHEMES -->
      <section class="screen" id="schemes">
        <div class="section-title">
          <h3>Available Schemes</h3>
          <div class="muted">Filter and explore schemes relevant to your business</div>
        </div>

        <div class="scheme-list" id="schemeList"></div>
      </section>

      <!-- SCHEME DETAIL -->
      <section class="screen" id="scheme-detail">
        <div class="detail-box">
          <div class="card">
            <div id="schemeDetailContent"></div>
          </div>
          <div class="stack">
            <div class="card">
              <h3>Eligibility Snapshot</h3>
              <div id="eligibilityBox" class="list"></div>
            </div>
            <div class="card">
              <h3>Quick Actions</h3>
              <div style="display:grid; gap:10px;">
                <button class="btn btn-primary" onclick="goToScreen('apply')">Start Application</button>
                <button class="btn btn-light" onclick="goToScreen('track')">Track Existing Application</button>
                <button class="btn btn-light" onclick="goToScreen('help')">Get Help</button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- APPLY -->
      <section class="screen" id="apply">
        <div class="card">
          <div class="section-title">
            <h3>Apply for a Scheme</h3>
            <div class="muted">Simulated form submission for prototype testing</div>
          </div>

          <form id="applicationForm">
            <div class="two-col">
              <label>
                Applicant Name
                <input type="text" name="name" placeholder="Enter full name" required />
              </label>

              <label>
                Business Name
                <input type="text" name="business" placeholder="Enter business name" required />
              </label>
            </div>

            <div class="two-col">
              <label>
                Scheme
                <select name="scheme" required>
                  <option value="">Select a scheme</option>
                  <option>Subsidy for New Machines</option>
                  <option>Low-Interest MSME Loans</option>
                  <option>First-Time Entrepreneur Assistance</option>
                  <option>Export Support Program</option>
                </select>
              </label>

              <label>
                Business Type
                <select name="type" required>
                  <option value="">Select business type</option>
                  <option>Manufacturing</option>
                  <option>Services</option>
                  <option>Trading</option>
                  <option>Food Processing</option>
                </select>
              </label>
            </div>

            <div class="two-col">
              <label>
                Udyam Number
                <input type="text" name="udyam" placeholder="UDYAM-XX-00-0000000" />
              </label>

              <label>
                Annual Turnover
                <input type="text" name="turnover" placeholder="e.g. ₹25 lakh" />
              </label>
            </div>

            <label>
              Purpose of Application
              <textarea name="purpose" placeholder="Describe machinery purchase, expansion plan, working capital needs, etc." required></textarea>
            </label>

            <div class="two-col">
              <label>
                Upload KYC
                <input type="file" />
              </label>
              <label>
                Upload Business Proof
                <input type="file" />
              </label>
            </div>

            <div style="display:flex; gap:12px; flex-wrap:wrap;">
              <button class="btn btn-primary" type="submit">Submit Application</button>
              <button class="btn btn-light" type="reset">Save as Draft</button>
            </div>
          </form>

          <div id="applicationSuccess" class="hidden" style="margin-top:18px;">
            <div class="card" style="background:#ecfdf5; border-color:#bbf7d0;">
              <h3 style="margin-top:0;">Application Submitted</h3>
              <p class="muted" style="color:#166534;">
                Your prototype application has been submitted successfully. Tracking ID:
                <strong id="trackingId"></strong>
              </p>
            </div>
          </div>
        </div>
      </section>

      <!-- TRACK -->
      <section class="screen" id="track">
        <div class="card">
          <div class="section-title">
            <h3>Track Applications</h3>
            <div class="muted">Monitor progress across all submitted schemes</div>
          </div>

          <div class="list" id="applicationsList"></div>
        </div>
      </section>

      <!-- MARKET -->
      <section class="screen" id="market">
        <div class="grid">
          <div class="card">
            <div class="section-title">
              <h3>Buy Raw Materials</h3>
            </div>
            <div class="list">
              <div class="list-item">
                <div>
                  <strong>Industrial Steel Sheets</strong>
                  <div class="muted">Supplier: Bharat Metals Hub</div>
                </div>
                <button class="btn btn-light">View</button>
              </div>
              <div class="list-item">
                <div>
                  <strong>Copper Wiring Rolls</strong>
                  <div class="muted">Supplier: Electro Source</div>
                </div>
                <button class="btn btn-light">View</button>
              </div>
              <div class="list-item">
                <div>
                  <strong>Packaging Cartons</strong>
                  <div class="muted">Supplier: PackRight India</div>
                </div>
                <button class="btn btn-light">View</button>
              </div>
            </div>
          </div>

          <div class="card">
            <div class="section-title">
              <h3>Sell Products Online</h3>
            </div>
            <div class="list">
              <div class="list-item">
                <div>
                  <strong>List Your Product</strong>
                  <div class="muted">Create a product page for buyers</div>
                </div>
              </div>
              <div class="list-item">
                <div>
                  <strong>Logistics Support</strong>
                  <div class="muted">Compare shipping and fulfillment options</div>
                </div>
              </div>
              <div class="list-item">
                <div>
                  <strong>Buyer Leads</strong>
                  <div class="muted">Connect with wholesale and institutional buyers</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- HELP -->
      <section class="screen" id="help">
        <div class="grid">
          <div class="card">
            <h3>Help Center</h3>
            <div class="list">
              <div class="list-item">
                <div>
                  <strong>How do I check scheme eligibility?</strong>
                  <div class="muted">Use search or browse schemes by business type, funding type, and category.</div>
                </div>
              </div>
              <div class="list-item">
                <div>
                  <strong>What documents are commonly required?</strong>
                  <div class="muted">KYC, business registration proof, bank details, and project purpose documents.</div>
                </div>
              </div>
              <div class="list-item">
                <div>
                  <strong>How do I track my application?</strong>
                  <div class="muted">Open the Track Applications section to view timeline stages and status updates.</div>
                </div>
              </div>
            </div>
          </div>

          <div class="card">
            <h3>Support Options</h3>
            <div class="list">
              <div class="list-item">
                <div>
                  <strong>Chat with Experts</strong>
                  <div class="muted">Live assisted support for filing and documentation</div>
                </div>
              </div>
              <div class="list-item">
                <div>
                  <strong>Video Tutorials</strong>
                  <div class="muted">Application walkthroughs and policy explainer videos</div>
                </div>
              </div>
              <div class="list-item">
                <div>
                  <strong>Consultation Booking</strong>
                  <div class="muted">Book a one-to-one support slot</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>

  <script>
    const schemeData = {
      machines: {
        title: "Subsidy for New Machines",
        description: "Financial assistance for MSMEs investing in machinery, equipment modernization, and productivity upgrades.",
        tags: ["Manufacturing", "Capital Subsidy", "Technology Upgrade"],
        eligibility: [
          "Registered MSME with valid business proof",
          "New machinery purchase or modernization plan",
          "Basic financial and KYC documents required"
        ]
      },
      loans: {
        title: "Low-Interest MSME Loans",
        description: "Access affordable credit for working capital, business expansion, and cash-flow support.",
        tags: ["Loans", "Credit Access", "Working Capital"],
        eligibility: [
          "Operational MSME or eligible applicant",
          "Repayment capacity and business use case",
          "Banking and identity documents required"
        ]
      },
      entrepreneur: {
        title: "First-Time Entrepreneur Assistance",
        description: "Support pathway for first-time founders, especially women and underserved entrepreneurs.",
        tags: ["Entrepreneurship", "Inclusion", "New Business"],
        eligibility: [
          "First-time entrepreneur",
          "New project proposal",
          "Identity, category proof if applicable, and business concept note"
        ]
      },
      export: {
        title: "Export Support Program",
        description: "Enable MSMEs to prepare for export markets with compliance, packaging, and market linkage support.",
        tags: ["Export", "Training", "Market Access"],
        eligibility: [
          "MSME with export intent or existing supply capability",
          "Product and compliance readiness",
          "Basic registration and business documentation"
        ]
      }
    };

    const applications = [
      {
        id: "MSME-24031",
        scheme: "Subsidy for New Machines",
        status: "In Review",
        className: "review",
        timeline: "Applied → Docs Submitted → Approval Pending"
      },
      {
        id: "MSME-24012",
        scheme: "Low-Interest MSME Loans",
        status: "Approved",
        className: "success",
        timeline: "Applied → Bank Review → Approved"
      },
      {
        id: "MSME-23988",
        scheme: "Export Support Program",
        status: "Draft",
        className: "warning",
        timeline: "Draft saved, submission pending"
      }
    ];

    function goToScreen(screenId) {
      document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
      const target = document.getElementById(screenId);
      if (target) target.classList.add('active');

      document.querySelectorAll('.nav-link').forEach(btn => {
        btn.classList.toggle('active', btn.dataset.screen === screenId);
      });
    }

    function renderSchemes(filter = "") {
      const container = document.getElementById("schemeList");
      const entries = Object.entries(schemeData).filter(([_, item]) => {
        const q = filter.toLowerCase();
        return (
          item.title.toLowerCase().includes(q) ||
          item.description.toLowerCase().includes(q) ||
          item.tags.join(" ").toLowerCase().includes(q)
        );
      });

      container.innerHTML = entries.map(([key, item]) => `
        <div class="card scheme-card">
          <div class="tag-row">
            ${item.tags.map(tag => `<span class="tag">${tag}</span>`).join("")}
          </div>
          <h3>${item.title}</h3>
          <p class="muted">${item.description}</p>
          <div style="display:flex; gap:10px; flex-wrap:wrap;">
            <button class="btn btn-primary" onclick="openScheme('${key}')">View Details</button>
            <button class="btn btn-light" onclick="goToScreen('apply')">Apply</button>
          </div>
        </div>
      `).join("");
    }

    function openScheme(key) {
      const scheme = schemeData[key];
      if (!scheme) return;

      document.getElementById("schemeDetailContent").innerHTML = `
        <div class="tag-row" style="margin-bottom:10px;">
          ${scheme.tags.map(tag => `<span class="tag">${tag}</span>`).join("")}
        </div>
        <h2 style="margin-top:0;">${scheme.title}</h2>
        <p class="muted">${scheme.description}</p>

        <h3>Benefits</h3>
        <ul>
          <li>Centralized discovery of a relevant scheme</li>
          <li>Simplified application support through a unified interface</li>
          <li>Status tracking and guided document submission</li>
        </ul>

        <h3>Prototype Flow</h3>
        <p class="muted">Check eligibility → submit business details → upload documents → track approval stages.</p>
      `;

      document.getElementById("eligibilityBox").innerHTML = scheme.eligibility.map(item => `
        <div class="list-item">
          <div>${item}</div>
        </div>
      `).join("");

      goToScreen("scheme-detail");
    }

    function renderApplications() {
      const list = document.getElementById("applicationsList");
      list.innerHTML = applications.map(app => `
        <div class="list-item">
          <div>
            <strong>${app.scheme}</strong>
            <div class="muted">Tracking ID: ${app.id}</div>
            <div class="muted">${app.timeline}</div>
          </div>
          <span class="status ${app.className}">${app.status}</span>
        </div>
      `).join("");
    }

    document.querySelectorAll(".nav-link").forEach(btn => {
      btn.addEventListener("click", () => goToScreen(btn.dataset.screen));
    });

    document.getElementById("applicationForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const tracking = "MSME-" + Math.floor(10000 + Math.random() * 90000);
      document.getElementById("trackingId").textContent = tracking;
      document.getElementById("applicationSuccess").classList.remove("hidden");

      applications.unshift({
        id: tracking,
        scheme: this.scheme.value || "Selected Scheme",
        status: "Submitted",
        className: "review",
        timeline: "Application submitted → Initial verification pending"
      });

      renderApplications();
      this.reset();
    });

    document.getElementById("searchBtn").addEventListener("click", () => {
      const value = document.getElementById("globalSearch").value.trim();
      renderSchemes(value);
      goToScreen("schemes");
    });

    document.getElementById("globalSearch").addEventListener("keydown", (e) => {
      if (e.key === "Enter") {
        e.preventDefault();
        document.getElementById("searchBtn").click();
      }
    });

    renderSchemes();
    renderApplications();
  </script>
</body>
</html>
