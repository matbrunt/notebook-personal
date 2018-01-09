# Rightmove Page Structure

Html structure taken from: `http://www.rightmove.co.uk/property-to-rent/property-52325163.html?utm_content=v2-ealertspropertyimage&utm_medium=email&utm_source=emailupdates&utm_campaign=emailupdatesinstant&utm_term=letting&sc_id=25412504&onetime_FromEmail=true`.

Whilst the page uses javascript binding on data objects to generate content, it is possible the majority of structure is present in the initial html fetch.

**Run a scraper from behind VPN just in case IP addresses are tracked**, but also put in a large delay between hits to be respectable, there is no rush to gather data.

wrapper `div#primaryContent`

composed of multiple divs `.row .one-col`

row 1: property header

row 2: image gallery

row 3: Descriptions, details, maps, school checker

row 4: disclaimer and right move small print

details tabbed section: `div#detailsTabs`

## Summary, Address, Price

```html
<div class="property-header-bedroom-and-price ">
  <div class="left">
    <h1 class="fs-22" itemprop="name">3 bedroom flat to rent</h1>
    <address class="pad-0 fs-16 grid-25" itemprop="address" itemscope="" itemtype="http://schema.org/PostalAddress">
      <meta itemprop="streetAddress" content="7 Waverley Park, Edinburgh EH8 8EW">
      <meta itemprop="addressCountry" content="GB">
        7 Waverley Park, Edinburgh EH8 8EW
    </address>
  </div>
  <p id="propertyHeaderPrice" class="property-header-price " style="cursor: pointer;">
    <strong>
      £1,100 pcm<br>
    </strong>
  </p>
</div>
```

## Number of Photos

```html
<span class="gallery-main-status"><span class="js-gallery-index">1</span> of 5</span>
```

## Tab Header (shows active tab with class `.active`)

```html
<ul class="clearfix tabbed-content-nav print-hidden ">
    <li class="tabbed-content-nav-item active" id="">
        <a href="#description">
          Description
        </a>
    </li>
    <li class="tabbed-content-nav-item " id="locationTab">
        <a href="#location">Map &amp; Street View</a>
    </li>
    <li class="tabbed-content-nav-item " id="schoolsTab">
        <a href="#schools">SchoolChecker</a>
    </li>
</ul>
```

Tabs content is selected with # anchors, e.g. `#location`, `#schools`.

## Tab Content

Tab content sits in `div .tabs`, under a div with class `div .tabbed-content-tab`.

Each content div has an id:

- #description

- #location

- #schools

Inside each tab content there are 3 orderedsections:

- `div .left` (left pane: letting information, key features, full description)

- `div .right` (right pane: minimap, nearest stations)

- `sect .clearfix` (footer: agent details)

### Letting Information

Furnished / Unfurnished
Deposit
Date added to Rightmove

```html
<div id="lettingInformation" class="sect">
    <h3>Letting information:</h3>
    <table class="table-reset width-100">
        <colgroup>
            <col class="col-1 width-50">
            <col class="col-2 width-50">
        </colgroup>
        <tbody>
        <tr>
            <td>Furnishing:</td>
            <td id="furnishedType">Unfurnished</td>
        </tr>
        <tr>
            <td>Deposit:</td>
            <td>£1200</td>
        </tr>
        <tr>
            <td>Added on Rightmove: </td>
            <td>08 January 2018 (19 hours ago)</td>
        </tr>
        </tbody>
    </table>
</div>
```

### Key Features

```html
<div class="sect key-features">
    <h3>Key features</h3>
    <ul class="list-two-col list-style-square">
        <li>Dish washer</li>
        <li>Electric Oven</li>
        <li>Ensuite Facilities</li>
        <li>Fridge Freezer</li>
        <li>Gas central heating</li>
        <li>Shower</li>
        <li>Smoke Detector</li>
        <li>Telephone Point</li>
        <li>Washing machine</li>
        <li>Double Glazing</li>
    </ul>
</div>
```

### Full Description

Sits inside `div .sect` following a `h3` element with content *Full description*.

```html
<p itemprop="description">
    Unfurnished Accommodation comprises: Very large square hallway with all rooms off through to extensive living room with direct views toward Arthurs Seat and beyond.  Master bedroom with built in wardrobes and ensuite facilities. Large 2nd bedroom with built in wardrobes.  Bright and spacious 3rd bedroom with park views.  Stylish modern fitted breakfasting kitchen with all mod cons. 3 large storage cupboards. Free on street parking. Finished to a high standard throughout. Call early to view.
</p>
```

- [] Find an example with large description, see if there is a 'read more' link or anything similar.

### Minimap with location pin

```html
<div class="pos-rel">
    <a class="block js-tab-trigger js-ga-minimap" href="#location">
        <img src="//media.rightmove.co.uk/map/_generate?latitude=55.954760&amp;longitude=-3.166650&amp;zoomLevel=14&amp;width=190&amp;height=222&amp;signature=WcD677sdCbWGWyTCB4qUPZuimm0=" width="190px" height="222px" alt="Get map and local information">
    </a>
    <img src="/ps/images18005/maps/icons/rmpin.png" alt="Location on map" class="icon-house-pin-centered">
</div>
```

We can pull the property latitude and longitude from parsing the img url.

Looking in the html source we can also extract details from the embedded javascript functions, that are called through `setTimeout()` following page load:

