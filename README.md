# Advanced PocketBase MCP Server

[![smithery badge](https://smithery.ai/badge/pocketbase-server)](https://smithery.ai/server/pocketbase-server)

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/bisen/advanced-pocketbase-mcp-server)

A comprehensive MCP server that provides sophisticated tools for interacting with PocketBase databases. This server enables advanced database operations, schema management, and data manipulation through the Model Context Protocol (MCP). **Now with full Cloudflare Workers support and Durable Objects for serverless deployment!**

<a href="https://glama.ai/mcp/servers/z2xjuegxxh"><img width="380" height="200" src="https://glama.ai/mcp/servers/z2xjuegxxh/badge" alt="pocketbase-mcp-server MCP server" /></a>

## Changelog

### v4.0.0 (June 30, 2025) - Cloudflare Workers & Durable Objects Support

#### Added - Serverless Deployment & Production Readiness
- **🚀 Cloudflare Workers Support**: Complete serverless deployment capability
  - `worker.ts`: Main Cloudflare Worker entry point with routing and request handling
  - `durable-object.ts`: Advanced Durable Object implementation for stateful MCP sessions
  - `agent-worker-compatible.ts`: Worker-optimized PocketBase MCP agent
  - Full WebSocket support for real-time MCP connections over Durable Objects
- **🔧 Production Deployment Tools**: Ready-to-deploy configuration
  - `wrangler.toml`: Complete Cloudflare Workers configuration
  - `Dockerfile` and `Dockerfile.test`: Docker support for development and testing
  - `tsconfig.worker.json`: Worker-specific TypeScript configuration
- **🛡️ Super Admin Authentication**: Runtime admin privilege escalation
  - `pocketbase_super_admin_auth` tool: Authenticate as super admin during runtime
  - Enables admin operations (collection creation, schema changes) programmatically
  - Comprehensive security analysis and capability testing
- **📊 Advanced Diagnostics**: Production monitoring and debugging tools
  - `debug_pocketbase_auth`: Authentication and connection testing
  - `check_pocketbase_write_permissions`: Write operation capability analysis
  - `analyze_pocketbase_capabilities`: Complete security model documentation
  - Production vs development environment detection and guidance

#### Enhanced - Serverless Architecture
- **🌐 Multiple Deployment Options**: 
  - Traditional Node.js server (existing)
  - Cloudflare Workers with Durable Objects (new)
  - Docker containerization support (new)
- **⚡ Performance Optimizations**: 
  - Durable Object hibernation for cost efficiency
  - Connection pooling and session management
  - Automatic retry logic with exponential backoff
- **🔐 Enterprise Security**: 
  - Production security mode detection
  - Admin operation restrictions with bypass capability
  - Comprehensive audit logging and session tracking

#### Documentation
- **📖 Complete Deployment Guides**: 
  - `CLOUDFLARE_DEPLOYMENT.md`: Step-by-step Cloudflare deployment
  - `SUPER_ADMIN_AUTH.md`: Super admin authentication usage guide
  - `OPERATION_CAPABILITIES.md`: Production security model explanation
- **🔄 Migration Support**: `CLOUDFLARE_AGENT.md` for transitioning to serverless

#### Technical Improvements
- Full TypeScript compatibility across Node.js and Cloudflare Workers
- Environment variable management for multiple deployment targets
- Comprehensive error handling for network and authentication failures
- Resource cleanup and memory management for long-running sessions

This major release transforms the Advanced PocketBase MCP Server into a production-ready, serverless-capable solution that can be deployed on Cloudflare's global edge network while maintaining full compatibility with traditional deployments.

## Changelog

### v3.0.0 (June 10, 2025)

#### Added - Complete Full-Stack SaaS Backend Integration
- **Email Service Integration**: Complete email functionality with SMTP and SendGrid support
  - 10 comprehensive email MCP tools: create/update/delete templates, send templated/custom emails
  - Email logging and template management system
  - Connection testing and default template setup
- **Enhanced Stripe Service**: Advanced payment processing capabilities
  - 10 additional Stripe MCP tools for complete payment management
  - Payment intent creation, customer management, subscription handling
  - Full webhook processing and product synchronization
- **Full-Stack SaaS Automation**: 5 complete workflow automation tools
  - `register_user_with_automation`: Complete user registration with email and Stripe customer creation
  - `create_subscription_flow`: End-to-end subscription setup with email notifications
  - `process_payment_webhook_with_email`: Webhook processing with automated email notifications
  - `setup_complete_saas_backend`: One-click SaaS backend initialization
  - `cancel_subscription_with_email`: Subscription cancellation with customer notifications
- **Production-Ready Monitoring**: Backend status monitoring and health checks
  - `get_saas_backend_status`: Comprehensive status reporting for production readiness
  - Service health checks, collection validation, template verification
  - Production readiness assessment and recommendations

#### Enhanced Services
- **EmailService**: Added `updateTemplate()` and `testConnection()` methods
- **StripeService**: Added `createPaymentIntent()`, `retrieveCustomer()`, `updateCustomer()`, `cancelSubscription()` methods
- **Advanced Collections**: Automated setup for `stripe_products`, `stripe_customers`, `stripe_subscriptions`, `stripe_payments`, `email_templates`, `email_logs`

#### Fixed
- **TypeScript Syntax Errors**: Resolved all compilation errors in index.ts
- **Import Statements**: Fixed malformed import in email.ts service
- **Tool Registration**: Corrected MCP tool registration syntax and structure

#### Technical Improvements
- Complete type safety across all new services and tools
- Comprehensive error handling for all email and payment operations
- Modular service architecture with proper separation of concerns
- Environment-based configuration for all external services

This release transforms the Advanced PocketBase MCP Server into a complete full-stack SaaS backend solution, providing everything needed for user management, payment processing, email communications, and business automation through the Model Context Protocol.

## Changelog

### v2.3.0 (June 12, 2025)

#### Added - SDK Compatibility & Modernization
- **Complete SDK Compatibility**: Full compatibility with latest PocketBase JavaScript SDK v0.26.1
- **Modern Type Definitions**: Completely rewrote `src/types/pocketbase.d.ts` to match actual SDK API
  - Added correct interfaces for CollectionService, RecordService, FileService, HealthService, RealtimeService
  - Updated AuthStore, AuthData, AuthMethodsList with proper method signatures
  - Removed incompatible features that don't exist in current SDK version
- **Authentication Method Modernization**: Updated all authentication tools to use current SDK patterns
  - Fixed `authenticate_with_otp` to use `requestOTP()` for initiating OTP flow
  - Updated `authenticate_with_oauth2` to use `authWithOAuth2Code()` with proper parameters
  - Corrected method casing from `authWithOtp` to `authWithOTP` to match SDK
  - Fixed all AuthStore references from deprecated `model` property to correct `record` property

#### Fixed - SDK Compatibility Issues
- **Removed Incompatible Features**: Cleaned up tools using non-existent SDK methods
  - Removed `get_collection_scaffolds` tool (used non-existent `collections.getScaffolds()`)
  - Removed `import_collections` tool (used non-existent `collections.import()`)
  - Replaced `createBatch()` API calls with sequential execution in batch operation tools
- **Interface Cleanup**: Removed `ExtendedPocketBase` interface, using standard `PocketBase` type directly
- **Syntax Corrections**: Fixed various syntax errors including missing parentheses and semicolons
- **Build System**: Successfully compiled TypeScript project without errors, server starts properly

#### Enhanced
- **Tool Registration**: All MCP tool registrations now follow correct patterns with modern SDK capabilities
- **Error Handling**: Improved error handling throughout all authentication and data operations
- **Type Safety**: Enhanced TypeScript support with accurate type definitions matching SDK v0.26.1
- **Documentation**: Created comprehensive CHANGELOG.md documenting all changes and breaking changes

#### Technical Improvements
- Verified compatibility with MCP TypeScript SDK v1.12.1
- Ensured all tool implementations use actual PocketBase SDK v0.26.1 methods
- Replaced batch operations with sequential execution to work within SDK limitations
- Improved overall code stability and maintainability

This release ensures the Advanced PocketBase MCP Server is fully compatible with the latest SDK versions and follows modern development patterns.

### v2.2.0 (June 7, 2025)

#### Added
- **SSE Transport Support**: Added Server-Sent Events transport for real-time streaming capabilities
- **Multiple Transport Options**: Now supports stdio, HTTP, and SSE transports
- **Real-time Streaming**: Enhanced `stream_collection_changes` tool with MCP notification system
- **HTTP Server Mode**: New HTTP server with health check endpoint
- **Express Integration**: Added Express.js for HTTP/SSE server functionality
- **Streamable HTTP Protocol**: Support for latest MCP protocol version 2025-03-26
- **Backward Compatibility**: Maintains support for legacy HTTP+SSE protocol 2024-11-05

#### Updated
- **MCP SDK**: Updated to latest version 1.12.1
- **PocketBase SDK**: Updated to latest version 0.26.1
- **TypeScript Support**: Enhanced type definitions and error handling
- **Package Scripts**: Added new npm scripts for different server modes

#### Enhanced
- **Documentation**: Comprehensive README updates with SSE examples
- **Error Handling**: Improved error messages and type safety
- **Development Experience**: Better TypeScript integration and debugging

#### Technical Improvements
- Added Express types for better TypeScript support
- Enhanced session management for SSE connections
- Improved transport lifecycle management
- Better resource cleanup on server shutdown

## Changelog

### v2.1.0 (April 3, 2025)

#### Added
- Added `batch_update_records` tool for updating multiple records at once.
- Added `batch_delete_records` tool for deleting multiple records at once.
- Added `subscribe_to_collection` tool for real-time event subscriptions (requires `eventsource` polyfill).

#### Fixed
- Corrected schema for `authenticate_user` to allow admin authentication via environment variables without explicit email/password.
- Added `eventsource` dependency and polyfill to enable real-time subscriptions in Node.js.

### v2.0.0 (April 2, 2025)

#### Added
- Enhanced admin authentication support with environment variables
- Added support for admin impersonation via the `impersonate_user` tool
- Improved error handling for authentication operations
- Added comprehensive TypeScript type definitions for better development experience
- Added support for Cline integration

#### Fixed
- Fixed TypeScript errors in the PocketBase client implementation
- Improved schema field handling with proper type annotations
- Fixed issues with optional schema field properties

#### Changed
- Updated the authentication flow to support multiple authentication methods
- Improved documentation with more detailed examples
- Enhanced environment variable configuration options

## 🚀 Deployment Options

### Smithery Platform (Managed Hosting) ⭐ **Recommended for Beginners**

Deploy to Smithery's managed platform for hosted MCP servers with zero infrastructure management:

[![Deploy to Smithery](https://smithery.ai/badge/deploy)](https://smithery.ai/server/pocketbase-server)

**Benefits:**
- 🌐 Hosted MCP server with interactive web playground
- 🔧 Zero infrastructure or deployment complexity
- 🔍 Built-in testing and discovery tools
- 📊 Usage analytics and monitoring dashboard
- 🛡️ Automatic security updates and maintenance

**Quick Setup:**
1. Visit [Smithery PocketBase Server](https://smithery.ai/server/pocketbase-server)
2. Click "Deploy" and connect your GitHub account
3. Configure your PocketBase URL and optional admin credentials
4. Start using immediately with the web playground

**Configuration Options:**
- `pocketbaseUrl`: Your PocketBase instance URL (required)
- `adminEmail`: Admin email for elevated operations (optional)
- `adminPassword`: Admin password for elevated operations (optional)
- `debug`: Enable debug logging (optional, default: false)

### Cloudflare Workers (Production Scale)

Deploy to Cloudflare's global edge network with Durable Objects for stateful MCP sessions:

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/bisen/advanced-pocketbase-mcp-server)

**Quick Deploy:**
```bash
# Clone and deploy
git clone https://github.com/bisen/advanced-pocketbase-mcp-server
cd advanced-pocketbase-mcp-server
npm install
npm run build
npx wrangler deploy
```

**Benefits:**
- ⚡ Global edge deployment with sub-100ms latency
- 💰 Pay-per-use pricing (free tier available)
- 🔄 Automatic scaling and load balancing
- 🛡️ Built-in security and DDoS protection
- 📊 Advanced diagnostics and monitoring tools

### Traditional Node.js Server

Standard deployment for development and traditional hosting:

```bash
npm install
npm run build
npm start
```

### Docker Deployment

Containerized deployment for any platform:

```bash
docker build -t pocketbase-mcp-server .
docker run -p 3000:3000 -e POCKETBASE_URL=your_url pocketbase-mcp-server
```

## Features

### Collection Management
- Create and manage collections with custom schemas
- Migrate collection schemas with data preservation
- Advanced index management (create, delete, list)
- Schema validation and type safety
- Retrieve collection schemas and metadata

### Record Operations
- CRUD operations for records
- Advanced querying with filtering, sorting, and aggregation
- Batch import/export capabilities
- Relationship expansion support
- Pagination and cursor-based navigation

### User Management
- User authentication and token management
- User account creation and management
- Password management
- Role-based access control
- Session handling

### Database Operations
- Database backup and restore
- Multiple export formats (JSON/CSV)
- Data migration tools
- Index optimization
- Batch operations

## Available Tools

### Collection Management
- `create_collection`: Create a new collection with custom schema
- `get_collection_schema`: Get schema details for a collection
- `migrate_collection`: Migrate collection schema with data preservation
- `manage_indexes`: Create, delete, or list collection indexes

### Record Operations
- `create_record`: Create a new record in a collection
- `list_records`: List records with optional filters and pagination
- `update_record`: Update an existing record
- `delete_record`: Delete a record
- `query_collection`: Advanced query with filtering, sorting, and aggregation
- `batch_update_records`: Update multiple records in a single call
- `batch_delete_records`: Delete multiple records in a single call
- `subscribe_to_collection`: Subscribe to real-time changes in a collection (requires `eventsource` package in Node.js environment)
- `import_data`: Import data into a collection with create/update/upsert modes

### User Management
- `authenticate_user`: Authenticate a user and get auth token
- `create_user`: Create a new user account
- `list_auth_methods`: List all available authentication methods
- `authenticate_with_oauth2`: Authenticate a user with OAuth2
- `authenticate_with_otp`: Authenticate a user with one-time password
- `auth_refresh`: Refresh authentication token
- `request_verification`: Request email verification
- `confirm_verification`: Confirm email verification with token
- `request_password_reset`: Request password reset
- `confirm_password_reset`: Confirm password reset with token
- `request_email_change`: Request email change
- `confirm_email_change`: Confirm email change with token
- `impersonate_user`: Impersonate another user (admin only)

### Database Operations
- `backup_database`: Create a backup of the PocketBase database with format options
- `import_data`: Import data with various modes (create/update/upsert)

### 🔧 Production Diagnostics & Admin Tools
- `debug_pocketbase_auth`: Test authentication and connection status
- `check_pocketbase_write_permissions`: Analyze write operation capabilities
- `analyze_pocketbase_capabilities`: Document available vs restricted operations
- `pocketbase_super_admin_auth`: **Authenticate as super admin at runtime**
- `get_server_status`: Comprehensive server status and configuration
- `health_check`: Simple health check endpoint

### 🛡️ Super Admin Operations
After using `pocketbase_super_admin_auth`, these admin-level operations become available:
- Collection creation and schema modifications
- User management and authentication settings  
- System configuration changes
- Database administration tasks

> **Note**: Admin operations may be restricted in production environments for security. Use the diagnostic tools to understand your deployment's security model.

## Configuration

### Smithery Platform (Managed Hosting)
Configure through Smithery's web interface when deploying:

**Required:**
- `pocketbaseUrl`: Your PocketBase instance URL

**Optional:**
- `adminEmail`: Admin email for super admin authentication
- `adminPassword`: Admin password for elevated operations
- `debug`: Enable debug logging for troubleshooting

### Node.js Deployment
Required environment variables:
- `POCKETBASE_URL`: URL of your PocketBase instance (e.g., "http://127.0.0.1:8090")

Optional environment variables:
- `POCKETBASE_ADMIN_EMAIL`: Admin email for certain operations
- `POCKETBASE_ADMIN_PASSWORD`: Admin password
- `POCKETBASE_DATA_DIR`: Custom data directory path

### Cloudflare Workers Deployment
Configure in `wrangler.toml` or through Cloudflare dashboard:

```toml
[env.production.vars]
POCKETBASE_URL = "https://your-pocketbase-instance.com"
POCKETBASE_ADMIN_EMAIL = "admin@example.com"

[env.production.secrets]
POCKETBASE_ADMIN_PASSWORD = "your-super-secure-password"
```

**Environment-specific considerations:**
- **Development**: Use local PocketBase instance with full admin access
- **Production**: Use hosted PocketBase with potential admin restrictions
- **Edge**: Cloudflare Workers provide global deployment with Durable Objects

### Production Security & Super Admin Authentication
- Admin credentials enable the `pocketbase_super_admin_auth` tool
- Production environments may restrict admin API access for security
- Use diagnostic tools (`analyze_pocketbase_capabilities`) to understand your deployment
- The super admin tool bypasses production restrictions when credentials are valid

## Usage Examples

### Collection Management
```typescript
// Create a new collection
await mcp.use_tool("pocketbase", "create_collection", {
  name: "posts",
  schema: [
    {
      name: "title",
      type: "text",
      required: true
    },
    {
      name: "content",
      type: "text",
      required: true
    }
  ]
});

// Manage indexes
await mcp.use_tool("pocketbase", "manage_indexes", {
  collection: "posts",
  action: "create",
  index: {
    name: "title_idx",
    fields: ["title"],
    unique: true
  }
});
```

### Advanced Querying
```typescript
// Query with filtering, sorting, and aggregation
await mcp.use_tool("pocketbase", "query_collection", {
  collection: "posts",
  filter: "created >= '2024-01-01'",
  sort: "-created",
  aggregate: {
    totalLikes: "sum(likes)",
    avgRating: "avg(rating)"
  },
  expand: "author,categories"
});
```

### Data Import/Export
```typescript
// Import data with upsert mode
await mcp.use_tool("pocketbase", "import_data", {
  collection: "posts",
  data: [
    {
      title: "First Post",
      content: "Hello World"
    },
    {
      title: "Second Post",
      content: "More content"
    }
  ],
  mode: "upsert"
});

// Backup database
await mcp.use_tool("pocketbase", "backup_database", {
  format: "json" // or "csv"
});
```

### Schema Migration
```typescript
// Migrate collection schema
await mcp.use_tool("pocketbase", "migrate_collection", {
  collection: "posts",
  newSchema: [
    {
      name: "title",
      type: "text",
      required: true
    },
    {
      name: "content",
      type: "text",
      required: true
    },
    {
      name: "tags",
      type: "json",
      required: false
    }
  ],
  dataTransforms: {
    // Optional field transformations during migration
    tags: "JSON.parse(oldTags)"
  }
});
```

### Batch & Real-time Operations
```typescript
// Batch update records
await mcp.use_tool("pocketbase", "batch_update_records", {
  collection: "products",
  records: [
    { id: "record_id_1", data: { price: 19.99 } },
    { id: "record_id_2", data: { status: "published" } }
  ]
});

// Batch delete records
await mcp.use_tool("pocketbase", "batch_delete_records", {
  collection: "products",
  recordIds: ["record_id_3", "record_id_4"]
});

// Subscribe to collection changes (logs events to server console)
// Note: Requires 'eventsource' package installed in the Node.js environment running the server.
await mcp.use_tool("pocketbase", "subscribe_to_collection", {
  collection: "products"
});

// Subscribe to a specific record
await mcp.use_tool("pocketbase", "subscribe_to_collection", {
  collection: "products",
  recordId: "specific_product_id"
});
```

### Authentication Methods
```typescript
// List available authentication methods
await mcp.use_tool("pocketbase", "list_auth_methods", {
  collection: "users"
});

// Authenticate with password
await mcp.use_tool("pocketbase", "authenticate_user", {
  email: "user@example.com",
  password: "securepassword",
  collection: "users"
});

// Authenticate with OAuth2
await mcp.use_tool("pocketbase", "authenticate_with_oauth2", {
  provider: "google",
  code: "auth_code_from_provider",
  codeVerifier: "code_verifier_from_pkce",
  redirectUrl: "https://your-app.com/auth/callback",
  collection: "users"
});

// Request password reset
await mcp.use_tool("pocketbase", "request_password_reset", {
  email: "user@example.com",
  collection: "users"
});

// Confirm password reset
await mcp.use_tool("pocketbase", "confirm_password_reset", {
  token: "verification_token",
  password: "new_password",
  passwordConfirm: "new_password",
  collection: "users"
});

// Refresh authentication token
await mcp.use_tool("pocketbase", "auth_refresh", {
  collection: "users"
});
```

## Error Handling

All tools include comprehensive error handling with detailed error messages. Errors are properly typed and include:
- Invalid request errors
- Authentication errors
- Database operation errors
- Schema validation errors
- Network errors

## Type Safety

The server includes TypeScript definitions for all operations, ensuring type safety when using the tools. Each tool's input schema is strictly typed and validated.

## Best Practices

1. Always use proper error handling with try/catch blocks
2. Validate data before performing operations
3. Use appropriate indexes for better query performance
4. Regularly backup your database
5. Use migrations for schema changes
6. Follow security best practices for user management
7. Monitor and optimize database performance

## Development

### Smithery Platform Development
1. Clone the repository
2. Install dependencies: `npm install`
3. Install Smithery CLI: `npm install -g @smithery/cli` 
4. Start development server: `npm run smithery:dev`
5. Open the auto-generated playground URL to test

### Local Development (Node.js)
1. Clone the repository
2. Install dependencies: `npm install`
3. Copy `.env.example` to `.env` and configure
4. Build: `npm run build`
5. Start your PocketBase instance
6. Run: `npm start`

### Cloudflare Workers Development
1. Clone the repository
2. Install dependencies: `npm install`
3. Configure `wrangler.toml` with your settings
4. Build: `npm run build`
5. Deploy: `npx wrangler deploy`
6. Test with: `npx wrangler tail` for real-time logs

### Testing Super Admin Features
```bash
# Test the super admin authentication tool
node test-super-admin-tool.js

# Run all diagnostic tools to verify setup
# Use your MCP client to call:
# - debug_pocketbase_auth
# - check_pocketbase_write_permissions  
# - analyze_pocketbase_capabilities
# - pocketbase_super_admin_auth
```

### File Structure
```
src/
├── smithery-entry.ts             # Smithery platform entry point
├── worker.ts                     # Cloudflare Worker entry point
├── durable-object.ts             # Durable Object implementation
├── agent-worker-compatible.ts    # Worker-optimized MCP agent
├── main.ts                       # Node.js server entry point
├── index.ts                      # Legacy Node.js entry point
└── services/                     # Email, Stripe services
```

## Installing via Smithery

### Complete Advanced PocketBase Server with 100+ Tools

The Smithery deployment now includes the **complete comprehensive agent** with all advanced features:

### 🎯 All Available Tool Categories (100+ Tools Total):
- **🗃️ PocketBase Collections Management** (30+ tools): Create, manage, and migrate collections with full schema support
- **📊 PocketBase Records CRUD** (20+ tools): Complete record operations with advanced querying and batch processing  
- **🔐 PocketBase Authentication** (15+ tools): User management, OAuth2, OTP, admin operations, and super admin authentication
- **⚡ PocketBase Real-time & WebSocket** (10+ tools): Live data streaming, subscriptions, and real-time updates
- **💳 Stripe Payment Processing** (25+ tools): Complete payment infrastructure with customers, products, subscriptions, and webhooks
- **📧 Email & Communication** (15+ tools): SMTP, SendGrid, template management, and automated email workflows
- **🤖 SaaS Automation Workflows** (10+ tools): End-to-end business process automation
- **🔧 Utility & Diagnostic Tools** (10+ tools): Health checks, monitoring, and troubleshooting

### Option 1: Direct Installation (Recommended)
To install the **complete Advanced PocketBase Server** with **100+ tools** for Claude Desktop automatically via [Smithery](https://smithery.ai/server/pocketbase-server):

```bash
npx -y @smithery/cli install pocketbase-server --client claude
```

### What You Get with Smithery Deployment
- 🗄️ **PocketBase CRUD Operations** (30+ tools) - Complete database management
- 🔐 **Admin & Authentication Tools** (20+ tools) - User management and security  
- ⚡ **Real-time & WebSocket Tools** (10+ tools) - Live data streaming
- 💳 **Stripe Payment Processing** (25+ tools) - Complete payment workflows
- 📧 **Email & Communication Tools** (15+ tools) - Email templates and notifications
- 🛠️ **Utility & Diagnostic Tools** (10+ tools) - System monitoring and debugging
- 📚 **Resources & Prompts** - Enhanced AI interactions with examples

### Option 2: Web Platform Deployment
1. Visit [Smithery PocketBase Server](https://smithery.ai/server/pocketbase-server)
2. Click the "Deploy" button
3. Connect your GitHub account and configure settings
4. Use the web playground to test your server

### Option 3: Development with Smithery CLI
For developers who want to modify the server:

```bash
# Install Smithery CLI
npm install -g @smithery/cli

# Clone and develop
git clone https://github.com/bisen/advanced-pocketbase-mcp-server
cd advanced-pocketbase-mcp-server
npm install

# Start development server with hot reload
npm run smithery:dev

# Build for production
npm run smithery:build
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request
