
**File and fields specifications for the House Facts Open Data Standard**

### **Version:**  **0.2.3**

**Revision Date: 15 July, 2014**

### **Summary File Descriptions**

| **File Names** | **Required?** | **Contains** |
| --- | --- | --- |
| **feed.csv** | Required | This file contains information about the source of the data in the files in a single row|
| **buildings.csv** | Required | This file contains required and optional information about all residential building under an agency or localities regulatory authority. |
| **inspections.csv** | Required | This file contains information about regulatory inspections of residential buildings by one or more regulatory agencies. |
| **violations.csv** | Required | This file contains information about regulatory violations observed or documented by regulatory agencies. |
| **building\_performance.csv** | _Optional_ | This file contains information about achievement of various voluntary and regulatory high performance building standards. |
| **building\_utilities.csv** | _Optional_ | This file contains information about building utility consumption. |
| **parcels.zip** | _Optional_ | This optional file contains municipality-wide information about the parcel or lot property lines. The file should include six files with the same name with the following extensions .dbf, .prj, .sbn, .sbx, .shp, .shx, and .shp.xml. |

### **File Requirements**

- Data in HFDS feed may be published in individual comma-delimited text files, a single ZIP file - YYYYMMDD\_name.zip, or at open data portal that allows, at minimum, .CSV file exports
- The first line of each file must contain field names. Field names for each file are defined below under the 'Files' heading.
- All field names are case-sensitive.
- Field values may not contain tabs, carriage returns or new lines.
- Field values that categorize by type should contain a finite and standardized list of category descriptors with identical spelling, punctuation, capitalization and phrasing for all values in the same category.
- Field values that contain quotation marks or commas must be enclosed within quotation marks. In addition, each quotation mark in the field value must be preceded with a quotation mark. This is consistent with the manner in which Microsoft Excel outputs comma-delimited (CSV) files. For more information on the CSV file format, seehttp://tools.ietf.org/html/rfc4180.
- The following example demonstrates how a field value would appear in a comma-delimited file:
- Original field value: Contains "quotes", commas and text
- Field value in CSV file: "Contains ""quotes"", commas and text"
- Field values must not contain HTML tags, comments, escape sequences, or anything else designed to break or confuse our computers.
- Remove any extra spaces between fields or field names. Many parsers consider the spaces to be part of the value, which may cause errors.
- Each line must end with a CRLF or LF linebreak character.
- Files should be encoded in UTF-8 to support all Unicode characters. Files that include the Unicode byte-order mark (BOM) character are acceptable.
- Files should be updated weekly to reflect current inspection results.

###**File Specifications**

### **feed.csv**

Required File

| **Name** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| feed\_date | date | Yes | Date this feed was generated in YYYY-MM-DD format |
| feed\_version | string | Yes | Version of the OHHS specification used to generate this feed. For example '0.1' |
| feed\_url | string | Yes | URL where House Facts Data is published. |
| municipality\_name | string | Yes | Name of the municipality providing this feed, for example, 'San Francisco' or 'Multnomah County' |
| agency\_name | string | Yes | Name of agency providing this feed, for example, 'Building Department.' |
| building\_id\_definition | string | Yes | Describes how the municipality defines or creates the variable building\_id convention for defining building\_id. |
| parcel\_id\_definition | string | Yes | Describes how the municipality defines or creates the variable parcel\_id |
| municipality\_url | string | No | URL of the publishing municipality's website |
| contact\_email | string | No | Email address of the person to contact regarding invalid data in this feed |

### **buildings.csv**

Required File

| **Field Name** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| building\_id | string | Yes | Building\_id is a unique alpha-numeric identifier created or assigned by a single authoritative agency in a locale (e.g. tax collector) that identifies each residential building inspected by any agency in locality. See source and definition of building\_id in feed.csv below. |
| parcel\_id | string | No | Unique BLKLOT identifier |
| facility\_type | string | No | Type of residential property : Single Family - UncategorizedSingle Family - AttachedSingle Family - DetachedSingle Family - Mobile HomeMultifamily - DuplexMultifamily - TownhomeMultifamily - CondominiumMultifamily - ApartmentUncategorized |
| dwelling\_units | number | Yes | Number of residential dwelling units |
| occupancy | number | No | Occupancy of the building if available |
| built\_year | number | Yes | Year building was constructed or rebuilt. |
| gross\_floor\_area | number | Yes | Recorded building gross floor area (square feet) |
| heated\_floor\_area | number | No | Floor area of the building which is heated |
| cooled\_floor\_area | number | No | Floor area of the building which is cooled |
| lighted\_floor\_area | number | No | Floor area of the building which is lighted |
| building\_value | number | No | Current assessed property value. |
| from\_st | string | Yes | Lowest numerical value of the street number if the building has an address range or only building street number. |
| to\_st | string | No | Highest numerical value of the street number if the building has an address range. |
| street | string | Yes | Street name |
| predir | String | Yes | Field for the prefix that precedes the street name, for example, N(orth), E(ast), S(outh) or W(est) |
| sufdir | String | Yes | Field for the suffix that follows the street name, for example, N(orth), E(ast), S(outh) or W(est) |
| street\_type | string | Yes | Street type (St, Ave, Way) |
| city | string | Yes | City where the property is located. |
| state | string | Yes | State where the property is located. In the U.S. this should be the two-letter code for the state |
| postal\_code | string | Yes | Zip code or other postal code |
| latitude | number | Yes | Latitude of the residential building parcel. This field must be a valid WGS 84 latitude. For example 37.7859547 |
| longitude | number | Yes | Longitude of the residential building parcel. This field must be a valid WGS 84 longitude. For example -122.4024658 |
| operator\_type | string | No | The kind of entity which is responsible for operating the building: Private owner; property management; tenant; public institution; non-profit institution; bank. |
| owner\_name | string | Yes | Property owner. This may be an individual or business entity. |
| owner\_mailing\_address | string | No | Mailing address for the owner of record. For example Jane Smith 310 Polaris Way San Francisco CA 94117 |
| date\_updated | Date | No | date that the record was created or updated. |

