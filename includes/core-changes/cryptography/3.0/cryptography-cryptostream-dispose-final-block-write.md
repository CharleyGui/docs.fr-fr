---
ms.openlocfilehash: 7766a59131fffe2b436c15a5ff58e67001be7941
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065099"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a>CryptoStream. dispose transforme le bloc final uniquement lors de l’écriture

La <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> méthode, qui est utilisée pour terminer les `CryptoStream` opérations, ne tente plus de transformer le bloc final lors de la lecture.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, si un utilisateur effectuait une lecture incomplète lors de l’utilisation <xref:System.Security.Cryptography.CryptoStream> de en <xref:System.Security.Cryptography.CryptoStreamMode.Read> mode, la <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> méthode pourrait lever une exception (par exemple, lors de l’utilisation d’AES avec un remplissage). L’exception a été levée, car le dernier bloc a été tenté d’être transformé, mais les données étaient incomplètes.

Dans .NET Core 3,0 et versions ultérieures, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> ne tente plus de transformer le bloc final lors de la lecture, ce qui permet des lectures incomplètes.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification active les lectures incomplètes à partir du flux de chiffrement lors de l’annulation d’une opération réseau, sans qu’il soit nécessaire d’intercepter une exception.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La plupart des applications ne doivent pas être affectées par cette modification.

Si votre application a déjà intercepté une exception en cas de lecture incomplète, vous pouvez supprimer ce `catch` bloc.
Si votre application a utilisé la transformation du bloc final dans des scénarios de hachage, vous devrez peut-être vous assurer que le flux entier est lu avant d’être supprimé.

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
