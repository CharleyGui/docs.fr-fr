---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394129"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Identité: Version Bootstrap par défaut de l’interface utilisateur changé

À partir de ASP.NET Core 3.0, Identity UI par défaut à l’utilisation de la version 4 de Bootstrap.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

L’appel `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` de méthode était le même que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Nouveau comportement

L’appel `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` de méthode est le même que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Raison du changement

Bootstrap 4 a été libéré au cours ASP.NET période de base 3.0.

#### <a name="recommended-action"></a>Action recommandée

Vous êtes touché par ce changement si vous utilisez l’interface `Startup.ConfigureServices` utilisateur d’identité par défaut et l’avez ajouté comme indiqué dans l’exemple suivant :

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Effectuez l'une des opérations suivantes :

- Migrez votre application pour utiliser Bootstrap 4 à l’aide de leur [guide de migration](https://getbootstrap.com/docs/4.0/migration).
- Mise `Startup.ConfigureServices` à jour pour faire respecter l’utilisation de Bootstrap 3. Par exemple :

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
