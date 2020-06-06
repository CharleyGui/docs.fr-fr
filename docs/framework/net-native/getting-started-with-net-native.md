---
title: Prise en main de .NET Native
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
ms.openlocfilehash: 1c0c25ddf379c31a9c7b4437d36e7e0cbf1bb2f3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128408"
---
# <a name="getting-started-with-net-native"></a>Prise en main de .NET Native

Que vous écriviez une nouvelle application Windows pour Windows 10 ou que vous migriez une application du Windows Store existante, vous pouvez suivre le même ensemble de procédures. Pour créer une application .NET Native, procédez comme suit :

1. [Développez une application de la plateforme Windows universelle (UWP) qui cible Windows 10](#Step1), puis testez les versions Debug de votre application pour vous assurer qu’elle fonctionne correctement.

2. [Gérez l'utilisation de réflexion et de sérialisation supplémentaire](#Step2).

3. [Déployez et testez les builds de mise en production de votre application](#Step3).

4. [Résolvez manuellement les métadonnées manquantes](#Step4) et répétez l’[étape 3](#Step3) jusqu’à ce que tous les problèmes soient résolus.

> [!NOTE]
> Si vous migrez une application du Windows Store existante vers .NET Native, veillez à passer en revue [la rubrique migration de votre application du Windows Store vers .net Native](migrating-your-windows-store-app-to-net-native.md).

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Étape 1 : développer et tester les versions Debug de votre application UWP

Que vous développiez une nouvelle application ou que vous migriez une application existante, vous devez suivre la même procédure que pour n'importe quelle application Windows.

1. Créez un nouveau projet UWP dans Visual Studio à l’aide du modèle d’application Windows universelle pour Visual C# ou Visual Basic. Par défaut, toutes les applications UWP ciblent CoreCLR et leurs versions de mise en production sont compilées à l’aide de la chaîne de l’outil .NET Native.

2. Notez qu’il existe certains problèmes de compatibilité connus entre la compilation des projets d’application UWP avec la chaîne de l’outil .NET Native et sans elle. Pour plus d'informations, consultez le [guide de migration](migrating-your-windows-store-app-to-net-native.md) .

Vous pouvez maintenant écrire du code C# ou Visual Basic sur la surface d’exposition .NET Native qui s’exécute sur le système local (ou dans le simulateur).

> [!IMPORTANT]
> Quand vous développez votre application, notez toute utilisation de la sérialisation ou de la réflexion dans votre code.

Par défaut, les builds de débogage sont compilées juste-à-temps pour permettre un déploiement F5 rapide, tandis que les versions release sont compilées à l’aide de la technologie de précompilation .NET Native. Cela signifie que vous devez générer et tester les versions Debug de votre application pour vous assurer qu’elles fonctionnent normalement avant de les compiler avec la chaîne de l’outil .NET Native.

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Étape 2 : gérer l'utilisation d'une réflexion et d'une sérialisation supplémentaires

Un fichier de directives runtime, Default.rd.xml, est automatiquement ajouté à votre projet au moment de sa création. Si vous développez en C#, il se trouve dans le dossier **Propriétés** de votre projet. Si vous développez en Visual Basic, il se trouve dans le dossier **Mon projet** de votre projet.

> [!NOTE]
> Pour une vue d'ensemble du processus de compilation .NET Native apportant des informations générales sur la nécessité d'un fichier de directives de runtime, voir [.NET Native et compilation](net-native-and-compilation.md).

Le fichier de directives runtime permet de définir les métadonnées dont a besoin votre application au moment de l'exécution. Dans certains cas, la version par défaut du fichier peut convenir. Toutefois, un code qui s’appuie sur la sérialisation ou la réflexion peut nécessiter des entrées supplémentaires dans le fichier de directives runtime.

**Sérialisation**

Il existe deux catégories de sérialiseurs, et les deux peuvent nécessiter des entrées supplémentaires dans le fichier de directives runtime :

- Sérialiseurs non basés sur la réflexion. Les sérialiseurs qui se trouvent dans la bibliothèque de classes .NET Framework, tels que les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> , ne reposent pas sur la réflexion. Toutefois, ils nécessitent que du code soit généré en fonction de l'objet à sérialiser ou à désérialiser.  Pour plus d’informations, consultez la section « Sérialiseurs Microsoft » dans [Serialization and Metadata](serialization-and-metadata.md).

- Sérialiseurs tiers. Les bibliothèques de sérialisation tierces, dont la plus courante est le sérialiseur JSON Newtonsoft, sont généralement basées sur la réflexion et nécessitent des entrées dans le \* fichier. rd. xml pour prendre en charge la sérialisation et la désérialisation d’objets. Pour plus d’informations, consultez la section « Sérialiseurs tiers » dans [Serialization and Metadata](serialization-and-metadata.md).

**Méthodes basées sur la réflexion**

Dans certains cas, l'utilisation de la réflexion dans le code n'est pas évidente. Certains modèles de programmation ou API courants ne sont pas considérés comme faisant partie de l'API de réflexion, mais s'appuient sur la réflexion pour s'exécuter correctement. Cela comprend les méthodes d'instanciation de type et de construction de méthode suivantes :

- Méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType>

- Méthodes <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> et <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>

- Méthode <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType>

Pour plus d'informations, consultez [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).

> [!NOTE]
> Les noms de types utilisés dans les fichiers de directives runtime doivent être qualifiés complets. Par exemple, le fichier doit spécifier « System.String » au lieu de « String ».

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Étape 3 : déployer et tester les versions de mise en production de votre application

Une fois que vous avez mis à jour le fichier de directives runtime, vous pouvez régénérer et déployer les versions de mise en production de votre application. .NET Native fichiers binaires sont placés dans le sous-répertoire ILC. out du répertoire spécifié dans la zone de texte **chemin de sortie** de la génération de la boîte de dialogue **Propriétés** du projet, onglet **compiler** . les fichiers binaires qui ne figurent pas dans ce dossier n’ont pas été compilés avec .net native. Testez votre application minutieusement et testez tous les scénarios, y compris les scénarios d’erreur, sur chacune de ses plateformes cibles.

Si votre application ne fonctionne pas correctement (en particulier dans les cas où elle lève une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) ou [MissingInteropDataException](missinginteropdataexception-class-net-native.md) au moment de l’exécution), suivez les instructions de la section suivante, [Étape 4 : résoudre manuellement les métadonnées manquantes](#Step4). L'activation des exceptions de première chance peut vous aider à trouver ces bogues.

Une fois que vous avez testé et débogué les versions Debug de votre application et que vous êtes certain d’avoir éliminé les exceptions [MissingMetadataException](missingmetadataexception-class-net-native.md) et [MissingInteropDataException](missinginteropdataexception-class-net-native.md) , vous devez tester votre application en tant qu’application .net Native optimisée. Pour ce faire, dans la configuration du projet actif, remplacez **Débogage** par **Version finale**.

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a>Étape 4 : résoudre manuellement les métadonnées manquantes

La défaillance la plus courante que vous rencontrerez avec .NET Native que vous ne rencontrez pas sur le bureau est une exception Runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)ou [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . Dans certains cas, l'absence de métadonnées peut se manifester par un comportement imprévisible ou même se traduire par des erreurs d'application. Cette section explique comment vous pouvez déboguer et résoudre ces exceptions en ajoutant des directives au fichier de directives runtime. Pour plus d’informations sur le format des directives runtime, consultez le [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md). Après avoir ajouté les directives runtime, vous devez [déployer et tester votre application](#Step3) de nouveau et résoudre toute nouvelle exception [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)et  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) jusqu'à ce qu'aucune exception ne soit levée.

> [!TIP]
> Spécifiez les directives runtime à un niveau élevé pour que votre application tolère les modifications de code.  Nous vous recommandons d'ajouter les directives runtime aux niveaux de l'espace de noms et du type, plutôt qu'au niveau du membre. Notez qu'un compromis peut s'avérer nécessaire entre la résilience et les fichiers binaires volumineux dont la compilation prend plus de temps.

Quand vous traitez une exception liée à des métadonnées manquantes, prenez en compte les points suivants :

- Qu'est-ce que l'application essayait de faire avant l'exception ?

  - Par exemple, était-elle en train de lier, de sérialiser ou de désérialiser des données ou d'utiliser directement l'API de réflexion ?

- S'agit-il d'un cas isolé, ou pensez-vous que vous rencontrerez le même problème pour d'autres types ?

  - Par exemple, une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) est levée pendant la sérialisation d'un type dans le modèle objet de l'application.  Si vous connaissez d'autres types à sérialiser, vous pouvez ajouter des directives runtime pour ces types (ou pour leurs espaces de noms conteneurs, suivant la façon dont le code est organisé) en même temps.

- Pouvez-vous réécrire le code afin qu'il n'utilise pas la réflexion ?

  - Par exemple, le code utilise-t-il le mot clé `dynamic` quand vous connaissez le type attendu ?

  - Le code appelle-t-il une méthode basée sur la réflexion quand une meilleure solution est disponible ?

> [!NOTE]
> Pour plus d’informations sur la gestion des problèmes qui résultent des différences de réflexion et de la disponibilité des métadonnées dans les applications de bureau et les .NET Native, consultez [API qui reposent sur la réflexion](apis-that-rely-on-reflection.md).

Pour obtenir des exemples spécifiques de gestion des exceptions et d'autres problèmes qui se produisent quand vous testez votre application, consultez :

- [Exemple : Gestion des exceptions pendant la liaison de données](example-handling-exceptions-when-binding-data.md)

- [Exemple : Résolution des problèmes de programmation dynamique](example-troubleshooting-dynamic-programming.md)

- [Exceptions du runtime dans les applications natives .NET](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Installation et configuration de .NET Native](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))
- [Compilation et .NET natif](net-native-and-compilation.md)
- [Réflexion et .NET Native](reflection-and-net-native.md)
- [API qui s'appuient sur la réflexion](apis-that-rely-on-reflection.md)
- [Sérialisation et métadonnées](serialization-and-metadata.md)
- [Migration de votre application du Windows Store vers .NET Native](migrating-your-windows-store-app-to-net-native.md)
