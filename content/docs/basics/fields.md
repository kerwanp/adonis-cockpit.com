# Fields

## Field Types

### Boolean Field

The `Boolean` field represent a boolean (true/false) or a tiny integer (0/1).

```ts
import { Boolean } from "@foadonis/cockpit/fields";

Boolean.make("isAdmin");
```

You can configure custom true/false values by using `trueValue` and `falseValue`.

```ts
import { Boolean } from "@foadonis/cockpit/fields";

Boolean.make("checked").trueValue("on").falseValue("off");
```

### Email Field

The `Email` field is a simple `Text` field with email validation that display a `mailto:` link on the index and detail views.

```ts
import { Email } from "@foadonis/cockpit/fields";

Email.make("email");
```

### Password Field

The `Password` field displays a password input with a score.

```ts
import { Password } from "@foadonis/cockpit/fields";

Password.make("password");
```

### Select Field

The `Select` field creates a drop-down select in the form views. The options may be defined using the `options` method.

```ts
import { Select } from "@foadonis/cockpit/fields";

Select.make("role").options(["admin", "user", "guest"]);
```

You may define custom labels by passing a `Record<string, string>` to the `options` method.

```ts
import { Select } from "@foadonis/cockpit/fields";

Select.make("role").options({
  admin: "Admin",
  user: "User",
  guest: "Guest",
});
```

### MultiSelect Field

The `MultiSelect` field is similar to the [`Select` field](#select-field) but allows multiple values to be selected.

```ts
import { MultiSelect } from "@foadonis/cockpit/fields";

MultiSelect.make("roles").options({
  admin: "Admin",
  user: "User",
  guest: "Guest",
});
```

### Text Field

The `Text` field represents a `string` and displays a simple text input.

```ts
import { Text } from "@foadonis/cockpit/fields";

Text.make("name");
```
