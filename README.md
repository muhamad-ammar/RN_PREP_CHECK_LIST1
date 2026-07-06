# ABC – Senior Mobile Developer Interview Prep Checklist
**8-Hour Focused Prep | Covers: JS/TS core, MERN, React Native depth, Networking/Security, System Design**

> Priority key: 🔴 Must-know (they already flagged this) | 🟡 Very likely | 🟢 Good to mention if it comes up

---

## HOUR 1–2: JavaScript & TypeScript Core (🔴 — cofounder specifically asked this)

### JavaScript Fundamentals
- [x] What is the **Event Loop**? Call stack, Web APIs, Callback queue, Microtask queue
- [x] **Microtask vs Macrotask** — why `Promise.then` runs before `setTimeout(fn, 0)`
- [x] **Closures** — practical example (counter, memoization)
- [x] **Hoisting** — var vs let/const, temporal dead zone
- [x] `this` keyword — in normal function, arrow function, class method, event handler
- [x] **Prototypal inheritance** — `__proto__`, prototype chain, `Object.create`
- [x] **Promises** — states (pending/fulfilled/rejected), `Promise.all` vs `allSettled` vs `race` vs `any`
- [x] `async/await` — how it desugars to promises, error handling with try/catch
- [x] **Debounce vs Throttle** — implement one from scratch on a whiteboard
- [x] **Currying / Higher-order functions**
- [x] Shallow copy vs deep copy (spread, `structuredClone`, JSON tricks and their limits)
- [x] Event bubbling vs capturing, `stopPropagation` vs `preventDefault`
- [x] `==` vs `===`, type coercion gotchas
- [x] Map/Set vs Object/Array — when to use which
- [x] Generators (`function*`, `yield`) — at least know what they are

### TypeScript (🔴 explicitly asked)
- [x] `interface` vs `type` — when to use which, declaration merging (interfaces only)
- [x] `any` vs `unknown` vs `never` vs `void`
- [x] **Generics** — write a generic function/component (e.g., `function identity<T>(x: T): T`)
- [x] **Utility types**: `Partial`, `Pick`, `Omit`, `Required`, `Record`, `Readonly`
- [x] Union types vs Intersection types
- [x] **Type narrowing** — `typeof`, `instanceof`, discriminated unions, type guards (`is` keyword)
- [x] Enums vs union of string literals (why many teams prefer literal unions)
- [x] Optional chaining `?.` and nullish coalescing `??`
- [x] `as const`, readonly arrays/tuples
- [x] Function overloads
- [x] Decorators (basic awareness — used in NestJS/Angular)
- [x] How TS compiles down (`tsc`), difference between compile-time and runtime safety
- [x] Explain a time you caught a bug **because of** TypeScript

---

## HOUR 2–3: MERN Stack Recall (🔴 — you learned this 4 yrs ago, refresh hard)

### MongoDB
- [x] Document vs Collection vs Database (compare to SQL table/row)
- [x] Schema design — embedding vs referencing (when to embed vs use ObjectId ref)
- [x] Mongoose basics — Schema, Model, `.populate()`
- [x] Indexing — why it speeds reads, tradeoff on writes
- [x] Aggregation pipeline — `$match`, `$group`, `$lookup` (just know the concept)
- [x] CRUD operations syntax refresh (`find`, `findOne`, `updateOne`, `insertMany`)

### Express.js
- [x] What is **middleware**? `(req, res, next)` — order matters
- [x] Error-handling middleware (4-arg function signature)
- [x] Routing basics, route params vs query params vs body
- [x] `req`, `res` object — common methods (`res.status().json()`, `req.headers`)
- [x] CORS — what it is, why it exists, how to enable it in Express
- [x] Rate limiting (concept — e.g., `express-rate-limit`)
- [x] REST API design principles — resource naming, idempotency, status codes (200/201/204/400/401/403/404/409/422/500)

