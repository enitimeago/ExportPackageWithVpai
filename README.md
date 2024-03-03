# ExportPackageWithVpai

This is a proof-of-concept for a drop-in `AssetDatabase.ExportPackage` replacement that can bundle anatawa12's [VPMPackageAutoInstaller](https://github.com/anatawa12/VPMPackageAutoInstaller).

This would be useful for distributing assets that depend on a VPM package and offer to auto-install that dependency.

This was initially envisioned to be for package authors, hence it would be a minimal Git repository with pre-compiled VPMPackageAutoInstaller and the C# scripts needed for package authors to use this as a library.

However, it may make sense to contribute this effort back upstream to VPMPackageAutoInstaller. This could be useful not just for package authors, but also for end-users.

`com.anatawa12.vpm-package-auto-installer.dll` compiled with VPMPackageAutoInstaller at [`750c4f0c52ff3e0e685c7aa83f25ad569715f83c`](https://github.com/anatawa12/VPMPackageAutoInstaller/commit/750c4f0c52ff3e0e685c7aa83f25ad569715f83c)

## Usage

Add as a submodule, then include VpaiPackageExporter.cs, com.anatawa12.vpm-package-auto-installer.dll, and all .cs files under tar-cs/tar-cs.

This could be copies or by symlink.

```
git submodule add https://github.com/enitimeago/ExportPackageWithVpai.git
git submodule update --init --recursive
ln -s ExportPackageWithVpai/VpaiPackageExporter.cs .
ln -s tar-cs/tar-cs/*.cs .
```

In Unity, ignore the error popped up by VPMPackageAutoInstaller, then find com.anatawa12.vpm-package-auto-installer.dll and disable all checks to ensure the dll does not activate, alternatively use these meta contents:

```
fileFormatVersion: 2
guid: <REPLACE_THIS_WITH_WHATEVER_UNITY_AUTOASSIGNED_THIS_DLL>
PluginImporter:
  externalObjects: {}
  serializedVersion: 2
  iconMap: {}
  executionOrder: {}
  defineConstraints: []
  isPreloaded: 0
  isOverridable: 1
  isExplicitlyReferenced: 1
  validateReferences: 0
  platformData:
  - first:
      : Any
    second:
      enabled: 0
      settings:
        Exclude Android: 1
        Exclude Editor: 1
        Exclude Linux64: 1
        Exclude OSXUniversal: 1
        Exclude Win: 1
        Exclude Win64: 1
  - first:
      Android: Android
    second:
      enabled: 0
      settings:
        CPU: ARMv7
  - first:
      Any: 
    second:
      enabled: 0
      settings: {}
  - first:
      Editor: Editor
    second:
      enabled: 0
      settings:
        CPU: AnyCPU
        DefaultValueInitialized: true
        OS: AnyOS
  - first:
      Standalone: Linux64
    second:
      enabled: 0
      settings:
        CPU: AnyCPU
  - first:
      Standalone: OSXUniversal
    second:
      enabled: 0
      settings:
        CPU: x86_64
  - first:
      Standalone: Win
    second:
      enabled: 0
      settings:
        CPU: x86
  - first:
      Standalone: Win64
    second:
      enabled: 0
      settings:
        CPU: x86_64
  - first:
      Windows Store Apps: WindowsStoreApps
    second:
      enabled: 0
      settings:
        CPU: AnyCPU
  userData: 
  assetBundleName: 
  assetBundleVariant: 
```
