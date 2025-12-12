# CCCOLUMNS

A minimalist, password-protected markdown note-taking app with multi-column layout and optional GitHub sync for cloud backup.

## ⚠️ Important Disclaimer

**This is a personal project built for a very specific use case.** The security implementation is minimal and uses client-side authentication only. 

**DO NOT use this app for ANY sensitive, confidential, or personal data.** The password hash is visible in the client-side code, and while SHA-256 hashing provides some protection, this is not suitable for anything requiring real security.

**Use at your own risk** for casual notes, public information, or non-sensitive content only.

## Features

- 📝 **Markdown Support** - Full markdown rendering with live preview
- 🔒 **Password Protected** - SHA-256 encrypted password authentication
- 📊 **Multi-Column Layout** - View multiple notes side by side (1-9 columns)
- ☁️ **GitHub Sync** - Optional cloud backup via GitHub integration
- ✅ **Task Lists** - Interactive checkboxes with keyboard shortcuts
- 💾 **Local Storage** - All data saved in browser localStorage
- 📦 **Backup & Restore** - Download and restore your data as JSON
- 🎨 **Clean Interface** - Distraction-free writing environment
- ⚡ **Keyboard Shortcuts** - Fast navigation and editing

## Live Demo

Try it out: [cccolumns.axel.mx](https://cccolumns.axel.mx)

You can use **local-only mode** (no password required) or set up your own instance.

## Quick Start

### Option 1: Local-Only Mode

1. Visit the app URL
2. Click "or enter in local-only mode"
3. Start taking notes immediately
4. Data is saved only in your browser

**Note:** Local-only mode stores data only in your browser. Clearing browser data will delete your notes.

### Option 2: Install Your Own Instance

Follow the installation instructions below to set up password protection and cloud backup.

## Installation

### Prerequisites

- A web server (local or hosted)
- A GitHub account (optional, for cloud sync)

### Step 1: Clone or Download

```bash
git clone https://github.com/axelvaldez/cccolumns.git
cd cccolumns
```

Or download the repository as a ZIP file.

### Step 2: Set Your Password

1. Go to [SHA-256 Hash Generator](https://emn178.github.io/online-tools/sha256.html)
2. Enter your desired password and copy the hash
3. Open `index.html` and find this line (around line 625):
   ```javascript
   const PASSWORD_HASH = '47bf9eec014b3707612577ed1c2cb2e860937c78080abd8240c71a5ddedcd1e2';
   ```
4. Replace the hash with your generated hash

**Default password:** `test123` (hash shown above)

### Step 3: Deploy

Choose one of the following deployment methods:

#### Local Server (Python)

```bash
# Python 3
python3 -m http.server 8000

# Access at http://localhost:8000
```

#### Local Server (Node.js)

```bash
npm install -g http-server
http-server -p 8000

# Access at http://localhost:8000
```

#### GitHub Pages

1. Push to your GitHub repository
2. Go to repository Settings > Pages
3. Select branch and folder
4. Access at `https://yourusername.github.io/cccolumns`

#### Netlify

1. Drop the `index.html` file on [Netlify Drop](https://app.netlify.com/drop)
2. Or connect your GitHub repository for continuous deployment

#### Vercel

```bash
npm i -g vercel
vercel
```

## Configuration

### GitHub Sync Setup (Optional)

Enable automatic cloud backup by configuring GitHub sync:

1. **Create a Private GitHub Repository**
   - Go to GitHub and create a new private repository
   - Name it something like `cccolumns-data`

2. **Generate a Personal Access Token**
   - Visit [GitHub Tokens](https://github.com/settings/tokens)
   - Click "Generate new token (classic)"
   - Give it a name (e.g., "CCCOLUMNS Sync")
   - Select scope: `repo` (Full control of private repositories)
   - Click "Generate token" and copy it

3. **Configure in App**
   - Open Settings (Ctrl+,)
   - Go to "GitHub Sync" tab
   - Enter your Personal Access Token
   - Enter repository in format: `username/repository-name`
   - Click "Sync Now" to test

Your data will now automatically sync to GitHub whenever you make changes!

## Usage

### Basic Operations

**Login:**
- Enter your password to access the app
- Or use "local-only mode" for quick access without authentication

**Edit Mode:**
- Press `Ctrl+E` to toggle edit mode
- Click column titles to rename them
- Press `Esc` to save and exit edit mode

**Navigation:**
- Press number keys `1-9` to show that many columns
- Scroll horizontally to see more columns
- Click column titles to edit them

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+E` | Toggle edit mode |
| `Ctrl+,` | Open settings |
| `Esc` | Save and close edit mode/settings |
| `1-9` | Show 1-9 columns |

### Markdown Features

CCCOLUMNS supports full markdown syntax:

```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*

- Bullet list
- Another item

1. Numbered list
2. Another item

+ [ ] Unchecked task
+ [x] Checked task

> Blockquote

`inline code`

\`\`\`
code block
\`\`\`

[Links](https://example.com)

![Images](image-url.jpg)
```

### Task Lists

Interactive checkboxes with smart formatting:

- Use `+ text` or `- [ ] text` for unchecked tasks
- Use `x text` or `- [x] text` for checked tasks
- Click checkboxes in view mode to toggle
- Press Enter while editing to continue the list
- Press Enter on an empty task to exit the list

### Managing Columns

**Add Column:**
1. Open Settings (Ctrl+,)
2. Go to "Columns" tab
3. Click "+ Add Column"

**Remove Column:**
1. Open Settings
2. Find the column in the list
3. Click "Remove"

**Reorder Columns:**
1. Open Settings
2. Drag and drop columns using the ⋮⋮ handle

**Change Visible Columns:**
- Use number keys `1-9` while viewing
- Or adjust in Settings > Visible Columns

### Backup & Restore

**Download Backup:**
1. Open Settings (Ctrl+,)
2. Go to "Backup & Restore" tab
3. Click "Download Backup"
4. Save the JSON file securely

**Restore from Backup:**
1. Open Settings
2. Go to "Backup & Restore" tab
3. Click "Choose File to Restore"
4. Select your backup JSON file
5. Confirm the restoration

**Important:** Restoring will replace all current data!

## Data Storage

### Where is my data stored?

- **Local Storage:** All data is stored in your browser's localStorage
- **GitHub Sync:** Optionally synced to your private GitHub repository
- **Backups:** Manual JSON downloads for safekeeping

### Data Privacy

- Your password never leaves your browser (only the hash is stored)
- All data is stored locally in your browser
- GitHub sync is optional and uses your private repository
- No third-party services have access to your data

### Data Persistence

- Data persists across browser sessions
- Clearing browser data will delete local storage
- Use backups or GitHub sync to prevent data loss
- Private/incognito mode data is cleared when browser closes

## Troubleshooting

### I forgot my password

1. Generate a new password hash
2. Edit the `PASSWORD_HASH` in `index.html`
3. Re-deploy or refresh your local server

Your data in localStorage remains intact.

### GitHub sync isn't working

- Check your Personal Access Token has `repo` scope
- Verify repository format: `username/repository-name`
- Ensure the repository exists and is accessible
- Check browser console for error messages

### My data disappeared

- Check if you're in the correct browser/profile
- Look for backup files in your downloads
- Check your GitHub repository if sync was enabled
- Data may be cleared if using private/incognito mode

### Columns not showing

- Press number keys to adjust visible columns
- Check Settings > Visible Columns setting
- Ensure columns exist in Settings > Manage Columns

## Development

### File Structure

```
cccolumns/
├── index.html          # Main application file (single-file app)
└── README.md          # This file
```

### Technologies Used

- Pure HTML/CSS/JavaScript (no build step required)
- [marked.js](https://marked.js.org/) for markdown rendering
- localStorage for data persistence
- GitHub API for cloud sync

### Customization

The app is contained in a single `index.html` file. You can customize:

- Colors and styling (CSS section)
- Password hash (JavaScript section)
- Default columns (CatchAllApp.init method)
- Keyboard shortcuts (setupEventListeners method)

## Security Considerations

- Password is hashed with SHA-256 (client-side only)
- Store your password hash securely
- Use strong, unique passwords
- Keep GitHub tokens private
- Use private repositories for sensitive data
- Regular backups recommended

## Browser Compatibility

Tested and working on:
- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Opera (latest)

Requires modern browser with:
- localStorage support
- ES6+ JavaScript
- CSS Grid/Flexbox

## Contributing

Contributions are welcome! Feel free to:

- Report bugs
- Suggest features
- Submit pull requests
- Improve documentation

## License

MIT License - Feel free to use, modify, and distribute.

## Credits

Created as a simple, self-contained note-taking solution for personal use.

## Support

For issues, questions, or feature requests, please open an issue on GitHub:
https://github.com/axelvaldez/cccolumns/issues

---

**Remember:** Always keep backups of important data! 💾
