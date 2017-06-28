# Repro test case for Xamarin.iOS bug [#57842][bug]

## Summary

Unable to reference a .NET Standard 2.0 library project from a Xamarin.iOS
library project.

## Repro Steps

1. Create a new iOS library project

2. Create a new .NET Standard 2.0 library project

3. Attempt to reference the .NET Standard 2.0 library project from the iOS 
   library project

4. Attempt to build the iOS library project and notice the failure:
   ```
   /Library/Frameworks/Mono.framework/Versions/5.2.0/lib/mono/xbuild/Microsoft/NuGet/Microsoft.NuGet.targets(5,5):
   Error: Your project is not referencing the "Xamarin.iOS,Version=v1.0" framework. Add a reference to
   "Xamarin.iOS,Version=v1.0" in the "frameworks" section of your project.json, and then re-run NuGet restore. (iOSLibrary)
   ```

   At this point there are no NuGets to restore, nor is there a project.json to
   edit. The iOS library's .csproj (old style) still has its target framework
   set to Xamarin.iOS.

5. Add the .NETStandard 2.0 NuGet (preview) to the iOS project and try to
   rebuild again, and note the same build error.

**Review the complete history of this repository in chronological order
for more insight into reproducing this issue.**

[bug]: https://bugzilla.xamarin.com/show_bug.cgi?id=57842