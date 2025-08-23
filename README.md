# Go-to-TypeScript Porting Template

A comprehensive template for creating high-quality TypeScript ports of Go packages with 100% API compatibility.

## 🚀 Quick Start

### 1. Use this template

Click "Use this template" on GitHub or clone it:

```bash
git clone https://github.com/SubtleTools/go-ts-template.git my-go-port
cd my-go-port
```

### 2. Initialize for your Go package

Run the initialization script with your target Go package:

```bash
# Install dependencies
bun install

# Initialize template (example with rivo/uniseg)
bun run init https://github.com/rivo/uniseg @subtletools/uniseg-ts

# Or with custom description
bun run init https://github.com/charmbracelet/lipgloss @subtletools/lipgloss-ts "Terminal styling library for TypeScript"
```

### 3. Implement your port

```bash
# Analyze the Go codebase
ls test/reference/

# Implement TypeScript version
# Edit src/index.ts, src/core.ts, etc.

# Test as you go
bun test

# Build when ready
bun run build
```

## 📁 Template Structure

```
├── src/
│   ├── index.ts          # TypeScript-native API (camelCase)
│   ├── go-style.ts       # Go-compatible API (PascalCase)
│   ├── types.ts          # TypeScript type definitions
│   └── ...               # Your implementation files
├── test/
│   ├── basic.test.ts     # Basic functionality tests
│   ├── reference/        # Go reference (auto-cloned)
│   └── ...               # Compatibility tests
├── scripts/
│   └── init.ts           # Template initialization script
├── .github/
│   └── workflows/        # CI/CD workflows
└── README.md             # Generated project README
```

## 🎯 Features

### Dual API Support
The template supports both TypeScript-native and Go-compatible APIs:

```typescript
// TypeScript-native API (recommended)
import { mainFunction } from 'my-package';
const result = mainFunction(input);

// Go-compatible API (for Go developers)
import { MainFunction } from 'my-package/go-style';
const result = MainFunction(input);
```

### Complete Project Setup
- **TypeScript configuration** with strict type checking
- **Bun-powered** build and test system
- **GitHub Actions** for CI/CD and automated publishing
- **Comprehensive documentation** templates
- **Go compatibility testing** framework

### Quality Assurance
- **100% API compatibility** testing framework
- **Cross-platform CI** (Ubuntu, macOS, Windows)  
- **Multiple Node.js versions** (18, 20, 22)
- **Automated publishing** to NPM on release

## 🔧 Development Commands

```bash
# Install dependencies
bun install

# Initialize template
bun run init <go-repo-url> <typescript-package-name>

# Development
bun run dev              # Watch mode
bun test                 # Run tests
bun test --watch         # Test watch mode
bun run build            # Build TypeScript

# Testing Go compatibility
cd test/reference
go run main.go > go-output.txt
cd ../..
bun run my-test.ts > ts-output.txt
diff go-output.txt ts-output.txt  # Should be identical

# Publishing
bun run prepublishOnly   # Build and test before publishing
```

## 📋 Porting Checklist

### Phase 1: Setup
- [ ] Run `bun run init` with your Go package
- [ ] Analyze Go codebase structure in `test/reference/`
- [ ] Plan TypeScript module organization
- [ ] Set up basic type definitions in `src/types.ts`

### Phase 2: Core Implementation
- [ ] Port main algorithms to TypeScript
- [ ] Implement TypeScript-native API in `src/index.ts`
- [ ] Create Go-compatible API in `src/go-style.ts`
- [ ] Add comprehensive error handling

### Phase 3: Testing & Compatibility
- [ ] Create test cases in `test/`
- [ ] Verify outputs match Go implementation exactly
- [ ] Test edge cases and error conditions
- [ ] Add performance benchmarks if needed

### Phase 4: Documentation & Polish
- [ ] Update README.md with usage examples
- [ ] Add comprehensive API documentation
- [ ] Update CHANGELOG.md
- [ ] Ensure all CI checks pass

### Phase 5: Publishing
- [ ] Test package installation locally
- [ ] Create GitHub release
- [ ] Verify automated NPM publishing
- [ ] Announce on relevant communities

## 🧪 Testing Strategy

### Go Compatibility Testing
Create test cases that verify identical behavior:

```typescript
// test/compatibility.test.ts
import { test, expect } from 'bun:test';
import { myFunction } from '../src/index.js';

test('matches Go output for basic case', () => {
  // Expected output from Go implementation
  const expected = 'go-output-here';
  const actual = myFunction('input');
  expect(actual).toBe(expected);
});
```

### Automated Testing
The template includes workflows for:
- **Unit tests** with Bun test runner
- **Go comparison tests** using reference implementation
- **Cross-platform testing** on multiple OS and Node.js versions
- **Performance benchmarking** (optional)

## 🎨 API Design Principles

### 1. Dual API Pattern
```typescript
// TypeScript-native (recommended)
export function graphemeCount(text: string): number;

// Go-compatible (for migration)
export function GraphemeCount(text: string): number;
```

### 2. Type Safety
```typescript
// Strong typing for all public APIs
export interface SegmentOptions {
  locale?: string;
  boundaries?: BoundaryType[];
}

export function segment(text: string, options?: SegmentOptions): Segment[];
```

### 3. Performance
- Use efficient data structures matching Go implementation
- Minimize allocations and copying
- Benchmark against Go version when possible

### 4. Error Handling
```typescript
// Follow TypeScript conventions while maintaining Go compatibility
export function parseInput(input: string): Result<Data, Error>;
```

## 📚 Resources

### Go Analysis
- Understand the Go package's architecture and patterns
- Identify core algorithms and data structures
- Note any Go-specific idioms that need TypeScript equivalents
- Study the test cases for expected behavior

### TypeScript Best Practices
- Use strict TypeScript configuration
- Leverage advanced types for better developer experience
- Follow modern ESM module patterns
- Ensure tree-shaking compatibility

### Compatibility Tools
- Use the Go reference in `test/reference/` for validation
- Create comparison scripts for complex outputs
- Set up automated compatibility testing in CI

## 🤝 Contributing

1. Fork this template repository
2. Create your port using the template
3. Share improvements back to the template
4. Help others with their porting efforts

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🏆 Success Stories

Ports created using this template:
- [`@subtletools/uniseg-ts`](https://github.com/SubtleTools/uniseg-ts) - Unicode text segmentation
- *Add your successful port here!*

## 🙏 Acknowledgments

- **Go Community** - For creating excellent packages to port
- **TypeScript Team** - For the amazing type system and tooling
- **Bun Team** - For the fast runtime and package manager

---

**Ready to port your favorite Go package to TypeScript? Let's go! 🚀**