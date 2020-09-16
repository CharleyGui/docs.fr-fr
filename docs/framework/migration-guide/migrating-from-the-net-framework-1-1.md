---
title: Migration à partir du .NET Framework 1.1
description: En savoir plus sur les étapes nécessaires à l’exécution d’une application compilée à l’aide de .NET Framework 1,1 sur Windows 7 ou version ultérieure.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: 7312de7d812aa714447a60f5aa04cb48890e40e8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553725"
---
# <a name="migrate-from-the-net-framework-11"></a>Migrer à partir de la .NET Framework 1,1

Windows 7 et les versions ultérieures du système d’exploitation Windows ne prennent pas en charge la .NET Framework 1,1. Par conséquent, les applications qui ciblent le .NET Framework 1,1 ne s’exécuteront pas sans modification sur les versions de système d’exploitation Windows 7 ou version ultérieure. Cette rubrique décrit les étapes nécessaires à l’exécution d’une application qui cible le .NET Framework 1,1 sous Windows 7 et les versions ultérieures du système d’exploitation Windows. Pour plus d’informations sur les .NET Framework 1,1 et Windows 8, consultez [exécuter des applications .NET Framework 1,1 sur Windows 8 et versions ultérieures](../install/run-net-framework-1-1-apps.md).

## <a name="retarget-or-recompile"></a>Reciblez ou recompilez

Il existe deux façons d’obtenir une application qui a été compilée à l’aide de l' .NET Framework 1,1 pour s’exécuter sur Windows 7 ou sur un système d’exploitation Windows ultérieur :

- Reciblez l’application pour qu’elle s’exécute sous .NET Framework 4 et versions ultérieures. Le reciblage nécessite que vous ajoutiez un [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) élément au fichier de configuration de l’application qui lui permet de s’exécuter sous .NET Framework 4 et versions ultérieures. Un tel fichier de configuration prend la forme suivante :

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Recompilez l’application avec un compilateur qui cible le .NET Framework 4 ou une version ultérieure. Si vous avez utilisé initialement Visual Studio 2003 pour développer et compiler votre solution, vous pouvez ouvrir cette dernière dans Visual Studio 2010 (et probablement les versions ultérieures également) et utiliser la boîte de dialogue de **compatibilité des projets** pour convertir les fichiers solution et projet des formats utilisés par Visual Studio 2003 au format Microsoft Build Engine (MSBuild).

Que vous préfériez recompiler ou recibler votre application, vous devez déterminer si elle est affectée par les modifications introduites dans les versions ultérieures du .NET Framework. Ces modifications sont de deux types :

- Changements cassants qui se sont produits entre .NET Framework 1.1 et les versions ultérieures du .NET Framework.

- Types et membres de type marqués comme dépréciés ou obsolètes entre .NET Framework 1.1 et les versions ultérieures du .NET Framework.

Si vous reciblez ou recompilez votre application, vous devez examiner à la fois les changements cassants et les types et membres obsolètes pour chaque version du .NET Framework commercialisée après .NET Framework 1.1.

## <a name="breaking-changes"></a>Changements cassants

Lorsqu'une modification avec rupture se produit, selon la modification spécifique, une solution de contournement peut être disponible pour les applications reciblées et recompilées. Dans certains cas, vous pouvez ajouter un élément enfant à l' [\<runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) élément du fichier de configuration de votre application pour restaurer le comportement précédent. Par exemple, le fichier de configuration suivant restaure le tri des chaînes et le comportement de comparaison utilisé dans .NET Framework 1.1 et peut être utilisé avec une application reciblée ou recompilée.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Toutefois, dans certains cas, vous devrez peut-être modifier votre code source et recompiler votre application.

Pour évaluer l'impact de modifications avec rupture possibles sur votre application, vous devez passer en revue les listes suivantes de modifications :

- L’article traitant des [changements cassants dans .NET Framework 2.0](/previous-versions/aa570326(v=msdn.10)) décrit les changements dans .NET Framework 2.0 SP1 qui peuvent affecter une application ciblant .NET Framework 1.1.

- L’article traitant des [modifications apportées dans .NET Framework 3.5 SP1](/previous-versions/dotnet/articles/dd310284(v=msdn.10)) décrit les modifications intervenues entre .NET Framework 3.5 et .NET Framework 3.5 SP1.

- [Problèmes de migration de .NET Framework 4](net-framework-4-migration-issues.md) décrit les changements intervenus entre .NET Framework 3.5 SP1 et .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Types et membres obsolètes

L'impact des types et membres déconseillés est quelque peu différent pour les applications de reciblées et les applications recompilées. L'utilisation de types et membres obsolètes n'affectera pas une application reciblée, sauf si le type ou le membre obsolète a été supprimé physiquement de son assembly. Recompiler une application qui utilise des types ou des membres obsolètes entraîne généralement un avertissement du compilateur plutôt qu'une erreur du compilateur. Toutefois, dans certains cas, cela entraîne une erreur du compilateur, et le code qui utilise le type ou le membre obsolète ne se compile pas correctement. Dans ce cas, vous devez réécrire le code source qui appelle le type ou membre obsolète avant de recompiler votre application. Pour plus d'informations sur les types et membres obsolètes, consultez [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md).

Pour évaluer l’impact des types et membres dépréciés depuis la mise en production de .NET Framework 2.0 SP1, consultez [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md). Passez en revue les listes de types et membres obsolètes pour .NET Framework 2.0 SP1, .NET Framework 3.5 et .NET Framework 4.
