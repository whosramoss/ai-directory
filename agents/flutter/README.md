# Flutter AI Agents

> Specialized AI agents for Flutter/Dart development with Clean Architecture, organized by Clean Architecture layers.

## 📁 Agent Organization

All agents are organized following Clean Architecture layers for easy discovery and use:

```
flutter-ai-agent/
├── architecture/       # High-level design and planning
├── data/              # Data layer implementation
├── domain/            # Business logic and entities
├── presentation/      # UI and state management
├── infrastructure/    # Cross-cutting concerns
└── quality/          # Testing and quality assurance
```

---

## 🏗️ Architecture Agents

Agents focused on high-level design, planning, and architectural decisions.

### [flutter-architect](architecture/flutter-architect.md)
**Expert Flutter architect** for Clean Architecture implementation, project structure, and architectural decisions.

**Use when:** Starting new projects, reorganizing structure, making architectural decisions

---

### [flutter-feature-planner](architecture/flutter-feature-planner.md)
**Expert Flutter feature planner** for analyzing requirements and planning implementation.

**Use BEFORE implementing ANY feature to:**
- Analyze feature requirements
- **Consult reference projects** (MANDATORY)
- Create implementation plans
- Ensure consistency with existing patterns

**⚠️ CRITICAL**: Always use this agent BEFORE coding!

---

## 📡 Data Layer Agents

### [flutter-data-layer](data/flutter-data-layer.md)
**Expert Flutter data layer specialist** for DataSources, Models, and API integration.

### [flutter-repository](data/flutter-repository.md)
**Expert Flutter repository specialist** for Repository implementations with Either pattern.

---

## 🧬 Domain Layer Agents

### [flutter-domain](domain/flutter-domain.md)
**Expert Flutter domain specialist** for Entities and Repository interfaces.

### [flutter-use-cases](domain/flutter-use-cases.md)
**Expert Flutter UseCase specialist** for business logic with validation.

**⚠️ CRITICAL**: UseCases are the ONLY layer that validates business rules!

---

## 🎨 Presentation Layer Agents

### [flutter-state](presentation/flutter-state.md)
**Expert Flutter state management** for Cubit/Bloc implementation.

**⚠️ CRITICAL**: Cubits must be inside page context!

### [flutter-ui](presentation/flutter-ui.md)
**Expert Flutter UI specialist** for Pages and Widgets.

**⚠️ CRITICAL**: UI ONLY invokes Cubit methods, NEVER UseCases directly!
**⚠️ CRITICAL**: NO empty actions allowed!

### [flutter-design-system](presentation/flutter-design-system.md)
**Expert Flutter design system** for design tokens and theme.

---

## 🔌 Infrastructure Agents

### [flutter-router](infrastructure/flutter-router.md)
**Expert Flutter navigation** for GoRouter implementation.

**⚠️ CRITICAL**: ALL new pages MUST have routes registered!

### [flutter-di](infrastructure/flutter-di.md)
**Expert Flutter dependency injection** for GetIt implementation.

**⚠️ CRITICAL**: ALL new classes MUST be registered in DI!

### [flutter-services](infrastructure/flutter-services.md)
**Expert Flutter services** for external service integration.

---

## ✅ Quality Agents

### [flutter-tester](quality/flutter-tester.md)
**Expert Flutter testing** for comprehensive test coverage.

### [flutter-quality](quality/flutter-quality.md)
**Expert Flutter quality** for code review and best practices.

---

## 🎯 Quick Reference Table

| Task | Agent | Priority |
|------|-------|----------|
| Plan feature | [flutter-feature-planner](architecture/flutter-feature-planner.md) | ⚠️ **FIRST** |
| Design architecture | [flutter-architect](architecture/flutter-architect.md) | High |
| Implement DataSource | [flutter-data-layer](data/flutter-data-layer.md) | Medium |
| Implement Repository | [flutter-repository](data/flutter-repository.md) | Medium |
| Create Entities | [flutter-domain](domain/flutter-domain.md) | High |
| Implement UseCases | [flutter-use-cases](domain/flutter-use-cases.md) | High |
| State management | [flutter-state](presentation/flutter-state.md) | Medium |
| Build UI | [flutter-ui](presentation/flutter-ui.md) | Medium |
| Design system | [flutter-design-system](presentation/flutter-design-system.md) | High |
| Configure routing | [flutter-router](infrastructure/flutter-router.md) | High |
| Configure DI | [flutter-di](infrastructure/flutter-di.md) | High |
| Integrate services | [flutter-services](infrastructure/flutter-services.md) | Medium |
| Write tests | [flutter-tester](quality/flutter-tester.md) | High |
| Code review | [flutter-quality](quality/flutter-quality.md) | High |

