# Amatak AI





---

### **Step 3: Add a Dynamic Copyright Year**

1. Update the `app.js` file to include the current year in the copyright message.
```javascript
const express = require('express');
const path = require('path');
const chalk = require('chalk');
const backend = require('./src/backend/server');
const frontend = express.static(path.join(__dirname, 'src/frontend'));

const app = express();

// ASCII Art for "AMATAK AI"
const banner = `
█████╗ ███╗   ███╗ █████╗ ████████╗ █████╗ ██╗  ██╗    █████╗ ██╗
██╔══██╗████╗ ████║██╔══██╗╚══██╔══╝██╔══██╗██║ ██╔╝   ██╔══██╗██║
███████║██╔████╔██║███████║   ██║   ███████║█████╔╝    ███████║██║
██╔══██║██║╚██╔╝██║██╔══██║   ██║   ██╔══██║██╔═██╗    ██╔══██║██║
██║  ██║██║ ╚═╝ ██║██║  ██║   ██║   ██║  ██║██║  ██╗██╗██║  ██║██║
╚═╝  ╚═╝╚═╝     ╚═╝╚═╝  ╚═╝   ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝╚═╝  ╚═╝╚═╝
`;

console.log(chalk.blue(banner));
console.log(chalk.blue('Amatak AI Server is Running...'));

// Serve backend API
app.use('/api', backend);

// Serve frontend static files
app.use(frontend);

// Start the combined app
const PORT = 4000;
const server = app.listen(PORT, () => {
    console.log(`Combined app running on http://localhost:${PORT}`);
    console.log(chalk.gray(`© ${new Date().getFullYear()} Amatak AI. All rights reserved.`));
});

// Export server for CLI
module.exports = server;
