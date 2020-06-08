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
ms.openlocfilehash: 6330a4c2733729da264065d1eec8c3c9eaf9f05c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501025"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profileurs CLR et applications du Windows Store

Cette rubrique explique ce que vous devez savoir lorsque vous écrivez des outils de diagnostic qui analysent le code managé s’exécutant dans une application du Windows Store. Il fournit également des instructions pour modifier vos outils de développement existants afin qu’ils continuent de fonctionner lorsque vous les exécutez sur des applications du Windows Store. Pour comprendre ces informations, il est préférable que vous soyez familiarisé avec l’API de profilage du Common Language Runtime. vous avez déjà utilisé cette API dans un outil de diagnostic qui s’exécute correctement sur les applications de bureau Windows, et vous êtes maintenant intéressé par la modification de l’outil pour qu’il s’exécute correctement sur les applications du Windows Store.

## <a name="introduction"></a>Introduction

Si vous l’avez fait au-delà du paragraphe d’introduction, vous êtes familiarisé avec l’API de profilage CLR. Vous avez déjà écrit un outil de diagnostic qui fonctionne bien sur les applications de bureau gérées. À présent, vous êtes curieux de savoir ce que vous devez faire pour que votre outil fonctionne avec une application Windows Store gérée. Peut-être avez-vous déjà essayé de faire ce travail et découvert qu’il ne s’agit pas d’une tâche simple. En effet, il existe un certain nombre de considérations qui peuvent ne pas être évidentes pour tous les développeurs d’outils. Par exemple :

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

Il s’agit du composant qui se charge dans l’espace de processus de l’application en cours d’analyse. Ce composant, également appelé « agent » du profileur, implémente les interfaces [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback interface](icorprofilercallback-interface.md)(2, 3, etc.) et consomme les interfaces [ICorProfilerInfo](icorprofilerinfo-interface.md)(2, 3, etc.) pour collecter des données sur l’application analysée et éventuellement modifier les aspects du comportement de l’application.

**Interface utilisateur du profileur**

Il s’agit d’une application de bureau avec laquelle l’utilisateur du profileur interagit. Il est chargé d’afficher l’état de l’application pour l’utilisateur et de donner à l’utilisateur la possibilité de contrôler le comportement de l’application analysée. Ce composant s’exécute toujours dans son propre espace de processus, distinct de l’espace de processus de l’application en cours de profilage. L’interface utilisateur du profileur peut également jouer le rôle de « déclencheur d’attachement », qui est le processus qui appelle la méthode [ICLRProfiling :: AttachProfiler](iclrprofiling-attachprofiler-method.md) pour que l’application analysée charge la dll du profileur dans les cas où la dll du profileur n’a pas été chargée au démarrage.

> [!IMPORTANT]
> L’interface utilisateur de votre profileur doit rester une application de bureau Windows, même lorsqu’elle est utilisée pour contrôler et créer des rapports sur une application du Windows Store. Ne vous attendez pas à pouvoir empaqueter et livrer votre outil de diagnostic dans le Windows Store. Votre outil doit effectuer des opérations que les applications du Windows Store ne peuvent pas effectuer, et la plupart de ces éléments résident dans votre interface utilisateur du profileur.

Dans ce document, l’exemple de code suppose que :

- Votre DLL du profileur est écrite en C++, car il doit s’agir d’une DLL native, conformément aux exigences de l’API de profilage CLR.

- L’interface utilisateur de votre profileur est écrite en C#. Cela n’est pas nécessaire, mais étant donné qu’il n’y a aucune exigence sur le langage pour le processus de votre interface utilisateur du profileur, pourquoi ne pas choisir une langue concise et simple ?

### <a name="windows-rt-devices"></a>Appareils Windows RT

Les appareils Windows RT sont tout à fait verrouillés. Les profileurs tiers ne peuvent pas être chargés simplement sur ces appareils. Ce document se concentre sur les PC Windows 8.

## <a name="consuming-windows-runtime-apis"></a>Utilisation des API Windows Runtime

Dans un certain nombre de scénarios décrits dans les sections suivantes, votre application de bureau de l’interface utilisateur du profileur doit utiliser de nouvelles API Windows Runtime. Vous pouvez consulter la documentation pour savoir quels Windows Runtime API peuvent être utilisées à partir d’applications de bureau et si leur comportement est différent lorsqu’ils sont appelés à partir d’applications de bureau et d’applications du Windows Store.

