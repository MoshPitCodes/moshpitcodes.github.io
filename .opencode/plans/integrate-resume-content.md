# Plan: Integrate Resume Content into Portfolio

## Task Description
Enrich the portfolio site (`index.html`) with professional content from `modern-min-resume1.html`. This covers five areas:

1. **Enrich Professional Work section** — expand from 2 generic cards to 4 detailed cards with quantified achievements, one for each major role (SSC-Services, SER Solutions, eviatec, mpl Software).
2. **Add Certifications section** — new section `06` between Journey and Contact showing 11 certifications in a compact grid.
3. **Expand Journey timeline** — add education entries and flesh out early-career history with concrete detail from the resume.
4. **Update hero stats** — replace the playful stats with more professional metrics from the resume (10+ years, 35+ projects, 5+ teams led) while keeping the tone.
5. **Update terminal meta** — reflect Boeblingen location and richer context.

## Objective
When complete, the portfolio will contain the full professional depth of the resume — quantified achievements, certifications, complete career history, and education — while maintaining the site's casual, personality-driven tone. Visitors will get a comprehensive picture of Patrick's career without needing to view a separate resume.

## Problem Statement
The portfolio's Professional Work section currently has only 2 generic cards with no quantified achievements. The Journey timeline is sparse and missing education entirely. There's no certifications section. The hero stats use joke metrics ("2AM flake debugs") instead of showcasing real professional breadth. The resume file contains rich, specific data (achievement percentages, certification names, education details) that would significantly strengthen the portfolio's credibility.

## Solution Approach
Work within the existing single-file architecture. Key decisions:

