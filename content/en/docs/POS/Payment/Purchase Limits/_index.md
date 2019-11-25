---
title: "Purchase Limits Validation"
linkTitle: "Purchase Limits Validation"
simple_list: true
weight: 20
---

# Purchase Limits

This guide will walk through Flourish cannabis purchase limits validation process. Recreational & Medical states all have something in common – they sell weed and each have limits too, restrictions on how much customers can buy on any given day or at any given time, to make sure Flourish legally selling them the amount mandated by law.

## Glossary

**Purchase Limit** are the limits that are established by law for the purchase of goods with the content of cannabis.

## Validation Process Overview

There are limits of 2 types, Medical and Recreational. Depending on the status of the custom, such a limit will be applied.

Facility has limits that are set by state law, so when customer makes a purchase and before he sends it for payment, purchase has to be *validated,* or otherwise all buttons are going to be hidden.

When customer adds the product to the basket, the "Validate" button appears. Selecting "Validate" button sends and API call to compare the amount of cannabis that customer have already bought in the last 24 hours and planning to buy in current purchase.

If customer exceeded the limits, then he or she will see an error message, stating that there are too many substances than are allowed.

![]()

If everything is ok, success message and the remaining buttons for working with the order appear.

![]()

Note: For Nevada, validation is a little different right now (November, 2019). During validation, the product that was purchased by the customer in the last 24 hours is not added to the quantity of goods in the basket, that is, validation occurs only within the order.

