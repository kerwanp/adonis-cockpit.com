# Installation

## Install `adonis-cockpit`

Adonis Cockpit tries to be an Out of the box Administration panel. It relies on different dependencies that will be installed and configured if they are not already present in your project:

- [Lucid](https://lucid.adonisjs.com/)
- [EdgeJS](https://edgejs.dev/)
- [VineJS](https://vinejs.dev/)
- [InertiaJS (Vue 3)](https://inertiajs.com/)
- [@adonisjs/inertia](https://docs.adonisjs.com/guides/views-and-templates/inertia)

Install and configure Adonis Cockpit using the following command.

```sh
node ace add adonis-cockpit
```

:::disclosure{title="See steps performed by the add command"}

1. Installs the `adonis-cockpit` package using the detected package manager.

2. Registers the following provider inside the `adonisrc.ts` file.

    ```ts
    {
      commands: [
        // ...other commands
        () => import('adonis-cockpit/providers/cockpit_provider')
      ]
    }
    ```

3. Registers the following commands inside the `adonisrc.ts` file.

    ```ts
    {
      providers: [
        // ...other providers
        () => import('adonis-cockpit/commands')
      ]
    }
    ```

4. Creates the start file `start/cockpit.ts` and registers it inside the `adonisrc` file.

    ```ts
    {
      preload: [
        // ...other preload
        () => import('#start/cockpit')
      ]
    }
    ```

5. Generates the file `inertia/app/cockpit.ts` that creates the Cockpit inertia app.

6. Generates the `config/cockpit.ts` configuration file.

7. Installs and configure the required peer dependencies.

:::

## Start your Adonis App

Start your Adonis application using `node ace serve` command and navigate to the `/admin` route.

You should already see an empty Administration Panel! It is now time to create your first [Resource](../basics/resources.md).
