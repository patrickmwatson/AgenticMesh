# Platform-Specific Considerations

This document outlines the specific considerations, limitations, and configurations for each AI platform supported by AgenticMesh.

## ChatGPT

### Custom Instructions

#### Character Limits
- **User-level custom instructions**: Limited to 1,500 characters
- **Project-level custom instructions**: Limited to 2,000 characters

#### Handling Strategy
1. **Summarization**: For custom instructions exceeding the character limit, AgenticMesh will create a summarized version that fits within the limit.
2. **File References**: The full custom instructions will be stored as a knowledge base file, and the summarized version will include references to this file.
3. **Chunking**: For complex instructions, AgenticMesh will split them into multiple files and create a navigation structure.

### Knowledge Base Files

#### Limitations
- **File types**: PDF, TXT, CSV, JSON, etc.
- **File size**: Limited to 20MB per file
- **Number of files**: Limited to 20 files per project

#### Handling Strategy
1. **File Conversion**: Convert files to supported formats when necessary.
2. **File Splitting**: Split large files into smaller chunks that fit within the size limit.
3. **File Indexing**: Create an index file that maps the original file structure to the chunked files.

### Project Structure

#### Limitations
- **Project naming**: Limited to 100 characters
- **Project hierarchy**: Flat structure (no nested projects)

#### Handling Strategy
1. **Name Truncation**: Truncate project names that exceed the limit while preserving meaning.
2. **Virtual Hierarchy**: Implement a virtual hierarchy in GitHub that maps to the flat structure in ChatGPT.

### Authentication

- **OAuth with Google**: For patrickmwatson@lifehackinnovations.com and patrickmwatson@gmail.com
- **Session Management**: Handle session expiration and renewal
- **Rate Limiting**: Respect API rate limits and implement backoff strategies

## Claude

### Custom Instructions

#### Character Limits
- **System prompts**: Limited to 100,000 characters

#### Handling Strategy
1. **Direct Mapping**: Claude's generous character limit allows for direct mapping of most custom instructions.
2. **Structured Formatting**: Optimize the formatting for Claude's specific capabilities.

### Knowledge Base Files

#### Limitations
- **File types**: Similar to ChatGPT but with different size constraints
- **Context window**: Consider Claude's context window when chunking files

#### Handling Strategy
1. **Context-Aware Chunking**: Split files based on Claude's context window size.
2. **Metadata Preservation**: Ensure file metadata is preserved during conversion.

### Authentication

- **API Key Authentication**: Use API keys for authentication
- **Key Rotation**: Implement secure key rotation policies
- **Rate Limiting**: Respect API rate limits and implement backoff strategies

## Cursor

### MDC Files

#### Structure
- **Format**: JSON-based format with specific schema requirements
- **Rule types**: Different types of rules with specific formats

#### Handling Strategy
1. **Schema Validation**: Validate markdown against Cursor's MDC schema.
2. **Format Conversion**: Convert markdown to MDC format with appropriate rule types.
3. **Rule Optimization**: Optimize rules for Cursor's specific capabilities.

### Integration

- **File System Access**: Cursor rules are stored as files in the IDE
- **Rule Application**: Rules are applied to specific file types or projects

#### Handling Strategy
1. **Path Mapping**: Map GitHub paths to Cursor file system paths.
2. **Rule Scoping**: Ensure rules are properly scoped to the appropriate files or projects.

## GitHub

### Repository Structure

#### Considerations
- **File organization**: Organize files in a logical structure that maps to AI platforms
- **Naming conventions**: Use consistent naming conventions across repositories
- **README files**: Include comprehensive README files for each repository

#### Handling Strategy
1. **Template Repositories**: Use template repositories for consistent structure.
2. **Metadata Files**: Include metadata files that describe the mapping to AI platforms.
3. **Documentation Generation**: Automatically generate documentation from the repository structure.

### Authentication

- **OAuth**: Use OAuth for authentication with GitHub
- **Personal Access Tokens**: Use PATs for API access
- **Webhook Secret**: Secure webhook endpoints with secrets

#### Handling Strategy
1. **Token Management**: Securely store and manage tokens.
2. **Permission Scoping**: Request only the necessary permissions.
3. **Webhook Verification**: Verify webhook payloads to prevent spoofing.

### Rate Limiting

- **API Rate Limits**: GitHub API has rate limits based on the authentication method
- **Abuse Detection**: GitHub has abuse detection mechanisms

#### Handling Strategy
1. **Rate Limit Tracking**: Track remaining rate limits and adjust request frequency.
2. **Conditional Requests**: Use conditional requests to reduce API usage.
3. **Bulk Operations**: Batch operations to reduce the number of API calls.

## Cross-Platform Considerations

### Data Mapping

- **Schema Differences**: Different platforms have different data schemas
- **Feature Parity**: Not all features are available on all platforms

#### Handling Strategy
1. **Common Data Model**: Define a common data model that can be mapped to each platform.
2. **Feature Detection**: Detect available features on each platform and adapt accordingly.
3. **Graceful Degradation**: Provide fallbacks for features not available on all platforms.

### Synchronization Frequency

- **Real-time vs. Polling**: Some platforms support webhooks for real-time updates, others require polling
- **Update Propagation**: Changes may not propagate immediately across all platforms

#### Handling Strategy
1. **Hybrid Approach**: Use webhooks where available and polling as a fallback.
2. **Consistency Guarantees**: Define consistency guarantees for different types of data.
3. **Conflict Resolution**: Implement strategies for resolving conflicts during synchronization.

### Error Handling

- **Platform-Specific Errors**: Different platforms have different error codes and messages
- **Transient Failures**: Temporary failures due to network issues or service outages

#### Handling Strategy
1. **Error Normalization**: Normalize error codes and messages across platforms.
2. **Retry Policies**: Implement platform-specific retry policies based on error types.
3. **Fallback Mechanisms**: Provide fallback mechanisms for critical operations.

### Security and Privacy

- **Data Sensitivity**: Different types of data have different sensitivity levels
- **Platform Security**: Different platforms have different security models

#### Handling Strategy
1. **Data Classification**: Classify data based on sensitivity and apply appropriate security controls.
2. **Encryption**: Encrypt sensitive data both at rest and in transit.
3. **Access Control**: Implement fine-grained access control based on data classification.