# Product Requirements Document: Context-Aware AI Rewrites
**Voxbox/Handy: Intelligent Dictation Rewrites Based on Active Application Context**

**Version:** 1.0  
**Date:** 2026-06-18  
**Status:** Ready for Implementation  

---

## Executive Summary

Voxbox is currently a solid dictation tool, but it lacks intelligent rewriting capabilities that match the sophistication of competitors like Whisperflow and Talkastics. Users frequently dictate across multiple contexts (emails, Slack, code comments, social media) but receive generic post-processing that requires manual cleanup.

**This feature adds context-aware rewrites:** The app automatically detects what application you're dictating into, understands what you're writing (email body vs. subject vs. code comment), and applies a customized rewrite prompt that matches your tone and style for that specific context.

**Business Impact:**
- **Competitive parity**: Matches Whisperflow and Talkastics capabilities
- **User retention**: Users spend less time cleaning up dictation → higher engagement
- **Premium tier opportunity**: Could become a paid feature tier
- **Differentiation**: Configurability by users (not one-size-fits-all)

**Key Value Proposition:** *"Your dictation sounds like you, for every context you work in."*

---

## Problem Statement

### Current State (Friction Points)

1. **Generic Rewrites**
   - Marketing manager dictates a professional email and gets back slang
   - Product owner records a Slack message and gets formal business language
   - Developer dictates a code comment and it's over-explained
   - All users apply the same generic rewrite prompt

2. **Manual Context Switching**
   - Users must manually select different post-processing prompts
   - Wastes cognitive load before they start typing
   - Error-prone (forget to switch prompts, apply wrong tone)

3. **Lost Time in Cleanup**
   - Even with post-processing, users manually edit 30-50% of output
   - Defeats the purpose of speech-to-text (speed)
   - Undermines Voxbox's competitive positioning

4. **No Intelligence About Where Text Goes**
   - App doesn't "know" if you're writing an email, Slack message, or GitHub comment
   - Can't adapt tone automatically
   - Users see value in tools like Whisperflow that do this

### Opportunity

Competitors like Whisperflow and Talkastics already offer app-context detection. Users are switching to those tools specifically for this feature. Voxbox can capture this market by offering:
- ✅ Automatic app detection (Gmail, Slack, VSCode, etc.)
- ✅ Customizable rewrite profiles (users control their own tone)
- ✅ Privacy-first (local detection, optional cloud backup)
- ✅ Flexibility (works with any app, not just popular ones)

---

## Goals & Success Metrics

### Primary Goals
1. **User time savings**: Average user spends 40% less time editing dictated text
2. **Accuracy improvement**: 85%+ of dictations require zero manual edits (currently ~50%)
3. **Feature adoption**: 60%+ of active users enable context-aware rewrites within 30 days
4. **User satisfaction**: NPS +10 points vs. baseline

### Secondary Goals
1. **Competitive positioning**: Feature parity with Whisperflow/Talkastics
2. **Premium tier enablement**: Revenue opportunity for pro/enterprise tier
3. **Retention**: 15% reduction in churn (users who use feature churn less)

### Success Metrics (KPIs)

| Metric | Target | Timeline |
|--------|--------|----------|
| Feature adoption rate | 60% | 30 days post-launch |
| Avg. time to publish after dictation | ↓ 40% | 60 days post-launch |
| Manual edit frequency | ↓ 50% | 60 days post-launch |
| Support tickets about "generic rewrites" | ↓ 80% | 30 days post-launch |
| User satisfaction (feature-specific NPS) | ≥ 8/10 | Ongoing |
| False positive rate (wrong context detected) | <5% | 60 days post-launch |

---

## User Personas & Stories

### Persona 1: Marketing Manager @ Digital Agency
**Name:** Sarah Chen  
**Title:** Senior Marketing Manager  
**Company:** 50-person digital marketing agency  
**Tech Comfort:** Moderate (uses Slack, Gmail, Google Docs daily; not a developer)  
**Pain Points:**
- Writes 20-30 emails daily to clients/team
- Uses Slack for quick team coordination
- Dictates client communication that must sound professional and personalized
- Wastes 5-10 minutes daily re-editing dictated emails

