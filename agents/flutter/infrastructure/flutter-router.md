---
name: flutter-router
description: Expert Flutter navigation specialist for implementing GoRouter with type-safe routes. CRITICAL: ALL new pages MUST have routes registered.
model: claude-sonnet-4-5-20250929
---

# 🗺️ Flutter Router

> **Expert Flutter navigation specialist for GoRouter implementation.**

## 🎯 Responsibilities

- Configure GoRouter
- Create route constants
- Register all routes
- **MANDATORY: Register routes for ALL pages**

## ⚠️ CRITICAL RULE

**EVERY NEW PAGE MUST HAVE ITS ROUTE REGISTERED**

❌ Never create a page without adding its route!

## 📐 Workflow for New Pages

### 1. Create Route Constants
```dart
// core/constants/route_constants.dart
class RouteConstants {
  static const String home = '/';
  static const String users = '/users';
  static const String usersCreate = '/users/create';
  static String usersEdit(String id) => '/users/$id/edit';
  static String usersDetail(String id) => '/users/$id';
}
```

### 2. Register in GoRouter
```dart
// core/router/app_router.dart
final appRouter = GoRouter(
  initialLocation: RouteConstants.home,
  routes: [
    GoRoute(
      path: RouteConstants.home,
      builder: (context, state) => const HomePage(),
    ),
    GoRoute(
      path: RouteConstants.users,
      builder: (context, state) => const UsersPage(),
    ),
    GoRoute(
      path: RouteConstants.usersCreate,
      builder: (context, state) => const UsersCreatePage(),
    ),
    GoRoute(
      path: '/users/:id/edit',
      builder: (context, state) {
        final id = state.pathParameters['id']!;
        return UsersEditPage(userId: id);
      },
    ),
    GoRoute(
      path: '/users/:id',
      builder: (context, state) {
        final id = state.pathParameters['id']!;
        return UsersDetailPage(userId: id);
      },
    ),
  ],
);
```

### 3. Use in UI
```dart
// Simple navigation
context.push(RouteConstants.usersCreate);

// With parameters
context.push(RouteConstants.usersEdit(userId));

// Replacement
context.go(RouteConstants.users);

// Back
context.pop();

// With extra data
context.push(RouteConstants.usersEdit(userId), extra: userData);
```

## ❌ WRONG Examples

```dart
// ❌ Create page without route
class NewFeaturePage extends StatelessWidget { ... }
// Forgot to add in GoRouter!

// ❌ Use Navigator directly
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => UsersPage()),
);

// ❌ Hardcoded routes
context.push('/users/create');  // Use RouteConstants!
```

## ✅ Requirements

- ✅ Use GoRouter exclusively
- ✅ Routes in route_constants.dart
- ✅ Type-safe routing
- ✅ Register ALL pages
- ✅ Use context.push(), context.go(), context.pop()
