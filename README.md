This project illustrates how referencing a 4.7.2 project from a .net standard 2.0 project where System.Net.Http is involved triggers the following warning on build

    Found conflicts between different versions of "System.Net.Http" that could not be resolved.  These reference conflicts are listed in the build log when log verbosity is set to detailed.	Nutstandard	C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild\15.0\Bin\Microsoft.Common.CurrentVersion.targets	2110	

The diagnostic build details

    There was a conflict between "System.Net.Http, Version=4.1.2.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" and "System.Net.Http, Version=4.2.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a".
        "System.Net.Http, Version=4.1.2.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" was chosen because it was primary and "System.Net.Http, Version=4.2.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" was not.
        References which depend on "System.Net.Http, Version=4.1.2.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" [C:\Users\wsullivan\.nuget\packages\netstandard.library\2.0.3\build\netstandard2.0\ref\System.Net.Http.dll].
            C:\Users\wsullivan\.nuget\packages\netstandard.library\2.0.3\build\netstandard2.0\ref\System.Net.Http.dll
              Project file item includes which caused reference "C:\Users\wsullivan\.nuget\packages\netstandard.library\2.0.3\build\netstandard2.0\ref\System.Net.Http.dll".
                C:\Users\wsullivan\.nuget\packages\netstandard.library\2.0.3\build\netstandard2.0\ref\System.Net.Http.dll
        References which depend on "System.Net.Http, Version=4.2.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" [].
            D:\GitHub.Com\System.Net.Http.Hell\System.Net.Http.Hell\bin\Debug\System.Net.Http.Hell.dll
              Project file item includes which caused reference "D:\GitHub.Com\System.Net.Http.Hell\System.Net.Http.Hell\bin\Debug\System.Net.Http.Hell.dll".
                D:\GitHub.Com\System.Net.Http.Hell\System.Net.Http.Hell\bin\Debug\System.Net.Http.Hell.dll

Adding the following to the .Net standard project file has no effect

    <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
    <GenerateBindingRedirectsOutputType>true</GenerateBindingRedirectsOutputType>

