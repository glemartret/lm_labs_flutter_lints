# lm_labs_flutter_lints

LM Labs recommended lints for Flutter apps, packages, and plugins to encourage good coding practices.

This package provides a centralized lint configuration that extends `flutter_lints` with custom rules tailored for LM Labs projects. It ensures consistency across all Flutter projects and simplifies maintenance.

## Features

- ✅ Centralized lint configuration for all LM Labs projects
- ✅ Customized rules based on LM Labs coding standards
- ✅ Pre-configured analyzer settings (custom_lint plugin, generated file exclusions)
- ✅ Formatter preferences (trailing commas preservation)
- ✅ Ready-to-use `build.yaml` configuration template

## Installation

Add `lm_labs_flutter_lints` to your `pubspec.yaml`:

```yaml
dev_dependencies:
  lm_labs_flutter_lints: ^1.0.0
```

## Usage

### 1. Configure analysis options

Create or update your `analysis_options.yaml` file at the root of your project:

```yaml
include: package:lm_labs_flutter_lints/flutter.yaml
```

That's it! Your project will now use all the LM Labs lint rules.

### 2. Configure build options (optional)

For projects using code generation (freezed, json_serializable, riverpod_generator, go_router_builder), you can use the provided `build.yaml` template.

**Note:** Unlike `analysis_options.yaml`, `build.yaml` cannot be included directly. You need to copy the template to your project root.

1. Copy `lib/build.yaml` from this package to your project root as `build.yaml`
2. Customize the `generate_for` paths according to your project structure

See the [Build Configuration](#build-configuration) section for details.

## Key Lint Rules

This package enables a comprehensive set of lint rules. Some notable configurations:

### Enabled Rules

- `always_use_package_imports` - Enforces package imports over relative imports
- `prefer_single_quotes` - Consistent string quoting style
- `require_trailing_commas` - Better git diffs and code formatting
- `always_declare_return_types` - Explicit return types for better code clarity
- `avoid_dynamic_calls` - Type safety enforcement
- `use_late_for_private_fields_and_variables` - Modern null safety patterns

### Disabled Rules

Some rules from `flutter_lints` are intentionally disabled based on LM Labs preferences:

- `avoid_print` - Allowed for debugging purposes
- `avoid_unnecessary_containers` - Disabled for flexibility
- `prefer_const_constructors_in_immutables` - Disabled for readability

See `lib/flutter.yaml` for the complete list of enabled/disabled rules.

## Build Configuration

The package includes a `build.yaml` template that configures common code generators used in LM Labs projects:

- **freezed** - Union types and data classes
- **json_serializable** - JSON serialization
- **riverpod_generator** - State management
- **go_router_builder** - Navigation routes
- **lm_labs_generator** - Custom route generators

### Using the build.yaml template

The package includes a `build.yaml` template at `lib/build.yaml` that you can use as a reference for your projects.

**To use it:**

1. Copy the template from `lib/build.yaml` to your project root as `build.yaml`

2. Customize the `generate_for` paths according to your project structure:
   - The template uses `lib/src/features/**/...` patterns (feature-first structure)
   - Adjust paths if your project uses a different structure

3. Add or remove generators based on your needs:
   - **freezed** - Union types and data classes
   - **json_serializable** - JSON serialization
   - **riverpod_generator** - State management
   - **go_router_builder** - Navigation routes
   - **lm_labs_generator|routes** - Custom route generation
   - **drift_dev** - Database code generation (if using Drift)

The template includes recommended configurations:
- `freezed`: `fallback_union: default` option
- `json_serializable`: `explicit_to_json: true` option
- Paths organized by layer (domain, application, data, presentation)

## Analyzer Configuration

The package pre-configures:

- **custom_lint plugin** - For advanced linting capabilities
- **Generated file exclusions** - Automatically excludes `**.freezed.dart` and `**.g.dart` files
- **Error handling** - Configures `invalid_annotation_target` for json_serializable compatibility

## Formatter Settings

- **trailing_commas**: `preserve` - Maintains existing trailing comma style

## Contributing

When proposing changes to lint rules:

1. Update `lib/flutter.yaml` with your changes
2. Test across multiple LM Labs projects
3. Update the CHANGELOG.md
4. Consider the impact on existing codebases

## Versioning

This package follows semantic versioning:

- **Major** - Breaking changes to lint rules (may require code changes in projects)
- **Minor** - New lint rules or non-breaking changes
- **Patch** - Bug fixes or dependency updates

## Related Packages

- [flutter_lints](https://pub.dev/packages/flutter_lints) - Base lint rules
- [custom_lint](https://pub.dev/packages/custom_lint) - Advanced linting capabilities

## License

See [LICENSE](LICENSE) file for details.
