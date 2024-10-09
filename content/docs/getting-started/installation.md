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

## Configure Inertia Root layout

Adonis Cockpit bring its own root layout, to avoid breaking your existing Inertia configuration you have to manually update it to use the Cockpit layout when the path starts with `/admin`.

```ts
// title: config/inertia.ts
const inertiaConfig = defineConfig({
  rootView: ({ request }: HttpContext) => {
    if (request.url().startsWith('/admin')) {
      return 'cockpit::layouts/app'
    }

    return 'inertia_layout'
  },
})

export default inertiaConfig
```

## Configure TailwindCSS

Adonis Cockpit uses [TailwindCSS](https://tailwindcss.com/) for styling. To give you the ability to customize the styles the CSS is not pre-generated.

```ts
// title: tailwind.config.ts
import { Config } from 'tailwindcss'
import cockpit from 'adonis-cockpit/tailwind'

export default {
  darkMode: 'class',
  content: ['./resources/views/**/*.edge', cockpit.contentPath],
  plugins: [cockpit],
} as Config
```

:::tip

TailwindCSS does not allow plugins to extend the `content` configuration, this is why you have to manually set it.

:::

## Start your Adonis App

Start your Adonis application using `node ace serve` command and navigate to the `/admin` route.

You should already see an empty Administration Panel! It is now time to create your first [Resource](../basics/resources.md).
