---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568117"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3.0 suit les meilleures pratiques d’Unicode lors du remplacement des séquences de byte UTF-8 mal formées

Lorsque <xref:System.Text.UTF8Encoding> la classe rencontre une séquence d’ente UTF-8 mal formée au cours d’une opération de transcodage d’au-dessus du caractère, elle remplacera cette séquence par un caractère « ' ' ( U-FFFD REPLACEMENT CHARACTER) dans la chaîne de sortie. .NET Core 3.0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant les meilleures pratiques d’Unicode pour effectuer ce remplacement pendant l’opération de transcodage.

Cela fait partie d’un effort plus vaste pour améliorer la manipulation <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> UTF-8 tout au long de .NET, y compris par le nouveau et les types. Le <xref:System.Text.UTF8Encoding> type a été donné la mécanique améliorée de manipulation d’erreur de sorte qu’il produit la sortie compatible avec les types nouvellement introduits.

#### <a name="change-description"></a>Description de la modification

En commençant par .NET Core 3.0, lorsque <xref:System.Text.UTF8Encoding> les octets transcontéraux vers des personnages, la classe effectue la substitution de caractères basée sur les meilleures pratiques Unicode. Le mécanisme de substitution utilisé est décrit par [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans le titre intitulé _U-FFFD Substitution of Maximal Subparts_.

Ce comportement ne s’applique _que_ lorsque la séquence d’entrées byte contient des données UTF-8 mal formées. En outre, <xref:System.Text.UTF8Encoding> si l’instance a été construite avec `throwOnInvalidBytes: true` (voir la<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>documentation `UTF8Encoding` [UTF8Encoding constructor](, l’instance continuera à jeter sur l’entrée invalide plutôt que d’effectuer le remplacement U -FFFD.

Ce qui suit illustre l’impact de ce changement avec une entrée invalide de 3 ans :

|Entrée 3-byte mal formée|Sortie avant .NET Core 3.0|Sortie à partir de .NET Core 3.0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(sortie de 2 caractères)| `[ FFFD FFFD FFFD ]`(sortie de 3 caractères)|

Cette sortie 3-char est la sortie préférée, selon _le tableau 3-9_ de l’Unicode Standard PDF précédemment lié.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
