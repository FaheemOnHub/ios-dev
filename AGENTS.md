# Copilot Rules for iOS App Development

These rules will guide GitHub Copilot to generate consistent, production-ready Swift and SwiftUI code for iOS app development.

---

## Project Structure
1. Always follow **MVVM (Model-View-ViewModel)** pattern unless explicitly stated otherwise.
2. Separate concerns: 
   - Views in `/Views`
   - Models in `/Models`
   - ViewModels in `/ViewModels`
   - Utilities/Helpers in `/Utils`

---

## Swift & SwiftUI Conventions
1. Use **Swift best practices**: prefer `struct` over `class` unless reference semantics are required.
2. Conform to **Swift naming guidelines**:
   - Variables & functions: `camelCase`
   - Types (struct, class, enum): `PascalCase`
   - Constants: `camelCase`
3. Use **SwiftUI property wrappers** correctly:
   - `@State` for local view state
   - `@Binding` for passing state between views
   - `@ObservedObject` for external observable objects
   - `@EnvironmentObject` for shared global state

---

## Error Handling
1. Always use **`do-catch` blocks** for throwing functions.
2. Prefer **`Result` type** when returning success/failure from async functions.
3. Never ignore errors — log them.

---

## Networking
1. Use **`URLSession`** or **`async/await`** for API calls.
2. Decode JSON with `Codable` models.
3. Ensure proper error handling for network failures.

---

## App Entitlements & Capabilities
1. Always check **required entitlements** before generating code:
   - `FamilyControls`
   - `ManagedSettings`
   - `DeviceActivity`
   - `NetworkExtension`
2. Do not assume availability; add comments and proper instructions how to add them from xcode or to request entitlements from Apple.

---

## UI/UX Guidelines
1. Respect **Apple’s Human Interface Guidelines (HIG)**.
2. Use `SF Symbols` for icons when possible.
3. Use adaptive layout with **`GeometryReader`** or **`LayoutPriority`** when necessary.

---

## Documentation
1. Every function and type must have a **docstring comment**.
2. Complex logic should include inline comments.
3. Use `///` for Swift documentation comments.

---

## Xcode Project Files (`project.pbxproj` and `Info.plist`)
1. **Never generate raw XML or direct edits for `project.pbxproj` or `Info.plist`.**
2. Instead, always output **step-by-step instructions** for making changes in Xcode’s UI.
3. For `project.pbxproj`:
   - Use Xcode to add targets, frameworks, or libraries OR provide detailed explaination on how to add them using xcode.
   - Do not create or modify UUIDs manually.
4. For `Info.plist`:
   - Suggest which keys to add (e.g. `NSCameraUsageDescription`) and provide the **exact value** to use.
   - Always specify human-readable permission strings (Apple rejects vague ones).
   - Never hardcode bundle identifiers; use `$(PRODUCT_BUNDLE_IDENTIFIER)` instead.

---
