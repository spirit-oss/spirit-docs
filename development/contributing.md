# Contributing to SPIRIT

Welcome to the SPIRIT community! We're excited that you want to contribute to creating an open-source smartphone that prioritizes privacy, repairability, and user control. This guide will help you get started with contributing to any part of the SPIRIT project.

## Code of Conduct

Before contributing, please read and agree to our [Code of Conduct](../community/code-of-conduct.md). We're committed to maintaining a welcoming, inclusive, and harassment-free environment for all contributors.

## Ways to Contribute

There are many ways to contribute to SPIRIT, regardless of your technical background:

### 🔧 Hardware Development
- PCB design improvements
- Component sourcing and optimization
- Mechanical design (case, buttons, etc.)
- Testing and validation
- Manufacturing process optimization

### 💻 Software Development
- AOSP device drivers
- Hardware Abstraction Layer (HAL) development
- Kernel patches and improvements
- Application development
- System optimization

### 📚 Documentation
- Writing and improving documentation
- Creating tutorials and guides
- Translating documentation
- Video documentation and tutorials

### 🧪 Testing & QA
- Hardware testing on prototypes
- Software testing and bug reporting
- User experience testing
- Performance benchmarking

### 🎨 Design & UX
- User interface design
- User experience improvements
- Branding and visual identity
- Marketing materials

### 🌍 Community & Outreach
- Community management
- Social media and communications
- Event organization
- Educational content creation

## Getting Started

### 1. Set Up Your Development Environment

