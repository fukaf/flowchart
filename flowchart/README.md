# Flowchart Tool - Complete Documentation

## Overview
A professional HTML5 Canvas-based flowchart editor with comprehensive features including multi-select, alignment, auto-layout algorithms, and AI agent integration via JSON import.

---

## Quick Start

### For End Users
1. Open `flowchart.html` in a web browser
2. Create flowcharts using the visual interface
3. Or paste JSON into "Import JSON" for instant visualization

### For AI Agents
1. Read `AI_AGENT_PROMPT.md` for complete schema
2. Generate flowchart JSON based on user requirements
3. User pastes your JSON into the tool
4. Instant visual flowchart!

---

## Feature Documentation

### Core Features
- **8 Block Types:** Process, Decision, Terminator, I/O, Document, Database, Subprocess, Manual
- **Visual Editor:** Drag, resize, edit text with double-click
- **Connections:** Click-to-connect mode with labeled arrows
- **Multi-line Text:** Press Enter for line breaks, automatic wrapping
- **Undo/Redo:** 50-state history with Ctrl+Z/Ctrl+Y

### Advanced Features
📖 **[Multi-Select & Alignment](ALIGNMENT_FEATURE.md)**
- Ctrl+Click to select multiple blocks
- 9 alignment operations (left, right, top, bottom, center H/V, distribute H/V, auto-layout)
- Keyboard shortcuts (Ctrl+Shift+L/R/T/B/H/V)
- Group dragging

📖 **[Force-Directed Layout](FORCE_DIRECTED_LAYOUT.md)**
- Two auto-layout modes: Hierarchical (BFS) and Force-Directed (physics)
- Toggle between modes with "Layout Mode" button
- Physics simulation with repulsion/attraction forces
- Ideal for complex interconnected graphs

📖 **[JSON Import](JSON_IMPORT_FEATURE.md)**
- Direct JSON text input via "Import JSON" button
- Replace or append modes
- Perfect for AI-generated flowcharts
- Copy-paste workflow

---

## File Structure

```
flowchart/
├── flowchart.html                 # Main application (self-contained)
├── AI_AGENT_PROMPT.md            # Complete guide for AI agents
├── example_flowchart.json        # Example JSON structure
├── ALIGNMENT_FEATURE.md          # Multi-select & alignment docs
├── FORCE_DIRECTED_LAYOUT.md      # Layout algorithm docs
├── JSON_IMPORT_FEATURE.md        # JSON import implementation
└── README.md                      # This file
```

---

## For AI Agents: JSON Generation Guide

### Quick Reference
See `AI_AGENT_PROMPT.md` for the complete guide. Here's the minimal example:

```json
{
  "nodes": [
    {
      "id": 0,
      "x": 400,
      "y": 100,
      "w": 160,
      "h": 60,
      "type": "process",
      "text": "Step 1"
    },
    {
      "id": 1,
      "x": 400,
      "y": 200,
      "w": 160,
      "h": 60,
      "type": "process",
      "text": "Step 2"
    }
  ],
  "connections": [
    {
      "from": 0,
      "to": 1,
      "label": ""
    }
  ]
}
```

### Node Types
| Type | Shape | Use For |
|------|-------|---------|
| `process` | Rectangle | General operations, calculations |
| `decision` | Diamond | Conditionals, yes/no questions |
| `terminator` | Pill | Start/End points |
| `io` | Parallelogram | Input/Output operations |
| `document` | Wavy bottom | Documents, reports, files |
| `database` | Cylinder | Database operations |
| `subprocess` | Double-border | Subroutines, function calls |
| `manual` | Trapezoid | Manual operations |

### Positioning Tips
- **Vertical spacing:** 100-150px between nodes
- **Horizontal spacing:** 150-200px for branches
- **Start position:** (400, 50) or (400, 100)
- **Flow direction:** Top to bottom (most common)

See `example_flowchart.json` for a complete working example.

---

## User Guide