Limits are set for a certain category of goods. The list of categories can be found below:

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#aabcfe;margin:0px auto;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;border-color:#aabcfe;color:#669;background-color:#e8edff;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;border-color:#aabcfe;color:#039;background-color:#b9c9fe;}
.tg .tg-lboi{border-color:inherit;text-align:left;vertical-align:middle}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg-sort-header::-moz-selection{background:0 0}.tg-sort-header::selection{background:0 0}.tg-sort-header{cursor:pointer}.tg-sort-header:after{content:'';float:right;margin-top:7px;border-width:0 5px 5px;border-style:solid;border-color:#404040 transparent;visibility:hidden}.tg-sort-header:hover:after{visibility:visible}.tg-sort-asc:after,.tg-sort-asc:hover:after,.tg-sort-desc:after{visibility:visible;opacity:.4}.tg-sort-desc:after{border-bottom:none;border-width:5px 5px 0}@media screen and (max-width: 767px) {.tg {width: auto !important;}.tg col {width: auto !important;}.tg-wrap {overflow-x: auto;-webkit-overflow-scrolling: touch;margin: auto 0px;}}</style>
<div class="tg-wrap"><table id="tg-wmmqw" class="tg">
  <tr>
    <th class="tg-lboi">Labeling<br>Lighting<br>ll123<br>Marijuana Flowers/Buds<br>Non-Solvent Based Concentrate<br>Non-Solvent Based Concentrate (Each)<br>Nutrients<br>Oral Oil<br>Packaging<br>Packaging Components<br>Packaging Container<br>Packaging Label<br>Pots and Trays<br>Pre-rolled cigs/joints<br>Pre-Rolls</th>
    <th class="tg-lboi">Propagation<br>R&amp;D Testing / Homogeneity Testing (Count-base<br>R&amp;D Testing / Homogeneity Testing (Weight-bas<br>Raw Materials<br>Refrigerated<br>Seeds<br>Seeds (bulk)<br>Seeds (each)<br>Seeds (weight)<br>Shake/Trim<br>Shake/Trim (by strain)<br>Shake/Trim Approved for Extraction<br>Small/Popcorn Buds<br>Soft Gel<br>Solvent Based Concentrate<br>Solvent Based Concentrate (Each)</th>
    <th class="tg-0pky">Supplies<br>Suppository<br>Suppository (each)<br>Terpenes<br>Tinctures<br>Tinctures (each)<br>Topicals<br>Topicals (each)<br>Transdermal Patch<br>Transdermal Patch (each)<br>Vape Cartridge<br>Vaporizer<br>Waste<br>Wet Whole Plant Approved for Extraction<br>Whole Harvested Plant<br>Whole Wet Plant</th>
  </tr>
</table></div>
<script charset="utf-8">var TGSort=window.TGSort||function(n){"use strict";function r(n){return n.length}function t(n,t){if(n)for(var e=0,a=r(n);a>e;++e)t(n[e],e)}function e(n){return n.split("").reverse().join("")}function a(n){var e=n[0];return t(n,function(n){for(;!n.startsWith(e);)e=e.substring(0,r(e)-1)}),r(e)}function o(n,r){return-1!=n.map(r).indexOf(!0)}function u(n,r){return function(t){var e="";return t.replace(n,function(n,t,a){return e=t.replace(r,"")+"."+(a||"").substring(1)}),l(e)}}function i(n){var t=l(n);return!isNaN(t)&&r(""+t)+1>=r(n)?t:NaN}function s(n){var e=[];return t([i,m,g],function(t){var a;r(e)||o(a=n.map(t),isNaN)||(e=a)}),e}function c(n){var t=s(n);if(!r(t)){var o=a(n),u=a(n.map(e)),i=n.map(function(n){return n.substring(o,r(n)-u)});t=s(i)}return t}function f(n){var r=n.map(Date.parse);return o(r,isNaN)?[]:r}function v(n,r){r(n),t(n.childNodes,function(n){v(n,r)})}function d(n){var r,t=[],e=[];return v(n,function(n){var a=n.nodeName;"TR"==a?(r=[],t.push(r),e.push(n)):("TD"==a||"TH"==a)&&r.push(n)}),[t,e]}function p(n){if("TABLE"==n.nodeName){for(var e=d(n),a=e[0],o=e[1],u=r(a),i=u>1&&r(a[0])<r(a[1])?1:0,s=i+1,v=a[i],p=r(v),l=[],m=[],g=[],h=s;u>h;++h){for(var N=0;p>N;++N){r(m)<p&&m.push([]);var T=a[h][N],C=T.textContent||T.innerText||"";m[N].push(C.trim())}g.push(h-s)}var L="tg-sort-asc",E="tg-sort-desc",b=function(){for(var n=0;p>n;++n){var r=v[n].classList;r.remove(L),r.remove(E),l[n]=0}};t(v,function(n,t){l[t]=0;var e=n.classList;e.add("tg-sort-header"),n.addEventListener("click",function(){function n(n,r){var t=d[n],e=d[r];return t>e?a:e>t?-a:a*(n-r)}var a=l[t];b(),a=1==a?-1:+!a,a&&e.add(a>0?L:E),l[t]=a;var i=m[t],v=function(n,r){return a*i[n].localeCompare(i[r])||a*(n-r)},d=c(i);(r(d)||r(d=f(i)))&&(v=n);var p=g.slice();p.sort(v);for(var h=null,N=s;u>N;++N)h=o[N].parentNode,h.removeChild(o[N]);for(var N=s;u>N;++N)h.appendChild(o[s+p[N-s]])})})}}var l=parseFloat,m=u(/^(?:\s*)([+-]?(?:\d+)(?:,\d{3})*)(\.\d*)?$/g,/,/g),g=u(/^(?:\s*)([+-]?(?:\d+)(?:\.\d{3})*)(,\d*)?$/g,/\./g);n.addEventListener("DOMContentLoaded",function(){for(var t=n.getElementsByClassName("tg"),e=0;e<r(t);++e)try{p(t[e])}catch(a){}})}(document);</script>

**Note:** If the purchase does not contain cannabis goods, then there is no validation.

## API Reference

### Facility-level limits validation

HandlerName: `GetPurchaseLimitsByFacility`

URL: `/v1/api/retail/purchaselimits/facilities/{facility}`

RequestType: **GET**

Response body should returns the following:

```json
[
    {
        integration_purchase_limit_id: 1,
        name: "Concentrate",
        med_limit: 10,
        rec_limit: 20,
        uom_id: 1
    },
    {
        integration_purchase_limit_id: 2,
        name: "Flower",
        med_limit: 24,
        rec_limit: 24,
        uom_id: 2
    }
]
```

SQL to get Facility-level limits information:

```sql
select
	integration_purchase_limit_id,
	name,
	med_limit,
    rec_limit,
    uom_id
from
	common.integration_purchase_limit ipl
    join facility_integration fi on fi.integration_id = ipl.integration_id
where
	fi.facility_id = '<FAC_ID>';
```

### Order-level limits validation

HandlerName: `GetPurchaseLimitsByOrder`

URL: `/v1/api/retail/purchaselimits/orders/{order}`

RequestType: **GET**

Response body should return the following:

```json
[
    {
        integration_purchase_limit_id: 1,
        name: "Concentrate",
        qty: 12,
        uom_id: 1
    },
    {
        integration_purchase_limit_id: 2,
        name: "Flower",
        qty: 10,
        uom_id: 2
    }
]
```

SQL to return Order-level limits information:

```sql
select
	ipl.integration_purchase_limit_id,
	ipl.name,
	sum(
		CASE
		WHEN ipl.uom_type = 'weight' AND i.standard_qty_uom_id = 1 THEN ol.qty * i.unit_weight * uw.conversion_factor
		WHEN ipl.uom_type = 'volume' AND i.standard_qty_uom_id = 1 THEN ol.qty * i.unit_volume * uv.conversion_factor
		ELSE ol.qty * usq.conversion_factor
		END
	) qty
from
	order_hdr oh
	join order_line ol on oh.order_id = ol.order_id
	join item i on ol.item_id = i.item_id
	join uom usq on i.standard_qty_uom_id = u.uom_id
	left outer join uom uw on i.weight_uom_id = uw.uom_id
	left outer join uom uv on i.volume_uom_id = uw.uom_id
	join item_category_integration ici on i.item_category_id = ici.item_category_id
	join common.integration_item_category iic on ici.integration_item_category_id = iic.integration_item_catgory_id
	join common.integration_purchase_limit ipl on iic.integration_purchase_limit_id = ipl.integration_purchase_limit_id
where
	oh.order_id = ?
group by
	oh.customer_id,
	ipl.integration_purchase_limit_id;
```

## Database reference

Puchase Limits database entries are store inside the **Common** database. To get more information on database structure and relations, please, follow to the [General Database Information]() guide.

### Limits Tables

- common.integration
- common.integration_purchase_limit
- common.integration_item_category
- company.item_category
- company.item_category_integration

### Tables Properties & Relations

**common.integration**

- `integration_id`
- `name` — e.g. Metrc California
- `area_type` — e.g. State
- `area` — e.g. CA
- `integrator_id`
- `active` — boolean: 1 or 0

**common.integration_purchase_limit**

- `integration_purchase_limit_id`
- `integration_id` --> `common.integration.integration_id`
- `name` — Flower, Concentrates, Edibles,  common cannabis class
- `med_limit`  — limit for medical usage
- `rec_limit`  — limit for recreational usage
- `uom_type` — e.g. weight
- `limit_type` — e.g thc or cbd

**common.integration_item_category**

- `integration_item_category_id`
- `integration_id` --> common.integration.*integration_id*
- `integration_purchase_limit_id` --> common.integration_purchase_limit.*integration_purchase_limit_id*
- `description` — e.g. Buds
- `external_id` — e.g. Buds/Concentrate/Capsule — more specified name for `name` column from `common.integration_purchase_limit`
- `active` — boolean: 1 or 0
- `last_sync` — date -
- `compliance_info` — stores json

**compliance_info JSON example:**

```json
{
"QuantityType": "WeightBased",
"RequiresStrain": false,
"CanBeRemediated": true,
"CanContainSeeds": true,
"RequiresItemBrand": false,
"RequiresUnitVolume": false,
"RequiresUnitWeight": false,
"ProductCategoryType": "Buds",
"RequiresIngredients": false,
"RequiresServingSize": false,
"RequiresProductPhoto": false,
"RequiresUnitCbdContent": false,
"RequiresUnitCbdPercent": false,
"RequiresUnitThcContent": false,
"RequiresUnitThcPercent": false,
"RequiresSupplyDurationDays": false,
"RequiresAdministrationMethod": false
}
```

**company.item_category**

- `item_category_id`
- `item_class_id`
- `description` — same as `external_id` from `common.integration_item_category` e.g. "Topicals (each)"
- `type_key` — one word e.g. topicalseach
- `active` — boolean: 1 or 0
- `uom_type` — e.g weight or count
- `metrc_description` — same info as in `description`
- `is_active` — same as `active`, boolean: 1 or 0

**company.item_category_integration**

The table consists entirely of relations to other tables

- `item_category_integration_id`
- `item_category_id` --> from `item_category`
- `integration_id` --> from `common.integration`
- `integration_item_category_id` --> from `common.integration_item_category`
- `active` — boolean: 1 or 0
