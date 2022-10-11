# Talent Connectors

Basically, we’ve noticed that a lot of the senior product/tech people get asked for talent recommendations all the time. Today, most of these requests go unmet due to a lack of time available and lack of access to talent.

We could establish a system that allows these ‘Connectors’ to send talent requests to Squad via the marketplace and receive profiles that they review and pass on to the client. They essentially act as individual matchmakers. Connectors get up to 50% of the marketplace fee once the talent that they helped connect to a mission starts to get paid. 

From a systems design perspective, how would you design the infrastructure of this peer-to-peer referral system such that it is as trustless and efficient as possible?

We are looking for your high-level thoughts on whatever simple form you prefer (bullet points, voice notes, a short paragraph). We can keep the brainstorming going asynchronously for a bit. Feel free to ask for clarification.


## Questions


## Systems

### How would you design the infrastructure of this peer-to-peer referral system such that it is as trustless and efficient as possible?
Connectors match talent with talent-requests (manually or via automated suggestions). Filled talent-requests are sent to Clients for approval. Client-approved talent-requests are sent to Talent for approval. Finally Connector recieves Talent & Client approved talent-requests for final review (can remove this step, efficiency--). 

### What parts need to be decentralized?
ether-js for payment, IPFS for storage, and a smart contract for the marketplace.
Zapper SDK for swaps.

Next.js or Meteor.js for the frontend.



## WIP - Connectors recieve automated suggested talent-requests based on talent-requests "talent-skills", "talent-types", and "availability".
match 60-100% configurable via Connector && Talent dashboards.


trustless + efficient

<!-- talent-requests -->
{
    "talent-request": {
        "id": "uuid",
        "connector-id": "uuid",
        "mission-id": "uuid",
        "talent-id": "uuid",
        "status": "pending|accepted|rejected",
        "created-at": "timestamp",
        "updated-at": "timestamp",
        "marketplace-fee-total": "number",
        "talent-types": ["string"],
        "talent-skills": ["string"],
        "availability": "datetime",
    }
}

connector-profile -> talent-request -> talent-profile

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

<!-- programming languages & tools -->

"programming-lang-tools" : { "JS", "React", "Node", "HTML", "CSS", "Rust", "C", "C++", "C#", "Ruby", "Deno", "Solidity", "Vyper", "Python", "Java", "Kotlin", "Swift", "Go", "R", "PHP", "Scala", "Elixir", "Clojure", "Haskell", "OCaml", "F#", "Erlang", "Julia", "Lua", "Perl", "Racket", "Scheme", "SQL", "Bash", "PowerShell", "Cobol", "Fortran", "Lisp", "Prolog", "Ada", "Assembly", "Dart", "Eiffel", "Forth", "Groovy", "Haxe", "J", "Julia", "LabVIEW", "Logo", "MATLAB", "Objective-C", "Pascal", "PL/SQL", "RPG", "SAS", "Scratch", "Smalltalk", "Tcl", "Visual Basic", "WebAssembly", "Z shell", "D", "Next.js", "Gatsby", "Vue", "Angular", "Ember", "Svelte", "React Native", "Flutter", "Ionic", "NativeScript", "Xamarin", "Electron", "jQuery", "Bootstrap", "Tailwind", "Material", "Ant Design", "Semantic UI", "Bulma", "Foundation", "UIKit", "Android", "iOS", "Windows", "macOS", "Linux", "Unix", "Chrome", "Firefox", "Safari", "Edge", "Opera", "Internet Explorer", "Node.js", "Express", "Koa", "Hapi", "Fastify", "Nest", "Sails", "Meteor", "Socket.io", "GraphQL", "Apollo", "REST", "SOAP", "gRPC", "WebSockets", "TCP", "UDP", "MQTT", "WebRTC", "WebAssembly", "WebGL", "OpenGL", "DirectX", "Vulkan", "Metal", "CUDA", "OpenCL", "OpenACC", "OpenMP", "MPI", "OpenMPI", "Docker", "Kubernetes", "AWS", "Azure", "GCP", "Heroku", "DigitalOcean", "Linode", "Vultr", "Cloudflare", "CloudFront", "CloudFlare Workers", "CloudRun", "CloudSQL", "CloudFunctions", "CloudStorage", "CloudFirestore", "CloudTasks", "CloudScheduler", "CloudBuild", "CloudComposer", "CloudDataflow", "CloudDataproc", "CloudDatastore", "CloudDebugger", "CloudDLP", "CloudDNS", "CloudIAM", "CloudIdentity", "CloudIOT", "CloudKMS", "CloudMemorystore", "CloudMonitoring", "CloudNaturalLanguage", "CloudOSConfig", "CloudPubSub", "CloudResourceManager", "CloudRuntimeConfig", "CloudSecretManager", "CloudSpanner", "CloudSpeech", "CloudStorage", "CloudTalent", "CloudTasks", "CloudTrace", "CloudTranslation", "CloudVideoIntelligence", "CloudVision", "CloudWebRisk", "CloudWorkflows", "CloudRun", "CloudSQL", "CloudFunctions", "CloudStorage", "CloudFirestore", "CloudTasks", "CloudScheduler", "CloudBuild", "CloudComposer", "CloudDataflow", "CloudDataproc", "CloudDatastore", "CloudDebugger}

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