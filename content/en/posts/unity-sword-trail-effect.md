+++
date = '2025-02-21T00:00:00+09:00'
title = 'Unity Sword Trail Effect'
tags = ['Unity', 'VFX', 'Shader', 'Sword Trail']
categories = ['Unity']
description = 'How to create a sword trail effect in Unity using mesh generation and shader texture offset'
+++

I added basic attack animations to my character controller.

![Basic attack](/images/posts/unity-sword-trail-effect/1.gif)

Swinging the sword felt empty. Games I've played always had that afterimage trail effect when swinging fast.

## Implementation

Generate a mesh along the sword's trajectory.

![Sword trajectory as mesh](/images/posts/unity-sword-trail-effect/2.png)

Draw a texture on the mesh and push it with a shader. The timing needs to follow right behind the sword's path.

To sync the timing, adjust the shader texture Offset while watching the sword in the animation.

After searching for how animation stores shader texture values, I found `Material._MainTex_ST`.

Now I can control shader values through animation.

![Sword trail texture following the blade](/images/posts/unity-sword-trail-effect/3.gif)

> **Tip:** Set the shader texture mode to **Clamp** instead of Wrap. Otherwise the texture keeps repeating. With Clamp, it extends the last pixel seamlessly.

![Final result](/images/posts/unity-sword-trail-effect/4.gif)

Basic sword trail effect done. Next step: make it 3D and add more options for fancier effects.

### Extra Tip

![Broken option](/images/posts/unity-sword-trail-effect/5.png)

When keying the animation, use the **Broken** tangent option to prevent the texture from visibly snapping back to the start when the attack animation ends.
