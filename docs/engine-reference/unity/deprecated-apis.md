# Unity 6.3 LTS — Deprecated APIs

**Last verified:** 2026-04-28

Quick lookup table for deprecated APIs and their replacements.
Format: **Don't use X** → **Use Y instead**

---

## Core API (Verified from official Unity 6.0 upgrade guide)

| Don't Use | Use Instead | Notes |
|-----------|-------------|-------|
| `Object.FindObjectsOfType<T>()` | `Object.FindObjectsByType<T>(FindObjectsSortMode.None)` | Pass sort mode; `.None` is fastest |
| `Object.FindObjectOfType<T>()` | `Object.FindFirstObjectByType<T>()` or `Object.FindAnyObjectByType<T>()` | `FindAny` fastest when order irrelevant |
| `LightingSettings.filteringGaussRadiusAO` (int) | `LightingSettings.filteringGaussianRadiusAO` (float) | Also Direct/Indirect variants |
| `GraphicsFormat.DepthAuto` | `GraphicsFormat.None` | Compile error in Unity 6 |
| `GraphicsFormat.ShadowAuto` | `GraphicsFormat.None` | Compile error in Unity 6 |
| `GraphicsFormat.VideoAuto` | `GraphicsFormat.None` | Compile error in Unity 6 |

## URP Renderer Features (Verified from official Unity 6 URP guide)

| Don't Use | Use Instead | Notes |
|-----------|-------------|-------|
| `ScriptableRenderer.cameraColorTarget` | `cameraColorTargetHandle` | Returns RTHandle |
| `ScriptableRenderer.cameraDepthTarget` | `cameraDepthTargetHandle` | Returns RTHandle |
| `RenderTargetHandle` struct | `RTHandle` via `RTHandles.Alloc()` | Use `RenderingUtils.ReAllocateIfNeeded()` for temporaries |
| `ScriptableRendererFeature.SetupRenderPasses()` | Render graph + `AddRenderPasses()` | Deprecated in 6.2 |
| URP Compatibility Mode (render graph disabled) | Render graph system | Deprecated in 6.0; will be removed |
| `SHADER_QUALITY_LOW/MEDIUM/HIGH` shader defines | `SHADER_API_MOBILE` or `SHADER_API_GLES` | Removed in URP 17 |
| AfterRendering injection point for post-processing | `AfterRenderingPostProcessing` | AfterRendering now runs after final blit (changed in 6.2) |

## UI Toolkit Event Handling (Verified)

| Don't Use | Use Instead | Notes |
|-----------|-------------|-------|
| `ExecuteDefaultAction()` | `HandleEventBubbleUp()` | Renamed in Unity 6 |
| `ExecuteDefaultActionAtTarget()` | `HandleEventTrickleDown()` | Renamed in Unity 6 |
| `PreventDefault()` | `StopPropagation()` | Renamed in Unity 6 |
| `VisualElement.transform` (write) | `element.style.translate / .rotate / .scale` | Deprecated in Unity 6.2 |
| `VisualElement.transform` (read) | `element.resolvedStyle.translate / .rotate / .scale` | Deprecated in Unity 6.2 |
| `UxmlTraits` + `UxmlFactory` | `[UxmlElement]` + `[UxmlAttribute]` attributes | New declarative UXML authoring |
| `CustomEditorForRenderPipelineAttribute` | `[CustomEditor]` + `[SupportedOnRenderPipeline]` | Unified approach |
| `VolumeComponentMenuForRenderPipelineAttribute` | `[VolumeComponentMenu]` + `[SupportedOnRenderPipeline]` | Unified approach |

---

## Input (Legacy Input System)

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `Input.GetKey()` | `Keyboard.current[Key.X].isPressed` | New Input System |
| `Input.GetKeyDown()` | `Keyboard.current[Key.X].wasPressedThisFrame` | New Input System |
| `Input.GetMouseButton()` | `Mouse.current.leftButton.isPressed` | New Input System |
| `Input.GetAxis()` | `InputAction` callbacks | New Input System |
| `Input.mousePosition` | `Mouse.current.position.ReadValue()` | New Input System |

