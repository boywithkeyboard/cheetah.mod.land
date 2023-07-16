---
title: LocationData
description: Inspect the geolocation data of the incoming request.
order: 4
---

You must either deploy your app to [Cloudflare Workers](https://developers.cloudflare.com/workers/runtime-apis/request/#incomingrequestcfproperties) or use [Cloudflare as a proxy](https://developers.cloudflare.com/support/network/configuring-ip-geolocation/) to use the `LocationData` API. {.tip}

## Setup

```ts
import { LocationData } from 'https://deno.land/x/cheetah/x/location_data.ts'

app.get('/', (c) => {
  const location = new LocationData(c)
})
```

## Get the city

The city the request originated from.

e.g. `Austin`

```ts
location.city
```

## Get the region

If known, the ISO 3166-2 name for the first level region associated with the IP address of the incoming request.

e.g. `Texas`

```ts
location.region
```

## Get the country

The [ISO 3166-1 Alpha 2](https://www.iso.org/iso-3166-country-codes.html) country code the request originated from.

If you're using CLoudflare Workers and your worker is [configured to accept TOR connections](https://support.cloudflare.com/hc/en-us/articles/203306930-Understanding-Cloudflare-Tor-support-and-Onion-Routing), this may also be `T1`, indicating a request that originated over TOR.

If Cloudflare is unable to determine where the request originated this property is omitted.

e.g. `GB`

```ts
location.country
```

## Get the continent

A two-letter code indicating the continent the request originated from.

e.g. `NA`

```ts
location.continent
```

## Get the region code

If known, the ISO 3166-2 code for the first-level region associated with the IP address of the incoming request.

e.g. `TX`

```ts
location.regionCode
```

## Get the latitude

Latitude of the incoming request.

e.g. `30.27130`

```ts
location.latitude
```

## Get the longitude

Longitude of the incoming request.

e.g. `-97.74260`

```ts
location.longitude
```

## Get the postal code

Postal code of the incoming request.

e.g. `78701`

```ts
location.postalCode
```

## Get the timezone

Timezone of the incoming request.

e.g. `America/Chicago`

```ts
location.timezone
```

## Get the datacenter

The three-letter [IATA](https://en.wikipedia.org/wiki/IATA_airport_code) airport code of the data center that the request hit.

e.g. `DFW`

```ts
location.datacenter
```
