---
layout: post
title:      "Animations with React Spring"
date:       2020-05-03 20:22:00 +0000
permalink:  animations_with_react_spring
---


In my quest for achieving the perfect user experience, building a killer UI is at the very top of the list. There's no such thing as a great interface without the right animations that's why I've decided to use a library called React spring for my application. react-spring is a spring-physics based animation library that should cover most of your UI related animation needs.

I'm still trying to figure out how everything works on the React Spring's API however I've seen some of the things that people have created with this library and it seems to be very powerful and offer endless posibilies. Besides my initial impression is that it's quite developer-friendly as you can implement animations with elegant and readable code. All it takes is intalling the react-spring gem:

```
npm install react-spring
```

After that you will have to fetch your imports:

```
import {useSpring, animated} from 'react-spring'
```

After that you'd have to define your animation:

```
const props = useSpring({opacity: 1, from: {opacity: 0}})
```

As you can see above, React sping is using a hook to take an element's opacity from 0 to 1, which comes in quite handy if you wish to create a fade in animation. Finally you will have to apply the animation to the elemement you want to animate, for instance:

```
return <animated.div style={props}>I will fade in</animated.div>
```

I can't wait to start using this library on my app!
