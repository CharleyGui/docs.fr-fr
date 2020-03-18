---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449214"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Boolean paramètre de SignedCms.ComputeSignature est respecté

Dans .NET Core, `silent` le paramètre Boolean de la <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> méthode est respecté. Une invite NIP n’est pas `true`indiquée si ce paramètre est défini pour .

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, `silent` le <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> paramètre de la méthode est ignoré, et une invite NIP est toujours affichée si nécessaire par le fournisseur. Dans .NET Core, le `silent` paramètre est `true`respecté, et si défini à , une invite NIP n’est jamais montré, même si elle est requise par le fournisseur.

La prise en charge des messages #7 CMS/PKCS a été introduite dans .NET Core dans la version 2.1.

#### <a name="version-introduced"></a>Version introduite

2.1

#### <a name="recommended-action"></a>Action recommandée

Pour s’assurer qu’une invite NIP apparaît si nécessaire, les applications de bureau doivent appeler <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> et définir le paramètre Boolean à `false`. Le comportement qui en résulte est le même que sur .NET Framework indépendamment du fait que le contexte silencieux y est désactivé.

### <a name="category"></a>Category

Chiffrement

### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
