---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721708"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Le paramètre booléen de SignedCms. ComputeSignature est respecté

Dans .NET Core, le `silent` paramètre booléen de la <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> méthode est respecté. Aucune invite de code confidentiel n’est affichée si ce paramètre a la valeur `true` .

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, le `silent` paramètre de la <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> méthode est ignoré et une invite de code confidentiel est toujours affichée si le fournisseur l’exige. Dans .NET Core, le `silent` paramètre est respecté et, s’il a la valeur `true` , une invite de code pin n’est jamais affichée, même si elle est requise par le fournisseur.

La prise en charge des messages de #7 CMS/PKCS a été introduite dans .NET Core dans la version 2,1.

#### <a name="version-introduced"></a>Version introduite

2.1

#### <a name="recommended-action"></a>Action recommandée

Pour vous assurer qu’une invite de code confidentiel s’affiche si nécessaire, les applications de bureau doivent appeler <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> et définir le paramètre booléen sur `false` . Le comportement résultant est le même que sur .NET Framework que le contexte silencieux soit désactivé ou non.

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