### **inspections.csv**

**Required File**


| **Name** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| inspection\_id | string | Yes | Unique ID for inspection; format provided by municipality |
| building\_id | string | Yes | Unique identifier for the residential property being inspected. |
| inspection\_date | date | Yes | Date of the inspection in YYYY-MM-DD format |
| inspection\_address | string | Yes | Address at which the inspection occurred |
| inspection\_unit\_number | string | No | Identification for specific unit in a multi-unit building where inspection was conducted, for example, "113" or "F." |
| inspection\_agency | string | Yes | Type of agency conducting the inspection. Must be one of the following types: **Health, Environment, Building, Housing, Planning, Fire, Code Enforcement** . |
| inspection\_purpose | string | Yes | Reason for the inspection. Must be one of the following types: **permit** [approval], **routine or periodic** [monitoring], **complaint or service request** [response], **follow-up** [of a previous inspection]. |
| inspection\_category | string | No | Functional category or subject of the inspection. For example, structural, mechanical, plumbing, pest-control, fire prevention, noise, indoor air quality, etc |
| inspection\_rating | string | Yes | Inspection rating or result, for example, " **pass/ fail** ," " **satisfactory/ not-satisfactory** ," if one exists. |
| inspection\_score | number | No | Numerical score associated with the inspection if one exists |
| latitude | number | Yes | Latitude of the residential building parcel. This field must be valid WGS 84 latitude. For example 37.7859547 |
| longitude | number | Yes | Longitude of the residential building parcel. This field must be valid WGS 84 longitude. For example -122.4024658 |
| Date\_updated | date | No | Date that the record was updated or created. |

### **violations.csv**

**Required File**

| **Name** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| violation\_id | number | Yes | Unique identifier for the violations |
| building\_id | string | Yes | Unique identifier for the property being inspected. |
| inspection\_id | number | Yes | Unique identifier for the inspection |
| Inspection\_agency | string | Yes | Type of agency issuing the violation, for example, Health, Environment, Building, Housing, Planning, Fire, Code Enforcement. |
| Inspection\_purpose | string | Yes | Reason for the inspection, for example, permit [approval] , routine or periodic [monitoring], complaint [response], follow-up [of a previous inspection]. |
| violation\_date | date | Yes | Date that the violation was recorded in YYYY-MM-DD format. |
| violation\_status | string | Yes  | Violation status: Open or Closed. |
| violation\_address | string | Yes | Address where violation observed. |
| violation\_unit\_number | string | No | Identification for specific unit in a multi-unit building where violation occurred, for example, "113" or "F." |
| violation\_date\_closed | date | Yes | Date that the violation was closed in YYYY-MM-DD format. |
| violation\_reason\_closed | string  | No | Reason that the violation was closed (e.g. violation corrected by responsible party) |
| violation\_category | string | Yes | Violation category. Must be one of the categories in the HFDS list of violation categories. |
| violation\_type | string | Yes | Violation type (bedbugs, mold, etc) |
| violation\_code | string | no | The legal authority under which a violation is issued, for example, a section of the housing code. |
| violation\_severity | string | No | May be one of the following categories: high (imminently harmful to health and requires rapid correction) and low (nuisance with correction over a reasonable period of time) |
| latitude | number | Yes | Latitude of the residential building parcel. This field must be a valid WGS 84 latitude. For example 37.7859547 |
| longitude | number | Yes | Longitude of the residential building parcel. This field must be a valid WGS 84 longitude. For example -122.4024658 |
| Date\_updated | Date | No | Date the violation record was created or updated. |

### **building\_performance\_standards.csv**

**(optional file)**

This optional file provides information on building performance certifications achieved for the residential building. Building performance can be rated with regards to energy efficiency, air quality, or overall sustainability performance. A single building may have multiple performance certifications represented as multiple file records.