**Migration:** Install `com.unity.inputsystem` package.

---

## UI

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `Canvas` (UGUI) | `UIDocument` (UI Toolkit) | UI Toolkit is now production-ready |
| `Text` component | `TextMeshPro` or UI Toolkit `Label` | Better rendering, fewer draw calls |
| `Image` component | UI Toolkit `VisualElement` with background | More flexible styling |

**Migration:** UGUI still works, but UI Toolkit is recommended for new projects.

---

## DOTS/Entities

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `ComponentSystem` | `ISystem` (unmanaged) | Entities 1.0+ complete rewrite |
| `JobComponentSystem` | `ISystem` with `IJobEntity` | Burst-compatible |
| `GameObjectEntity` | Pure ECS workflow | No GameObject conversion |
| `EntityManager.CreateEntity()` (old signature) | `EntityManager.CreateEntity(EntityArchetype)` | Explicit archetype |
| `ComponentDataFromEntity<T>` | `ComponentLookup<T>` | Entities 1.0+ rename |

**Migration:** See Entities package migration guide. Major refactor required.

---

## Rendering

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `CommandBuffer.DrawMesh()` | RenderGraph API | URP/HDRP render passes |
| `OnPreRender()` / `OnPostRender()` | `RenderPipelineManager` callbacks | SRP compatibility |
| `Camera.SetReplacementShader()` | Custom render pass | Not supported in SRP |

---

## Physics

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `Physics.RaycastAll()` | `Physics.RaycastNonAlloc()` | Avoid GC allocations |
| `Rigidbody.velocity` (direct write) | `Rigidbody.AddForce()` | Better physics stability |

---

## Asset Loading

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `Resources.Load()` | Addressables | Better memory control, async loading |
| Synchronous asset loading | `Addressables.LoadAssetAsync()` | Non-blocking |

---

## Animation

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| Legacy Animation component | Animator Controller | Mecanim system |
| `Animation.Play()` | `Animator.Play()` | State machine control |

---

## Particles

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| Legacy Particle System | Visual Effect Graph | GPU-accelerated, more performant |

---

## Scripting

| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| `WWW` class | `UnityWebRequest` | Modern async networking |
| `Application.LoadLevel()` | `SceneManager.LoadScene()` | Scene management |

---

## Platform-Specific

### WebGL
| Deprecated | Replacement | Notes |
|------------|-------------|-------|
| WebGL 1.0 | WebGL 2.0 or WebGPU | Unity 6+ defaults to WebGPU |

---

## Quick Migration Patterns

### Input Example
```csharp
// ❌ Deprecated
if (Input.GetKeyDown(KeyCode.Space)) {
    Jump();
}

// ✅ New Input System
using UnityEngine.InputSystem;
if (Keyboard.current.spaceKey.wasPressedThisFrame) {
    Jump();
}
```

### Asset Loading Example
```csharp
// ❌ Deprecated
var prefab = Resources.Load<GameObject>("Enemies/Goblin");

// ✅ Addressables
var handle = Addressables.LoadAssetAsync<GameObject>("Enemies/Goblin");
await handle.Task;
var prefab = handle.Result;
```

### UI Example
```csharp
// ❌ Deprecated (UGUI)
GetComponent<Text>().text = "Score: 100";

// ✅ TextMeshPro
GetComponent<TextMeshProUGUI>().text = "Score: 100";

// ✅ UI Toolkit
rootVisualElement.Q<Label>("score-label").text = "Score: 100";
```

---

**Sources:**
- https://docs.unity3d.com/6000.0/Documentation/Manual/deprecated-features.html
- https://docs.unity3d.com/Packages/com.unity.inputsystem@1.11/manual/Migration.html
