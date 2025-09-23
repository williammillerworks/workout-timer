# Timer Execution Screen - PRD for v0

09.22.25 Make workout timer fit viewport and remove interval badge

09.23.25 Added workout list selection, comprehensive edit functionality

## Overview
Create a workout timer execution screen that guides users through their custom exercise routines with audio and visual feedback, following Toss app's minimal design principles.

## Core Requirements

### Timer Data Structure
```javascript
const sampleTimer = {
  name: "5 minutes squat daily",
  intervals: [
    {type: "exercise", duration: 30, name: "Squat"},
    {type: "rest", duration: 10, name: "Rest"},
    {type: "exercise", duration: 40, name: "Squat"},
    {type: "rest", duration: 10, name: "Rest"},
    {type: "exercise", duration: 50, name: "Squat"},
    {type: "rest", duration: 10, name: "Rest"},
    {type: "exercise", duration: 60, name: "Squat"},
    {type: "rest", duration: 10, name: "Rest"},
    {type: "exercise", duration: 30, name: "Squat"},
    {type: "rest", duration: 10, name: "Rest"},
    {type: "exercise", duration: 30, name: "Squat"},
    {type: "rest", duration: 10, name: "Rest"}
  ]
}
```

## Visual Requirements

### Layout (Mobile-first)
- **Current interval name** (large, prominent)
- **Remaining time** (big countdown display)
- **Progress indicator** (circular or linear)
- **Next interval preview** (small text)
- **Control buttons** (pause/resume, stop)

### Design System (Toss Style)
- **Colors**: Primary blue (#0064FF), Success green (#00C896), Warning orange (#FF8A00)
- **Typography**: Clean, bold numbers for countdown
- **Spacing**: Generous whitespace, card-based layout
- **Buttons**: Rounded corners, clear hierarchy

### States
1. **Exercise State**: Green accent, "EXERCISE" label, exercise name
2. **Rest State**: Orange accent, "REST" label, "Rest" text
3. **Paused State**: Gray overlay, "PAUSED" indicator
4. **Countdown State**: Special styling for final 5 seconds

## Audio Requirements

### Audio Cues (English)
- **Every second**: Subtle tick sound
- **Halfway point**: "15 seconds left" (example for 30s interval)
- **Final 5 seconds**: "5, 4, 3, 2, 1, Done!"
- **Rest countdown**: "Next in 5, 4, 3, 2, 1"

### Audio Implementation
- Use Web Audio API or HTML5 audio
- Text-to-speech for voice announcements
- Sound effects for ticks and transitions

## Functional Requirements

### Timer Logic
- Auto-advance through intervals
- Accurate timing (use performance.now())
- Handle pause/resume correctly
- Background execution support

### Controls
- **Pause/Resume**: Toggle current interval
- **Stop**: End workout completely
- **Skip**: Jump to next interval (optional for MVP)

### Edge Cases
- Handle page visibility changes
- Prevent screen sleep during workout
- Audio permission handling

## Technical Notes
- React functional component with hooks
- Mobile-responsive (320px-768px)
- Smooth animations for state transitions
- Accessible for screen readers

## Success Criteria
- Clear visual feedback for current state
- Reliable audio cues at correct timing
- Intuitive pause/resume functionality
- Matches Toss app's visual quality