### Node.js
- [x] Node is single-threaded but non-blocking — **why** (libuv, thread pool)
- [x] `require` vs `import` (CommonJS vs ES Modules)
- [x] Streams (basic idea — reading large files without loading into memory)
- [x] Environment variables / `.env` and why secrets shouldn't be hardcoded
- [x] npm vs yarn vs pnpm (just be aware)

### React (web, but concepts transfer 1:1 to RN)
- [x] **`useEffect`** — dependency array behavior, cleanup function, common bugs (stale closures, infinite loops)
- [x] `useState` — batching updates, functional updates `setX(prev => ...).`
- [x] `useMemo` vs `useCallback` — when each actually matters (don't over-optimize)
- [x] `useRef` — mutable value that doesn't trigger re-render, DOM/node access
- [x] Custom hooks — write one live if asked (e.g., `useDebounce`, `useFetch`)
- [x] Context API — when to use vs Redux, re-render pitfalls
- [x] Controlled vs uncontrolled components
- [x] Reconciliation & Virtual DOM — why `key` prop matters in lists
- [x] `React.memo` — shallow comparison, when it helps/hurts
- [x] Prop drilling and how Context/state managers solve it

---

## HOUR 3–4.5: React Native Deep Dive (🔴 your actual strength — go deep here)

### Architecture
- [ ] Old architecture: **Bridge** (async, JSON serialization bottleneck)
- [ ] New architecture: **JSI** (JavaScript Interface — direct C++ binding, no serialization)
- [ ] **Fabric** renderer vs old UIManager
- [ ] **TurboModules** vs old Native Modules (lazy loading)
- [ ] **Hermes** engine — why it improves startup time, bytecode precompilation
- [ ] Metro bundler — what it does

### Performance
- [ ] Causes of unnecessary re-renders (inline functions/objects as props, missing memo)
- [ ] `FlatList` optimization: `keyExtractor`, `getItemLayout`, `windowSize`, `initialNumToRender`, `removeClippedSubviews`
- [ ] `FlashList` (Shopify) — why it's faster than FlatList (recycling views)
- [ ] Image optimization/caching (FastImage vs native Image)
- [ ] JS thread vs UI/Native thread vs Shadow thread — what runs where
- [ ] Detecting memory leaks — tools (Flipper, Xcode Instruments, Android Profiler)
- [ ] Bundle size reduction — Hermes, ProGuard/R8, code splitting

### Storage & Security (🔴 they may probe this given HR/payroll data)
- [ ] AsyncStorage vs **MMKV** vs SQLite vs Realm — tradeoffs
- [ ] **Secure token storage**: Keychain (iOS) / Keystore (Android) via `react-native-keychain` or `expo-secure-store` — never AsyncStorage for tokens
- [ ] **SSL Pinning** — what it is, why it prevents MITM attacks, how it's implemented (cert/public key pinning)
- [ ] Jailbreak/Root detection (concept level)
- [ ] Obfuscation (ProGuard, Hermes bytecode)
- [ ] OWASP Mobile Top 10 (just recognize a few: insecure data storage, insecure communication, improper session handling)

### Native/Platform Layer
- [ ] Writing a simple Native Module (bridge a native iOS/Android function to JS)
- [ ] App permissions flow (runtime permissions Android, Info.plist iOS)
- [ ] Push notifications — FCM (Android) + APNs (iOS), how a push token is generated & used
- [ ] Background tasks/services (BackgroundFetch, WorkManager on Android)
- [ ] Deep linking / Universal links
- [ ] App lifecycle states: iOS (Active/Inactive/Background/Suspended) vs Android (Created/Started/Resumed/Paused/Stopped/Destroyed)
- [ ] Code signing basics — provisioning profiles (iOS), keystore (Android)
- [ ] OTA updates — CodePush / Expo EAS Update (what can/can't be updated OTA — no native code changes)

### State Management
- [ ] Redux core concepts: store, actions, reducers, single source of truth
- [ ] Redux middleware — Thunk vs Saga (generators for async flow)
- [ ] Redux Toolkit (RTK) — why it reduces boilerplate
- [ ] Zustand/Jotai — lightweight alternatives, when you'd pick them
- [ ] When Context API is enough vs when you truly need Redux

---

## HOUR 4.5–5.5: Networking, APIs & Auth (🔴 core to "API integration" line in JD)

- [ ] **REST vs GraphQL** — over-fetching/under-fetching problem GraphQL solves, single endpoint vs multiple, when REST is still better (simplicity, caching via HTTP)
- [ ] GraphQL basics — Query vs Mutation vs Subscription, resolvers (concept)
- [ ] **Axios** — interceptors (request/response), setting default headers, cancel tokens/AbortController, retry logic on 401
- [ ] HTTP methods — GET/POST/PUT/PATCH/DELETE and idempotency differences
- [ ] Status codes — 2xx/3xx/4xx/5xx meaning, specifically 401 vs 403
- [ ] **HTTPS/TLS handshake** — basic flow (client hello → server cert → symmetric key exchange)
- [ ] **JWT** — structure (header.payload.signature), where it's stored, why it's stateless
- [ ] **Access token + Refresh token flow** (the "token chain") — how silent refresh works, what happens when access token expires mid-request (queue pending requests, refresh once, retry all)
- [ ] OAuth2 flow (Authorization Code flow) — general idea, not deep implementation
- [ ] WebSockets — when you'd use over REST (real-time features like live shift updates/chat)
- [ ] Handling network errors gracefully — retry with backoff, offline queueing, showing user-friendly errors vs raw error codes
- [ ] API versioning strategies (`/v1/`, header-based)
- [ ] Pagination strategies — offset vs cursor-based (relevant for timesheets/shift lists)

---

## HOUR 5.5–6.5: System Design Scenario Prep (🔴 — practice explaining out loud)

### Scenario: "Design a multi-tenant app like Shopify where a user creates a store and all data (theme, icons, strings, config) comes from backend"

Structure your answer in this order when asked:

1. **Clarify requirements** — Single codebase, multiple tenants/stores, each with own branding/config. Ask: web+mobile? white-label apps or one app for all stores?
2. **Backend-driven UI (BDUI)** concept — server sends JSON describing UI/theme/copy; app renders dynamically instead of hardcoding
3. **Remote config layer** — tenant fetches a `config.json` on launch: colors, logo URL, feature flags, string translations (i18n keys from backend)
4. **Theming implementation** — dynamic theme provider (Context/Redux) that wraps app; components pull colors/fonts from a theme object, not hardcoded
5. **Caching strategy** — cache tenant config locally (AsyncStorage/MMKV) with a version/hash check, so app doesn't refetch on every launch; fallback to cached config if offline
6. **Asset delivery** — icons/images served via CDN, lazy-loaded, cached with something like FastImage
7. **Feature flags** — per-tenant feature toggles (e.g., one store has loyalty points, another doesn't) — LaunchDarkly-style or custom backend flag service
8. **Versioning & rollout** — how do you push a new theme structure without breaking older app versions still in the wild (backward-compatible config schema, default fallbacks)
9. **Performance concern** — don't block app startup on config fetch; show skeleton/cached version first, then update in background (stale-while-revalidate pattern)
10. **Scalability concern** — thousands of tenants: config shouldn't be baked into app binary; must be fully data-driven and fetched per tenant ID/subdomain
11. **Security** — tenant isolation: one store's user must never see another tenant's data — validate tenant ID server-side per request, not just trust client-supplied tenant ID

- [ ] Practice saying this out loud in under 3–4 minutes without reading
- [ ] Prepare one **real example** from your own experience (EV Charging Network project) that had a similar "config-driven / multi-environment" flavor, even partially

### Other likely system-design/scenario questions
- [ ] "How would you handle a user going offline mid-shift-checkin?" → offline-first queue, sync on reconnect, conflict resolution
- [ ] "How do you structure a large RN app folder-wise?" → feature-based modules vs type-based, separation of API layer/hooks/components/screens
- [ ] "How would you handle app crash reporting at scale?" → Firebase Crashlytics/Sentry, breadcrumbs, source maps for RN
- [ ] "How do you review a junior's PR that has a memory leak?" (you already have this WebSocket story — reuse it)

---

## HOUR 6.5–7: Testing, Git, CI/CD & Release (🟡 mentioned directly in JD)

- [ ] Unit testing — Jest basics, mocking modules/API calls
- [ ] E2E testing — Detox or Appium (just be aware, know the name)
- [ ] Git — merge vs rebase, resolving conflicts, git flow / trunk-based branching
- [ ] `git cherry-pick`, `git stash` — practical use cases
- [ ] Code review best practices — what you look for (readability, edge cases, performance, security)
- [ ] CI/CD pipeline — Fastlane, GitHub Actions/Bitrise for automated builds
- [ ] App Store & Play Store release process — TestFlight, staged rollout, review rejection common reasons
- [ ] Semantic versioning (major.minor.patch)

---

## HOUR 7–7.5: Behavioral / Ownership (🟡 — JD emphasizes "ownership mindset")

- [ ] Prepare 60-sec intro (you already have this — make sure it emphasizes **ownership** and **cross-team communication with international/remote teams**, since ABC is Belgian)
- [ ] STAR: EV Charging Network project
- [ ] STAR: WebSocket memory leak (~60% memory reduction)
- [ ] STAR: Code review with junior Flutter dev
- [ ] New STAR to prepare: a time you **took ownership** of a feature end-to-end (planning → release) — JD repeats "ownership" 3 times, they will ask this directly
- [ ] Why did you leave 10Pearls — keep your "slow project pipeline" framing, keep it brief and forward-looking
- [ ] Why are you a good fit despite MERN being 4 years old — be honest: "My recent 5 years have been deep in React Native/mobile, but my JS/TS fundamentals transfer directly since RN uses the same language and async patterns as MERN's frontend/backend layer — I refreshed the backend-specific pieces (Express, Mongo) this week."
- [ ] One good question to ask them: about their tech stack (is backend actually Node/Express?), team structure between Lahore and Belgium, or their approach to code review/ownership

---

## HOUR 7.5–8: Rapid-Fire Terminology Flashcards (🟢 skim right before interview)

Go through this list out loud, one-line definition each — if you hesitate on any, that's your last 10 minutes' focus:

`Event Loop` · `Call Stack` · `Microtask/Macrotask` · `Closures` · `Hoisting` · `Prototype chain` · `this` binding · `Promise.all/allSettled/race` · `async/await` · `Debounce/Throttle` · `Currying` · `Generics (TS)` · `Utility types (Pick/Omit/Partial)` · `Discriminated union` · `Type guard` · `useEffect cleanup` · `useMemo/useCallback` · `Reconciliation` · `Virtual DOM` · `Context API` · `Redux Thunk vs Saga` · `Middleware (Express)` · `CORS` · `REST vs GraphQL` · `Idempotency` · `Axios interceptor` · `JWT` · `Access/Refresh token flow` · `OAuth2` · `TLS handshake` · `SSL Pinning` · `JSI` · `Fabric` · `TurboModules` · `Hermes` · `Bridge (old RN arch)` · `FlatList vs FlashList` · `Keychain/Keystore` · `MMKV` · `Deep linking` · `Push notification token flow (FCM/APNs)` · `App lifecycle states` · `CodePush/OTA` · `Feature flags` · `Backend-driven UI` · `Stale-while-revalidate` · `Rate limiting` · `Aggregation pipeline (Mongo)` · `Indexing` · `Websockets vs REST` · `Semantic versioning`

---

## Final Notes
- Since the **cofounder round already flagged MERN/TS as a gap**, expect this second round to test whether you closed that gap — don't just memorize definitions, be ready to say **how it maps to what you did in React Native** (e.g., "useEffect works the same in RN as React," "Express middleware auth is conceptually identical to how I set up axios interceptors for token refresh in my mobile apps").
- For the system design question, **talk out loud, draw boxes if there's a whiteboard/screen-share**, and narrate tradeoffs — interviewers care more about your reasoning process than a "correct" answer.
- Keep every answer under ~90 seconds unless they ask you to go deeper (matches your known communication style) — then expand with a concrete example.