Si votre interface utilisateur du profileur est écrite en code managé, vous devrez effectuer quelques étapes pour faciliter l’utilisation de ces Windows Runtime API. Pour plus d’informations, consultez l’article [applications et Windows Runtime de bureau gérés](https://docs.microsoft.com/previous-versions/windows/apps/jj856306(v=win.10)) .

## <a name="loading-the-profiler-dll"></a>Chargement de la DLL du profileur

Cette section décrit comment votre interface utilisateur du profileur provoque le chargement de votre DLL du profileur par l’application du Windows Store. Le code abordé dans cette section appartient à votre application de bureau de l’interface utilisateur du profileur. par conséquent, vous devez utiliser des API Windows qui sont sécurisées pour les applications de bureau, mais qui ne sont pas nécessairement sécurisées pour les applications du Windows Store.

L’interface utilisateur de votre profileur peut provoquer le chargement de la DLL de votre profileur dans l’espace de processus de l’application de deux manières :

- Au démarrage de l’application, tel qu’il est contrôlé par les variables d’environnement.

- En joignant à l’application une fois le démarrage terminé, en appelant la méthode [ICLRProfiling :: AttachProfiler](iclrprofiling-attachprofiler-method.md) .

L’un de vos premiers obstacles consistera à obtenir le chargement et le chargement de la DLL de votre profileur pour qu’il fonctionne correctement avec les applications du Windows Store. Les deux formes de chargement partagent des considérations spéciales en commun, commençons par les deux.

### <a name="common-considerations-for-startup-and-attach-loads"></a>Considérations courantes relatives aux chargements de démarrage et d’attachement

**Signature de votre DLL de profileur**

Lorsque Windows tente de charger votre DLL du profileur, il vérifie que la DLL du profileur est correctement signée. Si ce n’est pas le cas, le chargement échoue par défaut. Il existe deux façons d'effectuer cette opération :

- Vérifiez que la DLL du profileur est signée.

- Indiquez à votre utilisateur qu’il doit installer une licence de développeur sur son ordinateur Windows 8 avant d’utiliser votre outil. Vous pouvez effectuer cette opération automatiquement à partir de Visual Studio ou manuellement à partir d’une invite de commandes. Pour plus d’informations, consultez [obtenir une licence de développeur](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).

**Autorisations du système de fichiers**

L’application du Windows Store doit avoir l’autorisation de charger et d’exécuter votre DLL du profileur à partir de l’emplacement du système de fichiers dans lequel elle residesBy par défaut, l’application du Windows Store ne dispose pas de cette autorisation sur la plupart des répertoires, et toute tentative d’échec de chargement de votre DLL du profileur génère une entrée dans le journal des événements des applications Windows :

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

En règle générale, les applications du Windows Store sont uniquement autorisées à accéder à un ensemble limité d’emplacements sur le disque. Chaque application du Windows Store peut accéder à ses propres dossiers de données d’application, ainsi qu’à quelques autres zones du système de fichiers pour lesquelles toutes les applications du Windows Store bénéficient d’un accès. Il est préférable d’installer votre DLL du profileur et ses dépendances dans des fichiers programme ou des fichiers programme (x86), car toutes les applications du Windows Store disposent d’autorisations de lecture et d’exécution par défaut.

### <a name="startup-load"></a>Chargement de démarrage

En général, dans une application de bureau, l’interface utilisateur de votre profileur demande une charge de démarrage de votre DLL du profileur en initialisant un bloc d’environnement qui contient les variables d’environnement de l’API de profilage CLR requises (c’est-à-dire,, `COR_PROFILER` `COR_ENABLE_PROFILING` et `COR_PROFILER_PATH` ), puis en créant un nouveau processus avec ce bloc d’environnement. Il en va de même pour les applications du Windows Store, mais les mécanismes sont différents.

**Ne pas exécuter avec élévation de privilèges**

Si le processus A tente de générer le processus d’application du Windows Store B, le processus A doit être exécuté au niveau d’intégrité moyen, et non à un niveau d’intégrité élevé (c’est-à-dire, pas élevé). Cela signifie que l’interface utilisateur de votre profileur doit s’exécuter au niveau d’intégrité moyen, ou générer un autre processus de bureau au niveau d’intégrité moyen pour prendre en charge le lancement de l’application du Windows Store.

**Choix d’une application du Windows Store pour le profilage**

Tout d’abord, vous souhaiterez demander à votre profil utilisateur l’application Windows Store à lancer. Pour les applications de bureau, peut-être affiche-t-il une boîte de dialogue de recherche de fichiers et l’utilisateur trouve et sélectionne un fichier. exe. Toutefois, les applications du Windows Store sont différentes et l’utilisation d’une boîte de dialogue de navigation n’a aucun sens. Au lieu de cela, il est préférable d’afficher une liste d’applications du Windows Store installées pour que cet utilisateur sélectionne.

Vous pouvez utiliser la <xref:Windows.Management.Deployment.PackageManager> classe pour générer cette liste. `PackageManager`est une classe Windows Runtime qui est disponible pour les applications de bureau, et en fait, elle est *uniquement* disponible pour les applications de bureau.

L’exemple de code suivant issu d’une interface utilisateur de profileur hypothétique écrite en tant qu’application de bureau en C# utilise `PackageManager` pour générer une liste d’applications Windows :

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**Spécification du bloc d’environnement personnalisé**

Une nouvelle interface COM, [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), vous permet de personnaliser le comportement d’exécution d’une application du Windows Store pour faciliter certaines formes de Diagnostics. L’une de ses méthodes, [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), vous permet de passer un bloc d’environnement à l’application du Windows Store lors de son lancement, ainsi que d’autres effets utiles tels que la désactivation de la suspension automatique des processus. Le bloc environnement est important car vous devez spécifier les variables d’environnement ( `COR_PROFILER` , `COR_ENABLE_PROFILING` et `COR_PROFILER_PATH)` ) utilisées par le CLR pour charger votre dll du profileur.

Prenez l'exemple de l'extrait de code suivant :

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

Voici quelques éléments que vous devez obtenir :

- `packageFullName`peut être déterminée lors de l’itération au sein des packages et de la saisie `package.Id.FullName` .

- `debuggerCommandLine`est un peu plus intéressant. Pour passer le bloc d’environnement personnalisé à l’application du Windows Store, vous devez écrire votre propre débogueur factice simpliste. Windows génère l’application Windows Store en suspens, puis attache votre débogueur en lançant votre débogueur avec une ligne de commande comme dans cet exemple :

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     Lorsque `-p 1336` signifie que l’application Windows Store a l’ID de processus 1336 et `-tid 1424` que l’ID de thread 1424 est le thread qui est suspendu. Votre débogueur factice analyse le ThreadID à partir de la ligne de commande, reprend ce thread, puis s’arrête.

     Voici quelques exemples de code C++ pour effectuer cette opération (veillez à ajouter la vérification des erreurs !) :

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

     Vous devez déployer ce débogueur factice dans le cadre de l’installation de l’outil de diagnostic, puis spécifier le chemin d’accès à ce débogueur dans le `debuggerCommandLine` paramètre.

**Lancement de l’application du Windows Store**

Le moment de lancer l’application du Windows Store est enfin arrivé. Si vous avez déjà essayé de le faire vous-même, vous avez peut-être remarqué que [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) n’est pas la manière dont vous créez un processus d’application Windows Store. Au lieu de cela, vous devez utiliser la méthode [IApplicationActivationManager :: ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) . Pour ce faire, vous devez récupérer l’ID de modèle d’utilisateur de l’application du Windows Store que vous lancez. Cela signifie que vous devrez effectuer un petit examen du manifeste.

Lors de l’itération sur vos packages (voir « choix d’une application du Windows Store à profiler » dans la section [chargement de démarrage](#startup-load) ), vous pouvez extraire l’ensemble des applications contenues dans le manifeste du package actuel :

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

Oui, un package peut avoir plusieurs applications et chaque application possède son propre ID de modèle d’utilisateur d’application. Par conséquent, vous souhaiterez demander à votre utilisateur l’application à profiler et récupérer l’ID du modèle utilisateur de l’application à partir de cette application particulière :

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

Enfin, vous disposez maintenant de ce dont vous avez besoin pour lancer l’application du Windows Store :

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**N’oubliez pas d’appeler DisableDebugging**

Quand vous avez appelé [IPackageDebugSettings :: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), vous avez effectué une promesse de nettoyage après vous-même en appelant la méthode [IPackageDebugSettings ::D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) . Veillez donc à le faire lorsque la session de profilage est terminée.

### <a name="attach-load"></a>Joindre la charge

Quand votre interface utilisateur du profileur souhaite attacher sa DLL du profileur à une application qui a déjà démarré, elle utilise [ICLRProfiling :: AttachProfiler](iclrprofiling-attachprofiler-method.md). Il en va de même pour les applications du Windows Store. Mais en plus des considérations courantes répertoriées précédemment, vérifiez que l’application cible du Windows Store n’est pas suspendue.

**EnableDebugging**

Comme pour le chargement de démarrage, appelez la méthode [IPackageDebugSettings :: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) . Vous n’en avez pas besoin pour transmettre un bloc d’environnement, mais vous avez besoin de l’une de ses autres fonctionnalités : désactivation de la suspension de processus automatique. Dans le cas contraire, quand votre interface utilisateur du profileur appelle [AttachProfiler](iclrprofiling-attachprofiler-method.md), l’application du Windows Store cible peut être suspendue. En fait, cela est probablement le cas si l’utilisateur interagit à présent avec votre interface utilisateur du profileur et que l’application du Windows Store n’est pas active sur les écrans de l’utilisateur. Et si l’application du Windows Store est suspendue, elle ne peut pas répondre aux signaux que le CLR lui envoie pour attacher votre DLL de profileur.

Vous devez donc effectuer une opération similaire à ce qui suit :

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

Il s’agit du même appel que celui que vous faites pour le cas de chargement de démarrage, sauf que vous ne spécifiez pas de ligne de commande du débogueur ou d’un bloc d’environnement.

**DisableDebugging**

Comme toujours, n’oubliez pas d’appeler [IPackageDebugSettings ::D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) lorsque votre session de profilage est terminée.

## <a name="running-inside-the-windows-store-app"></a>Exécution à l’intérieur de l’application du Windows Store

Ainsi, l’application du Windows Store a finalement chargé la DLL du profileur. À présent, votre DLL de profileur doit être apprise dans les différentes règles requises par les applications du Windows Store, notamment les API qui sont autorisées et comment s’exécuter avec des autorisations réduites.

### <a name="stick-to-the-windows-store-app-apis"></a>Respecter les API d’application du Windows Store

Lorsque vous parcourez l’API Windows, vous remarquerez que chaque API est documentée comme s’appliquant aux applications de bureau, aux applications du Windows Store ou aux deux. Par exemple, la section **spécifications** de la documentation pour la fonction [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) indique que la fonction s’applique uniquement aux applications de bureau. En revanche, la fonction [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) est disponible pour les applications de bureau et les applications du Windows Store.

Lorsque vous développez votre DLL du profileur, traitez-le comme s’il s’agissait d’une application du Windows Store et utilisez uniquement les API documentées comme disponibles pour les applications du Windows Store. Analysez vos dépendances (par exemple, vous pouvez exécuter `link /dump /imports` votre dll du profileur pour effectuer l’audit), puis recherchez dans les documents les dépendances qui sont correctes et celles qui ne le sont pas. Dans la plupart des cas, vous pouvez corriger vos violations en les remplaçant simplement par une forme plus récente de l’API qui est documentée comme sécurisée (par exemple, en remplaçant [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) par [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).

Vous remarquerez peut-être que votre DLL du profileur appelle des API qui s’appliquent uniquement aux applications de bureau, mais qu’elles semblent fonctionner même lorsque votre DLL du profileur est chargée dans une application du Windows Store. N’oubliez pas qu’il est risqué d’utiliser n’importe quelle API non documentée pour une utilisation avec les applications du Windows Store dans votre DLL du profileur quand elle est chargée dans un processus d’application du Windows Store :

- Il n’est pas garanti que ces API fonctionnent quand elles sont appelées dans le contexte unique dans lequel les applications du Windows Store s’exécutent.

- Ces API peuvent ne pas fonctionner de manière cohérente quand elles sont appelées à partir de différents processus d’application du Windows Store.

- Ces API peuvent sembler fonctionner correctement à partir d’applications du Windows Store dans la version actuelle de Windows, mais elles peuvent s’arrêter ou être désactivées dans les versions ultérieures de Windows.

Le meilleur Conseil consiste à résoudre toutes vos violations et à éviter le risque.

Vous constaterez peut-être que vous ne pouvez absolument pas faire sans une API particulière et que vous ne trouvez pas de remplacement approprié pour les applications du Windows Store. Dans ce cas, au minimum :

- Testez, testez et testez les heures d’été de votre utilisation de cette API.

- Sachez que l’API peut soudainement s’arrêter ou disparaître si elle est appelée à partir d’applications du Windows Store dans les futures versions de Windows. Cela n’est pas considéré comme un problème de compatibilité de Microsoft et la prise en charge de l’utilisation de celle-ci n’est pas une priorité.

### <a name="reduced-permissions"></a>Autorisations réduites

En dehors du cadre de cette rubrique, vous pouvez répertorier toutes les façons dont les autorisations des applications du Windows Store diffèrent des applications de bureau. Toutefois, le comportement est certainement différent chaque fois que votre DLL de profileur (lorsqu’elle est chargée dans une application du Windows Store par rapport à une application de bureau) tente d’accéder à des ressources. Le système de fichiers est l’exemple le plus courant. Il existe cependant quelques emplacements sur le disque auxquels une application du Windows Store donnée est autorisée à accéder (consultez [accès aux fichiers et autorisations (Windows Runtime Apps](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))), et votre dll du profileur est soumise aux mêmes restrictions. Testez votre code minutieusement.

### <a name="inter-process-communication"></a>Communication entre processus

Comme indiqué dans le diagramme au début de ce document, votre DLL du profileur (chargée dans l’espace de processus de l’application du Windows Store) devra probablement communiquer avec votre interface utilisateur du profileur (exécutée dans un espace de processus d’application de bureau distinct) par le biais de votre propre canal de communication interprocessus (IPC) personnalisé. L’interface utilisateur du profileur envoie des signaux à la DLL du profileur pour modifier son comportement, et la DLL du profileur renvoie les données de l’application du Windows Store analysée à l’interface utilisateur du profileur pour le poster et les afficher à l’utilisateur du profileur.

La plupart des profileurs doivent fonctionner de cette manière, mais vos choix pour les mécanismes IPC sont plus limités lorsque votre DLL du profileur est chargée dans une application du Windows Store. Par exemple, les canaux nommés ne faisant pas partie du kit de développement logiciel (SDK) d’application du Windows Store, vous ne pouvez pas les utiliser.

Mais bien sûr, les fichiers se trouvent toujours dans, bien que de manière plus limitée. Les événements sont également disponibles.

**Communication via des fichiers**

La plupart de vos données sont susceptibles de passer entre la DLL du profileur et l’interface utilisateur du profileur via des fichiers. La clé consiste à choisir un emplacement de fichier qui, à la fois, la DLL du profileur (dans le contexte d’une application du Windows Store) et l’interface utilisateur du profileur ont accès en lecture et en écriture à. Par exemple, le chemin d’accès au dossier temporaire est un emplacement accessible à la fois à la DLL du profileur et à l’interface utilisateur du profileur, mais aucun autre package d’application du Windows Store ne peut accéder (protégeant ainsi toutes les informations que vous consignez à partir d’autres packages d’applications du Windows Store).

L’interface utilisateur du profileur et la DLL du profileur peuvent déterminer ce chemin d’accès indépendamment. L’interface utilisateur de votre profileur, lorsqu’elle itère au sein de tous les packages installés pour l’utilisateur actuel (Voir l’exemple de code précédent), obtient l’accès à la `PackageId` classe, à partir de laquelle le chemin d’accès au dossier temporaire peut être dérivé avec du code similaire à cet extrait de code. (Comme toujours, la vérification des erreurs est omise par souci de concision.)

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

Pendant ce temps, votre DLL de profileur peut faire la même chose, bien qu’il puisse plus facilement obtenir la classe à l' <xref:Windows.Storage.ApplicationData> aide de la propriété [ApplicationData. Current](xref:Windows.Storage.ApplicationData.Current%2A) .

**Communication via des événements**

Si vous souhaitez une sémantique de signalisation simple entre votre interface utilisateur du profileur et la DLL du profileur, vous pouvez utiliser des événements dans les applications du Windows Store ainsi que les applications de bureau.

À partir de votre DLL du profileur, vous pouvez simplement appeler la fonction [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) pour créer un événement nommé portant le nom de votre choix. Par exemple :

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

`<acSid>`est le SID AppContainer de l’application Windows Store. Une section précédente de cette rubrique a montré comment effectuer une itération sur les packages installés pour l’utilisateur actuel. À partir de cet exemple de code, vous pouvez obtenir packageId. Et à partir du packageId, vous pouvez obtenir le `<acSid>` Code avec un code similaire à ce qui suit :

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>Aucune notification d’arrêt

En cas d’exécution dans une application du Windows Store, votre DLL du profileur ne doit pas s’appuyer sur [ICorProfilerCallback :: Shutdown](icorprofilercallback-shutdown-method.md) ou même [DllMain](/windows/desktop/Dlls/dllmain) (avec) qui est `DLL_PROCESS_DETACH` appelé pour informer votre dll du profileur que l’application du Windows Store est en cours de fermeture. En fait, vous devez vous attendre à ce qu’elles ne soient jamais appelées. Historiquement, de nombreuses dll du profileur ont utilisé ces notifications comme des emplacements pratiques pour vider les caches sur le disque, fermer les fichiers, envoyer des notifications à l’interface utilisateur du profileur, etc. Mais maintenant, votre DLL de profileur doit être organisée un peu différemment.

Votre DLL du profileur doit enregistrer les informations au fur et à mesure. Pour des raisons de performances, vous souhaiterez peut-être traiter les informations en mémoire et les vider sur le disque à mesure que la taille du lot dépasse un certain seuil. Mais supposons que toutes les informations qui n’ont pas encore été vidées sur le disque peuvent être perdues. Cela signifie que vous pouvez choisir votre seuil avec prudence et que votre interface utilisateur du profileur doit être renforcée pour traiter les informations incomplètes écrites par la DLL du profileur.

## <a name="windows-runtime-metadata-files"></a>Windows Runtime les fichiers de métadonnées

Ce document ne décrit pas en détail les fichiers de métadonnées de Windows Runtime (WinMD). Cette section est limitée à la façon dont l’API de profilage CLR réagit lorsque des fichiers WinMD sont chargés par l’application du Windows Store que votre DLL du profileur analyse.

### <a name="managed-and-non-managed-winmds"></a>Winmd géré et non géré

Si un développeur utilise Visual Studio pour créer un projet de composant Windows Runtime, une build de ce projet produit un fichier WinMD qui décrit les métadonnées (les descriptions de type des classes, les interfaces, etc.) créées par le développeur. Si ce projet est un projet de langage managé écrit en C# ou Visual Basic, ce même fichier WinMD contient également l’implémentation de ces types (ce qui signifie qu’il contient tout le langage intermédiaire compilé à partir du code source du développeur). Ces fichiers sont appelés fichiers WinMD gérés. Ils sont intéressants en ce sens qu’ils contiennent à la fois les métadonnées Windows Runtime et l’implémentation sous-jacente.

En revanche, si un développeur crée un projet de composant Windows Runtime pour C++, une build de ce projet produit un fichier WinMD qui contient uniquement des métadonnées, et l’implémentation est compilée dans une DLL native distincte. De même, les fichiers WinMD fournis dans le SDK Windows contiennent uniquement des métadonnées, l’implémentation étant compilée dans des DLL natives distinctes fournies dans le cadre de Windows.

Les informations ci-dessous s’appliquent aux Winmd gérés, qui contiennent des métadonnées et de l’implémentation, et à des Winmd non managés qui contiennent uniquement des métadonnées.

### <a name="winmd-files-look-like-clr-modules"></a>Les fichiers WinMD ressemblent à des modules CLR

En ce qui concerne le CLR, tous les fichiers WinMD sont des modules. L’API de profilage CLR indique donc à votre DLL de profileur lorsque les fichiers WinMD sont chargés et ce que leurs ModuleID sont, de la même façon que pour les autres modules managés.

Votre DLL du profileur peut faire la distinction entre les fichiers WinMD et d’autres modules en appelant la méthode [ICorProfilerInfo3 :: GetModuleInfo2,](icorprofilerinfo3-getmoduleinfo2-method.md) et en inspectant le `pdwModuleFlags` paramètre de sortie de l’indicateur [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) . (Il est défini si et uniquement si le ModuleID représente un WinMD.)

### <a name="reading-metadata-from-winmds"></a>Lecture des métadonnées à partir de Winmd

Les fichiers WinMD, comme les modules standard, contiennent des métadonnées qui peuvent être lues via les [API de métadonnées](../metadata/index.md). Toutefois, le CLR mappe Windows Runtime types aux types de .NET Framework lorsqu’il lit les fichiers WinMD afin que les développeurs qui programment dans du code managé et consomment le fichier WinMD peuvent avoir une expérience de programmation plus naturelle. Pour obtenir des exemples de ces mappages, consultez [.NET Framework la prise en charge des applications et des Windows Runtime du Windows Store](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).

Par conséquent, quelle vue votre profileur obtiendra-t-il lorsqu’il utilise les API de métadonnées : la vue brute Windows Runtime ou la vue de .NET Framework mappée ?  Réponse : c’est à vous de faire.

Quand vous appelez la méthode [ICorProfilerInfo :: GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) sur un WinMD pour obtenir une interface de métadonnées, telle que [IMetaDataImport](../metadata/imetadataimport-interface.md), vous pouvez choisir de définir [ofNoTransform](../metadata/coropenflags-enumeration.md) dans le `dwOpenFlags` paramètre pour désactiver ce mappage. Dans le cas contraire, le mappage est activé par défaut. En règle générale, un profileur garde le mappage activé, afin que les chaînes obtenues par la DLL du profileur à partir des métadonnées WinMD (par exemple, les noms des types) semblent familières et naturelles pour l’utilisateur du profileur.

### <a name="modifying-metadata-from-winmds"></a>Modification des métadonnées à partir de Winmd

La modification des métadonnées dans Winmd n’est pas prise en charge. Si vous appelez la méthode [ICorProfilerInfo :: GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) pour un fichier WinMD et spécifiez [ofWrite](../metadata/coropenflags-enumeration.md) dans le `dwOpenFlags` paramètre ou demandez une interface de métadonnées accessible en écriture comme [IMetaDataEmit](../metadata/imetadataemit-interface.md), [GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) échouera. Cela revêt une importance particulière pour les profileurs de réécriture de l’IL, qui doivent modifier les métadonnées pour prendre en charge leur instrumentation (par exemple, pour ajouter AssemblyRefs ou de nouvelles méthodes). Par conséquent, vous devez rechercher d’abord [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) (comme indiqué dans la section précédente) et vous abstenir de demander des interfaces de métadonnées accessibles en écriture sur de tels modules.

### <a name="resolving-assembly-references-with-winmds"></a>Résolution des références d’assembly avec Winmd

De nombreux profileurs doivent résoudre les références de métadonnées manuellement pour faciliter l’instrumentation ou l’inspection de type. De tels profileurs doivent être conscients de la façon dont le CLR résout les références d’assembly qui pointent vers Winmd, car ces références sont résolues de façon complètement différente des références d’assembly standard.

## <a name="memory-profilers"></a>Profileurs de mémoire

Le garbage collector et le tas managé ne sont pas fondamentalement différents dans une application du Windows Store et dans une application de bureau. Toutefois, il existe quelques différences subtiles que les auteurs du profileur doivent connaître.

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC, crée un thread managé

Lors du profilage de la mémoire, la DLL de votre profileur crée généralement un thread distinct à partir duquel appeler la méthode de [méthode ForceGC,](icorprofilerinfo-forcegc-method.md) . Ce n’est rien de nouveau. Mais ce qui peut être surprenant, c’est que l’acte d’effectuer un garbage collection dans une application du Windows Store peut transformer votre thread en thread managé (par exemple, un objet de profilage de l’API de profilage sera créé pour ce thread).

Pour comprendre les conséquences de cette opération, il est important de comprendre les différences entre les appels synchrones et asynchrones, comme défini par l’API de profilage CLR. Notez que cela est très différent du concept des appels asynchrones dans les applications du Windows Store. Pour plus d’informations, consultez le billet de blog pour obtenir des [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) .

Le point pertinent est que les appels effectués sur les threads créés par votre profileur sont toujours considérés comme synchrones, même si ces appels sont effectués à partir de l’extérieur d’une implémentation de l’une des méthodes [ICorProfilerCallback](icorprofilercallback-interface.md) de votre dll de profileur. Au moins, qui était le cas. Maintenant que le CLR a converti le thread de votre profileur en thread managé en raison de votre appel à la [méthode ForceGC,](icorprofilerinfo-forcegc-method.md), ce thread n’est plus considéré comme le thread de votre profileur. Par conséquent, le CLR applique une définition plus stricte de ce qui se qualifie comme synchrone pour ce thread, à savoir qu’un appel doit provenir de l’intérieur de l’une des méthodes [ICorProfilerCallback](icorprofilercallback-interface.md) de votre dll de profileur pour qualifier comme synchrone.

Qu’est-ce que cela signifie dans la pratique ? La plupart des méthodes [ICorProfilerInfo](icorprofilerinfo-interface.md) ne peuvent être appelées en toute sécurité que de façon synchrone et échouent immédiatement dans le cas contraire. Par conséquent, si votre DLL de profileur réutilise votre thread de [méthode ForceGC,](icorprofilerinfo-forcegc-method.md) pour d’autres appels généralement effectués sur des threads créés par le profileur (par exemple, à [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [requestrejit,](icorprofilerinfo4-requestrejit-method.md)ou [requestrevert,](icorprofilerinfo4-requestrevert-method.md)), vous allez rencontrer des problèmes. Même une fonction sécurisée asynchrone telle que [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) a des règles spéciales quand elle est appelée à partir de threads managés. (Consultez le billet de blog parcours de la [pile : principes de base et au-delà](https://docs.microsoft.com/archive/blogs/davbr/profiler-stack-walking-basics-and-beyond) pour plus d’informations.)

Par conséquent, nous vous recommandons d’utiliser n’importe quel thread créé par votre DLL de profileur pour appeler la [méthode ForceGC,](icorprofilerinfo-forcegc-method.md) *uniquement* pour le déclenchement des catalogues globaux et la réponse aux rappels gc. Elle ne doit pas appeler l’API de profilage pour effectuer d’autres tâches telles que l’échantillonnage de pile ou le détachement.

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

À compter de la .NET Framework 4,5, il existe un nouveau rappel GC, [conditionalweaktableelementreferences,](icorprofilercallback5-conditionalweaktableelementreferences-method.md), qui donne au profileur des informations plus complètes sur les *Handles dépendants*. Ces handles ajoutent efficacement une référence d’un objet source à un objet cible dans le cadre de la gestion de la durée de vie du GC. Les handles dépendants ne sont pas nouveaux, et les développeurs qui programment dans du code managé ont été en mesure de créer leurs propres Handles dépendants à l’aide de la <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> classe avant Windows 8 et le .NET Framework 4,5.

Toutefois, les applications du Windows Store XAML managées utilisent désormais intensivement des handles dépendants. En particulier, le CLR les utilise pour faciliter la gestion des cycles de référence entre les objets managés et les objets Windows Runtime non managés. Cela signifie qu’il est plus important que jamais pour les profileurs de mémoire d’être informés de ces handles dépendants afin qu’ils puissent être visualisés avec le reste des bords dans le graphique du tas. Votre DLL du profileur doit utiliser [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md)et [conditionalweaktableelementreferences,](icorprofilercallback5-conditionalweaktableelementreferences-method.md) ensemble pour constituer une vue complète du graphique du tas.

## <a name="conclusion"></a>Conclusion

Il est possible d’utiliser l’API de profilage CLR pour analyser le code managé qui s’exécute dans les applications du Windows Store. En fait, vous pouvez prendre un profileur existant que vous développez et apporter des modifications spécifiques afin qu’il puisse cibler les applications du Windows Store. Votre interface utilisateur du profileur doit utiliser les nouvelles API pour activer l’application du Windows Store en mode débogage. Assurez-vous que votre DLL du profileur consomme uniquement les API applicables aux applications du Windows Store. Le mécanisme de communication entre votre DLL du profileur et l’interface utilisateur du profileur doit être écrit avec les restrictions de l’API d’application du Windows Store à l’esprit et avec la reconnaissance des autorisations restreintes en place pour les applications du Windows Store. Votre DLL du profileur doit savoir comment le CLR traite les Winmd et comment le comportement du garbage collector est différent en ce qui concerne les threads managés.

## <a name="resources"></a>Ressources

**Le Common Language Runtime**

- [Profilage (référence des API non managées)](index.md)

- [Métadonnées (informations de référence sur les API non managées)](../metadata/index.md)

**L’interaction du CLR avec le Windows Runtime**

- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Applications du Windows Store**

- [Accès aux fichiers et autorisations (applications Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [Obtenir une licence de développeur](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [Interface IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