| **field name** | **data type** | **required** | **description** |
| --- | --- | --- | --- |
| building\_id | string | yes |  |
| parcel\_id | string | no |  |
| building\_address | string | yes |  |
| building\_certification\_type | string | yes | Name of building performance certification system, standard, or program:Energy Star Home [Energy Star Indoor AirPlus](http://epa.gov/iaplus01/) [CEC Home Energy Rating System](http://www.energy.ca.gov/HERS/) [USGBC LEED for Homes](http://www.usgbc.org/leed/homes) [USGBC LEED Neighborhood Development](http://www.usgbc.org/neighborhoods) [Enterprise Green Communities](http://www.enterprisecommunity.com/solutions-and-innovation/enterprise-green-communities) [Earth Advantage Home](http://www.earthadvantage.org/certification/earth-advantage-home-certification) [Green Globes New Construction](http://www.thegbi.org/green-globes/new-construction.shtml) [Green Globes CIEB](http://www.thegbi.org/green-globes/continual-improvement-for-existing-buildings.shtml) |
| building\_certification\_value | string | yes | Certification rating, level, or score. This may be reported as a string or as a numerical score. |
| building\_rating\_date | date | no | Date of rating or performance measurement. |
| building\_certification\_source | string | yes | Data source for building certification information |
| date\_updated | date | No | Date record created or updated |

## **building\_utilities.csv**

**(optional file)**

This optional file provides for reporting of summary building-level data on environmental resources consumption (e.g. utilities). Each building would have a separate record for each utility type: water, sewage, electricity, natural gas, heating oil, landfill refuse, recycled refuse, etc. Data sources may include: government agencies which require reporting of utility and energy efficiency data; utilities; public data sets (e.g. DOE Building Performance Database); building owners. This standard is intended to be compatible with the US DOE [Building Energy Data Exchange Specification](http://www.eere.energy.gov/buildings/BEDES).

| **field name** | **data type** | **required** | **description** |
| --- | --- | --- | --- |
| building\_id | string | yes |  |
| parcel\_id | string | yes |  |
| building\_address | string | yes |  |
| utility\_type | string | yes | May be any one of the following types: Water, sewage, electricity, natural gas, heating oil, landfill refuse, recycled refuse, etc. |
| utility\_data\_source | string | yes | Source of utility data (e.g., utility provider, municipality, building owner, EPA portolio manager, private energy benchmarking software, etc) |
| utility\_measure | string | yes | \*Standardize units for this field include: kwh (electricity), therms (natural gas), gallons (water), |
| utility\_report\_date | date | yes | Date data provided by source |
| utility\_report\_period | number | yes | Number of months of utility data |
| monthly\_utility\_use | number | yes | Average utility consumption per unit |

## **parcels.zip**

**(optional file** )

| **Name** | **Type** | **Required** | **Description** |
| --- | --- | --- | --- |
| Shape | geometry | Yes | This field contains data that describes the boundaries of the lot. It is generated automatically when the shapefile is created and will display a type of polygon or multipolygon. |
| parcel\_id | string | Yes | Local identifier for all parcel footprint that the building sits on. |
| building\_id | string | Yes | Unique identifier for the residential building. Can correspond to more than one parcel\_id or an address range |



## **Standardized Violation Categories**

This table provides a table of standard violation categories for the violation categories field in violations.csv.

| **Violation Category** | **Violation Category Examples** |
| --- | --- |
| Animals and Pests | Cockroaches; rats; mice; bedbugs; racoons |
| Vegetation | Overgrown vegetation, landslide |
| Refuse | Refuse accumulation; dumping; spoiled food |
| Sanitation | Unsanitary floors or walls; non-functioning sewage system |
| Radiation Hazard | Radon |
| Air Pollutants and Odors | Nuisance odors; smoking in common areas |
| Biological Hazard | Medical waste; Contaminated Needles, mold/mildew |
| Chemical Hazards | Lead hazard; asbestos hazard |
| Noise | Interior noise violation; exterior noise violation |
| Indoor Climate | Inadequate heat or ventilation |
| Plumbing | No running water; inoperable toilet |
| Electrical | Exposed electrical hazards; excess electrical loads |
| Fire Hazards and Prevention | Non-functioning smoke detector; heat source near combustible material |
| Building Security | Inadequate exterior lighting |
| Building Structure | Water or moisture intrusion; structural hazard; |
| Planning or Zoning | Unpermitted use; violations of conditions of use |
| Abandon, Boarded or Substandard Building | Abandoned Building; Blighted Building; Dilapidated Housing |
| No Permit | No permit for electrical, gas, construction, plumbing ect |
| Water Hazard | Storm Water; Water Leak; Sewer Leak |
| Gas Hazard | Gas Leak, Illegal Gas Appliance |
| Other | Other |


House Facts Data Standard is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-nc-sa/3.0/deed.en_US).