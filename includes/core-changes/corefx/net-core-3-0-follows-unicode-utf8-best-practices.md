---
ms.openlocfilehash: 0795ee244bf3d1261bbe61dc0c67c3936f427f04
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216350"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3,0 suit les meilleures pratiques Unicode lors du remplacement de séquences d’octets UTF-8 incorrectes

Quand la <xref:System.Text.UTF8Encoding> classe rencontre une séquence d’octets UTF-8 incorrecte lors d’une opération de transcodage d’un octet à un caractère, elle remplace cette séquence par un caractère de remplacement «» (caractère de remplacement U + FFFD) dans la chaîne de sortie. .NET Core 3,0 diffère des versions précédentes de .NET Core et du .NET Framework en suivant la meilleure pratique Unicode pour effectuer ce remplacement pendant l’opération de transcodage.

Cela fait partie d’un effort plus important pour améliorer la gestion d’UTF-8 dans .net, y <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> compris <xref:System.Text.Rune?displayProperty=nameWithType> par les nouveaux types et. Le <xref:System.Text.UTF8Encoding> type a été amélioré pour la gestion des erreurs afin de produire une sortie cohérente avec les types nouvellement introduits.

#### <a name="details"></a>Détails

À compter de .net Core 3,0, lors du transcodage d’octets en <xref:System.Text.UTF8Encoding> caractères, la classe effectue une substitution de caractères basée sur les meilleures pratiques Unicode. Le mécanisme de substitution utilisé est décrit par [la norme Unicode, Version 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) dans l’en-tête intitulé _U + FFFD substitution of maximum subpartments_.

Ce comportement s’applique _uniquement_ lorsque la séquence d’octets en entrée contient des données UTF-8 incorrectes. En outre, si l' <xref:System.Text.UTF8Encoding> instance a été construite avec `throwOnInvalidBytes: true` (consultez la [documentation du constructeur UTF8Encoding]<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>(, `UTF8Encoding` l’instance continuera à lever sur une entrée non valide plutôt que d’exécuter U + FFFD nouveau.

L’exemple suivant illustre l’impact de cette modification avec une entrée non valide de 3 octets :

|Entrée de 3 octets incorrecte|Sortie avant .NET Core 3,0|Sortie à partir de .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(sortie à 2 caractères)| `[ FFFD FFFD FFFD ]`(sortie à 3 caractères)|

Cette sortie de 3 caractères est la sortie par défaut, selon la _Table 3-9_ du fichier PDF standard Unicode lié précédemment.

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
