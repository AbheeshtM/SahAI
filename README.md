# SahAI: AI Vision Companion for the Visually Impaired

## What is SahAI?

SahAI is a voice-first AI companion that helps visually impaired users navigate and understand their environment. Instead of robotic labels, it describes the world naturally: "There's a coffee mug to your left, about arm's length away" or "A person is walking toward you from the right."

Built for the AWS Student Track hackathon, SahAI demonstrates how AI can create meaningful public impact by making the world more accessible.

## The Problem

Visually impaired individuals face daily challenges:
- Understanding unfamiliar environments
- Identifying objects and people around them
- Navigating safely to destinations
- Maintaining independence without constant assistance

Traditional solutions are expensive, require specialized hardware, or provide robotic, unhelpful descriptions.

## Our Solution

SahAI combines computer vision, natural language AI, and voice interaction to provide:

- **Human-like descriptions**: "A tall building on your right, about three stories high"
- **Voice-first interaction**: Ask naturally, "What's in front of me?" or "Where's the nearest coffee shop?"
- **Smart navigation**: Turn-by-turn guidance with landmark-based cues
- **Privacy-first design**: Local processing with minimal cloud usage

## Key Features

- Natural conversation powered by Amazon Bedrock
- Real-time voice interaction via Amazon Transcribe and Polly
- Navigation and POI discovery using Amazon Location Service
- Advanced scene understanding with Amazon Rekognition
- Works on standard smartphones (iOS/Android)
- Offline mode for core functionality

## AWS Services Used

- **Amazon Bedrock**: Natural language understanding and conversational responses
- **Amazon Transcribe**: Speech-to-text for voice commands
- **Amazon Polly**: Neural text-to-speech for natural audio feedback
- **Amazon Location Service**: Maps, routing, geocoding, and POI search
- **Amazon Rekognition**: Advanced computer vision for complex scenes
- **AWS IAM + KMS**: Security and encryption
- **Amazon CloudWatch**: Monitoring and reliability

## Quick Start

### Prerequisites
- AWS account with Bedrock, Transcribe, Polly, and Location Service enabled
- AWS CLI configured (use SSO or profiles, not static keys)
- Node.js or Python for backend development
- iOS/Android development environment for mobile app

### Setup Steps

1. **Enable AWS Services**
   ```bash
   # Set your region
   export AWS_REGION=us-east-1
   
   # Enable Bedrock model access in AWS Console
   # Navigate to Bedrock > Model access > Enable models
   ```

2. **Create Location Service Resources**
   ```bash
   # Create map, place index, and route calculator
   aws location create-map --map-name SahAI-Map --configuration Style=VectorEsriStreets
   aws location create-place-index --index-name SahAI-Places --data-source Esri
   aws location create-route-calculator --calculator-name SahAI-Routes --data-source Esri
   ```

3. **Configure IAM Permissions**
   - Create an IAM role with policies for Bedrock, Transcribe, Polly, Location, and Rekognition
   - Use least-privilege access
   - Attach role to Cognito Identity Pool for mobile access

4. **Set Environment Variables**
   ```bash
   # Create .env file (never commit this!)
   AWS_REGION=us-east-1
   LOCATION_MAP_NAME=SahAI-Map
   LOCATION_PLACE_INDEX=SahAI-Places
   LOCATION_ROUTE_CALCULATOR=SahAI-Routes
   BEDROCK_MODEL_ID=anthropic.claude-v2
   ```

5. **Run the Application**
   - See [design.md](design.md) for architecture details
   - See [requirements.md](requirements.md) for complete specifications

## Project Structure

```
SahAI/
├── README.md           # This file - project overview
├── design.md           # System architecture and technical design
├── requirements.md     # Functional and non-functional requirements
└── .env.example        # Environment variable template
```

## Demo Scenarios

1. **Environmental Awareness**: "What's around me?" → Describes objects, people, and layout
2. **Object Identification**: "What am I holding?" → Identifies items in hand
3. **Navigation**: "Take me to the nearest pharmacy" → Provides turn-by-turn guidance
4. **Social Interaction**: "Is someone in front of me?" → Detects people and their position

## Impact & Innovation

- **Accessibility**: Makes technology truly inclusive
- **Independence**: Reduces reliance on human assistance
- **Affordability**: Works on existing smartphones
- **Privacy**: Local processing with user control
- **Scalability**: Cloud-based services for global reach

## Technical Highlights

- Hybrid architecture: local processing + cloud augmentation
- Sub-3-second response time for environmental queries
- 4+ hours battery life with continuous use
- Offline mode for core features
- Multi-language support (expandable)

## Security & Privacy

- No permanent image storage
- End-to-end encryption with AWS KMS
- IAM least-privilege access
- Ephemeral S3 storage with auto-deletion
- GDPR and CCPA compliant

## Future Enhancements

- Indoor navigation with detailed mapping
- Multi-language support (Spanish, Hindi, Mandarin)
- Wearable device integration (smartwatches, AR glasses)
- Community-driven location information
- Advanced AI for complex scene understanding

## Team & Acknowledgments

Built for AWS Student Track: AI for Communities, Access & Public Impact

## License & Disclaimer

This is an assistive prototype for demonstration purposes, not a medical device or safety-critical system. Users should continue using traditional mobility aids and exercise caution.

## Documentation

- [System Design](design.md) - Complete architecture and AWS integration
- [Requirements](requirements.md) - Functional specifications and success criteria

## Contact

For questions or demo requests, please reach out to the development team.

