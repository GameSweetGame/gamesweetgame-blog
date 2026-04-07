+++
date = '2025-02-21T00:00:00+09:00'
title = 'Unity Sword Trail Effect'
tags = ['Unity', 'VFX', 'Shader', 'Sword Trail']
categories = ['Unity']
description = 'How to create a sword trail effect in Unity using mesh generation and shader texture offset'
+++

I added basic attack animations to my character controller.

![Basic attack](https://blog.kakaocdn.net/dna/A6Zb0/btsMrtAMszF/AAAAAAAAAAAAAAAAAAAAAMruZrqDPWlMJ-mDmIy-ueKEQvvNUirIWJmFulX8BGpR/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=mIW43q0jPuofh%2FFZ5mq%2FPHVcF7M%3D)

Swinging the sword felt empty. Games I've played always had that afterimage trail effect when swinging fast.

## Implementation

Generate a mesh along the sword's trajectory.

![Sword trajectory as mesh](https://blog.kakaocdn.net/dna/8bn2x/btsMqA8ukv1/AAAAAAAAAAAAAAAAAAAAAGtaadReZgShxRodGqfPT6YB5uUKmA6-exa_R6IILODK/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=20Qdqj0gxdlhdpPEqkixn4ncIFw%3D)

Draw a texture on the mesh and push it with a shader. The timing needs to follow right behind the sword's path.

To sync the timing, adjust the shader texture Offset while watching the sword in the animation.

After searching for how animation stores shader texture values, I found `Material._MainTex_ST`.

Now I can control shader values through animation.

![Sword trail texture following the blade](https://blog.kakaocdn.net/dna/mxPTC/btsMsTMDBYk/AAAAAAAAAAAAAAAAAAAAAL5-77iuoBHeE5HfHEMIl9dg7qi8PaPRg04NSqNXTaoX/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=EXD8vtIx%2F832%2F9BARrBr6KlfRGU%3D)

> **Tip:** Set the shader texture mode to **Clamp** instead of Wrap. Otherwise the texture keeps repeating. With Clamp, it extends the last pixel seamlessly.

![Final result](https://blog.kakaocdn.net/dna/pPVjT/btsMqLCU6LJ/AAAAAAAAAAAAAAAAAAAAAAk4l-JIcGkrEoi1Rd8hefEzrQN-xoqndgqG6M4hvNl0/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=bJH9sX5lGLdW7d4WtsfQdtrY8Gk%3D)

Basic sword trail effect done. Next step: make it 3D and add more options for fancier effects.

### Extra Tip

![Broken option](https://blog.kakaocdn.net/dna/kLZ8q/btsMsUe9Z6Z/AAAAAAAAAAAAAAAAAAAAAJ_clEqvFw90usufkFjmIqkQlSxj3zZhtTyfvAIHo13p/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=Do2ln9XTIHv72qsJ6CO0msgUFxQ%3D)

When keying the animation, use the **Broken** tangent option to prevent the texture from visibly snapping back to the start when the attack animation ends.
