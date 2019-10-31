---
title: Profileurs CLR et applications du Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
ms.openlocfilehash: da5942f9a2138a536d158f75a6977d20bf31b41c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140390"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profileurs CLR et applications du Windows Store

Cette rubrique explique ce que vous devez savoir lorsque vous écrivez des outils de diagnostic qui analysent le code managé s’exécutant dans une application du Windows Store. Il fournit également des instructions pour modifier vos outils de développement existants afin qu’ils continuent de fonctionner lorsque vous les exécutez sur des applications du Windows Store. Pour comprendre ces informations, il est préférable que vous soyez familiarisé avec l’API de profilage du Common Language Runtime, que vous ayez déjà utilisé cette API dans un outil de diagnostic qui s’exécute correctement sur les applications de bureau Windows, et que vous êtes maintenant intéressé par la modification de l’outil. pour s’exécuter correctement sur les applications du Windows Store.

## <a name="introduction"></a>Introduction

Si vous l’avez fait au-delà du paragraphe d’introduction, vous êtes familiarisé avec l’API de profilage CLR. Vous avez déjà écrit un outil de diagnostic qui fonctionne bien sur les applications de bureau gérées. À présent, vous êtes curieux de savoir ce que vous devez faire pour que votre outil fonctionne avec une application Windows Store gérée. Peut-être avez-vous déjà essayé de faire ce travail et découvert qu’il ne s’agit pas d’une tâche simple. En effet, il existe un certain nombre de considérations qui peuvent ne pas être évidentes pour tous les développeurs d’outils. Exemple :

- Les applications du Windows Store s’exécutent dans un contexte avec des autorisations extrêmement réduites.

- Les fichiers de métadonnées Windows ont des caractéristiques uniques par rapport aux modules managés traditionnels.

- Les applications du Windows Store ont une habitude de s’interrompre lorsque l’interactivité tombe en panne.

- Vos mécanismes de communication entre processus peuvent ne plus fonctionner pour différentes raisons.

Cette rubrique répertorie les éléments dont vous devez être conscient et comment les traiter correctement.

Si vous débutez avec l’API de profilage CLR, passez aux ressources à la fin de cette rubrique pour trouver de meilleures informations de présentation.

La fourniture de détails sur des API Windows spécifiques et la façon dont elles doivent être utilisées ne sont pas non plus abordées dans cette rubrique. Considérez ce sujet comme un point de départ et reportez-vous à MSDN pour en savoir plus sur les API Windows référencées ici.

## <a name="architecture-and-terminology"></a>Architecture et terminologie

En règle générale, un outil de diagnostic a une architecture telle que celle présentée dans l’illustration suivante. Elle utilise le terme « Profiler », mais de nombreux outils de ce type vont bien au-delà des performances typiques ou du profilage de la mémoire dans des domaines tels que la couverture du code, les infrastructures d’objets factices, le débogage du temps, la surveillance des applications, etc. Par souci de simplicité, cette rubrique continuera à faire référence à tous ces outils comme profileurs.

La terminologie suivante est utilisée dans cette rubrique :

**Application**

Il s’agit de l’application analysée par le profileur. En général, le développeur de cette application utilise à présent le profileur pour aider à diagnostiquer les problèmes liés à l’application. Traditionnellement, cette application est une application de bureau Windows, mais dans cette rubrique, nous examinons les applications du Windows Store.

**DLL du profileur**

Il s’agit du composant qui se charge dans l’espace de processus de l’application en cours d’analyse. Ce composant, également appelé « agent du profileur », implémente les interfaces de l’interface [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback](icorprofilercallback-interface.md)(2, 3, etc.) et consomme les interfaces [ICorProfilerInfo](icorprofilerinfo-interface.md)(2,3, etc.) pour collecter les données relatives au application analysée et éventuellement modifier les aspects du comportement de l’application.

**Interface utilisateur du profileur**

Il s’agit d’une application de bureau avec laquelle l’utilisateur du profileur interagit. Il est chargé d’afficher l’état de l’application pour l’utilisateur et de donner à l’utilisateur la possibilité de contrôler le comportement de l’application analysée. Ce composant s’exécute toujours dans son propre espace de processus, distinct de l’espace de processus de l’application en cours de profilage. The Profiler UI can also act as the "attach trigger," which is the process that calls the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method, to cause the analyzed application to load the Profiler DLL in those cases where the profiler DLL did not load on startup.

