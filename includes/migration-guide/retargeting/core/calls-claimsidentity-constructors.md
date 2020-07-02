---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614430"
---
### <a name="calls-to-claimsidentity-constructors"></a>appels aux constructeurs ClaimsIdentity

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6.2, la façon dont les constructeurs <xref:System.Security.Claims.ClaimsIdentity> avec un paramètre <xref:System.Security.Principal.IIdentity?displayProperty=fullName> définissent la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> est modifiée. Si l’argument <xref:System.Security.Principal.IIdentity?displayProperty=fullName> est un objet <xref:System.Security.Claims.ClaimsIdentity> et que la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> de cet objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas `null`, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> est attachée à l’aide de la méthode <xref:System.Security.Claims.ClaimsIdentity.Clone>. Dans Framework 4.6.1 et les versions antérieures, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> est jointe comme une référence existante. En raison de ce changement, à compter de .NET Framework 4.6.2, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> du nouvel objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas égale à la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> de l’argument <xref:System.Security.Principal.IIdentity?displayProperty=fullName> du constructeur. Dans .NET Framework 4.6.1 et les versions antérieures, elle est égale.

#### <a name="suggestion"></a>Suggestion

Si ce comportement n’est pas souhaitable, vous pouvez restaurer le comportement précédent en réglant `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` dans votre fichier de configuration d’application sur `true`. Pour cela, vous ajoutez le code suivant à la section `<runtime>` de votre fichier web.config :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
