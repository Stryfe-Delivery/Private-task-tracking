# Routine Tasks Color Grid Tracker

## Overview
A mobile-first HTML application for tracking daily activities across six color-coded grids. Each grid represents a different category with 365 checkboxes (one for each day of the year) organized in a 12-column layout. The app features swipe navigation, persistent local storage, and touch-friendly interaction. There is no cloud data, AI, or account credentials

## Features
- Six color-coded grids (Red, Orange, Yellow, Green, Blue, Purple)
- 365 checkboxes total (12 columns × monthly varying rows)
- Swipe left/right navigation between grids (tasks/ activities)
- Persistent checkbox state using localStorage
- Touch-optimized for mobile devices
- Should work on pc, but may need grid control adjusted for vertical layout (manual code change)
- Leap year detection (February adjusts to 29 days)
- Month and day labels for easy orientation
- Color-coded navigation dots
- Keyboard arrow key support for desktop navigation (alpha quality)

## Usage
### Opening the App
1. Save the HTML code as a file (e.g., `goals-tracker.html`)
2. Open the file in any modern web browser
3. The app works immediately - no installation required

### Using the Grids on Mobile
- **Tap checkboxes** to toggle between checked and unchecked states
- **Swipe left/right** to navigate between color grids
- **Tap colored dots** at the bottom to jump to a specific grid


## Customizing Grid Titles (OPTIONAL)
To customize the grid titles for your specific tracking needs:

1. **Find the color configuration array** in the JavaScript section (around line 340):
```javascript
const COLORS = ['red', 'orange', 'yellow', 'green', 'blue', 'purple'];
```

2. **Find the header creation code** (around line 385-400):
```javascript
header.textContent = `${color.charAt(0).toUpperCase() + color.slice(1)} Grid - Daily Tracker`;
```

3. **Replace the header text** with your custom titles:
```javascript
const CUSTOM_TITLES = {
    'red': 'Exercise Tracker',
    'orange': 'Meditation Log',
    'yellow': 'Water Intake',
    'green': 'Medication Taken',
    'blue': 'Reading Time',
    'purple': 'Slept Well'
};

header.textContent = CUSTOM_TITLES[color];
```

Alternative approach for simpler customization:
```javascript
const TITLES = [
    'Exercise & Fitness',
    'Mindfulness Practice', 
    'Nutrition Tracking',
    'Learning & Growth',
    'Work & Productivity',
    'Personal Goals'
];

header.textContent = TITLES[colorIndex];
```

## Potential Issues and Data Loss

### LocalStorage Limitations
The app uses browser localStorage to save checkbox states. Data loss can occur if:

**Clearing Browser Data**
- Clearing browser history/cache with "cookies and site data" option enabled
- Using browser's "Clear Browsing Data" feature
- App opened in "Private/Incognito" mode - data is deleted when session ends
- Browser extensions that clear localStorage

**Browser/Device Changes**
- Switching to a different browser
- Using a different device
- Browser updates that clear localStorage
- Operating system reinstallation

**Storage Quotas**
- localStorage has size limits (typically 5-10MB per domain)
- If storage limit is exceeded, data may not save properly (this shouldn't occur but may if there's a leak)


### Browser-Specific Considerations
- **Mobile browsers** may clear localStorage during storage pressure
- **Safari** may clear localStorage after 7 days of non-use
- **Firefox** may clear localStorage in Private Browsing mode
- **Chrome** maintains data until explicitly cleared

### Technical Issues
- JavaScript errors could occur if scripts are blocked by an extension/setting
- Colors and elements may not load if they are blocked by an extension/setting
  - e.g. a dark mode extension or image element ad blocker
- Browser security settings blocking localStorage

### Mitigation Strategies
TODO **Regular backups**: Periodically save data (_not currently implemented_)

## Technical Details

### Storage Structure
Each checkbox state is saved with a unique key:
```
{color}-{dayNumber}
```
Example: `"red-152"` for day 152 on the red grid

### File Structure
- Single HTML file containing all CSS, JavaScript, and markup
- No external dependencies
- No server required

### Browser Compatibility
- Chrome (tested)
- Safari 
- Firefox (tested)
- Edge
- Opera

### Performance Considerations
- localStorage operations on every toggle


## Development Notes

### Code Organization
- **CSS**: Styles at the top, mobile-first approach
- **HTML**: Minimal markup, dynamically generated
- **JavaScript**: ES6 features, event-driven architecture

### Key Functions
- `init()`: Initializes the application
- `createPages()`: Builds the six color grids
- `toggleCell()`: Handles checkbox toggling
- `saveData()`/`loadData()`: Manages localStorage
- `handleSwipe()`: Processes swipe gestures

### Future Enhancements
Potential features that could be added:
- Local data import/export functionality
- Custom color selection
- Grid title editing via GUI
- Statistics and progress tracking


## License
See attached 

## Support
For issues or questions:
1. Ensure JavaScript is enabled in your browser
2. Check browser console for errors (F12 on desktop)
3. Verify localStorage is not disabled in browser settings
4. Test in a different browser to isolate issues
5. Take the resuts of the above and add to an "Issues" event here in Git
