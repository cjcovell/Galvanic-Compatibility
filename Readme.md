# Galvanic compatibility

An interactive reference tool for predicting corrosion intensity between dissimilar metals in exterior building assemblies.

**[→ Live demo](https://YOUR-USERNAME.github.io/galvanic-compatibility/)**

![Screenshot of the tool](screenshot.png)

-----

## What it does

Pick any two metals commonly used on building exteriors and the tool tells you:

- The **potential difference** in millivolts between them
- A **severity rating** (Compatible / Mild / Moderate / Severe) calibrated to the exposure environment
- Which metal will **corrode** (anode) and which will be **protected** (cathode)
- Specific **detailing guidance** — gaskets, isolators, fastener choices, the area-ratio rule

The exposure selector — **Sheltered**, **Standard**, or **Coastal** — adjusts the severity thresholds, because the same potential difference behaves very differently in a ventilated soffit than it does 50 yards from the ocean.

## Who it’s for

- Architects specifying flashing, fasteners, cladding, and rooftop equipment
- Contractors making field substitutions
- Building science teachers and students learning electrochemistry
- Anyone who’s ever wondered why the screws on their aluminum gutter rotted out

## Use it on the web, embed it, or fork it

**Standalone page**
Just visit the live demo link above.

**Iframe embed**

```html
<iframe src="https://YOUR-USERNAME.github.io/galvanic-compatibility/"
        style="width:100%;border:0;height:1600px;"
        title="Galvanic compatibility"></iframe>
```

**Deep-linking**
Append URL parameters to load a specific scenario:

```
?a=aluminum&b=copper&env=coastal
```

Useful for linking from a product page directly to a relevant compatibility check, or sharing a result with a colleague.

Metal IDs: `magnesium`, `zinc`, `aluminum`, `mild-steel`, `weather-steel`, `lead`, `brass`, `copper`, `bronze`, `stainless`, `titanium`
Environment IDs: `sheltered`, `standard`, `coastal`

**Inline integration**
The whole tool is one HTML file — no build step, no JavaScript dependencies, no framework. Copy the `<main>`, `<style>`, and `<script>` blocks into your own page and it just works. CSS variables at the top of the stylesheet make rebranding trivial.

## Methodology

Potentials are referenced to the saturated calomel electrode (SCE) in flowing seawater, drawn from standard corrosion engineering references including ASTM G82 and MIL-STD-889. Values are rounded to two decimal places for clarity.

Severity thresholds are based on the conventional rule of thumb that potential differences below ~150 mV are tolerable in most environments, while differences above ~500 mV produce aggressive galvanic action. The exposure multipliers (×2.0 for sheltered, ×1.0 for standard, ×0.5 for coastal) reflect how electrolyte availability changes the rate at which a given potential difference produces visible corrosion.

## Limitations

This is a **design screening tool**, not a substitute for project-specific corrosion engineering. It does not account for:

- Crevice, pitting, or stress corrosion mechanisms
- Microclimate effects (industrial pollution, agricultural runoff, road salt)
- Surface treatments (anodizing, powder coating, passivation)
- Area ratios between the two metals (mentioned in the detailing notes but not modeled quantitatively)
- Time-dependent passivation or weathering of the metals

For critical assemblies — coastal high-rises, marine structures, anything with a 50-year design life — consult a corrosion engineer.

## Technical

- **Single file**, no build system, no dependencies beyond Google Fonts
- **~27 KB** uncompressed
- **No data collection**, no tracking, no external API calls
- **Responsive** down to mobile widths
- **Print stylesheet** included — outputs cleanly for spec packages
- **Keyboard accessible** with `aria-live` on the result region
- **Respects** `prefers-reduced-motion`

## License

[Choose a license — MIT is the most permissive, CC-BY-NC if you want attribution and to prevent commercial reuse]

## Contributing

Issues and pull requests welcome. Particularly interested in:

- Additional metals relevant to building exteriors
- Refined potential values from regional standards (EN, ISO)
- Translations
- Better severity calibration backed by field data
