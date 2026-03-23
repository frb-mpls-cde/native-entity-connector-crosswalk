# 👋 About the data

*This page describes the goals of the Native Entity Connector Crosswalk and how it's assembled. For further technical details, please download the crosswalk and see its `data_dictionary` tab.*

------------------------------------------------------------------------

## 🎯Purpose

The [Native Entity Connector Crosswalk](https://www.minneapolisfed.org/indiancountry/resources/public-indian-country-datasets) is a public data product from the [Center for Indian Country Development (CICD)](https://www.minneapolisfed.org/indiancountry) at the Federal Reserve Bank of Minneapolis.

Sources of information focused on Native communities, governments, and other concepts are often difficult to connect to one another. Datasets often refer to Native entities in slightly different ways, making linkages challenging across scattered sources. Various information systems include only selected subsets of Native entities and typically do not reflect distinctive relationships among peoples, governance structures, and geographies.

This disconnected data landscape can make it daunting and time-intensive for analysts, researchers, students, and others working in Indian Country to explore their own research questions—especially when those questions involve links between data sources or over time.

To make the connections that will support more streamlined data work in Indian Country, CICD offers the Native Entity Connector Crosswalk. The crosswalk is built on an expansive and growing system of unique identifiers for government-recognized Native entities. This new system of identifiers is designed to be human-readable, comprehensive, consistent across data applications, and reflective of relationships between peoples and places.

The Native Entity Connector Crosswalk maps to other relevant public data sources, where these exist—such as resources from the U.S. Census Bureau and the Bureau of Indian Affairs. This allows users to connect concepts across the varying identifiers and entity definitions that different data providers use. CICD plans to update and expand this resource over time to incorporate additional sources of information.

The current version of the crosswalk reflects source information (see below) as of **February 2026**.

------------------------------------------------------------------------

## 🌍 Scope

This dataset includes **state- and federally recognized Native entities**.

------------------------------------------------------------------------

## 🏗️ Structure

The backbone of the Native Entity Connector Crosswalk is **Native entity identifier (NEID) tokens**. The components of this system of identifiers are:

#### `neid_prefix`

All entities have a four-letter token representing **entity type**:

-   AKNF = Federally recognized Alaska Native Village, as listed on the Federal Register

-   TRBF = Federally recognized tribe, as listed on the Federal Register

-   CNSF = Federal-level constituency entity (e.g., a band of a federally recognized tribe having a distinct decision-making body)

-   ANRC = Alaska Native Regional Corporation, as created by the Alaska Native Claims Settlement Act (ANCSA)

-   SGVF = Self-governance consortium, as identified by the Bureau of Indian Affairs (BIA) Office of Self-Governance

-   TRBS = State-recognized tribe, as documented on the state government website

-   CNSS = State-level constituency entity, as documented on the state government website (e.g., a distinct subgroup of a state-recognized tribe)

#### `neid_mid`

All entities have a six-letter **primary identifier** token. A given `neid_mid` value uniquely identifies a **"central"** **entity**.

Entities may or may not be clustered around a shared `neid_mid` value. Clusters represent entities with a documented political relationship, such as a tribe with constituent bands.

#### `neid_end`

All entities have a two-character **detail identifier** token.

A value of "00" indicates a central or organizing entity. All primary identifier values (that is, `neid_mid`) have a corresponding "00" record, with one exception.

Where a relational grouping exists, `neid_end` values differentiate entities that share a primary identifier.

#### **`neid_suffix`**

These six-letter tokens represent **relationships** among entities in this universe.

Entities may have none, one, or multiple. If there are multiple `neid_suffix`es, they are separated by `-` characters.

#### **`neid_full`**

The combination of `neid_mid` and `neid_end` uniquely identifies a Native entity in this universe. Adding `neid_prefix` and `neid_suffix` constitutes `neid_full`.

💡 **So, `neid_full` represents a unique Native entity along with its type and its direct structural relationships, if any, to other entities in this universe.**

------------------------------------------------------------------------

## 🪞 Entity attributes

The Native Entity Connector Crosswalk currently includes information about each entity's:

-   Identity

    -   Identifier components *(see above)*

    -   Name components

    -   Latitude and longitude

    -   City, county, ZIP Code Tabulation Area (ZCTA), and state

    -   Website

-   Federal Register elements, where applicable

    -   Type

    -   Full name

    -   Name components (e.g., "also known as", "previously known as", and "see also" information)

-   BIA Tribal Leaders Directory elements, where applicable

    -   Component type (that is, tribe or affiliate)

    -   Full name

    -   Alternate name(s)

    -   BIA region

    -   ANCSA region

-   BIA Office of Self-Governance elements, where applicable

    -   Self-governance status

    -   Membership in self-governance consortium

    -   Initial year of self-governance participation

-   BIA Office of Federal Acknowledgement elements, where applicable

    -   Petitioner number

    -   Petition status

    -   Petition decision effective date

    -   Web page with additional petition details and documentation

-   EPA elements, where applicable

    -   Internal numeric identifier with EPA *(not issued to all federal-level entities)*

    -   Internal numeric identifier with BIA, as distributed via the Environmental Protection Agency *(not issued to all federal-level entities)*

------------------------------------------------------------------------

## 🌱 Sources

#### **Entities**

The `native_entities` tab of the dataset includes all Native entities described above by `neid_prefix`.

Each row represents one entity. Entities are uniquely identified by the combination of `neid_mid` and `neid_end`. The field `neid_full` is the entity's unique identifier plus its type and its direct structural relationships, if any, to other entities in this universe.

Sources of this information are:

-   [Federal Register Notice 2026-01899](https://www.federalregister.gov/d/2026-01899) (91 FR 4102)

-   [Bureau of Indian Affairs Tribal Leaders Directory](https://biamaps.geoplatform.gov/Tribal-Leaders-Directory)

-   [Bureau of Indian Affairs Office of Self-Governance](https://www.bia.gov/as-ia/osg)

-   [Bureau of Indian Affairs Office of Federal Acknowledgement](https://www.bia.gov/as-ia/ofa)

-   [Environmental Protection Agency Tribes Names Service](https://www.epa.gov/data/tribes-names-service)

-   [Alaska Native Claims Settlement Act of 1971](https://uscode.house.gov/view.xhtml?path=/prelim@title43/chapter33&edition=prelim)

-   [U.S. Census Bureau TIGER/Line Shapefiles (2025)](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.2025.html)

-   Individual state government websites

    -   [Alabama](https://aiac.alabama.gov/)

    -   [Connecticut](https://portal.ct.gov/deep/environmental-justice/tribal-affairs)

    -   Delaware ([Source 1](https://delcode.delaware.gov/title29/c001/index.html), [Source 2](https://legis.delaware.gov/SessionLaws/Chapter?id=15903))

    -   [Georgia](https://georgiaindiancouncil.com/georgia_tribes)

    -   [Louisiana](https://gov.louisiana.gov/page/indian-affairs)

    -   [Maryland](https://goci.maryland.gov/maryland-commission-on-indian-affairs/)

    -   Massachusetts ([Source 1](https://www.mass.gov/info-details/indian-affairs), [Source 2](https://www.gao.gov/assets/gao-12-348.pdf))

    -   New Jersey ([Source 1](https://www.nj.gov/oag/newsreleases19/pr20190318b.html), [Source 2](https://www.nj.gov/oag/newsreleases19/pr20190318b.html))

    -   [New York](https://www.health.ny.gov/community/american_indian_nation/background_history.htm)

    -   [North Carolina](https://www.doa.nc.gov/divisions/american-indian-affairs)

    -   [North Dakota](https://www.indianaffairs.nd.gov/)

    -   [South Carolina](https://advance.sc.gov/south-carolinas-recognized-native-american-indian-entities)

    -   [Vermont](https://vcnaa.vermont.gov/recognition/recognized-tribes)

    -   [Virginia](https://www.commonwealth.virginia.gov/virginia-indians/)

-   Individual tribal government and Alaska Native Regional Corporation websites as needed; additional details available upon request

-   Geocoding performed via Google Maps Geocoding API

Download dates for each source can be found in the `data_dictionary` tab.

#### **Entity-geography pairings**

🔎 *Users are encouraged to refer to Department of Interior geography–entity crosswalk data products for further detail; links forthcoming.*

The `native_geopairs` tab of the dataset includes all Native geographies tabulated by the U.S. Census Bureau and all tribal and Alaska Native Village entities (state- and federally recognized).

Each row represents one entity–geography pairing. Some geographies have no associated entities, and vice versa.

Pairings were made by the following means:

-   Where available, using the latitude and longitude given for the associated entity in the Bureau of Indian Affairs Tribal Leaders Directory

-   Using the associated entity’s physical address, relying on the Bureau of Indian Affairs Tribal Leaders Directory where applicable

-   For collective entities explicitly cross-referenced in the Bureau of Indian Affairs Tribal Leaders Directory, transferring the pairings of their constituent affiliates

-   For an constituent entity otherwise unpaired, inheriting pairing(s) through its related collective entity

-   If no pairing was successful using geospatial methods, manually based on web research

#### **Entity-self-governance consortium pairings**

These pairings were made manually using affiliate information listed on consortium websites.

------------------------------------------------------------------------

## 📝 Additional notes

In this dataset, not all fields apply to all entities. For a given entity, fields are blank if not applicable to the entity itself or one of which it is a constituent.

Not all states have formalized tribal recognition processes. Because the scope of this data product is restricted by government recognition, it does not include entities with pending or unsuccessful petitions for federal recognition that are located in states lacking a recognition process.

------------------------------------------------------------------------

## 🤝 Contributors

Key contributors over time to the concept and compilation of this product have been Cassandra Hamilton, Amalea Jubara, Ava LaPlante, Vanessa Palmer, and William Zeng.

------------------------------------------------------------------------

## 📫 Contact

The Center for Indian Country Development welcomes questions and feedback: [CICD.data\@mpls.frb.org](mailto:CICD.data@mpls.frb.org).
