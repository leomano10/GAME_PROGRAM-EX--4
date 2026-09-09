# GAME_PROGRAM-EX--4

### NAME    : MANORAJAPRIYAN L. E.

### REG. NO.: 212225040227

---

# EXP: 4

## Attaching a Rifle to a Character Mesh and Implementing Bullet Spawn from the Rifle

## Aim

To create an aiming and shooting system in Unreal Engine by attaching a rifle to a third-person character, implementing an aiming mechanism, and spawning bullets from the rifle.

---

## Procedure

### 1. Attach the Rifle to the Character

* Import the **Rifle Skeletal Mesh** into Unreal Engine.
* Open the Character Blueprint, for example:

`BP_ThirdPersonCharacter`

* In the **Components** tab, add a **Skeletal Mesh** or **Static Mesh** component.
* Name the component:

`Rifle`

* Set its Skeletal Mesh property to the imported rifle asset.

---

### 2. Attach the Rifle to a Socket on the Character

Attach the rifle to the character's right-hand socket.

In the Rifle component, set the **Parent Socket** to a suitable socket such as:

`hand_r`

Alternatively, the rifle can be attached manually in the **Event Graph** using the attachment logic:

`Rifle → AttachToComponent`

Attach the Rifle component to the Character Mesh using:

`hand_rSocket`

Use the **Snap to Target** attachment transform rule to correctly align the rifle with the character's hand.

---

### 3. Add an Aiming Mechanism

Create a Boolean variable called:

`IsAiming`

Set up the aiming input in:

**Edit → Project Settings → Input**

Add an **Action Mapping** named:

`Aim`

Assign the **Right Mouse Button** as the input key.

When the Aim button is pressed:

* Set `IsAiming` to `True`.
* Change the character into aiming mode.

When the Aim button is released:

* Set `IsAiming` to `False`.
* Return the character to normal movement mode.

---

### 4. Adjust the Camera While Aiming

Add the following camera components to the Character Blueprint:

* **Camera Boom (Spring Arm)**
* **Follow Camera**

In the **Event Graph**, when:

`IsAiming = True`

Perform the following actions:

* Zoom the camera by reducing the **Field of View (FOV)**.
* Slightly shift the camera over the character's shoulder.
* Adjust the Spring Arm length if required.

When aiming is disabled:

* Restore the camera to its default FOV.
* Return the camera to its normal third-person position.

---

### 5. Implement Bullet Spawning from the Rifle

Create a bullet Blueprint Actor, for example:

`BP_Bullet`

Add a suitable collision component and projectile movement component.

Create a socket or spawn location at the end of the rifle barrel, such as:

`MuzzleSocket`

When the player presses the Fire button:

1. Get the transform of the rifle's `MuzzleSocket`.
2. Use **Spawn Actor from Class**.
3. Select `BP_Bullet` as the actor class.
4. Use the muzzle socket location and rotation as the spawn transform.
5. Spawn the bullet in the direction the rifle is aiming.

The projectile then moves forward using the **Projectile Movement Component**.

---

## Output

### Rifle Attached to Character

<img width="1040" height="840" alt="Rifle Attached to Character" src="https://github.com/user-attachments/assets/d8b27060-1298-4b23-bba3-d5068f9ffaa5" />

<br>

### Rifle Blueprint

<img width="1052" height="657" alt="Rifle Blueprint" src="https://github.com/user-attachments/assets/c88e8d4e-d3d3-4e05-9b36-3948ede465ed" />

---

## Result

Thus, attaching the rifle to the character mesh and implementing bullet spawning from the rifle was successfully completed.

The character can successfully hold the rifle, enter aiming mode, and spawn bullets from the rifle muzzle during gameplay.
