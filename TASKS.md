# Reel Development Tasks

## Phase 1: Plex Authentication & Basic Browsing

### 🔐 Authentication Foundation
- [x] **Implement Plex OAuth authentication flow**
  - [x] Create Plex auth module with PIN-based authentication
  - [x] Implement auth token exchange with Plex.tv API
  - [x] Store auth token to disk (temporary solution)
  - [ ] Store auth token securely in system keyring
  - [ ] Handle token refresh and expiration
  - [x] Create auth status UI indicators

- [x] **Server Discovery & Connection**
  - [x] Implement Plex server discovery via API
  - [x] Parallel connection testing for best server
  - [x] Test server connectivity with latency measurement
  - [x] Store server URL and connection details
  - [x] Handle connection errors gracefully
  - [ ] Create server selection dialog (for multiple servers)

### 📚 Library Browsing
- [x] **Fetch and Display Libraries**
  - [x] Implement `/library/sections` API call
  - [x] Parse library metadata (movies, shows, music)
  - [x] Update home page with actual library counts
  - [x] Create library type icons and badges
  - [x] Cache library data locally

- [x] **Movies Library Implementation**
  - [x] Fetch movies from library endpoint
  - [x] Parse movie metadata (title, year, rating, poster)
  - [x] Create movie grid view component
  - [x] Implement lazy loading for large libraries
  - [ ] Add movie detail view

- [x] **TV Shows Library Implementation**
  - [x] Fetch shows from library endpoint
  - [x] Parse show/season/episode structure
  - [x] Create show grid view component
  - [x] Implement season/episode navigation with modern dropdown selector
  - [x] Add episode carousel view with thumbnails and watch indicators

### 🖼️ Media & Metadata
- [x] **Image Loading & Caching** (Partially Working - Performance Issues)
  - [x] Implement poster/thumb URL construction
  - [x] Create async image download service with throttling
  - [x] Implement disk-based image cache (~/.cache/reel/images/)
  - [x] Add placeholder images for unloaded content
  - [x] Handle image loading errors with fallback
  - [x] Viewport-based lazy loading for performance
  - [x] Concurrent download limiting (increased to 50 simultaneous)
  - [x] Memory cache for instant access
  - [x] Pre-fetch 2 screens ahead for smoother scrolling
  - [x] Reduced debounce delay to 50ms
  - [ ] **Performance still needs improvement** - images load too slowly

- [ ] **Metadata Display**
  - [ ] Create media info cards
  - [ ] Display ratings, duration, genre
  - [ ] Show cast and crew information
  - [ ] Implement synopsis/overview display
  - [ ] Add media badges (4K, HDR, etc.)

### 🔄 Sync & Cache System
- [x] **SQLite Database Setup**
  - [x] Create database schema migrations
  - [x] Implement cache manager
  - [x] Create CRUD operations for media
  - [ ] Add indexes for performance
  - [ ] Implement cache expiration logic

- [x] **Background Sync Service**
  - [x] Create sync manager structure
  - [x] Implement incremental sync
  - [x] Add sync status indicators
  - [ ] Handle sync conflicts
  - [ ] Create sync scheduling system

### 🎨 UI Improvements
- [x] **Blueprint UI Setup**
  - [x] Migrate to GNOME Blueprint for UI definitions
  - [x] Create reusable Blueprint components
  - [x] Set up resource compilation in build.rs
  
- [ ] **Navigation & Routing**
  - [ ] Fix navigation between pages
  - [ ] Implement back button handling
  - [ ] Add breadcrumb navigation
  - [ ] Create loading states
  - [ ] Add error state displays

- [x] **Server Connection UI**
  - [x] Create connection dialog with Blueprint
  - [x] Add server status indicators
  - [x] Show connected user and server status
  - [x] Display server name with connection type (Local/Remote/Relay)
  - [x] Add connection type icons (wired/wireless/cellular)
  - [x] Hide welcome screen when connected
  - [ ] Implement connection retry UI
  - [x] Show sync progress
  - [ ] Add offline mode banner

