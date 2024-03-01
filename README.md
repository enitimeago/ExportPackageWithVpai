# ExportPackageWithVPAI

This is a proof-of-concept for a drop-in `AssetDatabase.ExportPackage` replacement that can bundle anatawa12's VPMPackageAutoInstaller.

This would be useful for distributing assets that depend on a VPM package and offer to auto-install that dependency.

This was initially envisioned to be for package authors, hence it would be a minimal Git repository with pre-compiled VPMPackageAutoInstaller and the C# scripts needed for package authors to use this as a library.

However, it may make sense to contribute this effort back upstream to VPMPackageAutoInstaller. This could be useful not just for package authors, but also for end-users.