- **Professional Work section**: Replace the 2 existing generic cards with 4 detailed cards (SSC-Services, SER Solutions, eviatec, mpl Software). Each card gets a description paragraph with 2-3 key quantified achievements woven into natural prose (matching the site's tone), plus the standard Core/Automation/Stack footer. Early-career roles (working students, internships) are NOT added as cards — they belong in the Journey timeline.
- **Certifications section**: New section numbered `06` placed between Journey (`05`) and Contact. Uses a compact grid of certification badges/pills rather than full cards. CSS reuses existing patterns with minimal new classes.
- **Journey timeline**: Add 2-3 new timeline entries for education and flesh out existing entries with more specific achievements from the resume. Keep the timeline focused on major milestones (not every working student role).
- **Hero stats**: Keep 4 stats but replace 2 joke stats with professional ones. Proposed: `10+` Years Building, `35+` Projects Shipped, `5+` Teams Led, `1` Homelab (growing).
- **Terminal meta**: Update location from Stuttgart to Boeblingen.
- **Nav**: Add "Certs" link for the new certifications section.

## Relevant Files
- `index.html` — the entire site. All changes happen here.
- `modern-min-resume1.html` — read-only reference for content.

### New Files
- None required.

## Implementation Phases

### Phase 1: Professional Work Enrichment
- Replace the 2 existing cards with 4 detailed role cards.
- Add quantified achievements in natural prose.
- Update card tags and footers.

### Phase 2: Certifications Section
- Add CSS for certification grid and badges.
- Create new section with 11 certifications.
- Update section numbering and nav.

### Phase 3: Journey & Hero Updates
- Expand timeline with education entries.
- Flesh out existing timeline entries with achievement specifics.
- Update hero stats with professional metrics.
- Update terminal meta location.

### Phase 4: Validation
- Responsive testing at all breakpoints.
- Content accuracy check against resume.
- Nav behavior verification.

## TD Tasks

### 1) Enrich Professional Work with detailed role cards
- Title: `Enrich Professional Work section with 4 detailed role cards`
- Type: `feature`
- Priority: `P0`
- Acceptance Criteria:
  - 4 project cards in the Professional Work section: SSC-Services, SER Solutions, eviatec, mpl Software.
  - Each card has a description paragraph with 2-3 quantified achievements.
  - Each card has appropriate tags and Core/Automation/Stack footer.
  - Cards are ordered chronologically (newest first).

### 2) Add Certifications section
- Title: `Add Certifications section with 11 certifications`
- Type: `feature`
- Priority: `P0`
- Acceptance Criteria:
  - New section numbered `06` between Journey and Contact.
  - Shows all 11 certifications with title, issuer, and year.
  - Uses a compact grid layout.
  - Nav updated with "Certs" link.
  - Section numbering: Journey stays `05`, new Certs becomes `06`.

### 3) Expand Journey timeline with education and achievements
- Title: `Expand Journey timeline with education and richer detail`
- Type: `enhancement`
- Priority: `P1`
- Acceptance Criteria:
  - Education entries added: HS Mannheim (Business Info Systems), HS Pforzheim, Macromedia.
  - Existing timeline entries enriched with specific achievements from resume.
  - Timeline remains focused on major milestones (no separate entry per working student role).
  - Entries are in reverse chronological order.

### 4) Update hero stats and terminal meta
- Title: `Update hero stats with professional metrics and fix terminal location`
- Type: `enhancement`
- Priority: `P1`
- Acceptance Criteria:
  - Hero stats: `10+` Years Building, `35+` Projects Shipped, `5+` Teams Led, `1` Homelab (growing).
  - Terminal meta shows `location=Boeblingen` instead of `location=Stuttgart`.
  - Counter animation still works on numeric stat values.

### 5) Validate responsive layout and content accuracy
- Title: `Validate responsive layout, content accuracy, and nav behavior`
- Type: `task`
- Priority: `P1`
- Acceptance Criteria:
  - All 4 professional cards render correctly at 360/768/1024/1280px.
  - Certifications grid is responsive and readable at all breakpoints.
  - Timeline doesn't overflow or clip.
  - Nav highlights correctly for all sections including new Certs.
  - Content matches resume data exactly (cert names, years, achievement numbers).
  - No JS console errors.

```bash
td create "Integrate resume content into portfolio" --type feature --priority P0 --description "Enrich portfolio with resume data: detailed professional cards, certifications section, expanded timeline, updated hero stats."
# Save returned id as <PARENT_ID>

td create "Enrich Professional Work section with 4 detailed role cards" --type feature --priority P0 --parent <PARENT_ID> --description "Replace 2 generic cards with 4 detailed role cards (SSC, SER, eviatec, mpl) with quantified achievements and proper footers."
td create "Add Certifications section with 11 certifications" --type feature --priority P0 --parent <PARENT_ID> --description "New section 06 between Journey and Contact. Compact grid with all 11 certs. Nav updated with Certs link."
td create "Expand Journey timeline with education and richer detail" --type enhancement --priority P1 --parent <PARENT_ID> --description "Add education entries (HS Mannheim, Pforzheim, Macromedia). Enrich existing entries with achievement specifics."
td create "Update hero stats with professional metrics and fix terminal location" --type enhancement --priority P1 --parent <PARENT_ID> --description "Hero: 10+ Years, 35+ Projects, 5+ Teams Led, 1 Homelab. Terminal: location=Boeblingen."
td create "Validate responsive layout, content accuracy, and nav behavior" --type task --priority P1 --parent <PARENT_ID> --description "Test at 360/768/1024/1280px. Verify cert grid, professional cards, timeline, nav. Content must match resume exactly."

td start <TASK_ID_FOR_PROFESSIONAL_CARDS>
```

## Step by Step Tasks
IMPORTANT: Execute every step in order, top to bottom.

### 1. Replace Professional Work cards with 4 detailed role cards
Replace the existing 2 cards in `<section id="work">` with 4 cards:

**Card 1: SSC-Services (2022 - Present)**
- Tags: `green` DevOps, `blue` Cloud, `amber` Product
- Title: "IT Consultant & Product Owner — SSC-Services"
- Description: "The current chapter. Leading DevOps transformation that cut deployment time by 11%, managing cloud migration projects worth over one million euros, and implementing agile practices across 5 teams. I own a 400+ item product backlog and have optimized operational processes by 17%. It's the kind of role where no two weeks look the same."
- Footer: `Core: Platform Ownership` / `Automation: DevOps Pipelines` / `Stack: Azure + IaC`

**Card 2: SER Solutions (2019)**
- Tags: `blue` ECM, `green` Automation
- Title: "IT Consultant & Project Lead — SER Solutions"
- Description: "Managed Doxis4 iECM Suite implementation for 3 enterprise clients. The headline achievement: reducing invoice processing time by 60%. Led workshops with 50+ stakeholders and trained 100+ users on systems they initially didn't want."
- Footer: `Core: Document Management` / `Automation: Invoice Processing` / `Stack: Doxis4 + SQL Server`

**Card 3: eviatec Systems AG (2018)**
- Tags: `blue` ECM, `purple` Architecture
- Title: "ECM Consultant & Solution Architect — eviatec"
- Description: "Architected ELO ECM enterprise solutions and redesigned legacy system landscapes. Handled pre-sales technical consulting and managed QA processes. The role where I learned that selling a solution is almost as important as building it."
- Footer: `Core: Solution Architecture` / `Automation: ELO Workflows` / `Stack: ELO + Windows Server`

**Card 4: mpl Software (2016 - 2018)**
- Tags: `green` Dev, `blue` Backend
- Title: "Software Developer — mpl Software"
- Description: "Where it all started properly. Built custom enterprise software, implemented third-party integrations, and enhanced the company's proprietary product suite. First real taste of CRM development with CAS genesisWorld and full-stack work with C#, Node.js, and AngularJS."
- Footer: `Core: Enterprise Software` / `Automation: System Integration` / `Stack: C# + Node.js`

### 2. Add CSS for certifications grid
Add after the existing timeline CSS (before `/* --- Contact --- */`):

```css
/* --- Certifications --- */
.certs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 16px;
}

.cert-item {
  background: var(--bg-elevated);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 18px 22px;
  transition: all 0.3s var(--ease-out);
}

.cert-item:hover {
  border-color: var(--border-light);
  transform: translateY(-2px);
}

.cert-name {
  font-size: 14px;
  font-weight: 500;
  color: var(--text);
  margin-bottom: 4px;
}

.cert-meta {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--text-dim);
}

.cert-meta .cert-year {
  color: var(--accent);
}
```

### 3. Create Certifications section HTML
Add a new section after the Journey section (before Contact):

```html
<!-- Certifications -->
<section id="certs">
  <div class="container">
  <div class="section-header reveal">
    <span class="section-num">06</span>
    <span class="section-title">Certifications</span>
    <div class="section-line"></div>
  </div>

  <div class="certs-grid">
    <!-- 2024 -->
    <div class="cert-item reveal">
      <div class="cert-name">Professional Scrum Product Owner (PSPO)</div>
      <div class="cert-meta">Scrum.org · <span class="cert-year">2024</span></div>
    </div>
    <div class="cert-item reveal reveal-delay-1">
      <div class="cert-name">Professional Scrum Master I (PSM I)</div>
      <div class="cert-meta">Scrum.org · <span class="cert-year">2024</span></div>
    </div>
    <div class="cert-item reveal reveal-delay-2">
      <div class="cert-name">CPRE-AL Requirements Engineering</div>
      <div class="cert-meta">iSQI Group · <span class="cert-year">2024</span></div>
    </div>
    <!-- 2023 -->
    <div class="cert-item reveal">
      <div class="cert-name">ITIL 4 Foundation</div>
      <div class="cert-meta">PeopleCert · <span class="cert-year">2023</span></div>
    </div>
    <!-- 2019 -->
    <div class="cert-item reveal reveal-delay-1">
      <div class="cert-name">Doxis4 BPM</div>
      <div class="cert-meta">SER Group · <span class="cert-year">2019</span></div>
    </div>
    <div class="cert-item reveal reveal-delay-2">
      <div class="cert-name">Doxis4 Systemadministration</div>
      <div class="cert-meta">SER Group · <span class="cert-year">2019</span></div>
    </div>
    <div class="cert-item reveal">
      <div class="cert-name">Doxis4 winCube Scripting</div>
      <div class="cert-meta">SER Group · <span class="cert-year">2019</span></div>
    </div>
    <div class="cert-item reveal reveal-delay-1">
      <div class="cert-name">Doxis4 CSB Fachadministration</div>
      <div class="cert-meta">SER Group · <span class="cert-year">2019</span></div>
    </div>
    <div class="cert-item reveal reveal-delay-2">
      <div class="cert-name">Doxis4 CSB Overview</div>
      <div class="cert-meta">SER Group · <span class="cert-year">2019</span></div>
    </div>
    <!-- 2017-2018 -->
    <div class="cert-item reveal">
      <div class="cert-name">Certified Solution Developer</div>
      <div class="cert-meta">CAS Software AG · <span class="cert-year">2018</span></div>
    </div>
    <div class="cert-item reveal reveal-delay-1">
      <div class="cert-name">Certified Solution Developer</div>
      <div class="cert-meta">CAS Software AG · <span class="cert-year">2017</span></div>
    </div>
  </div>
  </div>
</section>
```

### 4. Update nav with Certs link
Add `<a href="#certs" class="nav-link">Certs</a>` between Journey and Contact in the nav.

### 5. Expand Journey timeline
Replace the existing timeline with an expanded version that includes education:

**Updated entries (reverse chronological):**
1. `2022 - NOW` — Product Owner & IT Consultant, SSC-Services (existing, add: "Led DevOps transformation cutting deployment time by 11%. Managing cloud migration projects and a 400+ item product backlog.")
2. `2019 - 2022` — Self-employed IT Consultant (existing, keep as-is)
3. `2019` — IT Consultant & Project Lead, SER Solutions (new — "Managed Doxis4 implementations for 3 enterprise clients. Cut invoice processing time by 60% and trained 100+ users.")
4. `2018` — ECM Consultant & Solution Architect, eviatec (existing entry merged, add specifics)
5. `2016 - 2018` — Software Developer, mpl Software (existing, enrich)
6. `2012 - 2018` — B.Sc. Business Information Systems, HS Mannheim (new education entry — "Focus on Enterprise Architecture, Software Engineering, and BPM. Thesis: Gamification in SMEs.")
7. `2013 - 2016` — The Early Days (existing, keep)
8. `2010 - 2012` — Business Administration, HS Pforzheim (new education entry)
9. `2005 - 2007` — Media & Event Management, Macromedia (new education entry)

### 6. Update hero stats
Replace the current hero-stats content:
- `10+` Years Building
- `35+` Projects Shipped
- `5+` Teams Led
- `1` Homelab (growing)

Remove `data-count="2"` from the old "2AM Flake Debugs" stat. Add `data-count` attributes to `35+` and `5+` for counter animation.

### 7. Update terminal meta
Change `location=Stuttgart` to `location=Boeblingen` in the terminal typing animation lines.

### 8. Add responsive rules for certifications
Add to the `@media (max-width: 768px)` block:
```css
.certs-grid { grid-template-columns: 1fr; }
```

### 9. Validate everything
- Serve locally and verify:
  - 4 professional cards with achievements render correctly.
  - Certifications section shows all 11 certs in a responsive grid.
  - Journey timeline has education entries interspersed chronologically.
  - Hero stats show professional metrics.
  - Terminal shows Boeblingen.
  - Nav has 7 links: About, Projects, Work, Stack, Journey, Certs, Contact.
  - All reveal animations fire.
  - No JS console errors.

## Testing Strategy
- **Content accuracy**: Cross-reference every achievement number, certification name, education detail, and date against `modern-min-resume1.html`.
- **Layout**: Test certifications grid at 1280px (expect 3-4 columns), 768px (2 columns), 360px (1 column).
- **Professional cards**: 4 cards in a 3-column grid means row 1 has 3, row 2 has 1 — should look intentional.
- **Timeline length**: With ~9 entries, verify the timeline line gradient extends properly and doesn't cut off.
- **Nav**: 7 links should still fit on desktop. Mobile hamburger menu should accommodate the extra link.
- **Hero animation**: Counter animation on `35+` and `5+` stats should work. The `+` suffix needs to be preserved after animation.

## Acceptance Criteria
- Professional Work section has 4 cards with quantified achievements matching resume data.
- Certifications section (`06`) shows all 11 certifications with correct names, issuers, and years.
- Journey timeline includes education entries (HS Mannheim, Pforzheim, Macromedia).
- Hero stats: 10+ Years Building, 35+ Projects Shipped, 5+ Teams Led, 1 Homelab (growing).
- Terminal meta: `location=Boeblingen`.
- Nav: 7 links including "Certs".
- All section numbers correct: 01-06.
- Responsive layout works at 360/768/1024/1280px.
- No JS console errors.
- All content matches `modern-min-resume1.html` exactly.

## Validation Commands
Execute these commands to validate the task is complete:

- `python3 -m http.server 4173` — Serve the site locally.
- `grep -c 'project-card' index.html` — Count project cards in Professional Work (expect ~4 in work section).
- `grep -c 'cert-item' index.html` — Count certification items (expect 11 + CSS references).
- `grep -c 'timeline-item' index.html` — Count timeline entries (expect ~9).
- `grep -c 'section-num' index.html` — Count section numbers (expect 6: 01-06).
- `grep 'id="certs"' index.html` — Verify certifications section exists.
- `grep 'Boeblingen\|Böblingen' index.html` — Verify location update.
- `grep '35+\|5+' index.html` — Verify hero stats.
- `grep 'PSPO\|PSM I\|ITIL' index.html` — Verify certifications present.

## Notes
- The tone of professional card descriptions should match the existing site voice: casual, self-aware, slightly wry. Not corporate-speak.
- Early-career roles (working students, internships) are NOT individual professional cards — they stay summarized in the Journey timeline's "Early Days" entry. The portfolio is not a CV; it highlights significant roles.
- The certifications section uses a simpler layout than project cards since certs are informational, not interactive stories.
- Education entries in the Journey timeline use a slightly different visual treatment (could use a different dot color or a book icon) to distinguish them from career entries.
- Counter animation for `35+` needs to handle the `+` suffix — the animation counts to 35, then appends `+`.
