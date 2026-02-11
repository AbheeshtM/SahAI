# SahAI: Requirements Specification

## Executive Summary

**Project:** SahAI - AI Vision Companion for the Visually Impaired  
**Hackathon Track:** AWS Student Track – AI for Communities, Access & Public Impact  
**Mission:** Empower visually impaired individuals with AI-powered environmental awareness and navigation

**What Makes SahAI Different:**
- Conversational, human-like descriptions instead of robotic labels
- Voice-first interaction requiring zero visual interface
- Privacy-first architecture with local processing
- Runs on standard smartphones with AWS cloud augmentation
- Designed for real-world independence and accessibility

**Target Users:** Visually impaired individuals seeking independent navigation and environmental awareness in daily life.

## Core User Stories

**As a visually impaired user, I want to:**
1. Ask "What's around me?" and hear natural descriptions of my environment
2. Navigate to nearby locations with voice-guided directions
3. Identify objects I'm holding or encountering
4. Know if people are nearby and where they're positioned
5. Find points of interest like restaurants, shops, or transit stops
6. Use the app entirely through voice without touching the screen

## Functional Requirements

### FR1: Environmental Description & Scene Understanding

**Priority: Critical**

- **FR1.1:** Capture real-time visual input from device camera at 15-30 FPS
- **FR1.2:** Identify objects, people, obstacles, and environmental features using computer vision
- **FR1.3:** Provide human-like descriptions with body-relative positioning:
  - "A chair to your left, about two steps away"
  - "Someone walking toward you from the right"
  - "A doorway directly in front of you"
- **FR1.4:** Use sensory comparisons for size and distance:
  - "About the size of a coffee mug"
  - "As tall as a person"
  - "Arm's length away"
- **FR1.5:** Generate conversational, natural language responses (no robotic labels)
- **FR1.6:** Detect and warn about obstacles and hazards in the user's path
- **FR1.7:** Update descriptions dynamically as the user moves or environment changes

### FR2: Voice Interaction & Natural Language

**Priority: Critical**

- **FR2.1:** Accept voice commands and questions in natural, conversational language
- **FR2.2:** Support common queries:
  - "What is on my right?"
  - "Is someone in front of me?"
  - "What am I holding?"
  - "Describe what's around me"
  - "Where's the nearest coffee shop?"
  - "How do I get to [destination]?"
- **FR2.3:** Use Amazon Transcribe for accurate speech-to-text conversion
- **FR2.4:** Use Amazon Bedrock for natural language understanding and response generation
- **FR2.5:** Use Amazon Polly neural voices for natural-sounding text-to-speech
- **FR2.6:** Support wake word activation for hands-free operation
- **FR2.7:** Handle ambient noise, accents, and varying speech patterns
- **FR2.8:** Maintain conversation context across multiple turns
- **FR2.9:** Provide adjustable speech rate and volume
- **FR2.10:** Support interruption and clarification requests

### FR3: Navigation & Location Services

**Priority: High**

- **FR3.1:** Integrate Amazon Location Service for maps, geocoding, routing, and POI search
- **FR3.2:** Provide voice-based turn-by-turn navigation with natural cues:
  - "In 50 feet, turn right at the corner"
  - "You're approaching Main Street"
  - "The pharmacy is on your left"
- **FR3.3:** Identify nearby points of interest by category:
  - Restaurants, cafes, shops
  - Public transit stops
  - Medical facilities
  - Public restrooms
- **FR3.4:** Calculate pedestrian-friendly, accessible routes
- **FR3.5:** Provide landmark-based navigation cues for orientation
- **FR3.6:** Support destination search by name or category
- **FR3.7:** Announce arrival at destination
- **FR3.8:** Offer alternative routes when obstacles are detected

### FR4: Real-time Processing & Responsiveness

**Priority: High**

- **FR4.1:** Process visual input and respond within 3 seconds for environmental queries
- **FR4.2:** Maintain continuous environmental monitoring when app is active
- **FR4.3:** Update descriptions dynamically as user moves or environment changes
- **FR4.4:** Prioritize relevant information based on:
  - User's current query
  - Proximity and importance of objects
  - Safety-critical information (obstacles, hazards)
- **FR4.5:** Balance local and cloud processing for optimal speed and accuracy
- **FR4.6:** Provide immediate feedback for user actions (button presses, voice commands)

## Non-Functional Requirements

### NFR1: Accessibility & Universal Design

**Priority: Critical**

- **NFR1.1:** Fully operable without any visual interface or screen interaction
- **NFR1.2:** Compatible with iOS VoiceOver and Android TalkBack screen readers
- **NFR1.3:** Provide clear, understandable audio feedback for all actions
- **NFR1.4:** Accommodate users with varying levels of vision impairment (total blindness to low vision)
- **NFR1.5:** Follow WCAG 2.1 Level AA accessibility guidelines
- **NFR1.6:** Support haptic feedback for important notifications
- **NFR1.7:** Provide spatial audio cues for directional information
- **NFR1.8:** Allow customization of voice, speed, and verbosity preferences