---

## 🚀 Implementation Workflow

### Follow this order for EVERY new feature:

```
1. flutter-feature-planner    → Analyze codebase (MANDATORY)
2. flutter-domain             → Entities & Repository Interface
3. flutter-use-cases          → UseCases with validation
4. flutter-data-layer         → DataSource & Models
5. flutter-repository         → Repository Implementation
6. flutter-di                 → Register DataSource, Repository, UseCases
7. flutter-state              → States & Cubit
8. flutter-di                 → Register Cubit
9. flutter-ui                 → Page & Widgets
10. flutter-router            → Register Routes
11. flutter-tester            → Write Tests
12. flutter-quality           → Code Review & Quality Check
```

---

## ⚠️ Critical Rules

### Clean Architecture Flow
```
UI → CUBIT → USE CASE → REPOSITORY → DATA SOURCE
```

### Never Skip Layers!
- ❌ UI calling UseCase directly
- ❌ Cubit calling Repository directly
- ❌ UseCase calling DataSource directly

### Validation ONLY in UseCases
- ✅ UseCases validate ALL business rules
- ❌ UI, Cubit, Repository should NOT validate

### Analyze Existing Codebase
**BEFORE implementing ANY feature**:
- Use Glob to find similar implementations
- Use Grep to search for patterns
- Review existing code structure
- Identify reusable components
- Maintain consistency

### No Empty UI Actions
- ❌ Empty `onPressed`
- ❌ "Em desenvolvimento" messages
- ✅ Every action invokes Cubit

### Register Everything
- ⚠️ ALL pages in GoRouter
- ⚠️ ALL classes in DI
- ⚠️ NO manual instantiation

### Use Design System
- ✅ AppColors, AppSpacing, AppTypography
- ❌ NO hardcoded values

### Zero Tolerance
- ❌ ZERO warnings
- ❌ ZERO errors
- ❌ ZERO useless comments
- ✅ `flutter analyze` = **No issues found!**

---

## 📚 Codebase Analysis

### Finding Existing Patterns
Before implementing new features, analyze your codebase:

**Using Glob tool:**
- `**/*user*.dart` - Find user-related files
- `**/*_cubit.dart` - Find all Cubits
- `**/*_repository.dart` - Find all Repositories

**Using Grep tool:**
- Search for: `class.*Cubit` - Find Cubit patterns
- Search for: `class.*Repository` - Find Repository patterns
- Search for: `class.*UseCase` - Find UseCase patterns

This ensures consistency and reusability!

---

## 💡 Best Practices

### Multi-Agent Approach
1. **Planning**: feature-planner + architect
2. **Implementation**: domain + data + presentation agents
3. **Infrastructure**: di + router + services
4. **Quality**: tester + quality

### Proactive Quality
- During development: Follow quality guidelines
- After implementation: Run quality checks
- Before PR: Write tests

---

## 🔥 Golden Rule

> **"SE FOI CRIADO, TEM QUE FUNCIONAR 100%"**

- No empty actions
- No "Em desenvolvimento"
- No shortcuts
- Always Clean Architecture
- Always analyze existing codebase
- Always register in DI and Router
- Always validate in UseCases
- Always use Design System
- Always write tests
- Always zero linter issues

**Quality is non-negotiable.** ✨

---

## 👤 Author

**Gabriel Rocha**
- Email: gscrweb@gmail.com
- GitHub: [@gabrielscr](https://github.com/gabrielscr)

---

## 📄 License

MIT License - Copyright (c) 2025 Gabriel Rocha

See the [LICENSE](../LICENSE) file for details.

---

**Model**: Claude Sonnet 4.5 (`claude-sonnet-4-5-20250929`)

**Last Updated**: October 2025


