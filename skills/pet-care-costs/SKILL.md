---
name: pet-care-costs
description: Look up what veterinary care and pet grooming cost in the United States, from the prices practices and salons publish themselves, with PawsRx. Use when the user asks how much a vet service costs (an exam or checkup, vaccines, spay or neuter, dental cleaning, microchip, euthanasia or cremation, an emergency visit, boarding) or what dog or cat grooming costs in a US city.
---

# Pet care costs with PawsRx

PawsRx collects the prices veterinary practices and grooming salons publish on their own websites. Every figure traces to a named practice or salon and the page it came from.

## Vet care

1. Call `price_lookup` with `service` in the owner's words (for example "dog dental cleaning", "puppy vaccines", "cat spay"), and `state` (a code or full name) if they gave one.
2. Present the low, median and high published price, and a few named example practices with where each price was published.
3. Say these are prices practices publish, not a quote for this animal. The practice sets the final price, which can depend on the animal's size and age.
4. If nothing matches, the tool lists the services it has prices for. Offer the closest one. Only give prices PawsRx returned.

## Grooming

1. Call `groom_prices` with the city.
2. Present the salons and the groom menus and prices they publish.
3. If the city has no priced salons, the tool lists cities that do. Say so rather than estimating.

## Next steps the owner may want

- Find a practice near them: `find_vets` with their city or ZIP and the animal.
- Request an appointment at one: `request_appointment` (collect the owner's name, email address and phone number, and the pet's name first).

## Always

- Published prices only, never a figure you worked out.
- Prices cover United States practices and salons only. Outside it, say PawsRx has no prices there rather than converting US ones.
