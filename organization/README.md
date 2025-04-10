# Organization Directory

This directory contains projects that are publicly available to members of organizations. Projects are managed to ensure minimal duplication and efficient sharing.

## Structure

```
organization/
├── Life_Hack_Innovations/
│   ├── shared_project_1/
│   │   └── README.md
│   └── shared_project_2/
│       └── README.md
└── other_organizations/
    └── ...
```

## Purpose

The organization directory serves as a central location for projects that are shared at the organizational level. This allows for:

1. **Centralized Management**: All shared projects are managed in one place.
2. **Access Control**: Access to shared projects can be controlled at the organization level.
3. **Efficient Sharing**: Projects can be shared without unnecessary duplication.

## Symlink/Reference Mechanism

To avoid unnecessary duplication of shared projects, AgenticMesh uses a symlink/reference mechanism:

1. **Project References**: Instead of duplicating files, AgenticMesh creates references to the original files.
2. **Metadata**: Metadata files describe the mapping between the organization structure and the original files.
3. **Access Control**: Access control is managed at the reference level, allowing for fine-grained control.

## Usage

### Sharing a Project

To share a project with an organization:

1. Navigate to the project in the web dashboard.
2. Click on "Share with Organization".
3. Select the organization to share with.
4. Configure access permissions.
5. Click "Share".

### Accessing a Shared Project

To access a shared project:

1. Navigate to the organization directory in the web dashboard.
2. Select the organization.
3. Select the shared project.
4. Access the project files and configurations.

## Best Practices

1. **Naming Conventions**: Use consistent naming conventions for shared projects.
2. **Documentation**: Include comprehensive documentation for shared projects.
3. **Access Control**: Regularly review and update access permissions.
4. **Cleanup**: Regularly review and remove unused shared projects.