### Creating Blocks
Click any of the 8 block type buttons in the control panel:
- **Process** - General rectangular block
- **Decision** - Diamond for conditionals
- **Terminator** - Start/End pill shape
- **I/O** - Parallelogram for input/output
- **Document** - Paper shape with wavy bottom
- **Database** - Cylinder for data storage
- **Subprocess** - Double-bordered rectangle
- **Manual** - Trapezoid for manual tasks

### Editing
- **Move:** Drag blocks
- **Resize:** Drag corner/edge handles
- **Edit text:** Double-click block
- **Multi-line:** Press Enter in text editor
- **Delete:** Select and press Delete/Backspace

### Connections
1. Click "Connect Mode" button
2. Click source block
3. Click target block
4. Double-click line to add label

### Alignment
1. **Ctrl+Click** blocks to multi-select
2. Click alignment buttons or use shortcuts:
   - `Ctrl+Shift+L` - Align Left
   - `Ctrl+Shift+R` - Align Right
   - `Ctrl+Shift+T` - Align Top
   - `Ctrl+Shift+B` - Align Bottom
   - `Ctrl+Shift+H` - Center Horizontally
   - `Ctrl+Shift+V` - Center Vertically

### Auto Layout
1. Click "Layout Mode" to toggle Hierarchical ↔ Force-Directed
2. Click "Auto Layout" to apply
   - **Hierarchical:** Top-down flow (BFS-based)
   - **Force-Directed:** Physics simulation

### Import/Export
- **Export:** Click "Export" → Choose filename/folder → Save as JSON
- **Import File:** Click "Import" → Select .json file
- **Import JSON:** Click "Import JSON" → Paste JSON text → Import

### Keyboard Shortcuts
| Action | Shortcut |
|--------|----------|
| Undo | `Ctrl+Z` |
| Redo | `Ctrl+Y` |
| Save (Export) | `Ctrl+S` |
| Copy | `Ctrl+C` |
| Paste | `Ctrl+V` |
| Duplicate | `Ctrl+D` |
| Delete | `Delete` / `Backspace` |
| Snap to Grid | `G` |
| Multi-select | `Ctrl+Click` |
| Zoom | `Mouse Wheel` |
| Pan | `Drag canvas` |

---

## AI Agent Workflow

### Example Use Case

**User to AI:**
> "Create a flowchart for user registration with email verification"

**AI Response:**
```
I'll create a user registration flowchart with email verification. Here's the JSON:

[AI generates JSON using AI_AGENT_PROMPT.md guidelines]

To visualize:
1. Copy the JSON above
2. Open flowchart.html in your browser
3. Click "📋 Import JSON" button
4. Paste the JSON and click Import
5. Your flowchart appears instantly!

You can then:
- Edit any text by double-clicking
- Move blocks around
- Add more connections
- Export for later use
```

### Integration Methods

1. **Copy-Paste (Simplest)**
   - AI generates JSON
   - User copies and pastes into tool
   - Instant visualization

2. **File Generation**
   ```python
   # Python example
   import json
   
   flowchart = {
       "nodes": [...],
       "connections": [...]
   }
   
   with open('flowchart.json', 'w') as f:
       json.dump(flowchart, f, indent=2)
   ```
   User imports file via "Import" button

3. **API Integration** (Future)
   - POST JSON to endpoint
   - Tool fetches and displays
   - Fully automated workflow

---

## Browser Compatibility

✅ **Fully Supported:**
- Chrome 90+ (Recommended)
- Edge 90+
- Firefox 88+
- Safari 14+

⚠️ **Limited Features:**
- Older browsers may not support File System Access API (folder selection)
- Falls back to standard download

---

## Technical Stack

- **Frontend:** Pure HTML5 + CSS3 + Vanilla JavaScript
- **Canvas:** 2D rendering with coordinate transformation
- **Storage:** localStorage for auto-save
- **File API:** File System Access API for exports
- **No Dependencies:** Self-contained single HTML file

---

## Color Scheme (KPMG)