### 🎬 Basic Playback
- [x] **Stream URL Generation**
  - [x] Construct direct play URLs
  - [ ] Handle transcoding decisions
  - [ ] Implement quality selection
  - [ ] Add subtitle/audio track selection
  - [ ] Create playback decision engine

- [x] **Player Integration** (Completed!)
  - [x] Initialize GStreamer player
  - [x] Load and play video streams
  - [x] Implement basic controls (play/pause/seek)
  - [x] Add immersive playback mode with auto-hiding controls
  - [x] Handle playback errors with user-friendly dialogs
  - [x] Fix seek loop issue in progress bar
  - [x] Implement hover-based UI controls (header and player controls)
  - [x] Add window resizing to match video aspect ratio
  - [x] Create overlay header bar that doesn't affect video layout
  - [ ] Add fullscreen support (partial - button exists but needs implementation)

### 📺 Watched/Unwatched Tracking (COMPLETED!)
- [x] **Data Model & Storage**
  - [x] Add watched status fields to Movie, Show, and Episode models
  - [x] Include view count and last watched timestamp
  - [x] Add playback position for resume functionality
  - [x] Update database schema with watch status fields

- [x] **Backend Integration**
  - [x] Add watch status methods to MediaBackend trait
  - [x] Implement Plex API calls for mark watched/unwatched
  - [x] Parse watch status from Plex API responses
  - [x] Add placeholder implementations for Jellyfin and Local backends

- [x] **UI Indicators** (Enhanced!)
  - [x] Add watched checkmark overlay to MediaCard
  - [x] Show progress bar for partially watched content
  - [x] Calculate and display watch progress percentage
  - [x] Automatic UI updates based on watch status
  - [x] **NEW: Enhanced unwatched indicator** - Glowing blue dot for unwatched content
  - [x] **NEW: Reversed logic** - Show indicators for unwatched items instead of watched
  - [x] **NEW: CPU-optimized design** - Static glow effect without animations

- [x] **Automatic Tracking**
  - [x] Monitor playback completion in player
  - [x] Auto-mark as watched when >90% viewed
  - [x] Sync watch status back to Plex server
  - [x] Handle playback interruption gracefully

- [ ] **Manual Controls** (Future Enhancement)
  - [ ] Add context menu to toggle watched status
  - [ ] Implement mark all as watched/unwatched
  - [ ] Add bulk selection for multiple items

## Phase 2: Enhanced Features (Future)

### 🏠 Homepage Implementation (COMPLETED!)
- [x] **Homepage Sections**
  - [x] Create HomePage UI component with scrollable sections
  - [x] Add "Home" navigation item in sidebar
  - [x] Implement Continue Watching section (On Deck)
  - [x] Implement Recently Added section
  - [x] Add trigger_load for poster images on homepage
  - [x] Fix layout to expand vertically
  - [x] Add library-specific hub sections (Popular, Top Rated, etc.)
  - [x] **Make homepage items clickable** - navigates to player/show details like in library view
  - [x] **Separate Home from Libraries** - Home now in its own section in sidebar
  - [ ] Implement "View All" navigation for sections

### 📊 Advanced Features
- [x] Continue Watching functionality (via homepage)
- [x] Recently Added section (via homepage)
- [ ] Search implementation
- [x] **Filters and Sorting Infrastructure** (COMPLETED!)
  - [x] Generic FilterManager for extensible filtering
  - [x] Watch status filters (All, Watched, Unwatched, In Progress)
  - [x] Sort options (Title, Year, Rating, Date Added)
  - [x] Filter controls in header bar for cleaner UI
  - [x] Filters only show on library views, not homepage
  - [ ] Genre filter implementation
  - [ ] Year range filter
  - [ ] Rating filter
  - [ ] Resolution filter
  - [ ] Advanced filter popover/dialog
- [x] **Library Visibility Management** (NEW!)
  - [x] Edit mode for showing/hiding libraries
  - [x] Checkbox selection in edit mode
  - [x] Persistent storage of visibility preferences in config
  - [x] Edit button in libraries header
  - [x] Integrated with existing Config system
