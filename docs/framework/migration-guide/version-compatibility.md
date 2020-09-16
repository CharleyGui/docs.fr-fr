---
title: Compatibilité des versions dans .NET Framework
description: En savoir plus sur la compatibilité entre les versions de .NET Framework, notamment la compatibilité descendante et l’exécution côte à côte.
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 824765e1f3ecfd1381f9c5f8b144b7b11aee8f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550382"
---
# <a name="version-compatibility"></a>Compatibilité des versions

La compatibilité descendante signifie qu'une application développée pour une version particulière d'une plateforme s'exécutera sur les versions ultérieures de cette plateforme. .NET Framework tente d’optimiser la compatibilité descendante : le code source écrit pour une version de .NET Framework doit compiler sur les versions ultérieures de .NET Framework, et les fichiers binaires qui s’exécutent sur une version de .NET Framework doivent se comporter de la même manière sur les versions ultérieures de .NET Framework.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a> Compatibilité des versions pour les applications

Par défaut, une application s’exécute sur la version de .NET Framework pour laquelle elle a été générée. Si cette version n’est pas présente et que le fichier de configuration de l’application ne définit pas les versions prises en charge, une erreur d’initialisation du .NET Framework peut se produire. Dans ce cas, la tentative d'exécution de l'application échouera.

Pour définir les versions spécifiques sur lesquelles votre application s’exécute, ajoutez un ou plusieurs [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) éléments au fichier de configuration de votre application. Chaque élément `<supportedRuntime>` fournit une liste des versions prises en charge de l'exécution ; la première spécifie la version préférée et la dernière correspond à la version la moins préférée.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Pour plus d’informations, consultez [Guide pratique pour configurer une application en vue de prendre en charge le .NET Framework 4 ou 4.x](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Compatibilité des versions pour les composants

Une application peut contrôler la version du .NET Framework sur laquelle elle s’exécute, mais un composant ne le peut pas. Les composants et bibliothèques de classes étant chargés dans le contexte d’une application particulière, ils s’exécutent automatiquement sur la version du .NET Framework sur lequel l’application s’exécute.

À cause de cette restriction, les garanties de compatibilité sont particulièrement importantes pour les composants. Depuis .NET Framework 4, vous pouvez spécifier le degré auquel un composant est supposé rester compatible entre plusieurs versions en appliquant l'attribut <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> à ce composant. Les outils peuvent utiliser cet attribut pour détecter des violations potentielles de la garantie de compatibilité dans les versions ultérieures d'un composant.

## <a name="backward-compatibility"></a>Compatibilité descendante

.NET Framework 4.5 et versions ultérieures présentent une compatibilité descendante avec les applications générées à l’aide des versions antérieures du .NET Framework. En d’autres termes, les applications et composants générés avec les versions antérieures du .NET Framework fonctionneront sur .NET Framework 4.5 et versions ultérieures sans être modifiés. Toutefois, par défaut, les applications sont exécutées sur la version du common language runtime pour laquelle elles ont été développées. Par conséquent, il est possible que vous deviez fournir un fichier de configuration pour permettre à votre application de s’exécuter sur .NET Framework 4.5 ou versions ultérieures. Pour plus d’informations, consultez la section [Compatibilité des versions pour les applications](#Apps) plus haut dans cet article.

Dans la pratique, cette compatibilité peut être arrêtée par des modifications apparemment sans importance du .NET Framework et des modifications des techniques de programmation. Par exemple, les améliorations des performances dans le .NET Framework 4.5 peuvent exposer une condition de concurrence critique qui ne se produit pas sur les versions antérieures. De la même façon, l’utilisation d’un chemin d’accès codé en dur aux assemblys .NET Framework, la comparaison d’égalité avec une version particulière du .NET Framework, et l’obtention de la valeur d’un champ privé à l’aide de la réflexion ne sont pas des pratiques à compatibilités descendante. De plus, chaque version du .NET Framework inclut des résolutions de bogue et des modifications relatives à la sécurité qui peuvent affecter la compatibilité de certains composants et applications.

Si votre application ou composant ne fonctionne pas comme prévu sur .NET Framework 4.5 (avec ses versions intermédiaires, NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8), utilisez les check-lists suivantes :

- Si votre application a été développée pour s’exécuter sur n’importe quelle version de la .NET Framework à partir de la .NET Framework 4,0, consultez [compatibilité des applications](application-compatibility.md) pour générer des listes de modifications entre votre version de .NET Framework ciblée et la version sur laquelle votre application s’exécute.

- S’il s’agit d’une application .NET Framework 3.5, consultez également [Problèmes de migration de .NET Framework 4](net-framework-4-migration-issues.md).

- S’il s’agit d’une application .NET Framework 2.0, consultez également [Modifications dans .NET Framework 3.5 SP1](/previous-versions/dotnet/articles/dd310284(v=msdn.10)).

- S’il s’agit d’une application .NET Framework 1.1, consultez également [Modifications dans .NET Framework 2.0](/previous-versions/aa570326(v=msdn.10)).

- Si vous recompilez le code source existant pour l’exécuter sur .NET Framework 4.5 ou ses versions intermédiaires, ou si vous développez une nouvelle version d’une application ou d’un composant qui cible .NET Framework 4.5 ou ses versions intermédiaires à partir d’une base de code source existante, consultez [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md) pour connaître les types et les membres obsolètes, et appliquer la solution de contournement décrite. (Le code précédemment compilé continuera à s'exécuter sur des types et des membres marqués comme obsolètes.)

- Si vous déterminez qu’une modification de la .NET Framework 4,5 a endommagé votre application, vérifiez le [schéma des paramètres d’exécution](../configure-apps/file-schema/runtime/index.md), et en particulier l' [ \<AppContextSwitchOverrides> élément](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), pour déterminer si vous pouvez utiliser un paramètre d’exécution dans le fichier de configuration de votre application pour restaurer le comportement précédent.

- Si vous rencontrez un problème qui n’est pas documenté, ouvrez un problème sur le [site de la communauté des développeurs pour .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) ou ouvrez un problème dans le [dépôt GitHub de Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).

## <a name="side-by-side-execution"></a>Exécution côte à côte

Si vous ne trouvez pas de solution de contournement appropriée pour votre problème, n’oubliez pas que .NET Framework 4,5 (ou l’une de ses versions intermédiaires) s’exécute côte à côte avec les versions 1,1, 2,0 et 3,5, et qu’il s’agit d’une mise à jour sur place qui remplace la version 4. Pour les applications qui ciblent les versions 1,1, 2,0 et 3,5, vous pouvez installer la version appropriée de .NET Framework sur l’ordinateur cible pour exécuter l’application dans son environnement optimal. Pour plus d’informations sur l’exécution côte à côte, consultez [Exécution côte à côte](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Voir aussi

- [Nouveautés](../whats-new/index.md)
- [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md)
- [Compatibilité des applications](application-compatibility.md)
- [.NET Framework la stratégie de support officielle](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 problèmes de migration](net-framework-4-migration-issues.md)
