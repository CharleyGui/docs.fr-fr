---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032565"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Identité : la version d’amorçage par défaut de l’interface utilisateur a changé

À partir de ASP.NET Core 3,0, l’interface utilisateur d’identité utilise la version 4 de bootstrap par défaut.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

L' `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` appel de méthode était le même que `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Nouveau comportement

L' `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` appel de la méthode est le même que `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Motif de modification

Le bootstrap 4 a été publié au cours de la période de ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Action recommandée

Vous êtes affecté par cette modification si vous utilisez l’interface utilisateur d’identité par défaut et que vous l’avez ajoutée `Startup.ConfigureServices` comme indiqué dans l’exemple suivant :

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Effectuez l'une des opérations suivantes :

- Migrez votre application pour utiliser bootstrap 4 à l’aide de leur [Guide de migration](https://getbootstrap.com/docs/4.0/migration).
- Mise à jour `Startup.ConfigureServices` pour appliquer l’utilisation du bootstrap 3. Par exemple :

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
