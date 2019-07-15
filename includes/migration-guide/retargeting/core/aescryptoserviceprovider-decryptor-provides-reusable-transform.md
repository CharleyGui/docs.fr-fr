---
ms.openlocfilehash: 846a6bcd3c668e6ad505f745bcb830c3b9dce437
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859329"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Le déchiffreur AesCryptoServiceProvider fournit une transformation réutilisable

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.6.2, le déchiffreur <xref:System.Security.Cryptography.AesCryptoServiceProvider> fournit une transformation réutilisable. Après un appel à <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, la transformation est réinitialisée et peut être réutilisée. Pour les applications qui ciblent des versions antérieures du .NET Framework, toute tentative de réutilisation du déchiffreur en appelant <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> après un appel à <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> lève un <xref:System.Security.Cryptography.CryptographicException> ou génère des données endommagées.|
|Suggestion|L’impact de ce changement devrait être minime, car il s’agit du comportement attendu. Les applications qui dépendent du comportement précédent peuvent refuser le changement en ajoutant le paramètre de configuration suivant dans la section <code>&lt;runtime&gt;</code> du fichier de configuration de l’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>De plus, les applications qui ciblent une version antérieure du .NET Framework mais qui s’exécutent dans .NET Framework 4.6.2 ou une version ultérieure peuvent accepter ce changement en ajoutant le paramètre de configuration suivant à la section <code>&lt;runtime&gt;</code> du fichier de configuration de l’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Portée|Mineur|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|

