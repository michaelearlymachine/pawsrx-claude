---
name: find-a-vet
description: Find and contact US veterinary practices with PawsRx. Use when the user wants to find or choose a vet, an animal hospital, an emergency or urgent-care vet, or a vet for a particular animal (including rabbits, birds, reptiles, ferrets and guinea pigs); asks about a practice's hours, open appointment times, whether it sees their animal or takes new patients; or wants to request, check or cancel a vet appointment in the United States.
---

# Find a vet with PawsRx

PawsRx is a directory of about 26,000 US veterinary practices, with the animals each one treats, its hours and the prices it publishes. The practices are independent. PawsRx is not a veterinary provider.

## If it cannot wait

If the owner says the animal is in an emergency, tell them to go to an emergency vet now, and call `find_vets` with `q: "emergency"` and their city or ZIP to find the nearest one. Do not request an appointment or send an Ask a Vet question instead.

## Finding a vet

1. Call `find_vets` with what the user gave: `city` and `state` (a code or full name) or `zip`, and `species` if they named the animal. If they said "near me" and you know their city, use it. Otherwise ask for a city or ZIP.
2. If they asked about a time ("open Saturday morning", "tonight"), pass `day` (a weekday, today, tomorrow or YYYY-MM-DD) and `period` (morning, midday, afternoon or evening).
3. If they named a practice ("Lake Emma Animal Hospital", "Banfield"), pass the name as `q` with the city. A chain returns several branches, so ask which one they mean.
4. Present the practices returned: name, address, phone, hours, the animals it treats, and its PawsRx page link. These are matches to what was asked, not a ranking, so do not call one the best.
5. If nothing matches, say so and pass on the note, which may name the nearest listed city. Only present practices that are in the results.

## A practice the user picked

- Contact details or hours: `practice_details` with its `practice_id` from `find_vets`.
- "Do they see rabbits?" or "are they taking new patients?": `check_eligibility` with `practice_id` and `species`. A null answer means the practice has not published it. Say it is unknown and suggest asking the practice. Do not turn unknown into yes or no.
- "When can they see my dog?": `check_availability`. If it returns open times, offer them. If `has_calendar` is false, there are no times to pick, and an appointment can still be requested.

## Requesting an appointment

1. Collect the owner's name, email address and a 10-digit phone number, the pet's name and species, the reason for the visit, and when they would like to come. Ask for anything missing. Use only details the owner gave.
2. Call `request_appointment`. It returns a reference and the status "requested".
3. Tell the owner the request has gone to the practice through PawsRx and that PawsRx emails them a copy and follows up by email. It is a request, not a booking: do not say it is booked or confirmed.
4. Later, `check_booking_status` with the reference gives the status. `cancel_booking` cancels it when the owner asks.

## Related

- A question for a veterinarian rather than a visit: `ask_a_vet` (see the ask-a-vet skill).
- What a visit costs: `price_lookup` (see the pet-care-costs skill).

## Always

- Questions about the animal itself are for the veterinarian or the practice.
- Refer to "the practice" or "the independent veterinarians who answer on PawsRx". PawsRx is the directory, not the vet.
- The directory and appointment requests cover the United States only. Outside it, say so. Ask a Vet works from any country.