### NFR2: Performance & Efficiency

**Priority: High**

- **NFR2.1:** Run lightweight AI models (< 50MB) on mobile devices for local processing
- **NFR2.2:** Function on low-bandwidth connections (< 1 Mbps) with graceful degradation
- **NFR2.3:** Achieve 4+ hours of battery life with continuous use
- **NFR2.4:** Start up and be ready within 10 seconds
- **NFR2.5:** Maintain responsive performance on mid-range devices (3+ years old)
- **NFR2.6:** Process 15-30 frames per second for real-time object detection
- **NFR2.7:** Cache frequently accessed data (maps, POIs) for faster access
- **NFR2.8:** Optimize AWS service calls to minimize latency and cost

### NFR3: Privacy & Security

**Priority: Critical**

- **NFR3.1:** Never permanently store captured images or video
- **NFR3.2:** Process visual data locally whenever possible; use cloud only when necessary
- **NFR3.3:** Encrypt all data in transit using TLS 1.3
- **NFR3.4:** Encrypt any data at rest using AWS KMS
- **NFR3.5:** Use IAM least-privilege roles and policies for all AWS service access
- **NFR3.6:** Treat any S3 storage as ephemeral with automatic lifecycle deletion (< 24 hours)
- **NFR3.7:** Provide clear privacy controls and settings accessible via voice
- **NFR3.8:** Comply with GDPR, CCPA, and accessibility regulations
- **NFR3.9:** No user tracking, analytics, or advertising
- **NFR3.10:** Provide transparent privacy policy in accessible format

### NFR4: Reliability & Resilience

**Priority: High**

- **NFR4.1:** Maintain 95%+ uptime for cloud services
- **NFR4.2:** Gracefully handle network connectivity issues with offline fallback
- **NFR4.3:** Provide offline functionality for:
  - Basic environmental description
  - Object identification
  - Cached map navigation
- **NFR4.4:** Recover from errors automatically without requiring app restart
- **NFR4.5:** Provide clear, actionable error messages via audio feedback
- **NFR4.6:** Implement retry logic for transient AWS service failures
- **NFR4.7:** Monitor system health with Amazon CloudWatch
- **NFR4.8:** Log errors for debugging while respecting privacy

### NFR5: Usability & User Experience

**Priority: High**

- **NFR5.1:** Require minimal setup (< 5 minutes from install to first use)
- **NFR5.2:** Provide intuitive, natural voice commands (no memorization required)
- **NFR5.3:** Offer voice-guided tutorial and help system
- **NFR5.4:** Support English initially, with architecture for multi-language expansion
- **NFR5.5:** Adapt to individual user speech patterns and preferences over time
- **NFR5.6:** Provide consistent, predictable interaction patterns
- **NFR5.7:** Minimize cognitive load with clear, concise responses
- **NFR5.8:** Allow users to interrupt and redirect conversations naturally

### NFR6: Portability & Compatibility

**Priority: Medium**

- **NFR6.1:** Run on iOS 14+ and Android 10+ platforms
- **NFR6.2:** Support various device form factors (phones, tablets)
- **NFR6.3:** Integrate with existing assistive technologies (screen readers, braille displays)
- **NFR6.4:** Work with standard mobile hardware (camera, microphone, speakers, GPS)
- **NFR6.5:** Support Bluetooth headphones and hearing aids
- **NFR6.6:** Function on devices with 3GB+ RAM and mid-range processors

## Technical Constraints & Assumptions

### Constraints
- **C1:** Assistive prototype for demonstration, not a medical device or safety-critical system
- **C2:** Zero dependency on visual UI elements (100% voice-operated)
- **C3:** Must use AWS services (Bedrock, Transcribe, Polly, Location Service)
- **C4:** Limited to mobile device computational capabilities
- **C5:** Must comply with iOS App Store and Google Play accessibility guidelines
- **C6:** AWS account with Bedrock model access required
- **C7:** Operating costs controlled via request throttling, caching, and quotas
- **C8:** Hackathon timeline: focus on core features and AWS integration

### Assumptions
- **A1:** Users have smartphones (iOS/Android) with camera, microphone, GPS
- **A2:** Users have basic familiarity with voice assistants (Siri, Google Assistant)
- **A3:** Internet connectivity available for navigation (offline mode for basic features)
- **A4:** Users understand this supplements, not replaces, traditional mobility aids
- **A5:** AWS services remain available and pricing stays within budget
- **A6:** Amazon Bedrock access to Claude or similar models is granted
- **A7:** Users consent to minimal data processing for functionality

## AWS Services Integration

### Core Services (Required)

| Service | Purpose | Usage |
|---------|---------|-------|
| **Amazon Bedrock** | Natural language understanding and conversational AI | Process user queries, generate human-like responses |
| **Amazon Transcribe** | Speech-to-text conversion | Convert voice commands to text in real-time |
| **Amazon Polly** | Text-to-speech synthesis | Generate natural-sounding audio responses |
| **Amazon Location Service** | Maps, routing, POI discovery | Navigation, geocoding, place search |

