---
title: Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)
description: Utilisez Fuslogvw.exe, la visionneuse du journal de liaison d’assembly. Cette visionneuse affiche les détails de la liaison d’assembly, qui permettent de diagnostiquer la raison pour laquelle .NET ne trouve pas d’assembly au moment de l’exécution.
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: 949f9cf98d5eb4e100be9837be120038f085cc40
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167125"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)

La Visionneuse du journal de liaison d’assembly affiche des détails sur les liaisons d’assemblys. Ces informations vous permettent d'identifier les raisons pour lesquelles le .NET Framework ne parvient pas à trouver un assembly au moment de l'exécution. Ces échecs résultent généralement d'un assembly déployé au mauvais emplacement, d'une image native qui n'est plus valide ou d'une incompatibilité entre les numéros de version ou les cultures. L'échec de la localisation d'un assembly par le Common Language Runtime s'affiche d'ordinaire sous la forme de <xref:System.TypeLoadException> dans votre application.

> [!IMPORTANT]
> Vous devez exécuter fuslogvw.exe avec les droits d'administrateur.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7) avec des informations d’identification d’administrateur. Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez :

```console
fuslogvw
```

La visionneuse affiche une entrée pour chaque liaison d'assembly ayant échoué. Pour chaque échec, la visionneuse décrit l'application qui a lancé la liaison, l'assembly concerné par la liaison (y compris le nom, la version, la culture et la clé publique), ainsi que la date et l'heure de l'échec.

### <a name="to-change-the-log-location-view"></a>Pour modifier l'affichage de l'emplacement du journal

1. Activez la case d’option **Par défaut** pour afficher les échecs de liaison pour tous les types d’applications. Par défaut, les entrées de journal sont stockées dans des répertoires par utilisateur sur le disque dans le cache WinInet.

2. Sélectionnez la case d’option **Personnalisé** pour afficher les échecs de liaison dans un répertoire personnalisé que vous spécifiez. Vous devez spécifier l’emplacement personnalisé dans lequel vous souhaitez que l’exécution stocke les journaux en affectant un nom de répertoire valide comme emplacement du journal personnalisé dans la boîte de dialogue **Paramètres du journal**. Ce répertoire doit être propre et contenir uniquement les fichiers générés par le runtime. S'il contient un exécutable qui génère un échec devant être enregistré dans le journal, ce dernier ne sera pas enregistré, car l'outil tente de créer un répertoire portant le même nom que l'exécutable. En outre, toute tentative d'exécution d'un exécutable à partir de l'emplacement du journal échouera.

    > [!NOTE]
    > L'emplacement des liaisons par défaut est préférable à l'emplacement des liaisons personnalisé. Le runtime stocke l’emplacement de liaison par défaut dans le cache WinInet et le nettoie par conséquent automatiquement. Si vous spécifiez un emplacement de liaison personnalisé, vous êtes chargé de le nettoyer.

### <a name="to-view-details-about-a-specific-failure"></a>Pour afficher des détails sur un échec spécifique

1. Sélectionnez le nom de l'application de l'entrée souhaitée dans la visionneuse.

2. Cliquez sur le bouton **Afficher le journal**. Vous pouvez également double-cliquer sur l'entrée sélectionnée.

    L'outil affiche les détails suivants sur l'échec de la liaison sélectionné :

    - La raison spécifique de l'échec de la liaison, telle que « fichier introuvable » ou « incompatibilité entre les versions »

    - Des informations sur l'application qui a lancé la liaison, parmi lesquelles son nom, le répertoire racine de l'application (AppBase) et le cas échéant, une description du chemin de recherche privé

    - L'identité de l'assembly recherché par l'outil

    - Une description des stratégies de version de l'application, de l'éditeur ou de l'administrateur qui ont été appliquées

    - Si l’assembly a été trouvé dans le [Global Assembly Cache](../app-domains/gac.md)

    - Une liste de toutes les URL recherchées

L'exemple d'entrée de journal suivant montre des informations détaillées sur l'échec d'une liaison d'assembly.

```output
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe
--- A detailed error log follows.

=== Pre-bind state information ===
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
 (Fully-specified)
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\
LOG: Initial PrivatePath = NULL
LOG: Dynamic Base = NULL
LOG: Cache Base = NULL
LOG: AppName = NULL
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
===

LOG: Processing DEVPATH.
LOG: DEVPATH is not set. Falling through to regular bind.
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.
LOG: All probing URLs attempted and failed.
```

### <a name="to-delete-a-single-entry-from-the-log"></a>Pour supprimer une seule entrée du journal

1. Sélectionnez une entrée dans la visionneuse.

2. Cliquez sur le bouton **Supprimer l’entrée**.

### <a name="to-delete-all-entries-from-the-log"></a>Pour supprimer toutes les entrées du journal

- Cliquez sur le bouton **Supprimer tout**.

### <a name="to-refresh-the-user-interface"></a>Pour actualiser l'interface utilisateur

- Cliquez sur le bouton **Actualiser** . La visionneuse ne détecte pas automatiquement les nouvelles entrées du journal pendant son exécution. Vous devez utiliser le bouton **Actualiser** pour les afficher.

### <a name="to-change-the-log-settings"></a>Pour modifier les paramètres du journal

- Cliquez sur le bouton **Paramètres** pour ouvrir la boîte de dialogue **Paramètres du journal**.

### <a name="to-view-the-about-dialog"></a>Pour afficher la boîte de dialogue À propos de

- Cliquez sur le bouton **À propos de**.

## <a name="binding-logs-for-native-images"></a>Liaison de journaux pour des Images natives