```javascript
RIGHTMOVE.ANALYTICS.PageViewTracker.trackOnClick('#mapAndSchoolsTab a', {"lon":"-3.1666790299326175","pst":"8","aer":"1","bed":"3","nph":"5","lft":"2","aed":"2018-01-08-12-10-23","au":"false","pd":"false","prc":"1100","pt":"2","st":"1","pq":"0","lat":"55.954758723884865","fp":"false","channel":"renting","propertyId":"52325163","branchId":"71783","videoType":"none"}, 'map-tab', '', '');

```

### Nearest Stations

```html
<div class="clearfix nearest-stations">
    <div class="bdr-2 box-1 pad-8">
        <h4>Nearest stations</h4>
        <ul class="stations-list">
            <li>
                <i class="icon icon-national-train-station"></i>
                <span>Edinburgh</span>
                <small>(0.9 mi)</small>
            </li>
            <li>
                <i class="icon icon-national-train-station"></i>
                <span>Edinburgh Waverley</span>
                <small>(0.9 mi)</small>
            </li>
            <li>
                <i class="icon icon-national-train-station"></i>
                <span>Haymarket</span>
                <small>(2.1 mi)</small>
            </li>
        </ul>
        <small class="disclaimer">Distances are straight line measurements from centre of postcode</small>
    </div>
</div>
```

### Agent Details

```html
<div class="agent-details-display">
    <p class="pad-0">
        <a title="Contact Zone Letting, Edinburgh" rel="nofollow" href="/property-to-rent/contactBranch.html/svr/3111;jsessionid=7D028D35E9654D81321B3C40C3FE6DD3?propertyId=52325163&amp;backToPropertyURL=%2Fproperty-to-rent%2Fproperty-52325163.html%3Futm_content%3Dv2-ealertspropertyimage%26utm_medium%3Demail%26utm_source%3Demailupdates%26utm_campaign%3Demailupdatesinstant%26utm_term%3Dletting%26sc_id%3D25412504&amp;fromButtonId=contactagent-footer"><strong>Zone Letting, Edinburgh</strong></a>
    </p>
    <address class="pad-0">30 St. Stephen Street, Edinburgh, EH3 5AL</address>
    <p>
        <a href="tel:0131 291 0045" class="branch-telephone-number">
            <strong>0131 291 0045</strong>
        </a>
        <a id="link-local-rate" href="#local-rate-message">
            <small>Local call rate</small>
        </a>
    </p>
    <div class="hide">
        <div id="local-rate-message">
            <h4>How much will it cost me to call the number displayed on the site?</h4>
            <p>Standard geographic charges from landlines and mobiles apply and calls may be included in your telecom provider's call package.</p>
        </div>
    </div>
</div>
```

## Javascript Content

```javascript
var schoolMapOptions = {"zoom":14,"latitudeLongitude":{"lat":55.95476,"lon":-3.16665},"exactLocation":true}

broadbandCtmUrl: "https://partnerships-broadband.sergei.io/v1/broadband/rightmove/EH88EW?apikey=5e5840cfe6fda01ba0643ff9e4d5b505da466f4a172dce3d8b9fc7c4f41552fe"

images : [{"index":1,"caption":"Picture 2","thumbnailUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_02_0000_max_135x100.jpg","masterUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_02_0000_max_656x437.jpg"},{"index":2,"caption":"Picture 3","thumbnailUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_05_0000_max_135x100.jpg","masterUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_05_0000_max_656x437.jpg"},{"index":3,"caption":"Picture 4","thumbnailUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_04_0000_max_135x100.jpg","masterUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_04_0000_max_656x437.jpg"},{"index":4,"caption":"Picture 5","thumbnailUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_03_0000_max_135x100.jpg","masterUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_03_0000_max_656x437.jpg"},{"index":5,"caption":"Picture 6","thumbnailUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_01_0000_max_135x100.jpg","masterUrl":"http://media.rightmove.co.uk/dir/72k/71783/52325163/71783_ACT76WPRK_IMG_01_0000_max_656x437.jpg"}],

thumbnailCarousel.init({
    totalImages : 5,
    maxThumbnailsToDisplay : 5,
    nextThumbnailPageSelector : '.js-thumbnail-next',
    prevThumbnailPageSelector : '.js-thumbnail-prev',
    imageElementWidth : 132,
    divToMove: '.js-thumbnail-main',
    thumbnailImageContainer : '.js-gallery-thumbnail img',
    failureThumbnailImageSrc: '/ps/images/fullsite/common/no_download_thumbnail.gif'
});
```

### Broadband Details

Calling the `broadbandCtmUrl` specified in the Javascript returns the following data object:

```json
{
    "bundle_type":["FibreBroadbandAndHomephone","BroadbandAndHomephone"],
    "postcode":"EH88EW",
    "speed":77824,
    "speed_display":"76Mb",
    "provider_name":"Vodafone Broadband",
    "provider_logo_url":"https://bucket.cdndtl.co.uk/bc/providerlogos/vodafone99.png",
    "contract_length":"18 months",
    "download_limit":"Truly Unlimited",
    "offer_image":"https://bucket.cdndtl.co.uk/bc/ICONS_70x70/Icon-ulimited-usage-hide.png",
    "first_year_cost":"£288.00",
    "monthly_cost":"£24.00",
    "setup_cost":"£0.00",
    "cost_breakdown":[
        {"key":"FirstMonthsCost","description":"(for 18 months)","value":"£24.00 p/m"}
    ],
    "all_offers_url":"https://broadband.comparethemarket.com/deeplink/packages/fastest?location=EH88EW&utm_source=Partner&utm_campaign=Rightmove_Broadband&utm_medium=Website&utm_content=BroadbandWidget&AFFCLIE=EI34&src=EI34"
}
```
