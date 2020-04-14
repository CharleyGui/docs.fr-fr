---
ms.openlocfilehash: c10d617e07ca2fa0239298d449d93cf833b83fce
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275512"
---
### <a name="calls-to-claimsidentity-constructors"></a>appels aux constructeurs ClaimsIdentity

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6.2, la façon dont les constructeurs <xref:System.Security.Claims.ClaimsIdentity> avec un paramètre <xref:System.Security.Principal.IIdentity?displayProperty=name> définissent la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> est modifiée. Si l’argument <xref:System.Security.Principal.IIdentity?displayProperty=name> est un objet <xref:System.Security.Claims.ClaimsIdentity> et que la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> de cet objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas <code>null</code>, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> est attachée à l’aide de la méthode <xref:System.Security.Claims.ClaimsIdentity.Clone>. Dans Framework 4.6.1 et les versions antérieures, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> est jointe comme une référence existante. En raison de ce changement, à compter de .NET Framework 4.6.2, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> du nouvel objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas égale à la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> de l’argument <xref:System.Security.Principal.IIdentity?displayProperty=name> du constructeur. Dans .NET Framework 4.6.1 et les versions antérieures, elle est égale.|
|Suggestion|Si ce comportement n’est pas souhaitable, vous pouvez restaurer le comportement précédent en réglant <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> dans votre fichier de configuration d’application sur <code>true</code>. Pour cela, vous ajoutez le code suivant à la section <code>&lt;runtime&gt;</code> de votre fichier web.config :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)></li></ul>|
