Agentic Publishing Node
An Open-Source Model Context Protocol (MCP) Server for the Sovereign Author.
The Blank Page is Obsolete
In the traditional publishing industry, 99% of authors use artificial intelligence as a glorified typewriter. They manually copy and paste manuscript paragraphs into web-based chat windows, individually read literary agent MSWLs (Manuscript Wish Lists), and spend countless hours managing administrative friction instead of focusing on the intellectual property itself.
The Agentic Publishing Node fundamentally alters this architecture. By utilizing the Model Context Protocol, this server exposes your manuscript, author dossier, and market positioning as a live API.
It transforms your local hard drive from a static storage unit into an autonomous literary agent.
The Architecture
This Node.js server sits on your local machine (or edge server) and allows AI clients like Claude Desktop to directly read your project files. You provide the raw, structured data in markdown templates; the AI handles the logic, cross-referencing, and execution.
The Tool Suite
Once connected, the gateway exposes the following tools to your AI agent:
•    publish-analyze_mswl: Reads an agent's MSWL, cross-references it against your book-proposal.md, calculates a match score, and extracts a customized hook.
•    publish-generate_query: Dynamically drafts a highly targeted, professional query letter using the hook, your author-dossier.md, and your manuscript premise.
•    publish-export_shunn: Formats designated chapters into strict Shunn Standard (double-spaced, 12pt reference) for immediate export.
•    publish-log_query: Automatically appends a record of the generated pitch (Date, Agent, Agency, Hook) directly to a local query_log.csv file.
Quick Start / Deployment
1. The Boilerplate Setup
Clone the repository and install dependencies:
git clone https://github.com/Maha-Strategies/agentic-publishing-node.git
cd agentic-publishing-node
npm install

2. Populate Your Ecosystem
Navigate to the public/ directory. You will find three blank markdown templates. Fill these out with your specific intellectual property:
•    author-dossier-template.md: Your biography, credentials, platform metrics, and professional history.
•    book-proposal-template.md: The structural breakdown, word count, comps, and core themes of your manuscript.
•    manuscript-sample.md: The raw text of your opening chapters.
Rename these files by removing the -template suffix once populated.
3. Environment Variables
Create a .env file in the root directory and securely add your Google Generative AI key (which powers the background semantic analysis).
GEMINI_API_KEY=your_google_api_key_here

4. Build and Run
npm run build
npm start

Connecting to Claude Desktop
To authorize Claude to access your newly deployed publishing node, add the following configuration to your claude_desktop_config.json file:
{
  "mcpServers": {
    "agentic-publisher": {
      "command": "node",
      "args": [
        "/absolute/path/to/your/agentic-publishing-node/build/index.js"
      ]
    }
  }
}

Restart Claude. You can now prompt the AI with: "I want to pitch [Agent Name]. Here is their MSWL. Run the analysis and draft the query."
The Output
The server will not hallucinate generic filler. Because the AI is actively reading your local markdown files, the resulting pitch will be tightly constrained to your specific structural blueprint and biographical credentials.
Maintainers
This open-source standard was architected by Maha Strategies LLC to facilitate high-leverage intellectual property management and establish decentralized publishing infrastructure.
License: MIT