- [ ] Collections support
- [ ] Playlists
- [ ] Watchlist/Up Next

### 🌐 Additional Backends
- [ ] Jellyfin integration
- [ ] Local file support
- [ ] Metadata provider integration

### 💾 Offline Support
- [ ] Download queue manager
- [ ] Offline playback
- [ ] Smart storage management
- [ ] Network-aware sync

## ✅ COMPLETED - Architecture Refactoring

### **Backend-Agnostic Architecture** (COMPLETED)
Successfully refactored the entire codebase to remove all backend-specific hard-coding. The UI layer is now completely agnostic and works with any backend type.

**Completed Fixes:**
- [x] Removed all "plex" string literals from UI code
- [x] Removed hard-coded movie/TV show assumptions from UI
- [x] Made cache manager backend-agnostic (uses dynamic backend IDs)
- [x] Store libraries in AppState with backend ID association
- [x] Made sync manager work with any backend generically
- [x] Updated all UI components to work with generic library data
- [x] Removed hard-coded library type filtering in sync
- [x] Store and load last active backend ID persistently
- [x] Support multiple backends of same type with unique IDs

**Completed Refactoring Tasks:**
1. [x] **AppState Refactoring**
   - [x] Added `libraries: HashMap<String, Vec<Library>>` to AppState
   - [x] Added `library_items: HashMap<String, Vec<MediaItem>>` for cached items
   - [x] Added methods to get libraries for active backend
   - [x] Added methods to get items for a specific library
   - [x] Added method to get active backend ID

2. [x] **Cache Manager Refactoring**
   - [x] Uses backend IDs dynamically instead of hard-coded "plex"
   - [x] Created generic cache keys: `{backend_id}:{type}:{id}`
   - [x] Supports multiple backends in same cache

3. [x] **Sync Manager Refactoring**
   - [x] Removed all hard-coded "plex" references
   - [x] Uses active backend from AppState
   - [x] Supports syncing any library type (Movies, Shows, Music, Photos)
   - [x] Generic `sync_library_items` method for all media types

4. [x] **UI Components Refactoring**
   - [x] Library list is completely generic
   - [x] Displays ALL library types from backend
   - [x] Uses library type from backend data, not hard-coded
   - [x] Removed PlexBackend downcasting - uses generic backend info

5. [x] **Backend Info System**
   - [x] Added `BackendInfo` struct with server details
   - [x] Added `get_backend_info()` to MediaBackend trait
   - [x] UI uses generic backend info instead of type-specific methods

6. [x] **Persistent Backend Management**
   - [x] Added RuntimeConfig to store last active backend
   - [x] Automatically loads last used backend on startup
   - [x] Generates unique backend IDs (plex, plex_1, plex_2, etc.)

7. [x] **Instant Cache Loading**
   - [x] Cache loads immediately on app startup
   - [x] Welcome UI hidden as soon as cached data is available
   - [x] Authentication happens in background without blocking UI

### **Architecture Principles to Enforce:**
1. **Backend Agnostic UI**: The UI layer should NEVER import or reference specific backend implementations
2. **Generic Data Flow**: UI → AppState → BackendManager → Active Backend
3. **Dynamic Backend Selection**: Support multiple backends simultaneously with runtime switching
4. **Universal Caching**: Cache should work identically for all backends
5. **Type Safety**: Use the MediaBackend trait exclusively in UI/services

### **Example of Correct Architecture:**
```
// BAD - UI knows about Plex
window.sync_and_update_libraries("plex", backend)

// GOOD - UI uses active backend
let backend_id = state.backend_manager.get_active_id();
window.sync_and_update_libraries(backend_id, backend)
```

## Current Priority Tasks

### ✅ Completed
1. [x] **Blueprint UI Implementation**
   - [x] Set up GNOME Blueprint for UI development
   - [x] Create Blueprint templates for main window
   - [x] Create auth dialog with Blueprint
   - [x] Fix Blueprint syntax errors (semicolons, signal handlers)
   - [x] Fix UI layout issues (vertical expansion, selectable PIN)
   - [x] Successfully compile and run with Blueprint UI

