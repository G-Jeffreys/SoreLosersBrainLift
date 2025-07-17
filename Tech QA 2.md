- For now, let's say that matchmaking is essentially just friend-to-friend, and any considerations of lobbies and random matchmaking and such can wait until the core product is finished. Let's also say that we are committing to a desktop-based experience, unless you can think of some compelling reasons this should be on browser instead. I have access to the elements.envato.com service, so I can hopefully source assets from there. I have free access to AWS, so any necessary hosting can be done through that if needed. Besides what I have already mentioned, I forgot that part of the project requirements are "character progression." My thinking is to add RPG-esque stats which improve as you play and which affect your ability to throw eggs, character speed (in terms of movement outside of the table), maybe composure (which would affect how quickly your chat window grows when you lose a round). Does that all make sense? If so, please summarize our discussion of the project up to this point
- ### ChatGPT said:
- ### Project Snapshot (as of 14 July 2025)
    - {{[[table]]}}
        - Layer
            - Current Decisions & Rationale
        - **Platform & Delivery**
            - **Desktop-only** for first release. Browser build is deprioritized because desktop affords easier keyboard chat, predictable performance, and no download-size ceiling.
        - **Matchmaking**
            - **Friends-only private sessions**—no public lobby or random match queue until core loop solidifies.
        - **Engine**
            - **Godot 4.x (GDScript)** chosen for its robust 2-D pipeline, lightweight builds, one-click desktop export, and built-in high-level networking (good enough for 2-4-player peer/host architecture).
        - **Hosting / Backend**
            - Free AWS credits can run a **headless Godot authoritative server** (or a lightweight Node service later, e.g., for LLM personas).
        - **Core Game Loop**
            - Turn-based card game (bluffing / trick-taking flavor). Each player has 10 s to act or auto-forfeits the round.
        - **Out-of-table Antics**
            - During another player’s turn you can stand up, fetch raw eggs, and throw them. Hits smear an egg overlay on the victim’s UI until they leave to wash it off.
        - **UI Sabotage Mechanic**
            - Losing a round enlarges the chat panel; it can overrun the screen, simulating taunts drowning out game info.
        - **Stretch Goal: Ludonarrative Dissonance**
            - Track “sync” between a player’s declared character persona and in-game choices (LLM-assisted or rule-based). Desync worsens UI readability.
        - **Character Progression (new)**
            - - **Throw Power / Accuracy** – affects egg trajectory and stun duration.
                - - **Move Speed** – how fast you reach the sink or snag eggs.
                    - - **Composure** – slows chat-panel growth rate and shrinks it faster after recovery.
                        - Stats improve through play (XP or milestone victories).
        - **Asset Pipeline**
            - Pull 2-D sprites, UI frames, and SFX from **elements.envato.com**; import into Godot with pixel-perfect settings (Filter off, Keep pixel-ratio).
        - **Networking Model**
            - Host-client (friend acting as host) or tiny AWS-hosted authoritative server; deck shuffles seeded on server to prevent cheating.
        - **Not in Scope Yet**
            - Public matchmaking, mobile/browser ports, advanced analytics, console releases, micro-transactions.
- ### Next Technical Milestones
    1. **Prototype card rules** in headless GDScript with unit tests.
    2. **Add network layer** (1 host + 1 client locally) to validate RPC flow.
    3. **Integrate character-stat system** (JSON save per player; simple XP curve).
    4. **Implement egg & chat-overlay UX** with Godot Tweens/AnimationPlayer.
    5. **Spin up AWS headless build** for remote-friend sessions.
    6. Everything on your wishlist fits comfortably within Godot’s sweet spots; no immediate pressure to jump to Unity or browser-first tooling.
