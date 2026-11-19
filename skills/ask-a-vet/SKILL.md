---
name: ask-a-vet
description: Send a pet owner's question to the independent veterinarians who answer on PawsRx Ask a Vet, with the answer sent back by email. Use when the user wants a veterinarian to answer a question about their dog, cat or other pet. Works from any country.
---

# Ask a Vet with PawsRx

Ask a Vet passes a pet owner's question to the independent veterinarians who answer on PawsRx. When a veterinarian answers, the answer is emailed to the owner. It works from any country and needs the owner's name and email address.

## Sending a question

1. Ask the owner for their name and email address. Use only details they gave.
2. Call `ask_a_vet` with:
   - `question`: the owner's question in their own words, with any details they gave.
   - `owner_name` and `owner_email`.
   - `pet_name` and `species` if they gave them.
3. It returns a reference that starts with `pawsrx-q-`. Tell the owner the question has been sent and the veterinarian's answer will be emailed to them.
4. The answer is the veterinarian's to write. Do not write one in its place or present your own as theirs, and do not guess what the reply will say.

If the tool says the same question was already sent, tell the owner it is already with the veterinarians and do not send it again.

## Checking for the answer

`check_booking_status` with the `pawsrx-q-` reference says whether the question has been answered. Once it has, it returns the veterinarian's answer, which you can pass on as written, with the veterinarian's name.

## If it cannot wait

If the owner says it is urgent, tell them to go to their nearest emergency vet now rather than send a question. In the United States, `find_vets` with `q: "emergency"` and their city or ZIP finds one.

## Always

- Refer to "the independent veterinarians who answer on PawsRx". PawsRx is not the vet.
- A veterinarian may publish an answered question on pawsrx.io, with the owner's name and contact details removed. If the owner asks, say so.
