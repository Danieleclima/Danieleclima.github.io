---
layout: post
title:      "Useful React UI Libraries"
date:       2020-07-05 19:45:00 +0000
permalink:  useful_react_ui_libraries
---


UI is the hard part. To some extends, it’s harder than the logic in the backend. In fact, users don’t care about what is in the backend because all they see is the frontend part. So, it’s important to captivate users at their first sight.
If you have time, you can code the UI from scratch to have fun. But if time is a luxury, you should go for the ready-to-use UI components from the libraries below:

1. React Suite
React Suite contains a lot of components such as tooltips, loaders, icons, buttons, etc. It provides a friendly UI which is well designed for enterprise system products.
Install:

```
# npm
npm i rsuite
# yarn
yarn add rsuite
```

Usage example:

```
import { Button } from ‘rsuite’;
import ‘rsuite/lib/styles/index.less’; // or ‘rsuite/dist/styles/rsuite-default.css’
export default function SignInButton() {
  return (
    <Button>Sign In</Button>
  );
}
```

2. Shards React

Shards React makes your UI as high quality as possible and will save you a lot of time by providing a massive list of components. You can build almost every kind of UI with this library.
Install:

```
# npm
npm i shards-react
# yarn
yarn add shards-react
```

Usage example:

```
import { Badge } from “shards-react”;
export default function VipBadge() {
  return (
    <Badge theme=’info’>VIP</Badge>
  );
};
```
