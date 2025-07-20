# Active Context: AI SDLC Playbook

## Current Work Focus
Expanded IDE support - Reworked the cursor-rules folder to support multiple AI-powered IDEs. The system now provides rule configurations for both Cursor IDE and Kiro, making the playbook applicable to a broader range of AI development environments.

## Recent Changes
- Renamed `cursor-rules` folder to `ide-rules` to reflect multi-IDE support
- Updated all rule files to include both Cursor MDC format and Kiro steering document format
- Updated documentation and README files to use IDE-agnostic terminology
- Modified project references to reflect expanded scope beyond just Cursor
- Updated Memory Bank to reflect the broader IDE support

## Next Steps
- Consider adding support for additional AI-powered IDEs as they emerge
- Create IDE-specific implementation guides for complex setups
- Develop templates that can be easily adapted between different IDE formats
- Gather feedback from teams using different AI development environments
- Document best practices for migrating rules between different IDE systems

## Active Decisions and Considerations
- **Multi-IDE Strategy**: Maintaining compatibility across different AI-powered development environments while keeping rules focused and actionable
- **Format Consistency**: Ensuring rule content remains consistent across different IDE-specific formats (MDC vs Markdown with YAML front-matter)
- **Documentation Structure**: Balancing comprehensive IDE coverage with maintainability and clarity
- **Update Strategy**: Establishing patterns for maintaining rule consistency across multiple IDE formats

## Important Patterns and Preferences
- **Dual Format Support**: All rules now include both Cursor MDC format and Kiro steering document format
- **IDE-Agnostic Content**: Core rule content remains the same across IDEs, only metadata and inclusion mechanisms differ
- **Clear Separation**: Each rule file clearly separates instructions for different IDEs
- **Consistent Naming**: Maintaining consistent naming conventions while adapting to IDE-specific requirements

## Learnings and Project Insights
- AI development environment landscape is expanding beyond single IDE solutions
- Rule content translates well between different IDE formats when properly structured
- Clear separation of concerns between rule content and IDE-specific metadata improves maintainability
- Documentation needs to be adaptable to serve multiple IDE ecosystems
- Project has strong foundation that enables expansion to new AI development tools 