---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568117"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3,0 suit les meilleures pratiques Unicode lors du remplacement de séquences d’octets UTF-8 incorrectes

Lorsque la classe <xref:System.Text.UTF8Encoding> rencontre une séquence d’octets UTF-8 incorrecte lors d’une opération de transcodage octet-à-caractère, elle remplace cette séquence par un caractère «» (caractère de remplacement U + FFFD) dans la chaîne de sortie. .NET Core 3,0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant la meilleure pratique Unicode pour effectuer ce remplacement pendant l’opération de transcodage.

Cela fait partie d’un effort plus important pour améliorer la gestion d’UTF-8 dans .NET, y compris par les nouveaux types de <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> et de <xref:System.Text.Rune?displayProperty=nameWithType>. Le type de <xref:System.Text.UTF8Encoding> a obtenu des mécanismes améliorés de gestion des erreurs afin de produire une sortie cohérente avec les types nouvellement introduits.

#### <a name="change-description"></a>Modifier la description

À compter de .NET Core 3,0, lors du transcodage d’octets en caractères, la classe <xref:System.Text.UTF8Encoding> effectue une substitution de caractères basée sur les meilleures pratiques Unicode. Le mécanisme de substitution utilisé est décrit par [la norme Unicode, Version 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans l’en-tête intitulé _U + FFFD substitution of maximum subpartments_.

Ce comportement s’applique _uniquement_ lorsque la séquence d’octets en entrée contient des données UTF-8 incorrectes. En outre, si l’instance <xref:System.Text.UTF8Encoding> a été construite avec `throwOnInvalidBytes: true` (consultez la [documentation du constructeur UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, l’instance `UTF8Encoding` continuera à lever sur une entrée non valide plutôt que d’effectuer un remplacement U + FFFD.

L’exemple suivant illustre l’impact de cette modification avec une entrée non valide de 3 octets :

|Entrée de 3 octets incorrecte|Sortie avant .NET Core 3,0|Sortie à partir de .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]` (sortie à 2 caractères)| `[ FFFD FFFD FFFD ]` (sortie à 3 caractères)|

Cette sortie de 3 caractères est la sortie par défaut, selon la _Table 3-9_ du fichier PDF standard Unicode lié précédemment.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur.

#### <a name="category"></a>Catégorie

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