2. [x] **Plex Authentication**
   - [x] Implement PIN-based authentication flow
   - [x] Generate 4-character PIN codes
   - [x] Poll for auth token
   - [x] Save token to disk
   - [x] Update UI to show auth status
   - [x] Auto-load saved credentials on startup

3. [x] **Server Discovery**
   - [x] Implement Plex server discovery API
   - [x] Parse server responses correctly
   - [x] Test all connections in parallel
   - [x] Select fastest responding server
   - [x] Handle connection failures gracefully
   - [x] Store server connection info (name, local/relay status)
   - [x] Display server details in UI status bar

4. [x] **Library Sync & Display**
   - [x] Implement Plex API for fetching libraries
   - [x] Create sync manager for background updates
   - [x] Cache libraries and media in SQLite
   - [x] Update UI with real library counts
   - [x] Show sync progress spinner
   - [x] Auto-sync on authentication

### ✅ Recently Completed
1. [x] **Library Navigation**
   - [x] Navigate to library views when clicked
   - [x] Create media grid view component (generic for all types)
   - [x] Implement movie and TV show views
   - [x] Fix AdwApplicationWindow navigation issues
   - [x] Create MediaCard widget for grid display
   - [x] Add back navigation from library view

2. [x] **Backend Management System**
   - [x] Create preferences window with AdwPreferencesWindow
   - [x] Implement backend list view with add/remove functionality
   - [x] Add backend removal with confirmation dialog
   - [x] Fix backend ID generation to reuse existing IDs
   - [x] Add clear cache functionality for removed backends
   - [x] Create add backend flow with type selection
   - [x] Integrate with existing auth dialog for Plex

3. [x] **Watched/Unwatched Tracking** (ENHANCED!)
   - [x] Added watched status fields to all media models
   - [x] Implemented Plex API integration for watch status
   - [x] Created visual indicators (checkmark and progress bar)
   - [x] Auto-mark items as watched on playback completion
   - [x] Upgraded to Rust edition 2024 for latest language features
   - [x] **Enhanced unwatched indicator** - Prominent glowing blue dot for unwatched content
   - [x] **Improved UX** - Reversed indicator logic to highlight new/unwatched content
   - [x] **Performance optimized** - Removed animations to reduce CPU usage

### 📋 Next Steps

1. [x] **Image Loading & Display** (COMPLETED)
   - [x] Implement poster/thumb URL construction for Plex
   - [x] Create async image download service
   - [x] Add disk-based image cache
   - [x] Load and display poster images in MediaCard
   - [x] Add loading spinner while images load
   - [x] Handle image loading errors gracefully
   - [x] Viewport-based lazy loading to prevent UI freezing
   - [x] Concurrent download throttling

2. [x] **Media Detail Views** (Partially Complete)
   - [x] Create media detail page layout
   - [ ] Implement movie detail view with full metadata
   - [x] **TV Show Detail View** (COMPLETED!)
     - [x] Modern layout with poster and show info
     - [x] Season dropdown selector for easy navigation
     - [x] Horizontal episode carousel with thumbnails
     - [x] Episode cards with titles, duration, and episode numbers
     - [x] Watch status indicators on episodes
     - [x] Progress bars for partially watched episodes
     - [x] Click to play functionality for episodes
     - [x] Genre tags display
     - [x] Rating display with star icon
   - [x] Display synopsis for shows
   - [ ] Display cast and crew information
   - [x] Add play button functionality (for episodes)

3. [ ] **Library Enhancements**
   - [x] Implement lazy loading for large libraries
   - [ ] Add search within library
   - [ ] Implement sorting options (title, year, rating)
   - [ ] Add filter by genre, year, etc.
   - [ ] Create list/grid view toggle

4. [ ] **Performance Optimizations** (High Priority)
   - [ ] Request smaller thumbnail sizes from Plex API (150x225 instead of full posters)
   - [ ] Implement progressive image loading (low-res placeholder → full image)
   - [ ] Use WebP format if Plex supports it for smaller file sizes
   - [ ] Pre-cache next library's images when idle
   - [ ] Consider using native GTK async image loading APIs
   - [ ] Investigate GdkPixbuf loader performance
   - [ ] Profile actual bottlenecks (network vs decoding vs rendering)

