---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021580"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Custom EncoderFallbackBuffer instances ne peuvent pas se replier de façon récursive

Les <xref:System.Text.EncoderFallbackBuffer> instances personnalisées ne peuvent pas se replier de façon récursive. La mise <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> en œuvre de doit entraîner une séquence de caractères qui est convertible à l’encodage de destination. Sinon, une exception se produit.

#### <a name="change-description"></a>Description de la modification

Au cours d’une opération de transcodage de caractère à l’autre, le temps d’exécution détecte les <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> séquences UTF-16 mal formées ou non révertisables et fournit ces caractères à la méthode. La `Fallback` méthode détermine quels caractères doivent être substitués aux données originales non <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> convertiables, et ces caractères sont drainés en appelant en boucle.

Le temps d’exécution tente alors de transcoder ces caractères de substitution au codage cible. Si cette opération réussit, le temps d’exécution continue le transcodage d’où il s’est détaché dans la chaîne d’entrée d’origine.

Dans .NET Core Preview 7 et les <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> versions antérieures, les implémentations personnalisées de peuvent retourner des séquences de caractères qui ne sont pas convertibles à l’encodage de destination. Si les caractères substitués ne peuvent pas être transcodés vers l’encodage cible, le temps d’exécution invoque à nouveau la <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> méthode avec les caractères de substitution, s’attendant à ce que la <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> méthode renvoie une nouvelle séquence de substitution. Ce processus se poursuit jusqu’à ce que le temps d’exécution voit finalement une substitution décapotable bien formée, ou jusqu’à ce qu’un nombre maximum de récurrence soit atteint.

En commençant par .NET Core 3.0, implémentations personnalisées de séquences de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caractères de retour de must qui sont convertibles à l’encodage de destination. Si les caractères substitués ne peuvent pas <xref:System.ArgumentException> être transcodés vers l’encodage cible, un est lancé. Le temps d’exécution ne fera plus <xref:System.Text.EncoderFallbackBuffer> d’appels récursifs dans l’instance.

Ce comportement ne s’applique que lorsque les trois conditions suivantes sont remplies :

- Le temps d’exécution détecte une séquence UTF-16 mal formée ou une séquence UTF-16 qui ne peut pas être convertie en codage cible.
- Une <xref:System.Text.EncoderFallback> coutume a été spécifiée.
- La <xref:System.Text.EncoderFallback> coutume tente de remplacer une nouvelle séquence UTF-16 mal formée ou non convertie.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La plupart des développeurs n’ont pas besoin de prendre aucune mesure.

Si une application <xref:System.Text.EncoderFallback> utilise <xref:System.Text.EncoderFallbackBuffer> une coutume et <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> une classe, assurez-vous que la mise en œuvre de peuple le <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> tampon de repli avec des données UTF-16 bien formées qui sont directement convertibles au codage cible lorsque la méthode est invoquée pour la première fois par le temps d’exécution.

#### <a name="category"></a>Category

Core .NET bibliothèques

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
