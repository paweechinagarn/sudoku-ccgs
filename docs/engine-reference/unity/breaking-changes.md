# Unity 6.3 LTS — Breaking Changes

**Last verified:** 2026-04-28

This document tracks breaking API changes and behavioral differences between Unity 2022 LTS
(likely in model training) and Unity 6.3 LTS (current version). Organized by risk level.

## Unity 6.0 Precise API Changes (Verified 2026-04-28)

These are confirmed from the official Unity 6.0 upgrade guide:

**Object.Find* (MUST migrate):**
- `Object.FindObjectsOfType<T>()` → `Object.FindObjectsByType<T>(FindObjectsSortMode.None)`
- `Object.FindObjectOfType<T>()` → `Object.FindFirstObjectByType<T>()` or `Object.FindAnyObjectByType<T>()`

**Removed graphics formats (compile error):**
- `GraphicsFormat.DepthAuto`, `GraphicsFormat.ShadowAuto`, `GraphicsFormat.VideoAuto` now cause compile errors.

**UI Toolkit event handling:**
- `ExecuteDefaultAction()` → `HandleEventBubbleUp()`
- `ExecuteDefaultActionAtTarget()` → `HandleEventTrickleDown()`
- `PreventDefault()` → `StopPropagation()`
- `AtTarget` dispatch phase removed; use `TrickleDown` or `BubbleUp`
- `UxmlTraits`/`UxmlFactory` pattern replaced by `[UxmlElement]`/`[UxmlAttribute]` attributes

**Android plugin bridge:**
- `UnityPlayer` no longer extends `FrameLayout`. Use `getFrameLayout()`. Base classes: `UnityPlayerForActivityOrService` or `UnityPlayerForGameActivity`.
- Required JDK: 17. Android Gradle Plugin: 8.7.2.

**Lighting:**
- Enlighten Baked GI removed; Auto Generate setting removed from Lighting window.
- `LightingSettings.filteringGaussRadiusAO` (int) → `filteringGaussianRadiusAO` (float).

## Unity 6.2 Precise API Changes (Verified 2026-04-28)

**URP SetupRenderPasses officially deprecated:**
- `ScriptableRendererFeature.SetupRenderPasses()` deprecated. Migrate to render graph + `AddRenderPasses`.
- AfterRendering injection point now always runs after final blit. Change to `AfterRenderingPostProcessing` to preserve old behavior.

**UI Toolkit:**
- `VisualElement.transform` deprecated.
  - Write: `element.style.translate`, `element.style.rotate`, `element.style.scale`
  - Read: `element.resolvedStyle.translate`, `element.resolvedStyle.rotate`, `element.resolvedStyle.scale`

**Render pipeline attributes:**
- `CustomEditorForRenderPipelineAttribute` → `[CustomEditor]` + `[SupportedOnRenderPipeline]`
- `VolumeComponentMenuForRenderPipelineAttribute` → `[VolumeComponentMenu]` + `[SupportedOnRenderPipeline]`

---

## HIGH RISK — Will Break Existing Code

### Entities/DOTS API Complete Overhaul
**Versions:** Entities 1.0+ (Unity 6.0+)

```csharp
// ❌ OLD (pre-Unity 6, GameObjectEntity pattern)
public class HealthComponent : ComponentData {
    public float Value;
}

// ✅ NEW (Unity 6+, IComponentData)
public struct HealthComponent : IComponentData {
    public float Value;
}

// ❌ OLD: ComponentSystem
public class DamageSystem : ComponentSystem { }

// ✅ NEW: ISystem (unmanaged, Burst-compatible)
public partial struct DamageSystem : ISystem {
    public void OnCreate(ref SystemState state) { }
    public void OnUpdate(ref SystemState state) { }
}
```

**Migration:** Follow Unity's ECS migration guide. Major architectural changes required.

---

### Input System — Legacy Input Deprecated
**Versions:** Unity 6.0+

```csharp
// ❌ OLD: Input class (deprecated)
if (Input.GetKeyDown(KeyCode.Space)) { }

// ✅ NEW: Input System package
using UnityEngine.InputSystem;
if (Keyboard.current.spaceKey.wasPressedThisFrame) { }
```

**Migration:** Install Input System package, replace all `Input.*` calls with new API.

---

### URP/HDRP Renderer Feature API Changes
**Versions:** Unity 6.0+

```csharp
// ❌ OLD: ScriptableRenderPass.Execute signature
public override void Execute(ScriptableRenderContext context, ref RenderingData data)

// ✅ NEW: Uses RenderGraph API
public override void RecordRenderGraph(RenderGraph renderGraph, ContextContainer frameData)
```

**Migration:** Update custom render passes to use RenderGraph API.

---

## MEDIUM RISK — Behavioral Changes

### Addressables — Asset Loading Returns
**Versions:** Unity 6.2+

Asset loading failures now throw exceptions by default instead of returning null.
Add proper exception handling or use `TryLoad` variants.

```csharp
// ❌ OLD: Silent null on failure
var handle = Addressables.LoadAssetAsync<Sprite>("key");
var sprite = handle.Result; // null if failed

// ✅ NEW: Throws on failure, use try/catch or TryLoad
try {
    var handle = Addressables.LoadAssetAsync<Sprite>("key");
    var sprite = await handle.Task;
} catch (Exception e) {
    Debug.LogError($"Failed to load: {e}");
}
```

---

### Physics — Default Solver Iterations Changed
**Versions:** Unity 6.0+

Default solver iterations increased for better stability.
Check `Physics.defaultSolverIterations` if you rely on old behavior.

---

## LOW RISK — Deprecations (Still Functional)

### UGUI (Legacy UI)
**Status:** Deprecated but supported
**Replacement:** UI Toolkit

UGUI still works but UI Toolkit is recommended for new projects.

---

### Legacy Particle System
**Status:** Deprecated
**Replacement:** Visual Effect Graph (VFX Graph)

---

### Old Animation System
**Status:** Deprecated
**Replacement:** Animator Controller (Mecanim)

---

## Platform-Specific Breaking Changes

### WebGL
- **Unity 6.0+**: WebGPU is now the default (WebGL 2.0 fallback available)
- Update shaders for WebGPU compatibility

### Android
- **Unity 6.0+**: Minimum API level raised to 24 (Android 7.0)

### iOS
- **Unity 6.0+**: Minimum deployment target raised to iOS 13

---

## Migration Checklist

When upgrading from 2022 LTS to Unity 6.3 LTS:

- [ ] Audit all DOTS/ECS code (complete rewrite likely needed)
- [ ] Replace `Input` class with Input System package
- [ ] Update custom render passes to RenderGraph API
- [ ] Add exception handling to Addressables calls
- [ ] Test physics behavior (solver iterations changed)
- [ ] Consider migrating UGUI to UI Toolkit for new UI
- [ ] Update WebGL shaders for WebGPU
- [ ] Verify minimum platform versions (Android/iOS)

---

**Sources:**
- https://docs.unity3d.com/6000.0/Documentation/Manual/upgrade-guides.html
- https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/upgrade-guide.html
