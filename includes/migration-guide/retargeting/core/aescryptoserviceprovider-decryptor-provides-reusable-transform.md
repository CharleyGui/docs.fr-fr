---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614443"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Le déchiffreur AesCryptoServiceProvider fournit une transformation réutilisable

#### <a name="details"></a>Détails

À partir des applications qui ciblent .NET Framework 4.6.2, le déchiffreur <xref:System.Security.Cryptography.AesCryptoServiceProvider> fournit une transformation réutilisable. Après un appel à <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, la transformation est réinitialisée et peut être réutilisée. Pour les applications qui ciblent des versions antérieures du .NET Framework, toute tentative de réutilisation du déchiffreur en appelant <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> après un appel à <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> lève un <xref:System.Security.Cryptography.CryptographicException> ou génère des données endommagées.

#### <a name="suggestion"></a>Suggestion

L’impact de ce changement devrait être minime, car il s’agit du comportement attendu. Les applications qui dépendent du comportement précédent peuvent refuser le changement en ajoutant le paramètre de configuration suivant dans la section `<runtime>` du fichier de configuration de l’application :

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

De plus, les applications qui ciblent une version antérieure du .NET Framework mais qui s’exécutent dans .NET Framework 4.6.2 ou une version ultérieure peuvent accepter ce changement en ajoutant le paramètre de configuration suivant à la section `<runtime>` du fichier de configuration de l’application :

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
