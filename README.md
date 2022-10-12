# Talent Connectors

Basically, we’ve noticed that a lot of the senior product/tech people get asked for talent recommendations all the time. Today, most of these requests go unmet due to a lack of time available and lack of access to talent.

We could establish a system that allows these ‘Connectors’ to send talent requests to Squad via the marketplace and receive profiles that they review and pass on to the client. They essentially act as individual matchmakers. Connectors get up to 50% of the marketplace fee once the talent that they helped connect to a mission starts to get paid.

From a systems design perspective, how would you design the infrastructure of this peer-to-peer referral system such that it is as trustless and efficient as possible?

We are looking for your high-level thoughts on whatever simple form you prefer (bullet points, voice notes, a short paragraph). We can keep the brainstorming going asynchronously for a bit. Feel free to ask for clarification.

## Questions

1) What is the most important metric for efficiency? Should we optimized for shortest time to a certain talent-request state? Or should we optimize for the number of talent requests that are fulfilled? Or something else?

2) What happens to the talent requests that are not fulfilled (ever), or that are not accepted by Connectors, Clients, Talent multiple times? Do they get deleted? Do they get archived? Do they get sent to a different connector? Do they get sent to a different connector after a certain amount of time?

3) What do we need to keep track of for Connectors? Number of talent-requests filled?

4) Does this system need to have a mechanism for Client and Talent onboarding/offboarding? If so, what does that look like? How about for Connectors?

5) What currency do we use for the marketplace? Do we use a stablecoin? Do we use a marketplace token? Do we use a combination of these? Are we building the marketplace around a specific chain (L2)? Is L1 infeasible due to gas costs? What is most important here?

## System Components

### Talent Request States

1) **NEW** - new talent-requests -> Connectors match Talent with talent-requests. New requests move to **Suggested** when potential Talent is suggested (manually or auto) by an Connector.
2) **SUGGESTED** Talent-requests are filled (manually or auto) and suggested=true and sent to Clients for approval. Unapproved talent-requests (by Client) become **New** again.
3) **CLIENT_APPROVED** Client-approved talent-requests are sent to Talent for approval. Rejected talent-requests become **New** again.
4) **OPTIONAL** - **FINAL_REVIEW** Finally, Connector recieves Talent & Client approved talent-requests for final review/tracking. Automatically become **Finalized** in X days set in config. (can remove this step, efficiency--).

5) **FINALIZED** talent-requests are stored long term on ledger. (IPFS -> shortterm, ETH?? L2?? SKALE?? -> longterm). Connector gets paid.

### What parts need to be decentralized?

ether-js for payment, IPFS for storage, and a smart contract for the marketplace.

### What parts don't?

Next.js or Meteor.js for the frontend.

### Other pieces (potentially)

<https://github.com/SocketDotTech/widget>
Zapper SDK for swaps.

## WIP - Connectors recieve automated suggested talent-requests based on talent-requests "talent-skills", "talent-types", and "availability"

match 60-100% configurable via Connector && Talent dashboards.

## TALENT REQUESTS

<!-- talent-requests -->
{
    "talent-request": {
        "id": "uuid",
        "connector-id": "uuid",
        "mission-id": "uuid",
        "talent-id": "uuid",
        "status": "request-state",
        "created-at": "timestamp",
        "updated-at": "timestamp",
        "marketplace-fee-total": "number",
        "talent-types": ["string"],
        "talent-skills": ["string"],
        "availability": "datetime",
    }
}
<!-- request-state -->
{
    "request-state": ["NEW", "SUGGESTED", "CLIENT-APPROVED", "TALENT-APPROVED", "FINAL-REVIEW", "FINALIZED"]
}

## PROFILES - TALENT, CLIENT, CONNECTOR
<!-- talent-profiles -->
{
    "talent-profile": {
        "id": "uuid",
        "connector-id": "uuid",
        "bio-id": "uuid",
        "talent-id": "uuid",
        "status": "pending|accepted|rejected",
        "created-at": "timestamp",
        "updated-at": "timestamp",
        "specialties": "programming-lang-tools",
        "type": "full-time|contract|freelance",
        "availability": "datetime",
    }
}

