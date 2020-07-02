---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614499"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>La sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG

#### <a name="details"></a>Détails

À partir des applications qui ciblent .NET Framework 4.6.2, la sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG). Cette prise en charge se limite aux certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur. Quand une application cible .NET Framework 4.6.2, cette fonctionnalité est activée par défaut. Dans les versions antérieures du .NET Framework, les tentatives d’utilisation de certificats X509 avec un fournisseur de stockage de clés CSG lèvent une exception.

#### <a name="suggestion"></a>Suggestion

Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures mais qui s’exécutent sur .NET Framework 4.6.2 peuvent activer la prise en charge des certificats CNG en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou web.config :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

Vous pouvez en faire autant par programmation avec un code de ce type :

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

Notez qu’en raison de cette modification, tout code de traitement des exceptions qui dépend de l’échec de la tentative d’établissement d’une communication sécurisée avec un certificat CNG ne s’exécutera plus.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6.2       |
| Type    | Reciblage |
