# Modern Swift API Guidelines

**Version:** August 2025  
**Minimum Target:** iOS 18.0, Swift 6.0  
**Preferred Target:** iOS 26 Beta

## Core Principle: Always Use the Newest APIs

When writing Swift/SwiftUI code, **ALWAYS** prefer the newest available APIs. If an API feels verbose or outdated, research modern replacements - they almost always exist.

## API Migration Guide

### ❌ NEVER Use → ✅ ALWAYS Use

#### SwiftUI Navigation
- ❌ `NavigationView` → ✅ `NavigationStack` (iOS 16+)
- ❌ `NavigationLink(destination:)` → ✅ `NavigationLink(value:)` with `.navigationDestination`
- ❌ `.sheet(isPresented:)` → ✅ `.sheet(item:)` when possible
- ❌ Custom back buttons → ✅ `.navigationBarBackButtonHidden()` with `.toolbar`

#### State Management
- ❌ `ObservableObject` + `@Published` → ✅ `@Observable` (iOS 17+)
- ❌ `@StateObject` → ✅ `@State` with `@Observable` (iOS 17+)
- ❌ `@ObservedObject` → ✅ `@Bindable` (iOS 17+)
- ❌ `@EnvironmentObject` → ✅ `@Environment` with `@Observable` (iOS 17+)
- ❌ Combine framework → ✅ Observation framework (iOS 17+)

#### ScrollView
- ❌ `ScrollViewReader` + `scrollTo` → ✅ `.scrollPosition` (iOS 17+)
- ❌ `GeometryReader` for scroll offset → ✅ `.scrollPosition` + `.scrollTargetLayout`
- ❌ Custom scroll indicators → ✅ `.scrollIndicators` modifiers
- ❌ `LazyVGrid` with manual columns → ✅ Consider `Grid` for simpler layouts (iOS 16+)

#### Lists & Forms
- ❌ `.listRowInsets(EdgeInsets())` → ✅ `.listRowSpacing` (iOS 17+)
- ❌ Custom swipe actions → ✅ `.swipeActions` with proper roles
- ❌ Manual search → ✅ `.searchable` with suggestions (iOS 17+)
- ❌ Custom empty states → ✅ `ContentUnavailableView` (iOS 17+)

#### Data & Persistence
- ❌ Core Data → ✅ SwiftData (iOS 17+) for new projects
- ❌ UserDefaults directly → ✅ `@AppStorage` or SwiftData
- ❌ Manual JSON coding → ✅ `Codable` with modern decoders
- ❌ FileManager directly → ✅ SwiftData or structured storage

#### Animations
- ❌ `withAnimation` everywhere → ✅ `.animation` with value parameter
- ❌ `AnimatableModifier` → ✅ `PhaseAnimator` (iOS 17+)
- ❌ Manual spring calculations → ✅ `.spring(duration:bounce:)` (iOS 17+)
- ❌ Timer.publish → ✅ `TimelineView` for time-based updates

#### Concurrency
- ❌ `DispatchQueue` → ✅ `async`/`await`
- ❌ Completion handlers → ✅ `async` functions
- ❌ `@MainActor` class → ✅ `@MainActor` on specific methods
- ❌ Manual task management → ✅ Structured concurrency with `TaskGroup`

#### iOS 26 Beta Features (Use with availability checks)
- ❌ `.blur()` → ✅ `.glassEffect()` for glass materials
- ❌ `Material` backgrounds → ✅ `LiquidGlassMaterial()`
- ❌ Standard navigation bars → ✅ `.navigationBarGlassified()`
- ❌ Basic animations → ✅ `.liquidMotion()` for fluid animations

## Code Example: Modern vs Legacy

### ❌ Legacy Pattern (iOS 15-17 style)
```swift
class ViewModel: ObservableObject {
    @Published var items: [Item] = []
    
    func loadItems() {
        DispatchQueue.global().async {
            // Load items
            DispatchQueue.main.async {
                self.items = loadedItems
            }
        }
    }
}

struct ContentView: View {
    @StateObject private var viewModel = ViewModel()
    
    var body: some View {
        NavigationView {
            List(viewModel.items) { item in
                NavigationLink(destination: DetailView(item: item)) {
                    Text(item.name)
                }
            }
        }
    }
}
```

### ✅ Modern Pattern (iOS 18+ / iOS 26 Beta)
```swift
@Observable
final class ItemManager {
    var items: [Item] = []
    
    func loadItems() async {
        // Using async/await
        items = await fetchItems()
    }
}

struct ContentView: View {
    @State private var manager = ItemManager()
    @State private var path = NavigationPath()
    @State private var scrollPosition: Item.ID?
    
    var body: some View {
        NavigationStack(path: $path) {
            ScrollView {
                LazyVStack {
                    ForEach(manager.items) { item in
                        NavigationLink(value: item) {
                            ItemRow(item: item)
                        }
                        .id(item.id)
                    }
                }
                .scrollTargetLayout()
            }
            .scrollPosition(id: $scrollPosition)
            .navigationDestination(for: Item.self) { item in
                ItemDetailView(item: item)
            }
            .overlay {
                if manager.items.isEmpty {
                    ContentUnavailableView(
                        "No Items",
                        systemImage: "tray",
                        description: Text("Add your first item to get started")
                    )
                }
            }
        }
        .task {
            await manager.loadItems()
        }
        .if #available(iOS 26, *) {
            $0.glassEffect(.systemThin)
        }
    }
}
```

## Research Strategy

When encountering verbose or outdated-feeling code:

1. **Check WWDC sessions** from current and previous year
2. **Search Apple Developer Forums** for modern alternatives
3. **Review iOS release notes** for the current beta
4. **Look for `@available` annotations** in framework headers
5. **Prefer beta features** with proper availability checks over stable but old APIs

## Enforcement Rules

1. **No iOS 15/16/17-only patterns** in new code
2. **Always use @Observable** over ObservableObject
3. **NavigationStack only**, never NavigationView
4. **Async/await required** for all async operations
5. **SwiftData preferred** over Core Data for new projects
6. **ContentUnavailableView required** for empty states
7. **PhaseAnimator preferred** for complex animations
8. **Beta features encouraged** with availability checks

## Version Requirements

- **Minimum**: iOS 18.0, Swift 6.0, Xcode 16.0
- **Recommended**: iOS 26 Beta, Swift 6.2, Xcode 26 Beta
- **Testing**: Always test on latest beta OS versions
- **Deployment**: Use availability checks for beta features

Remember: Most "standard" patterns you see online are from iOS 15-17 era. Always research if a newer, cleaner API exists - it usually does!