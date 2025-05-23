# Setup Allincart

Setup Allincart in your GitHub Actions pipeline to run tests.

## Usage

### Inputs:

- `env`: The environment for Allincart. Should be `test` for PHPUnit or `e2e` for E2E tests. (default: `test`)
- `allincart-version`: The Allincart version to install. (required)
- `allincart-repository`: The Allincart repository to check out. (required, default: `allincart-org/allincart`)
- `php-version`: The PHP version to use. Can be any PHP version supported by [setup-php](https://github.com/shivammathur/setup-php). (default: `8.2`)
- `php-extensions`: A comma-separated list of PHP extensions to install. See setup-php project (default: `")
- `composer-root-version`: The COMPOSER_ROOT_VERSION that should be set. Can be `.auto` to use the version from `composer.json`. (optional, default: `.auto`)
- `install`: Whether to install Allincart or not. If set to `false`, the action will only install PHP, MySQL, Composer packages. (required, default: `false`)
- `install-locale`: The locale to install Allincart with. (required, default: `en-GB`)
- `install-currency`: The currency to install Allincart with. (required, default: `EUR`)
- `keep-composer-tools`: Whether to keep Allincart Composer tools (PHP Stan, ECS/PHP-CS-Fixer, BC-Checker). (required, default: `false`)
- `mysql-version`: Specify any docker image to use instead of the bundled MySQL version of GitHub Actions (default: `builtin`)
- `node-version`: The Node.js version to use. Can be omitted if not needed. (optional, default: `20.x`)
- `install-admin`: Whether to install Administration and build the assets. Can be omitted if not needed. (optional, default: "")
- `install-storefront`: Whether to install Storefront and build the assets. Can be omitted if not needed. (optional, default: "")
- `path`: Relative path under `$GITHUB_WORKSPACE` to place the Allincart repository. (required, default: "")

## Example pipeline to run PHPUnit tests

```yaml
jobs:
    phpunit:
        runs-on: ubuntu-latest
        steps:
            - name: Setup Allincart
              uses: allincart-org/setup-allincart@v1
              with:
                env: test
                allincart-version: v6.5.3.2
                allincart-repository: allincart-org/allincart
                php-version: 8.1
                install: true
