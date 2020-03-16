# webstorm-ts-import-repro

For Meteor project we are using absolute path imports with the following tsconfig:
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "/*": ["./*"]
    },
    "esModuleInterop": true,
    "jsx": "react"
  }
}

```

When writing the following line in `.tsx` file which does *not* have `useState` imported

`const [value, setValue] = useState();`

If we then force import with Ctrl + Space, WebStorm adds  :
`import {useState} from "/node_modules/@types/react";`  

But it should add `import {useState} from 'react'` or merge into the existing `import React from 'react'`.


When doing the same thing in a `.jsx` file it is correctly imported there.