### Supporting Services (Required)

| Service | Purpose | Usage |
|---------|---------|-------|
| **AWS IAM** | Access control | Least-privilege roles and policies |
| **AWS KMS** | Encryption | Encrypt data at rest and manage keys |
| **Amazon CloudWatch** | Monitoring | Metrics, logs, alarms for reliability |

### Optional Services

| Service | Purpose | Usage |
|---------|---------|-------|
| **Amazon Rekognition** | Advanced computer vision | Complex scene analysis, facial detection |
| **Amazon Cognito** | User authentication | Optional user accounts and preferences |
| **Amazon S3** | Temporary storage | Ephemeral storage with auto-deletion |
| **AWS Lambda** | Serverless compute | API endpoints for mobile app |

### Recommended Bedrock Models

- **Primary:** Anthropic Claude (Claude 3 Sonnet) for conversational responses
- **Alternative:** Amazon Titan for cost-effective basic queries
- **Consideration:** Model selection based on query complexity and latency requirements

## Success Criteria & Metrics

### Hackathon Demo Success
- **Demo 1:** Live environmental description with natural language responses
- **Demo 2:** Voice-guided navigation to a nearby location
- **Demo 3:** Object identification and spatial awareness demonstration
- **Demo 4:** Showcase AWS service integration and architecture
- **Demo 5:** Demonstrate privacy-first design and offline capabilities

### Technical Success Metrics
- **T1:** 90%+ accuracy in object and person detection
- **T2:** < 3 seconds response time for environmental queries
- **T3:** < 2 seconds latency for voice interaction (STT + TTS)
- **T4:** 4+ hours battery life with continuous use
- **T5:** Successful AWS service integration with < 5% error rate

### User Experience Metrics
- **UX1:** Users can complete basic tasks without visual interface
- **UX2:** Natural conversation flow with < 2 clarification requests per task
- **UX3:** Positive feedback from accessibility testers
- **UX4:** Intuitive voice commands requiring no training
- **UX5:** User satisfaction rating of 4.0/5.0 or higher

### Impact Metrics
- **I1:** Demonstrate measurable improvement in environmental awareness
- **I2:** Reduce reliance on human assistance for basic navigation
- **I3:** Increase user confidence in unfamiliar environments
- **I4:** Positive reception from accessibility community
- **I5:** Showcase scalable solution for global accessibility challenges

## Out of Scope (For Hackathon)

### Not Included in Current Version
- Medical diagnosis or health monitoring
- Emergency response or 911 integration
- Professional mobility training or certification
- Specialized hardware (smart canes, AR glasses)
- Real-time language translation
- Social media or messaging features
- Commercial partnerships or advertising
- Indoor mapping and navigation (future enhancement)
- Multi-user or family sharing features
- Payment or transaction processing

### Future Enhancements (Post-Hackathon)
- Multi-language support (Spanish, Hindi, Mandarin, Arabic)
- Indoor navigation with detailed building maps
- Wearable device integration (smartwatches, AR glasses)
- Community-driven location reviews and accessibility ratings
- Advanced AI for complex scene understanding
- Integration with public transit systems
- Offline map downloads for entire cities
- Customizable voice personas and interaction styles

## Development Roadmap

### Phase 1: Hackathon MVP (Current)
- Core environmental description
- Voice interaction with AWS services
- Basic navigation with Amazon Location Service
- Privacy-first architecture
- iOS or Android prototype

### Phase 2: Beta Release (Post-Hackathon)
- Both iOS and Android apps
- Expanded object recognition
- Improved navigation with landmarks
- User testing with accessibility community
- Performance optimization

### Phase 3: Public Release
- Multi-language support
- Offline mode enhancements
- Community features
- Wearable integration
- Global availability

## Testing & Validation

### Testing Approach
1. **Unit Testing:** Individual components (CV, NLU, TTS)
2. **Integration Testing:** AWS service integration
3. **Accessibility Testing:** Screen reader compatibility, voice-only operation
4. **User Testing:** Real-world testing with visually impaired users
5. **Performance Testing:** Battery life, latency, accuracy
6. **Security Testing:** Privacy controls, encryption, data handling

### Validation Criteria
- All critical functional requirements met
- Accessibility guidelines compliance verified
- Performance benchmarks achieved
- Positive feedback from accessibility testers
- Successful AWS service integration demonstrated
- Privacy and security requirements validated

## Conclusion

SahAI represents a meaningful application of AI technology for social impact, specifically addressing accessibility challenges faced by visually impaired individuals. By leveraging AWS managed services, the project demonstrates how cloud-based AI can be combined with privacy-first design to create inclusive, empowering technology.

The requirements outlined in this document provide a clear roadmap for building a functional prototype that showcases both technical innovation and real-world impact, aligning perfectly with the AWS Student Track hackathon goals.
