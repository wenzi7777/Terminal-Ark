# Terminal Ark Changelog

## APP BUNDLE VERSION v0.3.2 Public Beta
## SERVER BUNDLE VERSION v0.3.2 Public Beta

## Release Date: Jan. 15th 2026 00:10 JST

### Bug Fixes
- Fixed missing import in `adminUtils.ts` that prevented TypeScript compilation.

### New Features
- **Admin Panel App**: Added new admin management interface accessible only to users with `admin` role, available in the app launcher.
- **Create Redeem Codes**: Admins can now generate redemption codes with customizable item rewards, currency amounts, usage limits, and expiration dates.
- **Error Reports Management**: Admins can view, filter, and resolve user-submitted error feedback reports with pagination support.
- **User Reports Management**: Admins can view, filter, and resolve player-reported user violations with status tracking (pending/resolved/dismissed).
- **User Role System**: Introduced role-based access control with `admin`, `chat_mod`, and `user` roles stored in the database.
- **User Reports Table**: Created dedicated `user_reports` table to store error feedback and user reports separately from private messages.


### Improvements
- **Error Feedback Submission**: Redesigned error feedback component to use dedicated `submit-report` API instead of private messaging system.
- **User Reporting System**: Updated user report submission to use the new `submit-report` API with proper report type categorization.
- **API Consolidation**: Consolidated multiple Supabase Edge Functions into two main functions (`private-message-action` and `admin-action`) to optimize free tier quota usage.
- **Admin Visibility Control**: Admin panel app is automatically hidden from non-admin users through client-side filtering.
- **Multilingual Support**: Added comprehensive translations for admin panel features across English, Traditional Chinese, Simplified Chinese, and Japanese.

### Others
- Included various minor fixes and performance optimizations.

***This is a hotfix update and will be installed automatically. You will receive a notification prompting you to refresh the page after the hotfix is installed.***