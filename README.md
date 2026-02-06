# Luxury-Residential-Property-Analysis
This project identifies and analyzes luxury single-family residences valued at $2,000,000 USD and above located within a 30-minute drive-time radius of the intersection of Yamato Rd &amp; US-441, Boca Raton, FL. The final output categorizes these properties by their gated community status and residency type.

# Strategic Use Cases
This analysis transforms raw municipal data into actionable business intelligence. Key applications include:

Precision Real Estate Marketing: Enables high-end service providers (wealth management, luxury landscaping, or home security) to target households with a verified property interest of $2M+, significantly reducing marketing waste.

Site Selection & Economic Study: Assists luxury brands and retail developers in identifying the "wealth-shed" within a 30-minute commute of core Boca Raton business hubs.

Security & Privacy Assessment: The categorization of Gated vs. Non-Gated status provides a baseline for privacy consultants and high-net-worth individuals to evaluate neighborhood perimeter security.

Investment Portfolio Analysis: The Owner-Occupancy logic (matching site to mailing addresses) helps identify high-value secondary residences and potential investment opportunities within the Palm Beach County luxury market.

# Data Sources

Parcel Geometry & Attributes: Obtained from the Palm Beach County Open Source Database.

Drive-Time Boundaries: Derived using the OpenStreetMap (OSM) Isochrone function.

Community Metadata: Supplemented by publicly available registries of gated communities and residential associations.

# Technical Workflow
**Step 1:** Spatial Filtering (Isochrone Analysis)
A starting point was established at Yamato Rd & US-441.

An OSM Isochrone function was run to generate a polygon representing all areas reachable within a 30-minute drive.

The raw Palm Beach County parcel dataset was clipped to this polygon to isolate properties within the requested radius.

**Step 2:** Attribute Calculation (Total Value Logic)
To accurately reflect market value, a new field, Total_Value, was calculated.


Formula: Land Value + Improvement Value = Total_Value.

Any properties with a Total_Value below $2,000,000 were filtered out of the final dataset.

**Step 3:** Residency Determination (Owner-Occupier Logic)
To identify if a property is a primary residence or an investment/rental, the Site Address was cross-referenced with the Owner’s Mailing Address.


Logical Inference: If the addresses are an exact match, the property is classified as Owner-Occupied, assuming the owner resides on-site.

**Step 4:** Classification of Gated Status
Properties were categorized into three distinct classes:


Gated: Verified restricted-access community.


Likely Gated: Inferred status based on neighborhood spatial layout and private infrastructure.


Not-Gated: Open-access parcels or standard street-frontage properties.

**Step 5:** Output Generation & Packaging
The processed data was exported into three primary formats for the client:

KMZ Files: Designed for interactive 3D viewing in Google Earth.


CSV Files: A cleaned table (Boca_Roca_clean.csv) containing only essential columns.

PDF Layout: A professional static map for high-level reporting.


ArcGIS Package: The full project file (.mpkx) for use in professional GIS software.