- **Primary Blue:** `#00338D`
- **Dark Blue:** `#0C233C`
- **Cobalt Blue:** `#1E49E2`
- **Light Blue:** `#ACEAFF`
- **Sky Blue:** `#76D2FF`
- **Orange (Multi-select):** `#FFB547`

---

## Performance

### Recommended Limits
- **Nodes:** Works well up to 200+ nodes
- **Force-Directed Layout:** Best for 20-80 nodes
- **Hierarchical Layout:** Fast for any number
- **Canvas Size:** Infinite scrollable workspace

### Optimization
- Undo/redo limited to 50 states
- Auto-save throttled to prevent lag
- Efficient collision detection
- Proportional zoom scaling

---

## Contributing

### Code Structure
- **Lines:** ~3,200
- **Functions:** 80+
- **Event Listeners:** 30+
- **Configuration:** Centralized CONFIG object

### Key Functions
- `draw()` - Main rendering loop
- `autoLayoutHierarchical()` - BFS layout
- `autoLayoutForceDirected()` - Physics layout
- `importFlowchart()` - JSON import with append mode
- `exportFlowchart()` - File/folder export

### Adding New Features
1. Add to CONFIG if configurable
2. Create function with JSDoc comment
3. Add event listener if UI-triggered
4. Update help modal
5. Document in appropriate .md file

---

## License & Credits

- **Tool:** Custom-built flowchart editor
- **Colors:** KPMG branding colors
- **Fonts:** System fonts (Inter preferred)
- **Icons:** Unicode emoji for universal support

---

## FAQ

**Q: Can I use this offline?**  
A: Yes! It's a single HTML file with no external dependencies.

**Q: Where is my data stored?**  
A: Locally in your browser's localStorage. Nothing is sent to servers.

**Q: Can AI agents use this?**  
A: Absolutely! See `AI_AGENT_PROMPT.md` for the complete schema.

**Q: What's the difference between the two auto-layout modes?**  
A: Hierarchical is fast and creates top-down flow. Force-Directed uses physics for natural clustering.

**Q: Can I import multiple flowcharts?**  
A: Yes! Use "Import JSON" with the "append" checkbox unchecked.

**Q: How do I share flowcharts?**  
A: Export as JSON and share the file, or copy-paste the JSON text.

**Q: Can I customize colors?**  
A: Currently uses KPMG colors. Edit the CONFIG object in the HTML to customize.

**Q: Does it work on mobile?**  
A: Basic viewing works, but editing is optimized for desktop with mouse/keyboard.

---

## Version History

### v3.0 (Current) - AI Integration Update
- Added JSON import modal
- Created comprehensive AI_AGENT_PROMPT.md
- Enhanced import with append mode
- Added example_flowchart.json

### v2.0 - Layout & Alignment Update
- Multi-select with Ctrl+Click
- 9 alignment operations
- Force-directed graph layout
- Layout mode toggle

### v1.0 - Initial Release
- 8 block types
- Visual editor
- Connection system
- Export/Import
- Undo/Redo

---

## Support

For issues or questions:
1. Check this README
2. Review relevant .md documentation
3. Check `example_flowchart.json` for structure
4. Inspect browser console for errors

---

## Quick Links

- 📖 [AI Agent Guide](AI_AGENT_PROMPT.md) - Complete schema for generating JSON
- 📖 [Alignment Features](ALIGNMENT_FEATURE.md) - Multi-select and alignment
- 📖 [Layout Algorithms](FORCE_DIRECTED_LAYOUT.md) - Auto-layout details
- 📖 [JSON Import](JSON_IMPORT_FEATURE.md) - Import feature implementation
- 📄 [Example JSON](example_flowchart.json) - Working example

---

## Summary

This flowchart tool bridges visual editing with AI generation. Users can:
1. **Create visually** with drag-and-drop interface
2. **Generate with AI** by pasting JSON from language models
3. **Collaborate** by sharing JSON text or files
4. **Export** for documentation or further processing

Perfect for process documentation, algorithm visualization, business workflows, and AI-assisted flowchart creation!