**For Hardware Development:**
- Install [KiCad](https://kicad.org/) (version 7 or later)
- Familiarize yourself with the [Hardware Documentation](../hardware/)
- Join the `#hardware` channel in our [Discord](https://discord.gg/zBG4KdHJWx)

**For Software Development:**
- Set up an AOSP build environment following our [Building Guide](../software/building-aosp.md)
- Read the [Development Setup Guide](development-setup.md)
- Join the `#software` channel in our Discord

**For Documentation:**
- Familiarity with Markdown
- Basic understanding of Git and GitHub
- Join the `#documentation` channel in our Discord

### 2. Find Something to Work On

**Browse Open Issues:**
- Check the issues in the relevant repository:
  - [spirit](https://github.com/V3lectronics/spirit/issues) - Main project issues
  - [spirit-design](https://github.com/V3lectronics/spirit-design/issues) - Hardware issues
  - [spirit-os](https://github.com/V3lectronics/spirit-os/issues) - Software issues
  - [spirit-docs](https://github.com/V3lectronics/spirit-docs/issues) - Documentation issues

**Good First Issues:**
Look for issues labeled with:
- `good first issue` - Perfect for new contributors
- `help wanted` - We need community help
- `documentation` - Documentation improvements needed
- `beginner friendly` - No deep expertise required

**Current Priorities:**
Check our [Project Roadmap](roadmap.md) for current development priorities.

### 3. Claim an Issue

Before starting work:

1. **Comment on the issue** saying you'd like to work on it
2. **Wait for confirmation** from a maintainer (usually within 24-48 hours)
3. **Ask questions** if anything is unclear
4. **Set realistic timelines** and communicate if you need more time

## Contribution Workflow

### 1. Fork and Clone

```bash
# Fork the repository on GitHub, then:
git clone https://github.com/YOUR-USERNAME/REPO-NAME.git
cd REPO-NAME

# Add upstream remote
git remote add upstream https://github.com/V3lectronics/REPO-NAME.git
```

### 2. Create a Feature Branch

```bash
# Create and switch to a new branch
git checkout -b feature/your-feature-name

# Or for bug fixes:
git checkout -b fix/issue-description
```

**Branch Naming Convention:**
- `feature/description` - New features
- `fix/description` - Bug fixes  
- `docs/description` - Documentation changes
- `refactor/description` - Code refactoring
- `test/description` - Testing improvements

### 3. Make Your Changes

**Code Quality Guidelines:**

**For Hardware (KiCad):**
- Use the latest stable KiCad version
- Follow PCB design best practices
- Include 3D models for new components
- Update the Bill of Materials (BOM)
- Run Design Rules Check (DRC) before submitting

**For Software (AOSP/C++):**
- Follow Google's Android coding style
- Write unit tests for new features
- Ensure code compiles without warnings
- Test on actual hardware when possible
- Update relevant documentation

**For Documentation:**
- Write in clear, accessible English
- Use proper Markdown formatting
- Include code examples where relevant
- Add images or diagrams for complex topics
- Test all links and commands

### 4. Test Your Changes

**Hardware Testing:**
- Verify schematics with peer review
- Test PCB layout with DRC
- Validate component availability
- Check mechanical compatibility

**Software Testing:**
- Build successfully on clean environment
- Test basic functionality
- Run automated tests if available
- Test on hardware if possible
- Check for memory leaks or performance issues

**Documentation Testing:**
- Verify all links work
- Test code examples
- Check formatting and spelling
- Validate against current software versions

### 5. Commit Your Changes

**Commit Message Format:**
```
type(scope): brief description

Longer description explaining the changes, why they were made,
and any important details for reviewers.

Fixes #123
```

**Examples:**
```bash
feat(hardware): add fingerprint sensor support

- Added Goodix fingerprint sensor to PCB design
- Updated BOM with sensor part number
- Added SPI interface routing

Fixes #45

fix(camera): resolve autofocus driver crash

- Fixed null pointer dereference in autofocus routine
- Added proper error handling for focus failures
- Improved logging for debugging

Fixes #78

docs(assembly): clarify PCB mounting instructions

- Added step-by-step photos for PCB installation
- Clarified screw specifications
- Updated parts list with current suppliers

Fixes #92
```

### 6. Push and Create Pull Request

```bash
# Push your branch
git push origin feature/your-feature-name

# Create pull request on GitHub
```

**Pull Request Template:**
Use this template for your PR description:

```markdown
## Description
Brief description of what this PR does.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Hardware design change
- [ ] Performance improvement

## Testing
- [ ] Built successfully
- [ ] Tested on hardware (if applicable)
- [ ] All existing tests pass
- [ ] Added new tests if needed

## Hardware Changes (if applicable)
- [ ] Updated schematics
- [ ] Updated PCB layout
- [ ] Updated BOM
- [ ] Ran DRC successfully

## Software Changes (if applicable)
- [ ] Follows coding standards
- [ ] No compiler warnings
- [ ] Memory leaks checked
- [ ] Performance impact considered

## Documentation Changes (if applicable)
- [ ] Updated relevant documentation
- [ ] All links verified
- [ ] Code examples tested

## Screenshots/Videos
If applicable, add screenshots or videos demonstrating the changes.

## Related Issues
Fixes #(issue number)
```

## Review Process

### What to Expect

1. **Initial Review** - A maintainer will review within 48-72 hours
2. **Feedback** - You may receive requests for changes
3. **Discussion** - Complex changes may require discussion
4. **Approval** - Once approved, your PR will be merged
5. **Recognition** - Contributors are credited in release notes

### Responding to Feedback

- **Be responsive** - Reply to feedback promptly
- **Ask questions** - Don't hesitate to ask for clarification
- **Be patient** - Complex reviews take time
- **Learn from feedback** - Use it to improve future contributions

## Hardware-Specific Guidelines

### KiCad Best Practices

**File Organization:**
```
/EDA-kicad/
├── component-libs/          # Custom components
│   ├── SPIRIT-footprints.pretty/
│   ├── SPIRIT-symbol-libs/
│   └── SPIRIT-3D-models/
├── *.kicad_sch            # Schematic files
├── *.kicad_pcb            # PCB layout
└── *.kicad_pro            # Project file
```

**Design Rules:**
- Use grid alignment (0.1mm minimum)
- Keep trace widths consistent within power domains
- Follow IPC design standards
- Include test points for critical signals
- Use meaningful net names and labels

**Component Guidelines:**
- Source components from DigiKey when possible
- Ensure RoHS compliance
- Include public datasheets
- Create symbols, footprints, and 3D models
- Document any special requirements

### PCB Layout Standards

- **Layer Stack:** Follow the established 4-layer stackup
- **Trace Routing:** 
  - Power: ≥0.2mm traces
  - Signals: ≥0.1mm traces
  - High-speed: Follow length matching rules
- **Via Size:** 0.2mm minimum, 0.25mm typical
- **Copper Pour:** Use on all layers for EMI reduction

## Software-Specific Guidelines

### AOSP Development

**Directory Structure:**
```
device/spirit/spirit/        # Device configuration
hardware/spirit/            # HAL implementations  
kernel/rpi/                 # Kernel source
vendor/spirit/              # Vendor-specific files
```

**Coding Standards:**
- Follow [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
- Use AOSP coding conventions
- Include proper error handling
- Add logging for debugging
- Document complex algorithms

**HAL Development:**
- Implement all required HAL interfaces
- Follow HIDL/AIDL interface definitions
- Handle hardware failures gracefully
- Test with hardware simulators when possible

### Privacy Feature Development

Privacy features are core to SPIRIT. When working on privacy-related code:

- **Hardware switches must be fail-safe** (off when switch is off)
- **Software cannot override hardware switches**
- **Status must be visible to users** (LED indicators, UI status)
- **Log privacy-sensitive operations** for user transparency
- **Test extensively** with actual hardware switches

## Documentation Guidelines

### Writing Style

- **Be clear and concise** - Avoid unnecessary jargon
- **Use active voice** - "Connect the cable" not "The cable should be connected"
- **Include examples** - Show, don't just tell
- **Structure logically** - Use headers, lists, and sections effectively
- **Consider your audience** - Adjust technical level appropriately

### Documentation Types

**API Documentation:**
- Include function signatures
- Explain parameters and return values  
- Provide usage examples
- Document error conditions

**User Guides:**
- Step-by-step instructions
- Screenshots or photos where helpful
- Troubleshooting sections
- Prerequisites clearly stated

**Developer Guides:**
- Background theory when relevant
- Code examples that compile and run
- Links to related documentation
- Common pitfalls and how to avoid them

## Quality Assurance

### Before Submitting

**Final Checklist:**
- [ ] Changes compile/build successfully
- [ ] All tests pass
- [ ] Documentation updated if needed
- [ ] Commit messages follow convention
- [ ] PR description is complete
- [ ] Changes tested on target platform

**Hardware QA:**
- [ ] Schematic review completed
- [ ] PCB DRC passes
- [ ] BOM updated with correct parts
- [ ] 3D models included for new components
- [ ] Manufacturing files generated if needed

**Software QA:**
- [ ] Code follows style guidelines
- [ ] No compiler warnings
- [ ] Memory usage reasonable
- [ ] Performance impact assessed
- [ ] Security implications considered

## Community Guidelines

### Communication

**Be Respectful:**
- Treat all community members with respect
- Welcome newcomers and help them get started
- Give constructive feedback, not criticism
- Be patient with questions and learning

**Be Professional:**
- Use appropriate language in all communications
- Stay on topic in discussions
- Credit others' work appropriately
- Be transparent about conflicts of interest

### Getting Help

**When You're Stuck:**
1. **Search existing issues** and documentation first
2. **Ask in the appropriate Discord channel**:
   - `#hardware` - PCB design, components, assembly
   - `#software` - AOSP, drivers, kernel
   - `#documentation` - Writing, guides, tutorials
   - `#general` - General questions and discussion
3. **Provide context** when asking questions:
   - What are you trying to do?
   - What have you tried?
   - What error messages do you see?
   - What hardware/software versions?

**When Helping Others:**
- Be patient and encouraging
- Provide complete answers when possible
- Point to relevant documentation
- Share your experience and lessons learned

## Recognition

We believe in recognizing contributors for their valuable work:

### Contributors List
All contributors are listed in:
- Repository README files
- Release notes and changelogs
- Annual contributor reports
- Conference presentations and talks

### Types of Recognition
- **Code contributors** - GitHub commit history
- **Documentation contributors** - Author credits in documentation
- **Community contributors** - Special mentions in newsletters
- **Long-term contributors** - Invited to join core team discussions

## Legal Considerations

### Licensing

**Hardware Contributions:**
- All hardware designs are released under open hardware licenses
- By contributing, you agree to license your work under the same terms
- Document any patented technologies or techniques

**Software Contributions:**
- AOSP components follow Apache License 2.0
- Kernel components follow GPL v2
- Original code must be compatible with these licenses
- Don't include proprietary or copyrighted code

**Documentation Contributions:**
- Documentation is typically released under Creative Commons licenses
- All content must be your original work or properly attributed
- Images and media must have appropriate usage rights

### Copyright

- **Your contributions remain yours** - we don't claim ownership
- **You grant us license** to use your contributions in the project
- **Be sure you have rights** to contribute any code, designs, or content
- **Don't contribute code** you don't own or can't license

## Advanced Contributing

### Becoming a Maintainer

Active contributors may be invited to become maintainers. Maintainers have additional responsibilities:

**Responsibilities:**
- Review and merge pull requests
- Triage issues and provide guidance
- Maintain project roadmap and priorities
- Enforce community guidelines and code of conduct
- Mentor new contributors

**Requirements:**
- Consistent high-quality contributions over time
- Deep understanding of relevant project areas
- Good communication and collaboration skills
- Commitment to project values and community

### Project Governance

SPIRIT follows an open governance model:

- **Technical decisions** are made through community discussion
- **Major changes** require consensus from core maintainers
- **Community input** is sought for significant direction changes
- **Transparency** in all project decisions and processes

## Conclusion

Thank you for your interest in contributing to SPIRIT! Whether you're fixing a small bug, designing new hardware features, writing documentation, or helping community members, every contribution makes a difference.

The goal of SPIRIT is to create a truly open smartphone that puts users in control. By contributing, you're helping to make that vision a reality and creating a better future for mobile technology.

**Ready to get started?**

1. **Join our [Discord community](https://discord.gg/zBG4KdHJWx)**
2. **Read through the relevant documentation** for your area of interest
3. **Look for a good first issue** to work on
4. **Introduce yourself** and let us know what you'd like to contribute

Welcome to the SPIRIT community! 🎉

---

*This contributing guide is a living document. If you have suggestions for improvements, please [open an issue](https://github.com/V3lectronics/spirit-docs/issues) or submit a pull request.*
