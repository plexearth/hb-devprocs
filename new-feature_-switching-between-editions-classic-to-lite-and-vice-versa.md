
### Plex-Earth Deployment Documentation

#### Overview
Plex-Earth is an AutoCAD plug-in designed to streamline the design process by integrating Google Earth imagery and other online maps directly into AutoCAD. This documentation outlines the steps required for deploying Plex-Earth, including how to configure the setup project in Visual Studio (VS), along with some hints and tricks to ensure a smooth setup.

#### Setup Projects
We have the following setup projects in our Setups Solution:
- Setup.PlexEarth.Acad
- Setup.PlexEarth.Acad.AppStore
- Setup.PlexEarth.BricsCAD
- Setup.PlexEarth.Lite.Acad
- Setup.PlexEarth.Lite.Acad.AppStore
- Setup.PlexEarth.Lite.BricsCAD

#### Setup Project Properties Description

The Setup Project Properties window in Visual Studio for the Plex-Earth deployment project is used to configure various settings for the installer. Below is a description of each property and its purpose:

##### Miscellaneous Properties

1. **AddRemoveProgramsIcon**:
   - Specifies the icon that will be displayed in the Add or Remove Programs list in Windows. In this case, it is set to `(Icon)`.

2. **Author**:
   - The name of the author or company that created the software.

3. **BackwardCompatibleIDGeneration**:
   - Indicates whether the setup project should generate backward-compatible IDs. It is set to `False`.

4. **Description**:
   - A brief description of the product. For this setup, it states `Copyright ©2024`.

5. **DetectNewerInstalledVersion**:
   - If set to `True`, the installer will check for newer versions of the application during installation. It is set to `True`.

6. **InstallAllUsers**:
   - Determines if the application should be installed for all users on the computer. It is set to `False`, meaning it will install only for the current user.

7. **Keywords**:
   - Keywords associated with the product to aid in searchability. Here, it includes `Plex-Earth, AutoCAD, 2025, Installer, MSI, Google Earth`.

8. **Manufacturer**:
   - The name of the company that manufactures the product.

9. **PreBuildEvent**:
   - Commands or scripts that run before the build starts. For example, it may clean temporary files or prepare resources.

10. **PostBuildEvent**:
    - Commands or scripts that run after the build completes. This might include packaging the installer or deploying it to a server.

11. **PreBuildEventCommandLine**:
    - The command line for the pre-build event, which is left empty if not needed.

12. **PostBuildEventCommandLine**:
    - The command line for the post-build event, configured to copy necessary files to the output directory.

13. **ProductCode**:
    - A unique identifier for the product. This code is automatically generated when the version is specified.

14. **ProductName**:
    - The name of the product. For this setup, it is `Plex-Earth for AutoCAD 2020-2025`.

15. **RemovePreviousVersions**:
    - Determines if the installer should remove previous versions of the product before installing the new version. It is set to `True`.

16. **RunPostBuildEvent**:
    - Specifies when the post-build event should be executed. It is set to `On successful build`.

17. **SearchPath**:
    - The search path for required files. This can be configured if needed.

18. **Subject**:
    - A more detailed description or subject of the installer. This can be customized as required.

19. **SupportPhone**:
    - The phone number for support, if specified.

20. **SupportUrl**:
    - The URL for the support page. It is set to `https://support.plexscape.com`.

21. **TargetPlatform**:
    - Specifies the platform for which the installer is built. Here, it is `x64`, indicating a 64-bit platform.

22. **Title**:
    - The title of the product, which often appears in the installer UI. It is `Plex-Earth for AutoCAD 2020-2025`.

23. **UpgradeCode**:
    - A unique identifier for the upgrade, which helps in managing updates. The `UpgradeCode` is unique to a product and consistent across versions to prevent simultaneous installations of different versions of the same product. For instance, `Plex-Earth for AutoCAD 2020-2025` shares the same `UpgradeCode` with `Plex-Earth Lite for AutoCAD 2020-2025` and older versions like `Plex-Earth 4 for AutoCAD`. In contrast, `Plex-Earth for BricsCAD` has a different `UpgradeCode` to allow simultaneous installations of both products.

24. **Version**:
    - The version of the product being installed. This is specified from the `PlexEarth.dll` assembly, and a new `ProductCode` is generated accordingly. Here, it is `25.0.8972`.
