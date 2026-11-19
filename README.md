# PawsRx for Claude

PawsRx is a directory of about 26,000 US veterinary practices and of grooming salons, with the animals each practice treats, its hours, and the prices it publishes on its own website. This plugin connects Claude to PawsRx so Claude can find a vet or a groomer, check whether a practice sees a particular animal and when it is open, look up published prices, send an appointment request, or send a question to an independent veterinarian.

PawsRx is not a veterinary provider. The practices and veterinarians are independent, and answers come from them. In an emergency, go to an emergency veterinary hospital.

## What the plugin contains

- **An MCP server:** `https://pawsrx.io/mcp`, a remote server run by PawsRx LLC. It needs no sign-in. It is the same server as the PawsRx connector, so people who have both see one set of tools.
- **Three skills** that show Claude how to use the tools: `find-a-vet`, `pet-care-costs` and `ask-a-vet`.
- **Nothing that runs on your computer:** no hooks, scripts, commands or packages.

## Tools

Read only:

| Tool | What it does |
|---|---|
| `find_vets` | Finds US veterinary practices by city, state or ZIP, the animal, the day and time of day, or a name |
| `practice_details` | One practice's address, phone, hours, the animals it treats, and its PawsRx page |
| `check_availability` | A practice's open appointment times, where it keeps an online calendar |
| `check_eligibility` | Whether a practice treats an animal and takes new clients, or unknown when it has not published it |
| `price_lookup` | The low, median and high price US practices publish for a service, with named examples |
| `groom_prices` | Grooming salons in a US city and the prices they publish |
| `check_booking_status` | The status of an appointment request, or the answer to an Ask a Vet question, by its reference |

Write (Claude asks you before it runs one):

| Tool | What it does |
|---|---|
| `request_appointment` | Sends an appointment request to a practice for the owner. It is a request, not a confirmed booking |
| `ask_a_vet` | Sends the owner's question to the independent veterinarians who answer on PawsRx |
| `cancel_booking` | Cancels an appointment request by its reference |

## Examples

- "Find a vet in Austin, Texas that sees rabbits and is open Saturday morning."
- "What does a dog dental cleaning cost in California?"
- "Request an appointment at that practice for my cat Miso next week, in the morning."
- "Ask a vet whether my rabbit can eat dandelion leaves."
- "What does it cost to get a doodle groomed in Dallas?"

## Data and privacy

- A search sends PawsRx only what you asked for: a place, the animal, a day or time, a practice name or a service.
- `request_appointment` and `ask_a_vet` send the details you give Claude for that purpose: your name, email address and phone number, your pet's name and species, the reason for the visit or your question, and the times you prefer. PawsRx sets up a PawsRx account under your email address so you can see the request or the answer, passes the request to the practice or the question to a veterinarian, and emails you a copy.
- A veterinarian may publish an answered question on pawsrx.io, with your name and contact details removed.
- For each call, PawsRx records the tool, the client that called it, whether it worked, how long it took and any reference it returned. It does not record what you typed into the tool, and it never receives your Claude conversation.
- How long PawsRx keeps your information, who it is shared with, and your rights over it: [pawsrx.io/privacy](https://pawsrx.io/privacy).

## Coverage

The directory, prices and appointment requests cover the United States. Ask a Vet works from any country.

## Support

Email hello@pawsrx.io. Full documentation, including how to connect PawsRx to other assistants: [pawsrx.io/connectors/docs](https://pawsrx.io/connectors/docs).

## License

MIT. See [LICENSE](LICENSE).
