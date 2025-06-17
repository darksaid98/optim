## Pull Requests

We use the [GitHub flow](https://guides.github.com/introduction/flow/) for contributions.

1. Fork the repository.
2. Create a new branch for each feature, fix or improvement.
3. Send a pull request from each feature branch to the **main** branch.

It is very important to separate new features or improvements into separate feature branches, and to send a pull request for each branch. This allow us to review and pull in new features or improvements individually.

## Specifications

### Commit Messages

All commit messages should adhere to the [Conventional Commits specification](https://conventionalcommits.org/).

#### Commit Types

- API relevant changes
    * `feat` Commits, that adds a new feature
    * `fix` Commits, that fixes a bug/issue
- `refactor` Commits, that rewrite/restructure your code, however does not change any API behaviour
    * `perf` Commits are special `refactor` commits, that improve performance
- `style` Commits, that do not affect the meaning (white-space, formatting, missing semi-colons, etc)
- `test` Commits, that add or correct existing tests
- `docs` Commits, that affect documentation only
- Tooling relevant changes
    * `build` Commits, that affect build components like build tool, dependencies, project version, ...
    * `ci` Commits, that affect CI configuration files and scripts
- `revert` Commits, that revert previous commits
- `chore` Miscellaneous commits without production code change, e.g. modifying `.gitignore`

### Versioning

Our project adheres to the [Semantic Versioning 2.0.0 specification](https://semver.org/) for versioning.

## Modifying The Pack

### Pre-requisites

To contribute and modify this pack you will need the [Packwiz CLI Tool](https://github.com/packwiz/packwiz) and [Git](https://git-scm.com/).

1. Follow the Packwiz [installation instructions here](https://packwiz.infra.link/installation/).

1. Install [Git here](https://git-scm.com/).

1. Clone the modpack to your PC using Git.

> [!NOTE]
> The Packwiz modpack is inside the `main` directory of the repository. Run Packwiz commands here. 


### Building

1. Execute `packwiz mr export` to create a Modrinth modpack you can import into any supported launcher.

### Updating

1. Update Minecraft version by doing `packwiz migrate minecraft x.x.x`.

2. Update mod-loader version by doing `packwiz migrate loader latest`.

> [!WARNING]  
> Some mods require a manual touch, such as ones using development builds/fork versions.
3. To update all mods to their latest supported version do `packwiz update --all`.

### Using Prism for Testing

Using a launcher like [Prism](https://prismlauncher.org/) you can make an instance automatically use your latest changes to the modpack.

This is enormously useful when developing and making changes to the modpack.

1. Create a Prism instance with the mod-loader and Minecraft version the modpack uses.

1. Download [packwiz-installer-bootstrap](https://github.com/packwiz/packwiz-installer-bootstrap/releases) and place it in the instance's `minecraft` directory.

1. Edit the instance settings by going to **`Edit Instance` -> `Settings` -> `Custom Commands`** and do the following:
    1. Tick the box `Custom Commands`

    1. Set `Pre-launch command:` to `"$INST_JAVA" -jar packwiz-installer-bootstrap.jar http://localhost:8080/pack.toml`

1. In Packwiz do `packwiz serve` to start serving the modpack.

1. **Launch your instance!** It will now use Packwiz while launching to apply your modpack changes.