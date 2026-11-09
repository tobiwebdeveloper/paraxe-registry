# React

Import named components from `@paraxe/react`. Controlled value components expose callback props such as `onModelValueChange` rather than relying on DOM event forwarding.

```tsx
import { Input } from "@paraxe/react";
import { useState } from "react";
export function EmailField() {
  const [email, setEmail] = useState("");
  return <Input modelValue={email} onModelValueChange={setEmail} type="email" />;
}
```

Only names exported by the package barrel are public; source files alone do not indicate support.
