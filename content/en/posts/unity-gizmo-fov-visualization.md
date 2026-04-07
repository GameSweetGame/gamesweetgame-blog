+++
date = '2025-03-13T00:00:00+09:00'
title = 'Visualize Character Field of View with Unity Gizmos'
tags = ['Unity', 'Gizmos', 'Debugging']
categories = ['Unity']
description = 'Using OnDrawGizmos in Unity to visualize character FOV and attack range for debugging'
+++

Unity has built-in Gizmo functions that get called automatically.

### OnDrawGizmos()
Always visible in the Scene view.

### OnDrawGizmosSelected()
Only visible when the object is **selected** in the Scene view.

Great for visualizing field of view, attack range, and other debug shapes.

![Blue lines drawn in scene](/images/posts/unity-gizmo-fov-visualization/1.png)
