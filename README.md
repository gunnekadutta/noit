# Noit: skincare ingredient intelligence

> **Know what’s in it.** A source aware skincare product checker that turns an ingredient list into clear context, personal preferences, and confident product comparisons.

**Project status:** early interactive prototype  
**Current interface:** static responsive web page  
**Current product data:** fictional samples only  
**Medical use:** Noit is educational software and does not diagnose allergies, skin conditions, or safety.

---

## Why Noit

Skincare labels can contain dozens of unfamiliar ingredients, while most existing tools reduce a product to a single universal score. That hides the context people actually need:

- What does this ingredient do in the formula?
- Why has it been flagged?
- Does the concern apply to my own sensitivity or preference?
- Which source supports the explanation?
- Has the formula changed since the last time I bought it?

Noit is being designed to make those answers visible. It will explain the formula, show uncertainty when information is incomplete, and leave the choice with the shopper.

---

## What the current prototype does

The current landing page is a functional front end concept. It uses three fictional skincare products to demonstrate the product experience.

| Feature | Current behaviour |
| --- | --- |
| Product search | Searches three fictional products by name or sample ingredient |
| Ingredient notes | Shows a concise note explaining a possible concern |
| Product score | Shows a sample score out of 10 with clear limitations |
| Alternative | Shows a fictional alternative with its own sample score |
| Comparison | Lets visitors compare any two sample formulas |
| Responsive layout | Uses a desktop sidebar and compact mobile navigation |

Open outputs/index.html in a browser to explore the prototype.

---

## Product vision

Noit will be a product recognition and ingredient intelligence service.

### Main product flow

~~~text
Search, barcode scan, or label photo
        ↓
Find a verified product and formula version
        ↓
Normalize the ingredient list into INCI entities
        ↓
Apply published rules and the user’s preferences
        ↓
Show source linked explanations, comparison, and uncertainty
~~~

### Planned capabilities

1. **Product search**  
   Find products by brand, name, product type, market, and barcode.

2. **Ingredient list analysis**  
   Paste an INCI list or scan a package label when the product is not yet in the catalog.

3. **Personal preferences**  
   Let shoppers save ingredients they prefer, avoid, or know they are sensitive to.

4. **Product comparison**  
   Compare formula versions, ingredient notes, and user specific matches side by side.

5. **Formula history**  
   Preserve regional and reformulated versions rather than treating a product name as one permanent formula.

6. **Mobile companion**  
   Add barcode scanning, label photography, saved products, and in store comparison once the product database and API are reliable.

---

## How product recognition will work

Noit will use structured data retrieval before any AI explanation.

| Input | Recognition path |
| --- | --- |
| Product name | Match brand, product name, variant, market, and formula version against the catalog |
| Barcode | Resolve GTIN or UPC in Noit’s catalog, then use a verified secondary source only as a fallback |
| Label photo | Use OCR to extract the ingredient section, normalize INCI names, and analyze the list even if the exact product is unknown |
| Pasted ingredients | Parse the raw INCI string, map aliases to known ingredients, then apply evidence rules |

Each real product record should include its barcode, market, source link or label photo, raw ingredient list, normalized ingredients, formula version, last verified date, and confidence level.

AI will help interpret known data and write plain language summaries. It must not invent product formulas, citations, confidence, or medical safety claims.

---

## Safety and scoring principles

Noit should not call an ingredient universally good, bad, safe, or harmful without context.

- A flag means “worth reviewing for this reason,” not “unsafe for everyone.”
- Every ingredient note should cite its evidence source or state that evidence is limited.
- Scores should explain their inputs and limits.
- Unknown concentration, market, or formula version should reduce confidence instead of producing a definitive answer.
- Users with a reaction or known allergy should be directed to a qualified health professional.

The EU [CosIng database](https://single-market-economy.ec.europa.eu/sectors/cosmetics/cosmetic-ingredient-database_en) is a useful ingredient reference, but it is informational and does not itself determine legal status. General consumer guidance can also reference the [FDA overview of cosmetic allergens](https://www.fda.gov/cosmetics/cosmetic-ingredients/allergens-cosmetics) and the [American Academy of Dermatology guide to testing skin care products](https://www.aad.org/public/everyday-care/skin-care-secrets/prevent-skin-problems/test-skin-care-products).

---

## Proposed product architecture

~~~text
Responsive web app / future mobile app
                ↓
             Noit API
                ↓
Product catalog · Formula versions · Ingredient evidence · User preferences
                ↓
Verified labels, brand sources, and curated regulatory or scientific references
~~~

### Core data records

| Record | Purpose |
| --- | --- |
| Product | Brand, name, category, barcode, and market |
| Formula version | Raw INCI list, effective date, label image, source, and verification date |
| Ingredient | INCI name, aliases, function, evidence notes, and citations |
| Rule | The condition that produces a note, target audience, severity, and confidence |
| User preference | Ingredients a user wants to avoid, prefer, or monitor |

---

## Technology

### Current prototype

| Layer | Technology |
| --- | --- |
| Front end | Semantic HTML, CSS, and vanilla JavaScript |
| Typography | Manrope via Google Fonts |
| Product data | Three fictional in browser sample records |
| Hosting | Not deployed |

### Proposed production direction

| Layer | Recommended responsibility |
| --- | --- |
| Responsive web | Product search, ingredient analysis, comparison, account preferences |
| API | Product retrieval, formula versioning, ingredient normalization, scoring rules |
| Database | Product catalog, formulas, evidence, citations, user settings |
| AI | OCR assistance, alias matching, and sourced plain language explanations |
| Mobile app | Barcode scan, camera capture, saved products, in store comparison |

The production framework, database, hosting provider, and AI provider have not been selected. This avoids locking the project to a stack before validating the product catalog and scoring methodology.

---

## Local setup

### Prerequisites

- Git
- A modern browser
- Visual Studio Code, optional

### Open the prototype

1. Clone the repository after a remote Git host has been connected.

~~~powershell
git clone <your-repository-url>
cd use-the-landing-page-design-skill
~~~

2. Open the folder in Visual Studio Code.

3. Open outputs/index.html in a browser.

There are currently no package dependencies, environment variables, API keys, or build commands.

---

## Project structure

~~~text
noit/
├── outputs/
│   └── index.html       # Interactive landing page prototype
├── .gitignore           # Local, secret, and dependency exclusions
└── README.md            # Product narrative and build plan
~~~

---

## Roadmap

### Phase 1: validate the product

- Test the landing page and concept with target users.
- Decide the first launch market, target audience, and initial product categories.
- Define an evidence and scoring methodology with qualified review.

### Phase 2: build the trusted catalog

- Add a small set of manually verified products.
- Store sources, label images, market, formula versions, and verification dates.
- Build ingredient normalization and source linked notes.

### Phase 3: build the MVP

- Product name search
- Paste ingredient list analysis
- Two product comparison
- Incorrect formula reporting and an internal review queue

### Phase 4: prepare for mobile

- Publish a stable API.
- Add barcode lookup and product submission flows.
- Build a mobile app that uses the same catalog and scoring engine.


---

## License

No license has been selected yet.
