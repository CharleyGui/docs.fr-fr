---
title: Migration à partir du .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c683ce454e4db36367cb097371427d27dc4c555
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636334"
---
# <a name="migrating-from-the-net-framework-11"></a>Migration à partir du .NET Framework 1.1

[!INCLUDE[win7](../../../includes/win7-md.md)] et les versions ultérieures du système d’exploitation Windows ne prennent pas en charge [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]. Ainsi, les applications qui ciblent [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ne s’exécutent pas sans modification sur [!INCLUDE[win7](../../../includes/win7-md.md)] ou les versions ultérieures du système d’exploitation. Cette rubrique décrit les étapes nécessaires pour exécuter une application qui cible [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] sur [!INCLUDE[win7](../../../includes/win7-md.md)] et les versions ultérieures du système d’exploitation Windows. Pour plus d'informations sur [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] et [!INCLUDE[win8](../../../includes/win8-md.md)], consultez [Exécution des applications .NET Framework 1.1 sous Windows 8 et versions ultérieures](../../../docs/framework/install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Reciblage ou recompilation

Il existe deux façons pour qu’une application compilée à l’aide de [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] s’exécute sur [!INCLUDE[win7](../../../includes/win7-md.md)] ou une version ultérieure du système d’exploitation Windows :

- Vous pouvez recibler l’application pour qu’elle s’exécute sous .NET Framework 4 et versions ultérieures. Le reciblage nécessite que vous ajoutiez un élément [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) au fichier de configuration de l'application qui lui permet de s'exécuter sous .NET Framework 4 et versions ultérieures. Un tel fichier de configuration prend la forme suivante :

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Vous pouvez recompiler l'application avec un compilateur qui cible .NET Framework 4 et versions ultérieures. Si vous avez utilisé initialement Visual Studio 2003 pour développer et compiler votre solution, vous pouvez ouvrir cette dernière dans Visual Studio 2010 (et probablement les versions ultérieures également) et utiliser la boîte de dialogue de **compatibilité des projets** pour convertir les fichiers solution et projet des formats utilisés par Visual Studio 2003 au format Microsoft Build Engine (MSBuild).

Que vous préfériez recompiler ou recibler votre application, vous devez déterminer si elle est affectée par les modifications introduites dans les versions ultérieures du .NET Framework. Ces modifications sont de deux types :

- Modifications avec rupture qui se sont produites entre le [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] et les versions ultérieures du .NET Framework.

- Types et membres de type marqués comme déconseillés ou obsolètes entre le [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] et les versions ultérieures du .NET Framework.

Si vous reciblez ou recompilez votre application, vous devez examiner à la fois les modifications avec rupture et les types et membres obsolètes pour chaque version du .NET Framework commercialisée après [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].

## <a name="breaking-changes"></a>Modifications avec rupture

Lorsqu'une modification avec rupture se produit, selon la modification spécifique, une solution de contournement peut être disponible pour les applications reciblées et recompilées. Dans certains cas, vous pouvez ajouter un élément enfant à l'élément [\<runtime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) du fichier de configuration de votre application pour restaurer le comportement précédent. Par exemple, le fichier de configuration suivant restaure le tri des chaînes et le comportement de comparaison utilisé dans le [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] et peut être utilisé avec une application reciblée ou recompilée.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Toutefois, dans certains cas, vous devrez peut-être modifier votre code source et recompiler votre application.

Pour évaluer l'impact de modifications avec rupture possibles sur votre application, vous devez passer en revue les listes suivantes de modifications :

- L’article traitant des[modifications avec rupture dans .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkId=125263) décrit les changements de [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] qui peuvent affecter une application ciblant [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].

- L’article traitant des[modifications apportées à .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkID=186989) décrit les modifications intervenues entre [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].

- [Problèmes de migration de .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) décrit les changements intervenus entre [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] et [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].

## <a name="obsolete-types-and-members"></a>Types et membres obsolètes

L'impact des types et membres déconseillés est quelque peu différent pour les applications de reciblées et les applications recompilées. L'utilisation de types et membres obsolètes n'affectera pas une application reciblée, sauf si le type ou le membre obsolète a été supprimé physiquement de son assembly. Recompiler une application qui utilise des types ou des membres obsolètes entraîne généralement un avertissement du compilateur plutôt qu'une erreur du compilateur. Toutefois, dans certains cas, cela entraîne une erreur du compilateur, et le code qui utilise le type ou le membre obsolète ne se compile pas correctement. Dans ce cas, vous devez réécrire le code source qui appelle le type ou membre obsolète avant de recompiler votre application. Pour plus d'informations sur les types et membres obsolètes, consultez [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md).

Pour évaluer l’impact de types et membres déconseillés depuis la mise en production de [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], consultez [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md). Passez en revue les listes de types et membres obsolètes pour le [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].
