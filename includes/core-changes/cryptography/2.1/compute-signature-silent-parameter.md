---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449214"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Le paramètre booléen de SignedCms. ComputeSignature est respecté

Dans .NET Core, le paramètre booléen `silent` de la méthode <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> est respecté. Aucune invite de code confidentiel n’est affichée si ce paramètre est défini sur `true`.

#### <a name="change-description"></a>Modifier la description

Dans .NET Framework, le paramètre `silent` de la méthode <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> est ignoré, et une invite de code PIN est toujours affichée si le fournisseur l’exige. Dans .NET Core, le paramètre `silent` est respecté et, s’il est défini sur `true`, une invite de code PIN n’est jamais affichée, même si elle est requise par le fournisseur.

La prise en charge des messages de #7 CMS/PKCS a été introduite dans .NET Core dans la version 2,1.

#### <a name="version-introduced"></a>Version introduite

2.1

#### <a name="recommended-action"></a>Action recommandée

Pour vous assurer qu’une invite de code confidentiel s’affiche si nécessaire, les applications de bureau doivent appeler <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> et définir le paramètre booléen sur `false`. Le comportement résultant est le même que sur .NET Framework que le contexte silencieux soit désactivé ou non.

### <a name="category"></a>Category

Chiffrement

### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