> [!IMPORTANT]
> Your Profiler UI should remain a Windows desktop application, even when it is used to control and report on a Windows Store app. Don’t expect to be able to package and ship your diagnostics tool in the Windows Store. Your tool needs to do things that Windows Store apps cannot do, and many of those things reside inside your Profiler UI.

Throughout this document, the sample code assumes that:

- Your Profiler DLL is written in C++, because it must be a native DLL, as per the requirements of the CLR Profiling API.

- Your Profiler UI is written in C#. This isn’t necessary, but because there are no requirements on the language for your Profiler UI’s process, why not pick a language that’s concise and simple?

### <a name="windows-rt-devices"></a>Windows RT devices

Windows RT devices are quite locked down. Third-party profilers simply cannot be loaded on such devices. This document focuses on Windows 8 PCs.

## <a name="consuming-windows-runtime-apis"></a>Consuming Windows Runtime APIs

In a number of scenarios discussed in the following sections, your Profiler UI desktop application needs to consume some new Windows Runtime APIs. You’ll want to consult the documentation to understand which Windows Runtime APIs can be used from desktop applications, and whether their behavior is different when called from desktop applications and Windows Store apps.

If your Profiler UI is written in managed code, there will be a few steps you’ll need to do to make consuming those Windows Runtime APIs easy. See the [Managed desktop apps and Windows Runtime](https://go.microsoft.com/fwlink/?LinkID=271858) article for more information.

## <a name="loading-the-profiler-dll"></a>Loading the Profiler DLL

This section describes how your Profiler UI causes the Windows Store app to load your Profiler DLL. The code discussed in this section belongs in your Profiler UI desktop app, and therefore involves using Windows APIs that are safe for desktop apps but not necessarily safe for Windows Store apps.

Your Profiler UI can cause your Profiler DLL to be loaded into the application’s process space in two ways:

- At application startup, as controlled by environment variables.

- By attaching to the application after startup is complete by calling the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method.

One of your first roadblocks will be getting startup-load and attach-load of your Profiler DLL to work properly with Windows Store apps. Both forms of loading share some special considerations in common, so let’s start with them.

### <a name="common-considerations-for-startup-and-attach-loads"></a>Common considerations for startup and attach loads

**Signing your Profiler DLL**

When Windows attempts to load your Profiler DLL, it verifies that your Profiler DLL is properly signed. If not, the load fails by default. Il existe deux façons d'effectuer cette opération :

- Ensure that your Profiler DLL is signed.

- Tell your user that they must install a developer license on their Windows 8 machine before using your tool. This can be done automatically from Visual Studio or manually from a command prompt. For more information, see [Get a developer license](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).

**File system permissions**

The Windows Store app must have permission to load and execute your Profiler DLL from the location on the file system in which it residesBy default, the Windows Store app doesn’t have such permission on most directories, and any failed attempt to load your Profiler DLL will produce an entry in the Windows Application event log that looks something like this:

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

Generally, Windows Store apps are only allowed to access a limited set of locations on the disk. Each Windows Store app can access its own application data folders, as well as a few other areas in the file system for which all Windows Store apps are granted access. It's best to install your Profiler DLL and its dependencies somewhere under Program Files or Program Files (x86), because all Windows Store apps have read and execute permissions there by default.

### <a name="startup-load"></a>Startup load

Typically, in a desktop app, your Profiler UI prompts a startup load of your Profiler DLL by initializing an environment block that contains the required CLR Profiling API environment variables (i.e., `COR_PROFILER`, `COR_ENABLE_PROFILING`, and `COR_PROFILER_PATH`), and then creating a new process with that environment block. The same holds true for Windows Store apps, but the mechanisms are different.

**Don’t run elevated**

If Process A attempts to spawn Windows Store app Process B, Process A should be run at medium integrity level, not at high integrity level (that is, not elevated). This means that either your Profiler UI should be running at medium integrity level, or it must spawn another desktop process at medium integrity level to take care of launching the Windows Store app.

**Choosing a Windows Store App to profile**

First, you’ll want to ask your profiler user which Windows Store app to launch. For desktop apps, perhaps you’d show a file Browse dialog, and the user would find and select an .exe file. But Windows Store apps are different, and using a Browse dialog doesn’t make sense. Instead, it’s better to show the user a list of Windows Store apps installed for that user to select from.

You can use the <xref:Windows.Management.Deployment.PackageManager> class to generate this list. `PackageManager` is a Windows Runtime class that is available to desktop apps, and in fact it is *only* available to desktop apps.

The following code example from a hypothetical Profiler UI written as a desktop app in C# uses the `PackageManager` to generate a list of Windows apps:

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**Specifying the custom environment block**

A new COM interface, [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), allows you to customize the execution behavior of a Windows Store app to make some forms of diagnostics easier. One of its methods, [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), lets you pass an environment block to the Windows Store app when it’s launched, along with other useful effects like disabling automatic process suspension. The environment block is important because that’s where you need to specify the environment variables (`COR_PROFILER`, `COR_ENABLE_PROFILING`, and `COR_PROFILER_PATH)`) used by the CLR to load your Profiler DLL .

Examinez l’extrait de code suivant :

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

There are a couple of items you'll need to get right:

- `packageFullName` can be determined while iterating over the packages and grabbing `package.Id.FullName`.

- `debuggerCommandLine` is a bit more interesting. In order to pass the custom environment block to the Windows Store app, you need to write your own, simplistic dummy debugger. Windows spawns the Windows Store app suspended and then attaches your debugger by launching your debugger with a command line like in this example:

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     where `-p 1336` means the Windows Store app has Process ID 1336, and `-tid 1424` means Thread ID 1424 is the thread that is suspended. Your dummy debugger would parse the ThreadID from the command-line, resume that thread, and then exit.

     Here’s some example C++ code to do this (be sure to add error checking!):

    ```cpp
    int wmain(int argc, wchar_t* argv[])
    {
        // …
        // Parse command line here
        // …

        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,
                                                                  FALSE /* bInheritHandle */, nThreadID);
        ResumeThread(hThread);
        CloseHandle(hThread);
        return 0;
    }
    ```

     You’ll need to deploy this dummy debugger as part of your diagnostics tool installation, and then specify the path to this debugger in the `debuggerCommandLine` parameter.

**Launching the Windows Store app**

The moment to launch the Windows Store app has finally arrived. If you’ve already tried doing this yourself, you may have noticed that [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) is not how you create a Windows Store app process. Instead, you’ll need to use the [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) method. To do that, you’ll need to get the App User Model ID of the Windows Store app that you’re launching. And that means you’ll need to do a little digging through the manifest.

While iterating over your packages (see "Choosing a Windows Store App to Profile" in the [Startup load](#startup-load) section earlier), you’ll want to grab the set of applications contained in the current package’s manifest:

```csharp
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";

AppxPackaging.IStream manifestStream;
SHCreateStreamOnFileEx(
                    manifestPath,
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE
                    0,              // file creation attributes
                    false,          // fCreate
                    null,           // reserved
                    out manifestStream);

IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);

IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();
```

Yes, one package can have multiple applications, and each application has its own Application User Model ID. So you’ll want to ask your user which application to profile, and grab the Application User Model ID from that particular application:

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

Finally, you now have what you need to launch the Windows Store app:

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**Remember to call DisableDebugging**

When you called [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), you made a promise that you would clean up after yourself by calling the [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) method, so be sure to do that when the profiling session is over.

### <a name="attach-load"></a>Attach load

When your Profiler UI wants to attach its Profiler DLL to an application that has already started running, it uses [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md). The same holds true with Windows Store apps. But in addition to the common considerations listed earlier, make sure the that the target Windows Store app is not suspended.

**EnableDebugging**

As with startup load, call the [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) method. You don’t need it for passing an environment block, but you need one of its other features: disabling automatic process suspension. Otherwise, when your Profiler UI calls [AttachProfiler](iclrprofiling-attachprofiler-method.md), the target Windows Store app may be suspended. In fact, this is likely if the user is now interacting with your Profiler UI, and the Windows Store app is not active on any of the user’s screens. And if the Windows Store app is suspended, it won’t be able to respond to any signal that the CLR sends to it to attach your Profiler DLL.

So you’ll want to do something like this:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

This is the same call you’d make for the startup load case, except you don’t specify a debugger command line or an environment block.

**DisableDebugging**

As always, don’t forget to call [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) when your profiling session is completed.

## <a name="running-inside-the-windows-store-app"></a>Running inside the Windows Store app

So the Windows Store app has finally loaded your Profiler DLL. Now your Profiler DLL must be taught how to play by the different rules required by Windows Store apps, including which APIs are allowable and how to run with reduced permissions.

### <a name="stick-to-the-windows-store-app-apis"></a>Stick to the Windows Store app APIs

As you browse the Windows API, you’ll notice that every API is documented as being applicable to desktop apps, Windows Store apps, or both. For example, the **Requirements** section of the documentation for the [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) function indicates that the function applies to desktop apps only. In contrast, the [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) function is available for both desktop apps and Windows Store apps.

When developing your Profiler DLL, treat it as if it’s a Windows Store app and only use APIs that are documented as available to Windows Store apps. Analyze your dependencies (for example, you can run `link /dump /imports` against your Profiler DLL to audit), and then search the docs to see which of your dependencies are ok and which aren’t. In most cases, your violations can be fixed by simply replacing them with a newer form of the API that is documented as safe (for example, replacing [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) with [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).

You might notice that your Profiler DLL calls some APIs that apply to desktop apps only, and yet they seem to work even when your Profiler DLL is loaded inside a Windows Store app. Be aware that it’s risky to use any API not documented for use with Windows Store apps in your Profiler DLL when loaded into a Windows Store app process:

- Such APIs are not guaranteed to work when called in the unique context that Windows Store apps run in.

- Such APIs might not work consistently when called from within different Windows Store app processes.

- Such APIs might seem to work fine from Windows Store apps in the current version of Windows, but may break or be disabled in future releases of Windows.

The best advice is to fix all your violations and avoid the risk.

You might find that you absolutely cannot do without a particular API and cannot find a replacement suitable for Windows Store apps. In such a case, at a minimum:

- Test, test, test the living daylights out of your usage of that API.

- Understand that the API might suddenly break or disappear if called from inside Windows Store apps in future releases of Windows. This won’t be considered a compatibility concern by Microsoft, and supporting your usage of it will not be a priority.

### <a name="reduced-permissions"></a>Reduced permissions

It’s outside the scope of this topic to list all the ways that Windows Store app permissions differ from desktop apps. But certainly the behavior will be different every time your Profiler DLL (when loaded into a Windows Store app as compared to a desktop app) tries to access any resources. The file system is the most common example. There are but a few places on disk that a given Windows Store app is allowed to access (see [File access and permissions (Windows Runtime apps](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))), and your Profiler DLL will be under the same restrictions. Test your code thoroughly.

### <a name="inter-process-communication"></a>Inter-process communication

As shown in the diagram at the beginning of this paper, your Profiler DLL (loaded into the Windows Store app process space) will likely need to communicate with your Profiler UI (running in a separate desktop app process space) through your own custom inter-process communication (IPC) channel. L’interface utilisateur du profileur envoie des signaux à la DLL du profileur pour modifier son comportement, et la DLL du profileur renvoie les données de l’application du Windows Store analysée à l’interface utilisateur du profileur pour le poster et les afficher à l’utilisateur du profileur.

La plupart des profileurs doivent fonctionner de cette manière, mais vos choix pour les mécanismes IPC sont plus limités lorsque votre DLL du profileur est chargée dans une application du Windows Store. Par exemple, les canaux nommés ne faisant pas partie du kit de développement logiciel (SDK) d’application du Windows Store, vous ne pouvez pas les utiliser.

Mais bien sûr, les fichiers se trouvent toujours dans, bien que de manière plus limitée. Les événements sont également disponibles.

**Communication via des fichiers**

La plupart de vos données sont susceptibles de passer entre la DLL du profileur et l’interface utilisateur du profileur via des fichiers. La clé consiste à choisir un emplacement de fichier qui, à la fois, la DLL du profileur (dans le contexte d’une application du Windows Store) et l’interface utilisateur du profileur ont accès en lecture et en écriture à. Par exemple, le chemin d’accès au dossier temporaire est un emplacement accessible à la fois à la DLL du profileur et à l’interface utilisateur du profileur, mais aucun autre package d’application du Windows Store ne peut accéder (protégeant ainsi toutes les informations que vous consignez à partir d’autres packages d’applications du Windows Store).

L’interface utilisateur du profileur et la DLL du profileur peuvent déterminer ce chemin d’accès indépendamment. L’interface utilisateur de votre profileur, lorsqu’elle itère au sein de tous les packages installés pour l’utilisateur actuel (Voir l’exemple de code précédent), obtient l’accès à la classe `PackageId`, à partir de laquelle le chemin d’accès au dossier temporaire peut être dérivé avec du code similaire à cet extrait de code. (Comme toujours, la vérification des erreurs est omise par souci de concision.)

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

Pendant ce temps, votre DLL de profileur peut faire la même chose, bien qu’il puisse accéder plus facilement à la classe <xref:Windows.Storage.ApplicationData> à l’aide de la propriété [ApplicationData. Current](xref:Windows.Storage.ApplicationData.Current%2A) .

**Communication via des événements**

Si vous souhaitez une sémantique de signalisation simple entre votre interface utilisateur du profileur et la DLL du profileur, vous pouvez utiliser des événements dans les applications du Windows Store ainsi que les applications de bureau.

À partir de votre DLL du profileur, vous pouvez simplement appeler la fonction [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) pour créer un événement nommé portant le nom de votre choix. Exemple :

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

L’interface utilisateur du profileur doit alors trouver cet événement nommé sous l’espace de noms de l’application Windows Store. Par exemple, votre interface utilisateur du profileur peut appeler [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), en spécifiant le nom de l’événement comme

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>` est le SID AppContainer de l’application Windows Store. Une section précédente de cette rubrique a montré comment effectuer une itération sur les packages installés pour l’utilisateur actuel. À partir de cet exemple de code, vous pouvez obtenir packageId. Et à partir du packageId, vous pouvez obtenir le `<acSid>` avec un code similaire à ce qui suit :

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>Aucune notification d’arrêt

En cas d’exécution dans une application du Windows Store, votre DLL du profileur ne doit pas s’appuyer sur [ICorProfilerCallback :: Shutdown](icorprofilercallback-shutdown-method.md) ou même [DllMain](/windows/desktop/Dlls/dllmain) (avec `DLL_PROCESS_DETACH`) appelé pour informer votre dll du profileur que l’application du Windows Store est en cours de fermeture. En fait, vous devez vous attendre à ce qu’elles ne soient jamais appelées. Historiquement, de nombreuses dll du profileur ont utilisé ces notifications comme des emplacements pratiques pour vider les caches sur le disque, fermer les fichiers, envoyer des notifications à l’interface utilisateur du profileur, etc. Mais maintenant, votre DLL de profileur doit être organisée un peu différemment.

Votre DLL du profileur doit enregistrer les informations au fur et à mesure. Pour des raisons de performances, vous souhaiterez peut-être traiter les informations en mémoire et les vider sur le disque à mesure que la taille du lot dépasse un certain seuil. Mais supposons que toutes les informations qui n’ont pas encore été vidées sur le disque peuvent être perdues. Cela signifie que vous pouvez choisir votre seuil avec prudence et que votre interface utilisateur du profileur doit être renforcée pour traiter les informations incomplètes écrites par la DLL du profileur.

## <a name="windows-runtime-metadata-files"></a>Windows Runtime les fichiers de métadonnées

Ce document ne décrit pas en détail les fichiers de métadonnées de Windows Runtime (WinMD). Cette section est limitée à la façon dont l’API de profilage CLR réagit lorsque des fichiers WinMD sont chargés par l’application du Windows Store que votre DLL du profileur analyse.

### <a name="managed-and-non-managed-winmds"></a>Winmd géré et non géré

Si un développeur utilise Visual Studio pour créer un projet de composant Windows Runtime, une build de ce projet produit un fichier WinMD qui décrit les métadonnées (les descriptions de type des classes, les interfaces, etc.) créées par le développeur. Si ce projet est un projet de langage managé écrit C# en ou vb, ce même fichier WinMD contient également l’implémentation de ces types (ce qui signifie qu’il contient tout le langage intermédiaire compilé à partir du code source du développeur). Ces fichiers sont appelés fichiers WinMD gérés. Ils sont intéressants en ce sens qu’ils contiennent à la fois les métadonnées Windows Runtime et l’implémentation sous-jacente.

En revanche, si un développeur crée un projet de composant Windows Runtime C++pour, une build de ce projet produit un fichier WinMD qui contient uniquement des métadonnées, et l’implémentation est compilée dans une DLL native distincte. De même, les fichiers WinMD fournis dans le SDK Windows contiennent uniquement des métadonnées, l’implémentation étant compilée dans des DLL natives distinctes fournies dans le cadre de Windows.

Les informations ci-dessous s’appliquent aux Winmd gérés, qui contiennent des métadonnées et de l’implémentation, et à des Winmd non managés qui contiennent uniquement des métadonnées.

### <a name="winmd-files-look-like-clr-modules"></a>Les fichiers WinMD ressemblent à des modules CLR

En ce qui concerne le CLR, tous les fichiers WinMD sont des modules. L’API de profilage CLR indique donc à votre DLL de profileur lorsque les fichiers WinMD sont chargés et ce que leurs ModuleID sont, de la même façon que pour les autres modules managés.

Votre DLL du profileur peut distinguer les fichiers WinMD d’autres modules en appelant la méthode [ICorProfilerInfo3 :: GetModuleInfo2,](icorprofilerinfo3-getmoduleinfo2-method.md) et en inspectant le paramètre de sortie `pdwModuleFlags` pour l’indicateur [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) . (Il est défini si et uniquement si le ModuleID représente un WinMD.)

### <a name="reading-metadata-from-winmds"></a>Lecture des métadonnées à partir de Winmd

Les fichiers WinMD, comme les modules standard, contiennent des métadonnées qui peuvent être lues via les [API de métadonnées](../../../../docs/framework/unmanaged-api/metadata/index.md). Toutefois, le CLR mappe Windows Runtime types aux types de .NET Framework lorsqu’il lit les fichiers WinMD afin que les développeurs qui programment dans du code managé et consomment le fichier WinMD peuvent avoir une expérience de programmation plus naturelle. Pour obtenir des exemples de ces mappages, consultez [.NET Framework la prise en charge des applications et des Windows Runtime du Windows Store](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).

Par conséquent, quelle vue votre profileur obtiendra-t-il lorsqu’il utilise les API de métadonnées : la vue brute Windows Runtime ou la vue de .NET Framework mappée ?  Réponse : c’est à vous de faire.

Quand vous appelez la méthode [ICorProfilerInfo :: GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) sur un WinMD pour obtenir une interface de métadonnées, telle que [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), vous pouvez choisir de définir [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) dans le paramètre `dwOpenFlags` pour désactiver ce mappage. Dans le cas contraire, le mappage est activé par défaut. En règle générale, un profileur garde le mappage activé, afin que les chaînes obtenues par la DLL du profileur à partir des métadonnées WinMD (par exemple, les noms des types) semblent familières et naturelles pour l’utilisateur du profileur.

### <a name="modifying-metadata-from-winmds"></a>Modification des métadonnées à partir de Winmd

La modification des métadonnées dans Winmd n’est pas prise en charge. Si vous appelez la méthode [ICorProfilerInfo :: GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) pour un fichier WinMD et spécifiez [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) dans le paramètre `dwOpenFlags` ou demandez une interface de métadonnées accessible en écriture comme [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) échouera. Cela revêt une importance particulière pour les profileurs de réécriture de l’IL, qui doivent modifier les métadonnées pour prendre en charge leur instrumentation (par exemple, pour ajouter AssemblyRefs ou de nouvelles méthodes). Vous devez donc rechercher d’abord [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) (comme indiqué dans la section précédente) et vous abstenir de demander des interfaces de métadonnées accessibles en écriture sur de tels modules.

### <a name="resolving-assembly-references-with-winmds"></a>Résolution des références d’assembly avec Winmd

De nombreux profileurs doivent résoudre les références de métadonnées manuellement pour faciliter l’instrumentation ou l’inspection de type. De tels profileurs doivent être conscients de la façon dont le CLR résout les références d’assembly qui pointent vers Winmd, car ces références sont résolues de façon complètement différente des références d’assembly standard.

## <a name="memory-profilers"></a>Profileurs de mémoire

Le garbage collector et le tas managé ne sont pas fondamentalement différents dans une application du Windows Store et dans une application de bureau. Toutefois, il existe quelques différences subtiles que les auteurs du profileur doivent connaître.

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC, crée un thread managé

Lors du profilage de la mémoire, la DLL de votre profileur crée généralement un thread distinct à partir duquel appeler la méthode de [méthode ForceGC,](icorprofilerinfo-forcegc-method.md) . Ce n’est rien de nouveau. Mais ce qui peut être surprenant, c’est que l’acte d’effectuer un garbage collection dans une application du Windows Store peut transformer votre thread en thread managé (par exemple, un objet de profilage de l’API de profilage sera créé pour ce thread).

Pour comprendre les conséquences de cette opération, il est important de comprendre les différences entre les appels synchrones et asynchrones, comme défini par l’API de profilage CLR. Notez que cela est très différent du concept des appels asynchrones dans les applications du Windows Store. Pour plus d’informations, consultez le billet de blog [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) .

Le point pertinent est que les appels effectués sur les threads créés par votre profileur sont toujours considérés comme synchrones, même si ces appels sont effectués à partir de l’extérieur d’une implémentation de l’une des méthodes [ICorProfilerCallback](icorprofilercallback-interface.md) de votre dll de profileur. Au moins, qui était le cas. Maintenant que le CLR a converti le thread de votre profileur en thread managé en raison de votre appel à la [méthode ForceGC,](icorprofilerinfo-forcegc-method.md), ce thread n’est plus considéré comme le thread de votre profileur. As such, the CLR enforces a more stringent definition of what qualifies as synchronous for that thread—namely that a call must originate from inside one of your Profiler DLL’s [ICorProfilerCallback](icorprofilercallback-interface.md) methods to qualify as synchronous.

What does this mean in practice? Most [ICorProfilerInfo](icorprofilerinfo-interface.md) methods are only safe to be called synchronously, and will immediately fail otherwise. So if your Profiler DLL reuses your [ForceGC Method](icorprofilerinfo-forcegc-method.md) thread for other calls typically made on profiler-created threads (for example, to [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](icorprofilerinfo4-requestrejit-method.md), or [RequestRevert](icorprofilerinfo4-requestrevert-method.md)), you’re going to have trouble. Even an asynchronous-safe function such as [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) has special rules when called from managed threads. (See the blog post [Profiler stack walking: Basics and beyond](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) for more information.)

Therefore, we recommend that any thread your Profiler DLL creates to call [ForceGC Method](icorprofilerinfo-forcegc-method.md) should be used *only* for the purpose of triggering GCs and then responding to the GC callbacks. It should not call into the Profiling API to perform other tasks like stack sampling or detaching.

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

Starting with the .NET Framework 4.5, there is a new GC callback, [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md), which gives the profiler more complete information about *dependent handles*. These handles effectively add a reference from a source object to a target object for the purpose of GC lifetime management. Dependent handles are nothing new, and developers who program in managed code have been able to create their own dependent handles by using the <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> class even before Windows 8 and the .NET Framework 4.5.

However, managed XAML Windows Store apps now make heavy use of dependent handles. In particular, the CLR uses them to aid with managing reference cycles between managed objects and unmanaged Windows Runtime objects. This means that it’s more important now than ever for memory profilers to be informed of these dependent handles so that they can be visualized along with the rest of the edges in the heap graph. Your Profiler DLL should use [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) together to form a complete view of the heap graph.

## <a name="conclusion"></a>Conclusion

It is possible to use the CLR Profiling API to analyze managed code running inside Windows Store apps. In fact, you can take an existing profiler that you’re developing and make some specific changes so that it can target Windows Store apps. Your Profiler UI should use the new APIs for activating the Windows Store app in debugging mode. Make sure that your Profiler DLL consumes only those APIs applicable for Windows Store apps. The communication mechanism between your Profiler DLL and Profiler UI should be written with the Windows Store app API restrictions in mind and with awareness of the restricted permissions in place for Windows Store apps. Your Profiler DLL should be aware of how the CLR treats WinMDs, and how the Garbage Collector’s behavior is different with respect to managed threads.

## <a name="resources"></a>Ressources

**The Common Language Runtime**

- [Profiling (Unmanaged API Reference)](index.md)

- [Metadata (Unmanaged API Reference)](../metadata/index.md)

**The CLR's interaction with the Windows Runtime**

- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Applications Windows Store**

- [File access and permissions (Windows Runtime apps](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [Obtenir une licence de développeur](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [IPackageDebugSettings Interface](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