Par défaut, Fuslogvw.exe enregistre les demandes de liaison d'assembly normales. Vous pouvez également enregistrer des liaisons d’assemblys pour les images natives qui ont été créées à l’aide de l’outil [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).

#### <a name="to-log-assembly-binds-for-native-images"></a>Pour enregistrer des liaisons d'assemblys pour les images natives

- Dans le groupe **Catégories de journaux**, activez la case d’option **Images natives**.

Le journal suivant affiche un échec provoqué par une dépendance qui n'existait pas au moment de la création de l'image native pour l'application. Si les dépendances au moment de l'exécution diffèrent des dépendances lorsque Ngen.exe est exécuté, la liaison à une image native n'est pas autorisée.

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\App.exe
--- A detailed error log follows.

LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\App.exe.
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.
WRN: No matching native image found.
LOG: Bind to native image assembly did not succeed. Use IL image.
```

Le journal suivant montre un échec de liaison à une image native qui s'est produit parce que les paramètres de sécurité sur l'ordinateur au moment où l'application a été exécutée étaient différents des paramètres de sécurité en vigueur au moment où l'image native a été créée.

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***

The operation failed.
Bind result: hr = 0x80004005. Unspecified error

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\Application101622.exe
--- A detailed error log follows.

LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\Application101622.exe.
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Dependency evaluation succeeded.
LOG: Validation of dependencies succeeded.
LOG: Start loading all the dependencies into load context.
LOG: Loading of dependencies succeeded.
LOG: Bind to native image succeeded.
Native image has correct version information.
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.
Discarding native image.
```

## <a name="the-log-settings-dialog"></a>La boîte de dialogue Paramètres du journal

Vous pouvez utiliser la boîte de dialogue **Paramètres du journal** pour effectuer les actions suivantes.

#### <a name="to-disable-logging"></a>Pour désactiver l'enregistrement

- Activez la case d’option **Journal désactivé**.  Notez que cette option est sélectionnée par défaut.

#### <a name="to-log-assembly-binds-in-exceptions"></a>Pour enregistrer des liaisons d'assemblys dans les exceptions

- Activez la case d’option **Enregistrer dans le texte de l’exception**. Seules les informations les moins détaillées du journal de fusion sont stockées dans un texte d'exception. Pour afficher des informations complètes, utilisez un des autres paramètres.

  Consultez la Remarque importante relative aux assemblys chargés comme étant indépendants du domaine.

#### <a name="to-log-assembly-bind-failures"></a>Pour enregistrer des échecs de liaison d'assemblys

- Activez la case d’option **Enregistrer les échecs de liaison sur le disque**.

  Consultez la Remarque importante relative aux assemblys chargés comme étant indépendants du domaine.

#### <a name="to-log-all-assembly-binds"></a>Pour enregistrer toutes les liaisons d'assemblys

- Activez la case d’option **Enregistrer toutes les liaisons sur le disque**.

  Consultez la Remarque importante relative aux assemblys chargés comme étant indépendants du domaine.

> [!IMPORTANT]
> Lorsqu'un assembly est chargé comme étant indépendant du domaine, par exemple en définissant la propriété <xref:System.AppDomainSetup.LoaderOptimization%2A> à <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> ou <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, l'activation de l'enregistrement peut entraîner une fuite de mémoire dans certains cas. Cela peut arriver si une entrée de journal est faite lorsqu'un module indépendant du domaine est chargé dans un domaine d'application, et qu'ultérieurement le domaine d'application est déchargé. L'entrée de journal ne peut pas être diffusée avant la fin du processus. Certains débogueurs activent automatiquement l'enregistrement.

#### <a name="to-enable-a-custom-log-path"></a>Pour activer un chemin de journal personnalisé

1. Activez la case d’option **Activer le chemin de journal personnalisé**.

2. Entrez le chemin dans la zone de texte **Chemin du journal personnalisé**.

> [!NOTE]
> La [visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) utilise le cache Internet Explorer (IE) pour stocker son journal de liaison. En raison de la perte d’intégrité occasionnelle du cache IE, la [visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) peut parfois cesser d’afficher les nouveaux journaux de liaison dans la fenêtre d’affichage. Suite à cette perte d’intégrité, l’infrastructure de liaison .NET (fusion) ne peut pas écrire ou lire dans le journal de liaison. (Ce problème ne se produit pas si vous utilisez un chemin d’accès de journal personnalisé.)  Pour résoudre le problème et permettre à la fusion d’afficher à nouveau les journaux de liaison, effacez le cache IE en supprimant les fichiers Internet temporaires à partir de la boîte de dialogue Options Internet d’Internet Explorer.
>
> Si votre application non managée héberge le Common Language Runtime en implémentant les interfaces `IHostAssemblyManager` et `IHostAssemblyStore`, les entrées de journal ne peuvent pas être stockées dans le cache de WinInet.  Pour consulter les entrées de journal correspondant aux hôtes personnalisés qui implémentent ces interfaces, vous devez spécifier un autre chemin d'accès au journal.

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Pour activer la journalisation pour les applications qui s'exécutent dans le conteneur d'application Windows

1. Activez un chemin du journal personnalisé, comme décrit dans la procédure précédente. Par défaut, les applications qui s'exécutent dans le conteneur d'application Windows ont un accès limité au disque dur. Le répertoire spécifié dispose d'un accès en lecture/écriture pour toutes les applications du conteneur d'application.

2. Cochez la case **Activer la journalisation immersive**.

    > [!NOTE]
    > Cette zone est activée uniquement sur Windows 8 ou version ultérieure.

## <a name="see-also"></a>Voir aussi

- <xref:System.TypeLoadException>
- [outils](index.md)
- [Global Assembly Cache](../app-domains/gac.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
