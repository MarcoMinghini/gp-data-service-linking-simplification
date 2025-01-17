
# Data Service Linking Simplification: Best Practice guidelines

`Version: draft 1.0`
`Date: 2021-10-20`

## Table of Contents

_TO_BE_REVIEWED_

* [1. Introduction](#introduction)
* [2. Scope](#scope)
* [3. Conformance](#conformance)
* [4. Normative references](#normative-references)
* [5. Terms and definitions](#terms-and-definitions)
* [6. Symbols and abbreviated terms](#symbols-and-abbreviated-terms)
* [7. Data Service Linking Simplification](#ds-linking-simplif)
    * [7.1. Main principles](#main-principles)
    * [7.2. From the definition to the data](#def-to-data)
    * [7.3. From the data to the definition](#data-to-def)
* [8. Conformance classes](#ccs)
    * [8.1. Conformance class: “INSPIRE-Data-set-Metadata-Resource-Locator”](#cc-ds-md-resloc)
    * [8.2. Conformance class: “INSPIRE-Network-Service-Metadata-Coupled-Resource”](#cc-ns-md-coupledres)
*  [9. Future developments](#future-dev)
* [Annex A: Examples](#annex-a)
* [Annex B: Mapping of INSPIRE elements in ExtendedCapabilities](#annex-b)

## 1. Introduction <a name="introduction"></a>

This good practice candidate is based on the collection and comparison of proposals received from the Member State members of the temporary MIWP technical sub-group on data and service linking simplification. This document leverages on the recommendations, initially described in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx), and further improved by the subsequent [proposals for the simplification approach](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/tree/main/proposals) made by the members of the technical sub-group.

The reference for the metadata specification used in this proposal is the [INSPIRE MD TG]. The reference for the INSPIRE Network Service (Download and View) specifications are the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG].

## 2. Scope <a name="scope"></a>

The scope of this document is to provide a well-defined series of opinionated interpretations and rules, that de facto standard web applications can currently support, based on the current list of Requirements and Recommendations expressed in the INSPIRE Technical Guidance (TG) documents.

## 3. Conformance <a name="conformance"></a>

The conformance classes and requirements expressed here apply to the data set and service metadata records, as well as to the service (capabilities) documents.
In particular, the data set and service metadata records shall be INSPIRE-compliant (checked through the Reference Validator), should be available in the relevant national geoportal catalog (see https://inspire.ec.europa.eu/INSPIRE-in-your-Country), and consecutively harvested by the [INSPIRE Geoportal](https://inspire-geoportal.ec.europa.eu).

Furthermore, at this moment the requirements expressed here for the Download Services cannot be applied to the ones that rely on the OGC API - Feature specification, due to the lack of the mapping for some conditional and mandatory INSPIRE metadata elements (ie. Coupled Resource, Unique Resource Identifier) in the [OAPIF BP] document.

## 4. Normative references <a name="normative-references"></a>

- **[ISO 19115-2:2019]** - ISO 19115-2:2019, *Geographic information — Metadata — Part 2: Extensions for acquisition and processing*
- **[ISO/TS 19139:2007]** - ISO/TS 19139:2007, *Geographic information — Metadata — XML schema implementation*
- **[IRs for NS]** - Commission Regulation (EC) No 976/2009 of 19 October 2009 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards the Network Services
- **[IRs for ISDSS]** - Commission Regulation (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services
- **[INSPIRE MD TG]** - JRC. *Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007*.  v2.0.1 - 2017-03-02
- **[INSPIRE NS - Download Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE Download Services*. v3.1 - 2013-08-09
- **[INSPIRE NS - View Service TG]** - JRC. *Technical Guidance for the implementation of INSPIRE View Services*. v3.11 - 2013-04-04
- **[RFC 4287]** - Internet Engineering Task Force (IETF). RFC 4287, *The Atom Syndication Format*. Initial release: December 2005
- **[OAPIF BP]** - Good Practice: INSPIRE download services based on OGC API - Features

<!-- Second parts of the reference-style links, see also https://www.markdownguide.org/basic-syntax/#reference-style-links  -->
[ISO 19115-2:2019]: https://schemas.isotc211.org/schemas/19115/-2/gmi/1.0/gmi.xsd "ISO 19115-2:2019, Geographic information — Metadata — Part 2: Extensions for acquisition and processing"
[ISO/TS 19139:2007]: https://www.isotc211.org/2005/gmd/ "ISO/TS 19139:2007, Geographic information — Metadata — XML schema implementation"
[IRs for NS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02009R0976-20141231&from=EN "Implementing Rules for Network Services (consolidated version of 31/12/2014)"
[IRs for ISDSS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&from=EN "Implementing Rules for interoperability of spatial data sets and services (consolidated version of 31/12/2014)"
[INSPIRE MD TG]: https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139 "Technical Guidance for the implementation of INSPIRE dataset and service metadata based on ISO/TS 19139:2007"
[INSPIRE NS - Download Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services "Technical Guidance for the implementation of INSPIRE Download Services"
[INSPIRE NS - View Service TG]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-view-services-1 "Technical Guidance for the implementation of INSPIRE View Services"
[RFC 4287]: https://www.rfc-editor.org/rfc/rfc4287 "The Atom Syndication Format"
[OAPIF BP]: https://github.com/INSPIRE-MIF/gp-ogc-api-features "Good Practice: INSPIRE download services based on OGC API - Features"

## 5. Terms and definitions <a name="terms-and-definitions"></a>

_TO_BE_REVIEWED_

For the purposes of this document, the following terms and definitions apply:

| Term | Definition | Source |
| --- | --- | --- |
| content negotiation | The practice of providing multiple representations available via the same URI | [ISO/IEC 19788](https://www.iso.org/obp/ui/#iso:std:iso-iec:19788:-7:ed-1:v1:en:sec:3.20) |
| data set | Identifiable collection of data. | [ISO 19115](https://www.iso.org/obp/ui/#iso:std:iso:19115:-2:ed-2:v1:en:sec:3.6) |
| direct access download service | Download Service which provides access to the Spatial Objects in Spatial Data Sets based upon a query | \[[IRs for NS]\] |
| encoding | Conversion of data into a series of codes. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.13) |
| encoding rule | Identifiable collection of conversion rules that define the encoding for a particular data structure. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.14) |

**NOTE** ISO and the European Commission maintain comprehensive terminological databases at the following addresses:
- [ISO Online browsing platform](https://www.iso.org/obp)
- [INSPIRE glossary](http://inspire.ec.europa.eu/glossary)

## 6. Symbols and abbreviated terms <a name="symbols-and-abbreviated-terms"></a>

_TO_BE_REVIEW_

| Abbreviation | Term |
| --- | --- |
| API | Application Programming Interface |
| GML | Geography Markup Language |
| URL | Uniform Resource Locator |
| WFS | Web Feature Service |
| WMS | Web Map Service |
| WMTS | Web Map Tile Service |

## 7. Data Service Linking Simplification <a name="ds-linking-simplif"></a>

### 7.1. Main principles <a name="main-principles"></a>

- A data set shall point to the INSPIRE View and Download Services.
- The linkage shall be ensured by the bidirectional relationship between the data set metadata and the service metadata.

### 7.2. Resources <a name="resources"></a>

![Diagram of Simplified linkage model](INSPIRE%20models_v1.1.jpg)

## 8. Conformance classes <a name="ccs"></a>

### 8.1. Conformance class: “INSPIRE-Data-set-Metadata-Resource-Locator”  <a name="cc-ds-md-resloc"></a>

| Conformance class | http://inspire.ec.europa.eu/id/spec/ds-linking-simplification/1.0/ds-md-resource-locator |
| --- | --- |
| Target type | Data set metadata |
| Dependency | N/A |

The Resource Locator of a metadata record shall point to the URL where the service can be contacted. 

Setting up the correct resource locators is important for the connection between the data and the services that provide access to them or for providing additional information concerning the resource.

In particular, the **TG Requirement 1.8** of [INSPIRE MD TG] expresses the obligation of providing online access, if available, to the described data set or data set series.

Furthermore, it suggests that at least two locators need to be expressed in the metadata: one for a Download Service, and one for a View Service.

The following requirements are also an enforcement of **TG Recommendation 1.9** in [INSPIRE MD TG] for the metadata record.

This conformance class requires that the ResourceLocator element shall point to the set of additional information about a service resource (ie. "Get Download/View Service Metadata" operation).

This conformance class requires the presence of `<gmd:protocol>` and `<gmd:applicationProfile>`: by using these two elements, paired with the defined codelist from the central INSPIRE Registry. This would imply fulfilling this portion of the simplification described here.

The presence of additional ResourceLocator elements, pointing to the data itself (e.g. "Get Spatial Data Set" request of a Download Service), is permitted, due to the multiplicity expressed by **TG Requirement 1.8**. Consequently, these additional ResourceLocator elements should avoid at least the use of the `<gmd:applicationProfile>` element, specified below, in order to reduce the complexity of a machine-to-machine element recognition made by an INSPIRE software implementation such as the INSPIRE Geoportal.

### Requirement: \<gmd:URL\> element

- Within this element, the URL shall point to the response of a "Get View/Download Service Metadata" request of the service providing access to this data set (e.g. the "GetCapabilities" document in case of a OGC:WFS service).

| **Requirement** | **/req/resource-locator-url** |
| --- | --- |
| A | The element `URL` SHALL point to the response of a "Get View/Download Service Metadata' request. |

### Requirement: \<gmd:protocol\> element

- For this element, the central INSPIRE Registry offers a series of external codelist values from the register: https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue
- Regarding the label of a codelist, the central INSPIRE Registry specifies the text to be used, and this should follow the metadata language.
- The [INSPIRE MD TG] already recommends the use of the `gmx:Anchor` element when the provided text is a term or code, instead of `gco:CharacterString`. This conformance class enforces the use of this element.
- The existence of the `gco:CharacterString` element is permitted only for backward compatibility with an existing ResourceLocator description that might be already compliant with this simplification approach.

| **Requirement** | **/req/resource-locator-protocol** |
| --- | --- |
| A | The element `protocol` SHALL be present in the Resource Locator. |
| B | The element `protocol` SHALL use the values from the [ProtocolValue codelist](https://inspire.ec.europa.eu/metadata-codelist/ProtocolValue). |
| C | The element `protocol` SHOULD be encoded with `gmx:Anchor`. The attribute `xlink:href` should point to a valid unique resource identifier of the mentioned codelist. The text value should match the related codelist label, expressed in the metadata language. |
| D | The element `protocol` MAY be encoded with `gco:CharacterString`. The text value SHALL match the related codelist label, expressed in the metadata language. |

#### Example of a View Service locator with `<gmx:Anchor>` encoding
```xml
<gmd:protocol>
    <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
</gmd:protocol>
```

#### Example of a View Service locator with `<gco:CharacterString>` encoding
```xml
<gmd:protocol>
    <gco:CharacterString>wms</gco:CharacterString>
</gmd:protocol>
```

### Requirement: \<gmd:applicationProfile\> element

- For this element, the central INSPIRE Registry offers the codelist values from the register: https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType
- Regarding the label of a codelist, the central INSPIRE Registry specifies the text to be use, and this should follow the metadata language.
- The [INSPIRE MD TG] already recommends the use of the `gmx:Anchor` element when the provided text is a term or code, instead of `gco:CharacterString`. This conformance class enforces the use of this element.
- The existence of element `gco:CharacterString` is permitted only for backward compatibility with an existing ResourceLocator description that might be already compliant with this simplification.

| **Requirement** | **/req/resource-locator-application-profile** |
| --- | --- |
| A | The element `applicationProfile` SHALL be present in the Resource Locator. |
| B | The element `applicationProfile` SHALL use the values from the [SpatialDataServiceType codelist](https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType). |
| C | The element `applicationProfile` SHOULD be encoded with `gmx:Anchor`. The attribute `xlink:href` should point to a valid unique resource identifier of the mentioned codelist. The text value should match the related codelist label, expressed in the metadata language. |
| D | The element `applicationProfile` MAY be encoded with `gco:characterString`. The text value SHALL match the related codelist label, expressed in the metadata language. |

#### Example of a Download Service locator with `<gmx:Anchor>` encoding
```xml
<gmd:applicationProfile>
    <gmx:Anchor xlink:href="https://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Downloaddienst</gmx:Anchor>
</gmd:applicationProfile>
```

#### Example of a Download Service locator with `<gco:CharacterString>` encoding
```xml
<gmd:applicationProfile>
    <gco:CharacterString>Downloaddienst</gco:CharacterString>
</gmd:applicationProfile>
```

### Requirement: INSPIRE Download Service linkage

| **Requirement** | **/req/download-linkage** |
| --- | --- |
| Definition | The ResourceLocator to an INSPIRE Download Service SHALL point to the Service Metadata (e.g. GetCapabilities) response of the associated INSPIRE Download Service. The Resource Locator SHALL include properly encoded the `URL`, `protocol` and `applicationProfile`  elements. |
| Dependency |  **/req/resource-locator-url** <br> **/req/resource-locator-protocol**<br> **/req/resource-locator-application-profile** |

See [Annex A: Examples](#annex-a) for an example of this linkage requirement.

### Requirement: INSPIRE View Service linkage

| **Requirement** | **/req/view-linkage** |
| --- | --- |
| Definition |The ResourceLocator to an INSPIRE View Service SHALL point to the Service Metadata (e.g. GetCapabilities) response of the associated INSPIRE View Service. The Resource Locator SHALL present the elements `URL`, `protocol` and `applicationProfile`, properly encoded. |
| Dependency |  **/req/resource-locator-url** <br> **/req/resource-locator-protocol**<br> **/req/resource-locator-application-profile** |

For an example of this linkage expression, see [Annex A: Examples](#annex-a)

### 8.2. Conformance class: “INSPIRE-Network-Service-Metadata-Coupled-Resource”  <a name="cc-ns-md-coupledres"></a>

| Conformance class | http://inspire.ec.europa.eu/id/spec/ds-linking-simplification/1.0/ns-md-coupled-resource |
| --- | --- |
| Target type | Service metadata |
| Dependency | N/A |

The CoupledResource metadata element refers to, where relevant, the target spatial data set(s) of the described service.  
It is implemented by reference, i.e. through a URL that points to the metadata record of the data on which the service operates. It therefore helps to link services to the relevant datasets.
This conformance class strictly follows the **TG Requirement 3.6** of the [INSPIRE MD TG] for the expression of the CoupledResource element.

Regarding the definition of a Network Service metadata, two scenarios have been identified for publishing metadata conforming to the [IRs for NS], and on the [INSPIRE MD TG]. It is up to the Member State to choose which scenario best fits their specific needs. As these scenarios are not mutually exclusive, a Member State may also choose to implement both.

**NOTE** For the ATOM implementation, the [INSPIRE NS - Download Service TG] does not offer a similar multiple scenario configuration due to the lack of mapping elements in such an implementation.

### 8.2.1 INSPIRE Network service - Scenario 1

- With the implementation of Scenario 1, the INSPIRE network service metadata is available in a Discovery Service catalog and is referenced through the `<inspire_common:MetadataURL>` element within the extended INSPIRE capabilities of such service.
- The service metadata shall define a `<srv:operatesOn>` element for every defined data set published by the service.
- The data set metadata URL may point to a Discovery Service different from the national reference catalog. This may apply especially for federated Discovery Service catalogues.

### Requirement: \<srv:operatesOn\> element

| **Requirement** | **/req/coupled-resource-operateson-locator** |
| --- | --- |
| A | The `xlink:href` attribute of each of the `srv:operatesOn` elements SHALL contain a URI pointing to the metadata record of the provided data set or data set series. |

### 8.2.2 INSPIRE Network service - Scenario 2

 - With the implementation of the Scenario 2, the [INSPIRE NS - Download Service TG] maps all INSPIRE metadata elements to the applicable elements in the service (ie. ATOM feed elements or OGC Capabilities), and in particular, for the OGC service, relies on the ExtendedCapabilities section for the remaining elements.
- The data set metadata URL may point to a Discovery Service different from the national reference catalog. This may apply especially for federated Discovery Service catalogues.

### Requirement: \<wms:MetadataURL\> and \<wfs:MetadataURL\> elements

| **Requirement** | **/req/coupled-resource-metadataurl-locator** |
| --- | --- |
| A | The URL expressed within the element `metadataURL` SHALL resolve to the metadata record of the data set or data set series, available in a Discovery Service catalog. |

## 9. Future developments <a name="future-dev"></a>

Within this document, the series of recommendations imply the possibility of further simplifications, on a broader level about the INSPIRE implementation.

Note that often the person or organization responsible for the metadata is not the same as the responsible for the service operations. This can lead to duplication, errors and/or outdated information. For instance, the more direct connection expressed with these recommendations could suggest the implementation of "_Scenario 2_", which requirements and definitions are already provided in both the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG] documents. In this case, the service metadata is no longer required (at least, for this linkage simplification purpose), so its creation can be skipped, or automated by dedicated features of a software implementation of the INSPIRE Discovery Service.

Furthermore, the implementation of the above mentioned "_Scenario 2_" for Network Service provides an opportunity for revision of the mapping of the INSPIRE requirements, currently expressed in the Extended Capabilities section (especially the Conformance declaration), since the current lack of support in some (especially proprietary) software products. Refer to the [Annex B](#annex-b) for further details.

# Annex A: Examples <a name="annex-a"></a>

## Examples (XML encoded)
The following collection shows a series of XML snippets.
_These examples are purely informative and do not constitute a reference definition of a conformant metadata._

### Examples of Resource Locator for INSPIRE View Service

#### Resource Locator to a "Get View Service Metadata" operation - WMS GetCapabilities

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wms?request=GetCapabilities&amp;service=WMS&amp;version=1.3.0</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">View Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Additional Resource Locator to an "View Service - Get Map" operation - WMS GetMap

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wms?request=GetMap&amp;service=WMS&amp;version=1.3.0&amp;layers=1&amp;styles=default&amp;CRS=EPSG:4258&amp;format=image/png&amp;bbox=0.87,43.26,11.68,48.13&amp;width=600&amp;height=400</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
        </gmd:protocol>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS - GetMap request</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

### Examples of Resource Locator for INSPIRE Download Service

#### Resource Locator  a "Get Download Service Metadata" operation - ATOM topfeed

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_dataset_2021</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Download Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Additional Resource Locator for a "Get Spatial Data Set" - ATOM subfeed

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_2021_Dataset.gml</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### _TO_BE_REVIEW_ Example of a Resource Locator of a data set metadata linking a Download Service (Get Download Service Metadata)

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wfs?service=wfs&amp;version=2.0.0&amp;request=GetCapabilities</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">wfs</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Download Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (WFS)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### _TO_BE_REVIEWED_ Example of an optional definition of a Resource Locator in the dataset metadata linking directly the downloadable dataset (Get Spatial Data Set)

_Note: this example covers the WFS definition. For a WCS/SOS service, use the proper codelist for the `protocol` element_

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wfs?service=wfs&amp;version=2.0.0&amp;request=GetFeature&amp;storedquery_id=http://inspire.ec.europa.eu/operation/download/GetSpatialDataSet&amp;DataSetIdCode=mycode&amp;DataSetIdNamespace=mynamespace&amp;CRS=EPSG:4326&amp;Language=eng</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">wfs</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">Download Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Dataset</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```
# Annex B: Mapping of INSPIRE elements in ExtendedCapabilities <a name="annex-b"></a>

The [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) proposes a new mapping of INSPIRE elements contained in the service metadata, as described for the Scenario2 in the INSPIRE Network Service TGs, in order to achieve an implementation simplification.

During the MIWP 2.3.2 action, Antonio Rotundo (IT) further explored this, by reallocating elements outside the ExtendedCapabilities.
The following tables express this simplification and reallocation:

|Extended capabilities|Simplification|Service type|
| :- | :- | :- |
|inspire\_common:ResourceType|By default = service|WMS - WFS|
|inspire\_common:ResourceLocator|Resource locator in the data set metadata|WMS - WFS|
|inspire\_common:SpatialDataServiceType|Moved to the applicationProfile in the data set metadata|WMS - WFS|
|inspire\_common:TemporalReference|Consider the temporalReference in the data set metadata?|WMS - WFS|
|inspire\_common:Conformity|Declared through the wms:keyword element |WMS - WFS|
|inspire\_common:MetadataPointOfContact|Consider the metadataPointOfContact in the data set metadata|WMS - WFS|
|inspire\_common:MetadataDate|Consider the metadataDate in the data set metadata|WMS - WFS|
|inspire\_common:SupportedLanguages|Consider the metadataLanguage in the data set metadata|WMS - WFS|
|inspire_dls:SpatialDataSetIdentifier/inspire_common:Code - inspire_dls:SpatialDataSetIdentifier/inspire_common:Namespace|Data set identifier in the data set metadata|WFS|
