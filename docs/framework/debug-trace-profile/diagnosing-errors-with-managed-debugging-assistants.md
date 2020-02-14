---
title: Diagnostic d'erreurs avec les Assistants Débogage managé
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
ms.openlocfilehash: 712fbbe9e0ad291385e8eef321c5e8a2fa092a5d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216554"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Diagnostiquer les erreurs avec les assistants débogage managés

Les Assistants Débogage managé sont des aides au débogage qui fonctionnent conjointement avec le Common Language Runtime (CLR) pour fournir des informations sur l'état d'exécution. Les Assistants génèrent des messages d'information sur les événements du runtime que vous ne pouvez pas intercepter en temps normal. Vous pouvez utiliser les Assistants Débogage managé pour isoler les bogues d'application difficiles à déceler qui se produisent pendant les phases de transition entre un code managé et un code non managé.

Vous pouvez [activer ou désactiver](#enable-and-disable-mdas) tous les Assistants Débogage managé en ajoutant une clé au registre Windows ou en définissant une variable d’environnement. Vous pouvez activer des Assistants Débogage managé spécifiques à l'aide de paramètres de configuration d'application. Vous pouvez définir des paramètres de configuration supplémentaires pour certains Assistants Débogage managé dans le fichier de configuration de l'application. Comme ces fichiers de configuration sont analysés au chargement du runtime, vous devez activer l'Assistant Débogage managé avant que l'application managée ne démarre. Vous ne pouvez pas l'activer pour les applications qui ont déjà démarré.

Le tableau suivant répertorie les MDA fournis avec l' .NET Framework :

|||
|-|-|
|[asynchronousThreadAbort](asynchronousthreadabort-mda.md)|[bindingFailure](bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](dirtycastandcalloninterface-mda.md)|[disconnectedContext](disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](failedqi-mda.md)|[fatalExecutionEngineError](fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](invalidapartmentstatechange-mda.md)|
|[invalidCERCall](invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](invalidgchandlecookie-mda.md)|[invalidIUnknown](invalidiunknown-mda.md)|
|[invalidMemberDeclaration](invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](invalidvariant-mda.md)|[jitCompilationStart](jitcompilationstart-mda.md)|
|[loaderLock](loaderlock-mda.md)|[loadFromContext](loadfromcontext-mda.md)|
|[marshalCleanupError](marshalcleanuperror-mda.md)|[marshaling](marshaling-mda.md)|
|[memberInfoCacheCreation](memberinfocachecreation-mda.md)|[moduloObjectHashcode](moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](noncomvisiblebaseclass-mda.md)|[notMarshalable](notmarshalable-mda.md)|
|[openGenericCERCall](opengenericcercall-mda.md)|[overlappedFreeError](overlappedfreeerror-mda.md)|
|[pInvokeLog](pinvokelog-mda.md)|[pInvokeStackImbalance](pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](raceonrcwcleanup-mda.md)|[reentrancy](reentrancy-mda.md)|
|[releaseHandleFailed](releasehandlefailed-mda.md)|[reportAvOnComRelease](reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](streamwriterbuffereddatalost-mda.md)|[virtualCERCall](virtualcercall-mda.md)|

Par défaut, le .NET Framework active une partie des Assistants Débogage managé pour tous les débogueurs managés. Vous pouvez afficher l’ensemble par défaut dans Visual Studio en choisissant **Windows** > les **paramètres d’exception** dans le menu **Déboguer** , puis en développant la liste **Assistants Débogage managé** .

![Fenêtre Paramètres d’exception dans Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Activer et désactiver les Assistants Débogage managé

Vous pouvez activer et désactiver les Assistants Débogage managé en utilisant une clé de Registre, une variable d'environnement et des paramètres de configuration d'application. Vous devez activer la clé de Registre ou la variable d'environnement pour utiliser les paramètres de configuration d'application.

> [!TIP]
> Au lieu de désactiver les MDA, vous pouvez empêcher Visual Studio d’afficher la boîte de dialogue Assistant Débogage managé chaque fois qu’une notification MDA est reçue. Pour ce faire, choisissez **Windows** > les paramètres d’exception dans le menu **Déboguer** , développez la liste **assistants débogage managés** , puis activez ou désactivez la case à cocher **arrêter la levée en cas** d' **exception** pour l’Assistant Débogage managé.

### <a name="registry-key"></a>Clé de Registre

Pour activer les MDA, ajoutez le **\\HKEY_LOCAL_MACHINE \Software\Microsoft.** Sous-clé NETFramework\MDA (type REG_SZ, valeur 1) dans le Registre Windows. Copiez l’exemple suivant dans un fichier texte nommé *MDAEnable. reg*. Ouvrez l’éditeur du Registre Windows (RegEdit. exe), puis, dans le menu **fichier** , choisissez **Importer**. Sélectionnez le fichier *MDAEnable. reg* pour activer les MDA sur cet ordinateur. La définition de la sous-clé sur la valeur de chaîne **1** (pas la valeur DWORD **1**) active la lecture des paramètres MDA à partir du fichier *applicationName. suffixe*. MDA. config. Par exemple, le fichier de configuration MDA pour le bloc-notes est nommé Notepad. exe. MDA. config.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Si l'ordinateur exécute une application 32 bits sur un système d'exploitation 64 bits, la clé MDA doit être définie comme suit :

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Pour plus d’informations, consultez [paramètres de configuration spécifiques](#application-specific-configuration-settings) à l’application. Le paramétrage du Registre peut être remplacé par la variable d'environnement COMPLUS_MDA. Pour plus d’informations, consultez [variable d’environnement](#environment-variable) .

Pour désactiver les MDA, définissez la sous-clé de l’Assistant Débogage managé sur **0** (zéro) à l’aide de l’éditeur du Registre Windows.

Par défaut, certains Assistants Débogage managé sont activés quand vous exécutez une application qui est attachée à un débogueur, même sans que la clé de Registre soit ajoutée. Vous pouvez désactiver ces assistants en exécutant le fichier *MDADisable. reg* comme décrit précédemment dans cette section.

### <a name="environment-variable"></a>Variable d’environnement

L'activation des Assistants Débogage managé peut également être contrôlée par la variable d'environnement COMPLUS_MDA, qui remplace la clé de Registre. La chaîne COMPLUS_MDA est une liste de noms d'Assistant Débogage managé ou d'autres chaînes de contrôle spéciales séparés par des points-virgules et sans distinction minuscules/majuscules. Démarrer sous un débogueur managé ou non managé active par défaut un ensemble d'Assistants Débogage managé. Pour ce faire, la valeur de la variable d'environnement ou de la clé de Registre doit être implicitement ajoutée au début de la liste délimitée par des points-virgules qui répertorie les Assistants Débogage managé activés par défaut sous les débogueurs. Les chaînes de contrôle spéciales sont les suivantes :

- `0` : désactive tous les Assistants Débogage managé.

- `1` : lit les paramètres d’Assistant Débogage managé dans le fichier *nom_application*.mda.config.

- `managedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable managé est démarré sous un débogueur.

- `unmanagedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable non managé est démarré sous un débogueur.

En cas de conflit de paramètres, les paramètres les plus récents remplacent les paramètres antérieurs :

- `COMPLUS_MDA=0` désactive tous les Assistants Débogage managé, y compris ceux qui sont implicitement activés sous un débogueur.

- `COMPLUS_MDA=gcUnmanagedToManaged` active `gcUnmanagedToManaged` outre tout Assistant Débogage managé implicitement activé sous un débogueur.

- `COMPLUS_MDA=0;gcUnmanagedToManaged` active `gcUnmanagedToManaged`, mais désactive tout Assistant Débogage managé implicitement activé sous un débogueur.

### <a name="application-specific-configuration-settings"></a>Paramètres de configuration spécifiques à l’application

Vous pouvez activer, désactiver et configurer certains Assistants séparément dans le fichier de configuration d'Assistant Débogage managé propre à l'application. Vous ne pouvez utiliser un fichier de configuration d'application pour configurer des Assistants Débogage managé que si la clé de Registre MDA ou la variable d'environnement COMPLUS_MDA est définie. En règle générale, le fichier de configuration d'application se trouve dans le même répertoire que le fichier exécutable (.exe) de l'application. Le nom de fichier prend la forme *applicationName*. MDA. config ; par exemple, Notepad. exe. MDA. config. Les assistants qui sont activés dans le fichier de configuration de l’application peuvent avoir des attributs ou des éléments conçus spécifiquement pour contrôler le comportement de l’Assistant.

L’exemple suivant montre comment activer et configurer le [marshaling](marshaling-mda.md):

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

L’Assistant Débogage managé `Marshaling` émet des informations sur le type managé qui est marshalé en un type non managé pour chaque transition de code managé vers un code non managé dans l’application. L’Assistant Débogage managé `Marshaling` peut également filtrer les noms des champs de méthode et de structure fournis dans les éléments enfants **methodFilter** et **fieldFilter** , respectivement.

L’exemple suivant montre comment activer plusieurs Assistants Débogage managé à l’aide de leurs paramètres par défaut :

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> Quand vous spécifiez plusieurs Assistants dans un fichier de configuration, vous devez les répertorier dans l'ordre alphabétique. Par exemple, pour activer les Assistants Débogage managé `virtualCERCall` et `invalidCERCall`, vous devez ajouter l'entrée `<invalidCERCall />` avant l'entrée `<virtualCERCall />`. Si vous n'indiquez pas les entrées dans l'ordre alphabétique, vous obtenez un message d'exception non gérée liée à un fichier de configuration non valide.

## <a name="mda-exceptions"></a>Exceptions MDA

Lorsqu’un Assistant Débogage managé est activé, il est actif même lorsque votre code ne s’exécute pas sous un débogueur. Si un événement d'Assistant Débogage managé est déclenché en l'absence de débogueur, le message de l'événement est présenté dans une boîte de dialogue d'exception non gérée, bien qu'il ne s'agisse pas d'une exception non gérée. Pour éviter l'affichage de la boîte de dialogue, supprimez les paramètres de désactivation de l'Assistant Débogage managé quand votre code ne s'exécute pas dans un environnement de débogage.

Lorsque votre code s’exécute dans l’environnement de développement intégré (IDE) de Visual Studio, vous pouvez éviter la boîte de dialogue d’exception qui s’affiche pour les événements MDA spécifiques. Pour ce faire, dans le menu **Déboguer** , choisissez **Windows** > **paramètres d’exception**. Dans la fenêtre Paramètres d’exception, développez la liste **Assistants Débogage managé** , puis désactivez la case à cocher **arrêter la levée en cas** d' **exception** pour chaque MDA. Vous pouvez également utiliser cette boîte de dialogue pour *activer* l’affichage des boîtes de dialogue d’exception d’Assistant Débogage managé.

## <a name="mda-output"></a>Sortie de l'Assistant Débogage managé

La sortie de l’Assistant Débogage managé est semblable à l’exemple suivant, qui montre la sortie de l’Assistant Débogage managé `PInvokeStackImbalance` :

**Un appel à la fonction PInvoke’MDATest ! MDATest. Program :: StdCall’a déséquilibré la pile. Cela est probablement dû au fait que la signature PInvoke managée ne correspond pas à la signature cible non managée. Vérifiez que la Convention d’appel et les paramètres de la signature PInvoke correspondent à la signature non managée cible.**

## <a name="see-also"></a>Voir aussi

- [Débogage, traçage et profilage](index.md)