**Current Workflow:**
1. Opens email, starts Voxbox recording
2. Dictates: "Follow up on the campaign proposal we sent Tuesday. Let me know your thoughts."
3. Voxbox output: "Follow up on campaign proposal we sent tuesday. Let me know your thoughts" (generic, lowercase)
4. Manually edits: caps, punctuation, adds professional closing
5. Sends (now 2 minutes later)

**Desired Workflow (with Context-Aware Rewrites):**
1. Opens email, starts Voxbox recording
2. Dictates: "Follow up on the campaign proposal we sent Tuesday. Let me know your thoughts."
3. Voxbox automatically detects Gmail, email body field
4. Auto-applies "Professional Email" profile (her custom profile)
5. Output: "Following up on the campaign proposal we sent on Tuesday. I'd appreciate your feedback on the proposal." (professional, grammatically perfect)
6. Sends immediately (or minor tweak in 30 seconds)

---

### User Story 1.1: Marketing Manager - Auto-Detect Email Context

**As a** marketing manager who spends most of my day in email  
**I want** Voxbox to automatically detect when I'm writing an email and apply my professional tone  
**So that** I can send polished client communications without manual editing  

**Acceptance Criteria:**
- [ ] When I dictate in Gmail compose window, Voxbox detects "email body" context
- [ ] App automatically selects my "Professional Email" profile without me doing anything
- [ ] Output is grammatically perfect, uses formal tone, includes proper punctuation
- [ ] Works for both email body and subject line (applies different profile to subject)
- [ ] Detection works 95%+ of the time (false positives <5%)
- [ ] I can manually override the auto-selected profile if needed
- [ ] If detection fails, it falls back to my default post-processing (doesn't break)

**Value:**
- Saves 2-3 minutes per email (30+ emails/day = 60-90 min/day saved)
- Increases confidence in client-facing communication quality
- Reduces proofreading burden

**Testing Scenarios:**
- Gmail desktop compose
- Gmail web compose
- Outlook email
- Apple Mail
- Gmail subject line vs. body (different profiles)

---

### User Story 1.2: Marketing Manager - Custom Profile Management

**As a** marketing manager with different client communication needs  
**I want** to create and manage multiple rewrite profiles for different contexts  
**So that** my dictation adapts to who I'm talking to (client vs. internal team)  

**Acceptance Criteria:**
- [ ] I can create a new rewrite profile in Settings with a name and custom prompt
- [ ] Examples: "Client Professional", "Team Casual", "Internal Update"
- [ ] I can define which apps/field types trigger each profile
- [ ] I can edit or delete profiles anytime
- [ ] Profiles persist across app sessions
- [ ] Settings UI is intuitive enough that I don't need a manual (drag & drop, tooltips)
- [ ] I can see preview examples of what each profile does
- [ ] I can duplicate a default profile to customize it

**Value:**
- Adapts tone to context (formal for clients, casual for team)
- More control vs. one-size-fits-all solution

**Testing Scenarios:**
- Create 3+ profiles with different prompts
- Apply profiles to different apps/field types
- Edit profile after creation
- Delete profile
- Profile list updates in real-time

---

### Persona 2: Product Manager @ SaaS Startup
**Name:** Alex Patel  
**Title:** Product Manager  
**Company:** 30-person SaaS startup  
**Tech Comfort:** High (technical background, comfortable with APIs and configuration)  
**Pain Points:**
- Writes product specs, feedback summaries, PRs (GitHub)
- Needs clear, concise communication style
- Uses Slack for team sync
- Wants to ensure dictation doesn't introduce fluff or emojis
- Wants feature to work across multiple apps without manual setup

**Current Workflow:**
1. Dictates PR description in VS Code comment
2. Gets: "Hey team, I've implemented a super cool feature that makes the dashboard lightning fast! Check it out!"
3. Must edit: remove exclamation marks, simplify, make it technical
4. Frustration: dictation added emojis and casual language that don't fit

**Desired Workflow (with Context-Aware Rewrites):**
1. Dictates PR description in VS Code
2. Voxbox detects code editor context
3. Auto-applies "Technical - Code Comments" profile
4. Output: "Optimized dashboard rendering by implementing virtual scrolling. Performance improved by 40%. See #2847 for details."
5. Sends without edits

---

### User Story 2.1: Product Manager - Multi-App Context Detection

**As a** product manager who works across Slack, GitHub, VS Code, and Google Docs  
**I want** Voxbox to detect which app I'm in and apply the right rewrite profile automatically  
**So that** I don't have to manually switch contexts or worry about tone mismatches  

**Acceptance Criteria:**
- [ ] When I dictate in Slack, it auto-applies my "Slack - Concise" profile
- [ ] When I dictate in VS Code or GitHub comment, it auto-applies my "Technical" profile
- [ ] When I dictate in Google Docs, it auto-applies my "Documentation" profile
- [ ] Detection works for all four apps with >90% accuracy
- [ ] If app is not recognized, it asks me to select a profile or uses a default
- [ ] Detection happens silently (no confirmation prompt that slows me down)
- [ ] I can see what profile was applied (in UI after paste)

**Value:**
- Single setup, works everywhere
- No cognitive load to switch profiles
- Consistent tone across communication channels

**Testing Scenarios:**
- Dictate in Slack channel (different from Slack DM)
- Dictate in GitHub PR description, PR review comment, issue
- Dictate in VS Code comment, docstring
- Dictate in Google Docs body text
- Dictate in unrecognized app (fallback behavior)

---

### User Story 2.2: Product Manager - Advanced Profile Configuration

**As a** technical product manager  
**I want** to configure profiles with custom prompts that specify my exact communication style  
**So that** Voxbox learns my preferences and rewrites match my voice exactly  

**Acceptance Criteria:**
- [ ] I can write custom prompts with variables like `${tone}`, `${audience}`, `${context}`
- [ ] Example prompt: "Rewrite as a technical specification. Tone: concise, no jargon. Audience: engineering team. Avoid exclamation marks and emojis."
- [ ] Prompts support multi-line text (not just single-line)
- [ ] I can test a profile by providing sample text and seeing the rewritten output
- [ ] Prompts are stored as JSON, can be exported/imported for backup
- [ ] I can version my prompts (track changes over time)
- [ ] Profile includes metadata: description, tags, auto-trigger rules

**Value:**
- Full control over output quality
- Can fine-tune profiles based on results
- Profiles can be versioned and rolled back

**Testing Scenarios:**
- Create profile with complex multi-line prompt
- Test profile with various sample inputs
- Export/import profiles
- Modify prompt and see different outputs

---

### Persona 3: Non-Technical User / Freelancer Using Claude Code
**Name:** Jordan** (they/them)  
**Title:** Freelance Content Creator + Claude Code User  
**Company:** Solopreneur  
**Tech Comfort:** Low-to-moderate (uses Claude Code to write, not Voxbox directly, but benefits from it)  
**Pain Points:**
- Uses Claude Code to help draft social media, blog posts, emails
- Often dictates to Claude Code prompts, needs those to be clear and structured
- Doesn't want to learn complex tech, just wants things to work
- Appreciates defaults that "just work"

**Current Workflow:**
1. Opens Claude Code session, starts dictating a feature request
2. Dictates: "Hey Claude, I need you to build a thing that does stuff. Like imagine you can just say what you want and it writes the code. That would be cool."
3. Output is rambling, vague, requires manual editing to turn into a good prompt
4. Frustration: Voxbox doesn't help with structured prompts

**Desired Workflow (with Context-Aware Rewrites):**
1. Opens Claude Code chat, starts dictating a feature request
2. Voxbox detects Claude Code web interface
3. Auto-applies "Claude Prompt - Clear & Structured" profile
4. Output: "I need a feature that automatically detects the active app and rewrites dictated text to match the context. Key requirements: (1) screenshot detection, (2) app identification, (3) custom rewrite profiles."
5. Sends directly to Claude Code without editing

---

### User Story 3.1: Non-Technical User - One-Click Setup

**As a** non-technical freelancer who just installed Voxbox  
**I want** context-aware rewrites to work out-of-the-box with zero configuration  
**So that** I can immediately benefit without being overwhelmed by settings  

**Acceptance Criteria:**
- [ ] After first launch, context detection is enabled by default (with toggle)
- [ ] App comes with 5-7 pre-configured profiles that cover common use cases
- [ ] Pre-configured profiles: Email, Slack, Code, Social Media, Documentation, Generic
- [ ] Pre-configured profiles work well without customization
- [ ] No Gemini API key required to get started (local detection works immediately)
- [ ] I can toggle context detection on/off with a single switch
- [ ] Settings UI is simple, not overwhelming (hide advanced options by default)
- [ ] First-time user sees a 30-second tutorial about the feature

**Value:**
- Immediate value on first use
- No intimidating configuration
- Works for ~80% of users without customization

**Testing Scenarios:**
- Fresh install (no prior settings)
- Enable/disable toggle
- Use pre-configured profiles
- See feature works immediately

---

### User Story 3.2: Non-Technical User - Manual Profile Selection

**As a** freelancer who wants manual control but doesn't want complexity  
**I want** a simple way to manually pick a rewrite profile before I start dictating  
**So that** I have control without learning a technical configuration system  

**Acceptance Criteria:**
- [ ] Before starting a recording, I can see a dropdown of available profiles
- [ ] Dropdown shows profile name, short description, and emoji/icon
- [ ] I can click one to select it for the next dictation
- [ ] Selected profile persists until I change it
- [ ] Profile selection UI is in the main recording window (prominent, not buried in settings)
- [ ] No technical jargon or advanced options visible
- [ ] If I forget to select, auto-detection kicks in automatically

**Value:**
- Simple override mechanism
- Stays in "easy mode" while having control

**Testing Scenarios:**
- Select profile from dropdown
- Selected profile persists across multiple dictations
- Auto-detection still works if I don't select manually
- Dropdown is responsive and fast

---

### User Story 3.3: Non-Technical User - See What Happened

**As a** non-technical user  
**I want** to see which rewrite profile was applied after each dictation  
**So that** I understand what's happening and can learn which profiles work best for me  

**Acceptance Criteria:**
- [ ] After dictation is pasted, a toast/notification shows: "Applied 'Professional Email' profile"
- [ ] Notification is non-intrusive (doesn't block my typing)
- [ ] Notification appears for 3-5 seconds then auto-disappears
- [ ] I can disable this notification if it's annoying
- [ ] Notification includes profile name and confidence level (e.g., "High confidence")
- [ ] I can click notification to see what prompt was used (optional)

**Value:**
- Transparency builds trust
- Feedback loop for learning

**Testing Scenarios:**
- Multiple dictations across different apps
- See notifications appear and disappear
- Disable notifications, verify they don't appear
- Click notification to see prompt

---

## Feature Requirements

### Functional Requirements

#### FR-1: Screenshot Capture
- **Requirement:** App captures a screenshot of the active window when recording stops
- **Scope:** Cross-platform (Windows, macOS, Linux)
- **Performance:** Complete capture in <100ms
- **Privacy:** Local only, no upload unless user explicitly enables Gemini
- **Fallback:** If screenshot fails, continue with default post-processing
- **User Control:** Toggleable in settings; can be disabled entirely

#### FR-2: Context Detection (Local)
- **Requirement:** Analyze screenshot to detect active app and field type
- **Detection Methods:**
  - OCR text extraction (identify keywords like "To:", "Subject:", `def`, `class`)
  - Layout analysis (field position, size, styling)
  - Active window title (Windows/macOS/Linux)
  - Color/shape heuristics (email formatting, code indentation)
- **Accuracy Target:** 85%+ for top 10 apps (Gmail, Slack, VSCode, GitHub, Google Docs, Notion, Apple Mail, Outlook, LinkedIn, Twitter)
- **Speed:** Analysis completes in <300ms
- **Fallback:** If detection fails, prompt user to select profile manually or use default

#### FR-3: Context Detection (Cloud - Optional)
- **Requirement:** If enabled and confidence <60%, call Gemini Vision API for enhanced detection
- **User Activation:** Requires explicit Gemini API key configuration
- **Privacy:** Prompts user before any screenshot leaves device
- **Rate Limiting:** Max 1 API call per minute (don't waste user's API quota)
- **Timeout:** 3-second timeout; if API doesn't respond, use local detection result
- **Cost:** ~$0.01 per 1000 images (Gemini Vision pricing)

#### FR-4: Rewrite Profiles
- **Structure:** Each profile has:
  - `id`: Unique identifier
  - `name`: Display name ("Professional Email")
  - `description`: One-line description
  - `prompt`: Custom rewrite instruction
  - `auto_triggers`: Rules for auto-selection
  - `enabled`: Boolean toggle
- **Default Profiles:** App includes 7 pre-configured profiles
- **User-Created Profiles:** Users can add unlimited custom profiles
- **Storage:** Persisted in app settings (JSON file)
- **Sharing:** Export/import profiles (JSON) for backup/sharing

#### FR-5: Profile Auto-Selection
- **Algorithm:** Score profiles based on matched triggers
  - App name match: +10 points
  - Field type match: +8 points
  - Text pattern match: +5 points
  - Select highest-scoring enabled profile
  - Tie-breaker: Most recently created/updated
- **Confidence Threshold:** Apply auto-selection if score ≥ threshold (80/100)
- **Low Confidence:** Prompt user to select manually or confirm auto-selection
- **Override:** User can always manually select a different profile

#### FR-6: Pipeline Integration
- **Integration Point:** `process_transcription_output()` in `actions.rs`
- **Flow:**
  1. Recording stops
  2. Capture screenshot (async, parallel with transcription)
  3. Transcribe audio (existing)
  4. Analyze screenshot context (existing code path)
  5. Auto-select profile based on context + user overrides
  6. If profile selected, use its prompt for LLM post-processing (reuse existing LLM integration)
  7. Paste result (existing)
- **No Breaking Changes:** If context detection fails or is disabled, app works exactly as before

#### FR-7: Settings & Configuration
- **New Settings:**
  - `context_detection_enabled`: Boolean (default: true)
  - `context_detection_use_gemini`: Boolean (default: false)
  - `gemini_api_key`: Encrypted string
  - `rewrite_profiles`: Array of RewriteProfile objects
  - `selected_rewrite_profile_id`: String or null (manual override)
- **UI Components:**
  - Toggle: Enable/disable context detection
  - Toggle: Enable/disable Gemini (with API key input)
  - Modal: List/create/edit/delete profiles
  - Dropdown: Manual profile selection (in recording UI)
  - Toast: Notification showing applied profile
- **Backward Compatibility:** Existing post-processing settings unchanged

#### FR-8: Error Handling
- **Screenshot Capture Failure:** Log error, skip detection, use default post-processing
- **OCR Failure:** Log error, fall back to window title heuristics only
- **Low Confidence Detection:** Prompt user to select profile or confirm auto-selection
- **Gemini API Error:** Log error, use local detection result
- **Network Timeout:** Timeout after 3s, fall back to local detection
- **No Profile Matches:** Use default post-processing prompt or user's last-selected profile

#### FR-9: Cross-Platform Support
- **Windows:** Use Win32 BitBlt for screenshot, GetForegroundWindow() for active app
- **macOS:** Use CGWindowListCreateImage, NSWorkspace.frontmostApplication
- **Linux:** Use X11 XGetImage / Wayland screenshot API, _NET_ACTIVE_WINDOW
- **Fallback:** If native APIs unavailable, OCR + heuristics alone (works on any platform)

#### FR-10: Performance & Startup
- **Screenshot Latency:** <100ms capture, <300ms analysis
- **Total Transcription Pipeline Overhead:** <500ms (acceptable, dwarfed by transcription time)
- **Startup Impact:** None (lazy loading of detection libraries)
- **First-Run Setup:** Tesseract OCR downloaded separately (not in app package)

### Non-Functional Requirements

#### NFR-1: Privacy
- ✅ Screenshots never leave device unless user enables Gemini
- ✅ Gemini API key stored encrypted in settings
- ✅ Users can disable context detection entirely
- ✅ No tracking or telemetry of detection results
- ✅ No screenshots stored to disk (kept in memory only)

#### NFR-2: Usability
- ✅ Feature works with zero configuration (defaults provided)
- ✅ Non-technical users can create profiles in <2 minutes
- ✅ Settings UI has tooltips and examples
- ✅ Errors show user-friendly messages (no stack traces)
- ✅ Notifications are non-blocking and auto-dismiss

#### NFR-3: Reliability
- ✅ Feature gracefully degrades if any component fails
- ✅ No crash on screenshot failure, OCR failure, API timeout
- ✅ Extensive logging for debugging (not visible to users)
- ✅ E2E tests cover happy path and error cases

#### NFR-4: Maintainability
- ✅ Clean architecture: separate concern modules (screenshot, analyzer, profiles)
- ✅ Extensive inline comments explaining heuristics
- ✅ Unit tests for profile selection algorithm
- ✅ Integration tests for each platform

#### NFR-5: Scalability
- ✅ Unlimited user-created profiles (no DB constraints)
- ✅ No server-side storage required (settings stored locally)
- ✅ Gemini API has built-in rate limiting (user's responsibility)

---

## Out of Scope (Phase 2+)

The following features are explicitly out of scope for Phase 1 but worth noting for future roadmap:

- ❌ **Cloud sync of profiles** (profiles only stored locally in Phase 1)
- ❌ **Shared profile library** (users can't browse/download others' profiles)
- ❌ **A/B testing profiles** (no analytics on profile effectiveness)
- ❌ **Gemini Vision integration** (available as option, not required)
- ❌ **Custom field detection** (limited to pre-defined field types)
- ❌ **Tone analysis of output** (no feedback loop on quality)
- ❌ **Mobile app support** (desktop only for Phase 1)
- ❌ **Video/screen recording integration** (screenshots only)

---

## Acceptance Criteria (Overall Feature)

### Before Launch

- [ ] **Core Functionality**
  - [ ] Screenshot capture works on Windows, macOS, Linux
  - [ ] Context detection accuracy ≥ 85% for top 10 apps
  - [ ] Profile auto-selection works correctly (scores and priorities)
  - [ ] Pipeline integration complete (screenshot → detection → profile selection → rewrite)
  - [ ] Fallback behavior tested (all error scenarios handled)

- [ ] **User Experience**
  - [ ] Settings UI is intuitive (5+ non-technical users can configure in <5 minutes)
  - [ ] Default profiles work out-of-the-box
  - [ ] Manual profile selection UI is prominent and easy
  - [ ] Notifications show applied profile
  - [ ] No jargon or technical terms in UI copy

- [ ] **Quality Assurance**
  - [ ] 100+ manual test cases passed
  - [ ] Performance <500ms overhead on transcription pipeline
  - [ ] Zero crashes in error scenarios
  - [ ] Privacy checklist: screenshots never leave device without consent
  - [ ] Cross-platform testing (Windows 10+, macOS 11+, Ubuntu 20.04+)

- [ ] **Documentation**
  - [ ] User guide for setting up context detection (blog post or help doc)
  - [ ] Profile creation tutorial
  - [ ] Troubleshooting guide (false detection, OCR failures)
  - [ ] Release notes with feature overview

- [ ] **Analytics & Monitoring**
  - [ ] Feature adoption rate tracked
  - [ ] Detection accuracy metrics collected (anonymized)
  - [ ] Error logging configured
  - [ ] Support team trained on feature

---

## Success Scenario: Day-1 User Experience

### Marketing Manager (Sarah) - Day 1

**8:00 AM** - Sarah installs Voxbox and launches it for the first time.
- Sees welcome screen with "New: Context-Aware Rewrites!" badge
- Gets 30-second interactive tutorial (click through 3 slides)
- Tutorial shows: screenshot detection → app recognition → auto-rewrite
- Context detection is ON by default

**8:05 AM** - Sarah opens Gmail and starts a new email.
- Clicks Voxbox record button
- Dictates: "Hi Mark, I wanted to follow up on the proposal we sent last week. Do you have any questions about the timeline or deliverables?"
- Stops recording
- **[Behind scenes]**
  - Screenshot captured (Gmail compose visible)
  - Context detected: App="Gmail", FieldType="EmailBody"
  - Profile matched: "Professional Email" (auto-trigger on Gmail)
  - Prompt sent to LLM: "Rewrite as professional business email. Perfect grammar, formal tone, include greeting."
- **[Sarah sees output]**
  - "Dear Mark, I wanted to follow up regarding the proposal we submitted last week. Would you be available to discuss the timeline and deliverables?"
  - Toast notification: "✓ Applied 'Professional Email' profile"
  - Text pasted into Gmail
- **[Result]** Sarah can send immediately or make minor tweaks. Saves 1-2 minutes.

**8:30 AM** - Sarah switches to Slack to message her team.
- Clicks Voxbox record button
- Dictates: "Hey team, quick reminder that the client review is tomorrow at 2 PM. Bring your notes."
- Stops recording
- **[Behind scenes]**
  - Screenshot captured (Slack chat visible)
  - Context detected: App="Slack", FieldType="ChatMessage"
  - Profile matched: "Slack - Casual" (auto-trigger on Slack)
  - Prompt sent to LLM: "Rewrite as brief, friendly Slack message. Under 2 sentences. Use conversational tone."
- **[Sarah sees output]**
  - "Quick reminder: client review is tomorrow at 2 PM. Bring your notes! 👀"
  - Toast notification: "✓ Applied 'Slack - Casual' profile"
  - Text pasted into Slack
- **[Result]** Perfect tone for Slack. Sends immediately.

**9:15 AM** - Sarah opens Google Docs to write a client proposal.
- Dictates: "The deliverables for this project include a redesigned website with improved performance, three rounds of revisions, and final deployment."
- **[Sarah sees output]**
  - "This project's deliverables encompass: (1) a redesigned website with enhanced performance, (2) three revision cycles, (3) final deployment."
  - Toast notification: "✓ Applied 'Documentation' profile"
- **[Result]** Formatted as a structured list. Exactly what she needed.

**[Sarah's Daily Wins]**
- ✅ 6 emails sent, all on first try (no re-edits)
- ✅ Slack messages are friendly and on-brand
- ✅ Proposal looks professional and organized
- ✅ Saved ~15-20 minutes of manual cleanup
- ✅ Feeling: "This finally matches Whisperflow quality. I can actually use this daily."

**[Evening]** - Sarah gets an email from her colleague asking how to use Voxbox's new feature. She responds, "It just works. Install it, and your email comes out perfect. No setup needed."

---

## Success Scenario: Advanced User (Alex) - First Week

### Product Manager (Alex) - Days 1-5

**Day 1** - Alex installs Voxbox, sees context detection is ON.
- Immediately dictates a Slack message: detects Slack, applies "Slack - Concise" profile ✓
- Tries VS Code comment: detects code editor, applies "Technical" profile ✓
- Goes to Settings → Context-Aware Rewrites
- Sees pre-built profiles, list is good but wants customization

**Day 2** - Alex creates custom profiles:
- "Spec - Detailed" - for product specs with clear structure
- "PR - Technical" - for GitHub PRs (no fluff, technical language)
- "Feedback - Constructive" - for feedback to team (positive tone, actionable)
- Tests each profile with sample text
- Sees preview before applying to real work

**Day 3-5** - Alex uses profiles daily:
- Dictating in Google Docs → auto-applies "Spec - Detailed" → Perfect structured spec
- Dictating PR in GitHub → auto-applies "PR - Technical" → Clean, technical description
- Dictating feedback in Slack → auto-applies "Feedback - Constructive" → Supportive, clear
- Realizes can export profiles for backup
- Exports profiles as JSON (just in case)

**[Alex's Week Results]**
- ✅ Specs are clearer and require less review
- ✅ GitHub PRs are more professional (team compliments the descriptions)
- ✅ Feedback comes across better (better team relationships)
- ✅ Feeling: "This is exactly what I wanted. Whisperflow can't match this level of customization."

---

## Competitive Positioning

### vs. Whisperflow
| Feature | Voxbox | Whisperflow |
|---------|--------|------------|
| App detection | ✅ Local + optional Gemini | ✅ Cloud-only |
| Custom profiles | ✅ Full control | ❌ Limited templates |
| Privacy | ✅ Local-first | ❌ Screenshots to cloud |
| Export/import profiles | ✅ Phase 1 | ❌ No |
| Cost | Free (local), ~$0.01/API call (Gemini optional) | Subscription tier |
| **Differentiator** | **User control + privacy** | **Established product** |

### vs. Talkastics
| Feature | Voxbox | Talkastics |
|---------|--------|-----------|
| App detection | ✅ Yes | ✅ Yes |
| Custom prompts | ✅ Full customization | ❌ Pre-set only |
| Local processing | ✅ Tesseract OCR local | ❌ Cloud-only |
| Profile management | ✅ Create/edit/delete | ❌ No |
| Integration: GitHub/Slack/VSCode | ✅ Works with any | ✅ Limited integrations |
| **Differentiator** | **Customization + privacy** | **Simplicity for mass market** |

**Voxbox's Advantage:** Power users and privacy-conscious users choose Voxbox. Mass market might prefer Talkastics' simplicity, but pros prefer Voxbox's flexibility.

---

## Rollout Plan

### Alpha (Internal) - Week 1-2
- Developers + early adopters test feature
- Gather feedback on UX
- Identify performance issues
- Test all error scenarios

### Beta (Public) - Week 3-4
- Release to beta users via opt-in flag
- Public announcement: "Try new context-aware rewrites!"
- Gather feedback in Discord/community
- Iterate on UX based on feedback
- Monitor error rates and performance

### General Availability - Week 5
- Enable for all users by default
- Announcement in app and blog
- Email to all users with tutorial
- Support team prepared for questions

### Post-Launch (Week 6+)
- Monitor adoption rate
- Collect success stories
- Plan Phase 2 (Gemini integration, cloud sync, etc.)

---

## Appendix: Marketing Copy

### Feature Announcement Headline
**"Your Dictation, Your Tone — Everywhere You Type"**

### Tagline
**"Context-aware rewrites that match the app you're in."**

### Key Message
*Voxbox now understands where you're typing. Email? Professional tone. Slack? Casual and concise. Code comments? Technical and clear. Stop copying and pasting between contexts. Voxbox handles it.*

### CTAs
- "Try context-aware rewrites today"
- "Create your first profile"
- "See it in action (video)"

---

## Questions for Stakeholders

**For Marketing:**
1. Which competitor positioning resonates most (customization vs. privacy vs. ease-of-use)?
2. Should this be a free feature or premium tier?
3. How do we communicate this to existing users vs. new users?

**For Product:**
1. What are our success metrics for adoption (user % or usage frequency)?
2. Should Phase 2 (Gemini integration, cloud sync) be premium or free?
3. How do we handle users who create many profiles (UI/performance)?

**For Eng/Design:**
1. Can we batch the work into 3-week sprints (Phase 1: 2 sprints, Phase 2: 1.5 sprints)?
2. Do we need a designer for the new UI components or can eng mock them up?
3. Should we add telemetry to track which profiles users create (for insights)?

---

**Document Prepared By:** Claude Code (Agent)  
**Review Status:** ✅ Ready for Product Team Review  
**Approval Required From:** Product Manager, Engineering Lead, Design Lead
