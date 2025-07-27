# Ferron example module

This is an example module for Ferron, demonstrating how to create a custom HTTP handler module with Ferron.

## Compiling Ferron with this module

To compile Ferron with this module, first clone the Ferron repository:

```bash
git clone https://github.com/ferronweb/ferron.git -b develop-2.x
cd ferron
```

Then, copy the `ferron-build.yaml` file to `ferron-build-override.yaml`:

```bash
cp ferron-build.yaml ferron-build-override.yaml
```

After that, add the following line to the `ferron-build-override.yaml` file:

```yaml
modules:
  # Other modules...
  - git: https://github.com/ferronweb/ferron-module-example.git
    crate: ferron-module-example
    loader: ExampleModuleLoader
```

It's suggested to define this module between the module with `ReverseProxyModuleLoader` and `FcgiModuleLoader`.

After modifying the `ferron-build-override.yaml` file, you can compile Ferron with this module by running the following command:

```bash
make build
```

You can then package it in a ZIP archive using the following command:

```bash
make package
```

The ZIP archive will be created in the `dist` directory, and can be installed using Ferron installer.
