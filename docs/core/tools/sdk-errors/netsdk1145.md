---
title: 'NETSDK1145 : ciblage ou apphost Pack manquant'
description: Comment résoudre le problème de l’absence du Pack de ciblage pendant la restauration du package NuGet
author: wli3
ms.topic: error-reference
ms.date: 09/14/2020
f1_keywords:
- NETSDK1145
ms.openlocfilehash: c343952582cafb63eae388fd216769e6c67d4741
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805323"
---
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a>NETSDK1145 : ciblage ou apphost Pack manquant

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 5.0.100 et versions ultérieures

Lorsque le kit de développement logiciel (SDK) .NET émet une erreur NETSDK1145, le Pack de ciblage ou apphost n’est pas installé et la restauration des packages NuGet n’est pas prise en charge. Cela est généralement dû à l’utilisation d’un kit de développement logiciel (SDK) plus récent que celui inclus dans Visual Studio pour les projets C++/CLI. Mettez à niveau Visual Studio, supprimez _global.js_ si elle spécifie une certaine version du SDK et désinstallez le kit de développement logiciel (SDK) plus récent. Vous pouvez également remplacer la version de ciblage ou de apphost. Recherchez la version qui existe sous le répertoire Pack à partir du message d’erreur et qui correspond au Framework cible du projet. Ajoutez le code suivant au projet :

Pour apphost Pack

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

Pour le Targeting Pack

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
