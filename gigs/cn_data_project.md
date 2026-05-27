

# Project Briefing: Aluminum Smelting Company Identification

### 1. Project Objective
The goal is to generate a verified list of all Chinese entities legally authorized to engage in aluminum smelting. This involves identifying the entities via **Business Scope (经营范围)** keywords and industry codes, then performing ownership analysis. 

### 2. Primary Data Sources
To build a comprehensive and authoritative list, the project will utilize a "Three-Tier" data approach:

*   **Tier 1: Commercial Aggregators (Qichacha/QCC or Tianyancha):** These platforms are essential for ownership chain analysis and identifying Ultimate Beneficial Owners (UBOs). They allow for structured searching of subsidiary chains and joint venture (JV) relationships that GSXT lacks.
*   **Tier 2: Supplemental Verification (Baidu Maps API):** Used for physical address verification to ensure the refinery or smelting facility exists at its registered coordinates.
*   **Tier 3 (only if needed): GSXT (National Enterprise Credit Information Publicity System):** Used as the authoritative anchor to validate legal existence and official business scope. While it lacks API access and ownership penetration, it provides the "source of truth" for registration status.

### 3. Search & Extraction Methodology
If possible, the project will follow an **API-first extraction** workflow rather than automated scraping, which is often blocked by Chinese government firewalls and CAPTCHAs.

1.  **Initial Mining:** Query QCC and Tianyancha for entities using the Unified Social Credit Code (USCC) or keywords such as **"aluminum smelting" (铝冶炼)** or **"primary aluminum production" (原铝生产)** within their registered business scope.
2.  **Filtering criteria:** For this project we are only interested in companies that produce aluminium ingots (this may be the trickiest part - document your logic). Companies must be currently **active** (not dormant or closed). Also filter out very small companies which can be done by looking at the share capital. 
3.  **Data Normalization:** Use LLMs (e.g., Claude) to extract text or HTML and convert it into structured **JSON format**, ensuring consistent transliteration of Chinese company names into Pinyin/English.

### 4. Required Data Points
For each entry in the final spreadsheet, the following fields must be collected:
*   **Entity Name (CN/EN):** Official Chinese name and standardized English transliteration.
*   **Unified Social Credit Code (USCC):** The unique identifier for the Chinese entity.
*   **Registered Capital:** Used as a proxy for operational scale; extremely low capital (e.g., RMB 1,000) for a smelting operation is a red flag.
*   **Business Scope Summary:** Confirmation of smelting authorization.
*   **Matching Commercial Codes:** All of the codes assigned to the company.
*   **Ownership Structure:** Traced through multiple layers to the UBO or natural person.
*   **Registration Status:** Must be "Active/In-operation" (存续/在营).

### 6. Infrastructure Requirements
*   **Mainland Access:** Accessing API aggregators (QCC/Tianyancha) requires a mainland Chinese IP address.
*   **API/Subscription Costs:** These will be provided to you.

### 7. Final Deliverables
*   **Master Spreadsheet:** A list of entities with all fields identified in Section 4.
*   **Owndership Summary Report:** For identified smelters, an English summary of the ownership chain diagram and other supporting data about the company such as contact person,.phone and email, images from Baidu Maps.
*   