<!-- connector-profiles -->
{
    "connector-profile": {
        "id": "uuid",
        "connector-id": "uuid",
        "bio-id": "uuid",
        "created-at": "timestamp",
        "updated-at": "timestamp",
        "talent-requests": [
            "talent-request-id"
        ],
        "availability": "datetime"
        }
}

<!-- client-profiles -->
{
    "client-profile": {
        "id": "uuid",
        "client-id": "uuid",
        "bio-id": "uuid",
        "created-at": "timestamp",
        "updated-at": "timestamp",
        "talent-requests": [
            "talent-request-id"
        ],
    }
}
<!-- programming languages & tools -->

"programming-lang-tools" : { "JS", "React", "Node", "HTML", "CSS", "Rust", "C", "C++", "C#", "Ruby", "Deno", "Solidity", "Vyper", "Python", "Java", "Kotlin", "Swift", "Go", "R", "PHP", "Scala", "Elixir", "Clojure", "Haskell", "OCaml", "F#", "Erlang", "Julia", "Lua", "Perl", "Racket", "Scheme", "SQL", "Bash", "PowerShell", "Cobol", "Fortran", "Lisp", "Prolog", "Ada", "Assembly", "Dart", "Eiffel", "Forth", "Groovy", "Haxe", "J", "Julia", "LabVIEW", "Logo", "MATLAB", "Objective-C", "Pascal", "PL/SQL", "RPG", "SAS", "Scratch", "Smalltalk", "Tcl", "Visual Basic", "WebAssembly", "Z shell", "D", "Next.js", "Gatsby", "Vue", "Angular", "Ember", "Svelte", "React Native", "Flutter", "Ionic", "NativeScript", "Xamarin", "Electron", "jQuery", "Bootstrap", "Tailwind", "Material", "Ant Design", "Semantic UI", "Bulma", "Foundation", "UIKit", "Android", "iOS", "Windows", "macOS", "Linux", "Unix", "Chrome", "Firefox", "Safari", "Edge", "Opera", "Internet Explorer", "Node.js", "Express", "Koa", "Hapi", "Fastify", "Nest", "Sails", "Meteor", "Socket.io", "GraphQL", "Apollo", "REST", "SOAP", "gRPC", "WebSockets", "TCP", "UDP", "MQTT", "WebRTC", "WebAssembly", "WebGL", "OpenGL", "DirectX", "Vulkan", "Metal", "CUDA", "OpenCL", "OpenACC", "OpenMP", "MPI", "OpenMPI", "Docker", "Kubernetes", "AWS", "Azure", "GCP", "Heroku", "DigitalOcean", "Linode", "Vultr", "Cloudflare", "CloudFront", "CloudFlare Workers", "CloudRun", "CloudSQL", "CloudFunctions", "CloudStorage", "CloudFirestore", "CloudTasks", "CloudScheduler", "CloudBuild", "CloudComposer", "CloudDataflow", "CloudDataproc", "CloudDatastore", "CloudDebugger", "CloudDLP", "CloudDNS", "CloudIAM", "CloudIdentity", "CloudIOT", "CloudKMS", "CloudMemorystore", "CloudMonitoring", "CloudNaturalLanguage", "CloudOSConfig", "CloudPubSub", "CloudResourceManager", "CloudRuntimeConfig", "CloudSecretManager", "CloudSpanner", "CloudSpeech", "CloudStorage", "CloudTalent", "CloudTasks", "CloudTrace", "CloudTranslation", "CloudVideoIntelligence", "CloudVision", "CloudWebRisk", "CloudWorkflows", "CloudRun", "CloudSQL", "CloudFunctions", "CloudStorage", "CloudFirestore", "CloudTasks", "CloudScheduler", "CloudBuild", "CloudComposer", "CloudDataflow", "CloudDataproc", "CloudDatastore", "CloudDebugger}
