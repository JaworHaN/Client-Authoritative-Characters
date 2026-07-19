# Client Auth Movement Replication
**Client-Authoritative Movement Replication Plugin Usage Guide**

---

## Overview
Client Auth Movement Replication is a lightweight UE5 runtime plugin for synchronizing player-controlled characters, custom pawns, and server-driven actors.

The plugin provides:

- **Client-authoritative movement**
- **Smooth remote interpolation**
- **Character Movement Component support**
- **Custom movement support**
- **Velocity and acceleration replication**
- **Grounded state replication**
- **Reliable transform synchronization**
- **Built-in debug visualization**

---

## Usage
1. Open your Character or Pawn Blueprint.
2. Add the **`Client Auth Movement`** component.
3. Open **Class Defaults** and disable **`Replicate Movement`**.
4. Make sure the actor's **`Replicates`** option remains enabled.
5. If your character uses Unreal Engine's **Character Movement Component**, enable **`Use Character Movement Component`** in the Client Auth Movement component settings.
6. If you use a custom movement system, leave **`Use Character Movement Component`** disabled.
7. For custom movement systems, call **`Set Custom Grounded State`** from your own floor detection logic when needed.

---

## Client-Authoritative Movement
The owning client calculates movement locally and sends movement states to the server.

The server receives these states and relays them to remote clients, where buffered interpolation is used to display smooth movement.

This provides:

- Responsive local movement
- Smooth remote motion
- Reduced visible jitter
- Support for both CMC and custom movement systems

> **Security Warning:** Client-authoritative movement can be vulnerable to speed hacks, teleporting, and other client-side manipulation. It is recommended for co-op, party, and casual multiplayer projects unless additional server validation is implemented.

---

## Blueprint Functions
The component provides Blueprint access to replicated movement data:

- **`Get Latest Movement State`**
- **`Get Replicated Location`**
- **`Get Replicated Rotation`**
- **`Get Replicated Velocity`**
- **`Get Replicated Acceleration`**
- **`Is Replicated Grounded`**
- **`Set Custom Grounded State`**
- **`Apply Movement Transform`**

Use **`Apply Movement Transform`** for teleports or important transform changes that must be sent reliably.

---

## Send Rate
The **`Send Rate`** setting controls how often movement states are sent.

Higher values provide more frequent updates but use more bandwidth, while lower values reduce network traffic.

The default value is:

```text
30 updates per second
```

---

## Debug System
Enable **`Enable Debug`** on the component to display:

- Movement source or remote proxy state
- Interpolation buffer size
- Grounded state
- Acceleration
- Buffered movement points

---

**Created by Batuu**
