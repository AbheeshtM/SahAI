# SahAITrack: Requirements Document

## Project Overview

**Project Name:** SahAITrack: Student Track – AI for Communities, Access & Public Impact

**Description:** SahAI is a voice-first, AI-powered assistive companion designed for visually impaired users. It uses computer vision and sound to describe objects, people, and environments in a human-like way using body-relative and sensory comparisons instead of robotic labels.

**Target Users:** Visually impaired individuals seeking independent navigation and environmental awareness assistance.

## Functional Requirements

### FR1: Environmental Description
- **FR1.1:** The system shall capture real-time visual input from device camera
- **FR1.2:** The system shall process visual data using computer vision to identify objects, people, and environmental features
- **FR1.3:** The system shall provide human-like descriptions using body-relative positioning (e.g., "to your left", "in front of you", "behind you")
- **FR1.4:** The system shall use sensory comparisons in descriptions (e.g., "about the size of a coffee mug", "as tall as a person")
- **FR1.5:** The system shall avoid robotic or technical labels in favor of conversational descriptions

### FR2: Voice Interaction
- **FR2.1:** The system shall accept voice commands and questions in natural language
- **FR2.2:** The system shall respond to conversational queries such as:
  - "What is on my right?"
  - "Is someone in front of me?"
  - "What am I holding?"
  - "Describe what's around me"
- **FR2.3:** The system shall provide audio responses using text-to-speech synthesis
- **FR2.4:** The system shall support voice activation/wake word functionality
- **FR2.5:** The system shall handle ambient noise and varying speech patterns

### FR3: Navigation Assistance
- **FR3.1:** The system shall integrate with free, publicly available map APIs
- **FR3.2:** The system shall provide voice-based turn-by-turn navigation guidance
- **FR3.3:** The system shall identify nearby points of interest (restaurants, shops, public facilities)
- **FR3.4:** The system shall calculate accessible routes when possible
- **FR3.5:** The system shall provide landmark-based navigation cues

### FR4: Real-time Processing
- **FR4.1:** The system shall process visual input with minimal latency (< 3 seconds)
- **FR4.2:** The system shall maintain continuous environmental monitoring
- **FR4.3:** The system shall update descriptions as the user moves or environment changes
- **FR4.4:** The system shall prioritize relevant information based on user queries

## Non-Functional Requirements

### NFR1: Accessibility
- **NFR1.1:** The system shall be fully operable without visual interface
- **NFR1.2:** The system shall support screen reader compatibility
- **NFR1.3:** The system shall provide clear, understandable audio feedback
- **NFR1.4:** The system shall accommodate users with varying levels of vision impairment
- **NFR1.5:** The system shall follow WCAG 2.1 AA accessibility guidelines where applicable

### NFR2: Performance
- **NFR2.1:** The system shall operate on lightweight AI models suitable for mobile devices
- **NFR2.2:** The system shall function on low-bandwidth connections (< 1 Mbps)
- **NFR2.3:** The system shall have battery life of at least 4 hours of continuous use
- **NFR2.4:** The system shall start up within 10 seconds
- **NFR2.5:** The system shall maintain responsive performance on mid-range mobile devices

### NFR3: Privacy and Security
- **NFR3.1:** The system shall not permanently store captured images
- **NFR3.2:** The system shall process visual data locally when possible
- **NFR3.3:** The system shall encrypt any data transmitted to external services
- **NFR3.4:** The system shall provide clear privacy controls and settings
- **NFR3.5:** The system shall comply with data protection regulations (GDPR, CCPA)

### NFR4: Reliability
- **NFR4.1:** The system shall maintain 95% uptime during normal operation
- **NFR4.2:** The system shall gracefully handle network connectivity issues
- **NFR4.3:** The system shall provide offline functionality for basic environmental description
- **NFR4.4:** The system shall recover from errors without requiring restart
- **NFR4.5:** The system shall provide clear error messages via audio feedback

### NFR5: Usability
- **NFR5.1:** The system shall require minimal setup and configuration
- **NFR5.2:** The system shall provide intuitive voice commands
- **NFR5.3:** The system shall offer help and tutorial functionality
- **NFR5.4:** The system shall support multiple languages (initially English)
- **NFR5.5:** The system shall adapt to individual user speech patterns over time

### NFR6: Portability
- **NFR6.1:** The system shall run on iOS and Android platforms
- **NFR6.2:** The system shall support various device form factors (phones, tablets)
- **NFR6.3:** The system shall integrate with existing assistive technologies
- **NFR6.4:** The system shall work with standard mobile hardware (camera, microphone, speakers)

## Constraints and Assumptions

### Constraints
- **C1:** This is an assistive prototype, not a medical or safety-critical system
- **C2:** No dependency on visual user interface elements
- **C3:** Must use free and publicly available APIs for mapping services
- **C4:** Limited to mobile device computational capabilities
- **C5:** Must comply with app store guidelines for accessibility apps

### Assumptions
- **A1:** Users have access to smartphones with camera and microphone
- **A2:** Users have basic familiarity with voice-controlled devices
- **A3:** Internet connectivity is available for navigation features
- **A4:** Users understand this is an assistive tool, not a replacement for traditional mobility aids
- **A5:** Free map APIs will remain available and accessible

## Success Criteria

### Primary Success Metrics
- **S1:** Users can successfully identify objects and people in their environment
- **S2:** Users can navigate to nearby locations with voice guidance
- **S3:** System provides accurate environmental descriptions 90% of the time
- **S4:** User satisfaction rating of 4.0/5.0 or higher
- **S5:** System response time under 3 seconds for environmental queries

### Secondary Success Metrics
- **S6:** Reduced reliance on human assistance for basic navigation tasks
- **S7:** Increased confidence in unfamiliar environments
- **S8:** Positive feedback from accessibility community
- **S9:** Successful integration with existing assistive technology workflows
- **S10:** Demonstration of measurable public impact through user testimonials

## Out of Scope

- Medical diagnosis or health monitoring
- Emergency response or safety-critical navigation
- Professional mobility training
- Integration with specialized hardware beyond standard mobile devices
- Real-time translation services
- Social media or communication features
- Commercial or advertising integrations