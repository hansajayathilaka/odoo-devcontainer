# Odoo Development Environment with VS Code Dev Containers

This repository provides a ready-to-use development environment for Odoo 17 using VS Code Dev Containers. This setup allows you to have a consistent development environment across different machines, with all the necessary tools and extensions pre-configured.

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Dev Containers extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- [Git](https://git-scm.com/)

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Trishan0/odoo-devcontainer.git
cd odoo-devcontainer
```

### 2. Open in VS Code with Dev Containers

There are two ways to open the project in VS Code with Dev Containers:

#### Option 1: Open in VS Code first, then use Dev Containers

1. Open VS Code
2. File > Open Folder > Select the cloned repository folder
3. When prompted to "Reopen in Container", click "Reopen in Container"
   - Alternatively, press F1, type "Dev Containers: Reopen in Container" and press Enter

#### Option 2: Use the command line

```bash
code odoo-devcontainer
```

Then follow step 3 from Option 1.

### 3. Wait for the Container to Build

The first time you open the project, VS Code will build the Docker container as defined in the `.devcontainer` folder. This might take a few minutes depending on your internet connection and machine performance.

## Running Odoo

Once the container is built and running, you can run Odoo in two ways:

### Option 1: Using the VS Code Debug Configuration

1. Go to the "Run and Debug" sidebar (Ctrl+Shift+D or Cmd+Shift+D on macOS)
2. Select one of the available launch configurations:
   - **Python: Odoo** - Starts Odoo server with the configuration from `odoo_config/odoo.conf`
   - **Python: Odoo Initial Setup** - Initializes the database and stops after initialization
3. Click the green "Start Debugging" button (F5)

### Option 2: Using the Terminal

1. Open a terminal in VS Code (Terminal > New Terminal)
2. Run the following command:

```bash
python3 -m odoo --config=/workspace/odoo_config/odoo.conf
```

## Accessing Odoo

Once Odoo is running, you can access it in your web browser at:

```
http://localhost:8069
```

Default credentials (if you're creating a new database):
- **Email**: admin
- **Password**: admin

## Project Structure

- `.devcontainer/` - Contains Dev Container configuration
- `odoo_config/` - Contains Odoo configuration files
- `src/` - Directory for your custom Odoo modules
- `odoo-workspace.code-workspace` - VS Code workspace configuration

## Development Workflow

### Creating a New Module

1. Create a new directory in the `src/` folder with your module name
2. Create the standard Odoo module structure:
   - `__init__.py`
   - `__manifest__.py`
   - `models/`, `views/`, etc.

### Installing Your Module

After creating your module, restart Odoo and install your module from the Apps menu.

## VS Code Extensions Included

This Dev Container comes with several useful extensions for Odoo development:

- Python language support and debugging
- PostgreSQL client for database management
- Odoo-specific extensions for better development experience
- OWL Vision for frontend development

## Customizing the Environment

### Changing the Odoo Version

To change the Odoo version, edit the `.devcontainer/docker-compose.yml` file and modify the image tag:

```yaml
services:
  app:
    image: odoo:16  # Change to the desired version (e.g., 15, 16, 17)
```

### Adding Python Dependencies

If your modules require additional Python packages, add them to the `requirements.txt` file. They will be automatically installed when the container is built.

## Troubleshooting

### Container Not Building

Make sure Docker Desktop is running before opening the project in VS Code.

### Database Connection Issues

If you're having trouble connecting to the database, check the database settings in `odoo_config/odoo.conf`. The default settings are:

```
db_host=localhost
db_port=5432
db_user=odoo
db_password=odoo
```

### Port Already in Use

If port 8069 is already in use on your machine, you can change it in the `.devcontainer/devcontainer.json` file under `forwardPorts`.

## Contributing

Feel free to open issues or submit pull requests to improve this development environment.

## License

This project is licensed under the MIT License - see the [LICENSE](https://github.com/Trishan0/odoo-devcontainer/blob/master/LICENSE)