5. [x] **Playback Foundation** (COMPLETED!)
   - [x] Initialize GStreamer player component
   - [x] Generate stream URLs from Plex
   - [x] Implement basic video playback
   - [x] Add playback controls overlay
   - [ ] Track playback progress (partially done - position tracking works, needs to save to server)

## Testing Checklist
- [ ] Test with local Plex server
- [ ] Test with remote Plex server
- [ ] Test with Plex Cloud
- [ ] Test offline scenarios
- [ ] Test large libraries (1000+ items)
- [ ] Test various media formats
- [ ] Test on different screen sizes

## Known Issues & Troubleshooting

### Current Issues
- [ ] **Music/Photo Libraries**: Views not yet implemented
- [ ] **Jellyfin Backend**: Integration pending implementation
- [ ] **Local Files Backend**: File browser not yet implemented
- [ ] **Image Loading Performance**: Still slow despite optimizations - needs further work
  - Loading takes 100-500ms per image even with parallel downloads
  - UI still feels sluggish when scrolling through large libraries
  - May need to implement thumbnail generation or smaller image variants
  - Consider pre-caching images in background after library load
- [ ] **Minor Player UI Issues**: 
  - Occasional duplicate back button in player overlay (mostly fixed)
  - Fullscreen button exists but not fully implemented

### Resolved Issues
- ✅ **GTK Template Loading Error**: Fixed by correcting Blueprint syntax
- ✅ **Plex PIN Authentication**: Fixed by removing "strong" parameter
- ✅ **Server Discovery Parsing**: Fixed by handling array response format
- ✅ **Connection Selection**: Implemented parallel testing for best server
- ✅ **UI Server Status Display**: Fixed RwLock deadlock and added server info display with connection type icons
- ✅ **Backend-Specific Hard-coding**: Completely refactored to backend-agnostic architecture
- ✅ **Slow Startup**: Cache now loads instantly before authentication
- ✅ **Backend ID Management**: Fixed to reuse existing IDs instead of creating new ones
- ✅ **AdwApplicationWindow Navigation**: Fixed set_child error by using set_content
- ✅ **RefCell Borrow Panic**: Fixed multiple borrow issue in library navigation
- ✅ **Widget Parent Issues**: Resolved GTK widget parent conflicts when switching views
- ✅ **Poster Images Not Loading**: Implemented async image loader with disk/memory caching
- ✅ **UI Freezing with Large Libraries**: Added viewport-based lazy loading with throttling
- ✅ **Source ID Removal Panic**: Fixed with counter-based debouncing approach
- ✅ **GStreamer Playback Issues**: Fixed missing typefind element, playbin creation, and video sink setup
- ✅ **Player Navigation**: Fixed page not changing when clicking movies
- ✅ **Seek Loop Bug**: Fixed infinite seeking caused by progress bar updates
- ✅ **Immersive Player Mode**: Implemented auto-hiding controls with overlay header bar
- ✅ **Window Aspect Ratio**: Window now resizes to match video aspect ratio
- ✅ **Player Controls Layout**: Header bar now overlays video instead of pushing it down
- ✅ **Homepage Navigation Fixed**: Homepage items now properly navigate to player/show details when clicked
- ✅ **Show Seasons Count**: Fixed "0 seasons" display by using episode count or "TV Series" fallback when season data isn't loaded
- ✅ **Show Details Page Enhanced**: Completely redesigned with modern dropdown season selector and horizontal episode carousel
- ✅ **Episode Thumbnails**: Added episode thumbnail support with play icon fallbacks
- ✅ **Enhanced Episode Cards**: Cards show episode number, duration, watch status, and progress indicators

## Documentation
- [ ] API documentation
- [ ] User guide
- [ ] Developer setup guide
- [ ] Contributing guidelines
- [ ] Blueprint UI development guide