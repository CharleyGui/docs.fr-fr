---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237347"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive

Les instances <xref:System.Text.EncoderFallbackBuffer> personnalisées ne peuvent pas être rétablies de manière récursive. L’implémentation de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> doit aboutir à une séquence de caractères convertible en l’encodage de destination. Dans le cas contraire, une exception se produit.

#### <a name="change-description"></a>Modifier la description

Pendant une opération de transcodage de caractère à octet, le runtime détecte les séquences UTF-16 mal formées ou non convertibles et fournit ces caractères à la méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>. La méthode `Fallback` détermine les caractères qui doivent être substitués aux données originales non convertibles, et ces caractères sont vidés en appelant <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> dans une boucle.

Le runtime tente ensuite de transcoder ces caractères de substitution dans l’encodage cible. Si cette opération a échoué, le runtime continue à effectuer le transcodage à partir de l’endroit où il s’est arrêté dans la chaîne d’entrée d’origine.

Dans .NET Core Preview 7 et les versions antérieures, les implémentations personnalisées de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> peuvent retourner des séquences de caractères qui ne sont pas convertibles en l’encodage de destination. Si les caractères substitués ne peuvent pas être transcodés dans l’encodage cible, le runtime appelle de nouveau la méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> avec les caractères de substitution, en attendant que la méthode <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> retourne une nouvelle séquence de substitution. Ce processus se poursuit jusqu’à ce que le Runtime découvre une substitution correctement formée et convertible, ou jusqu’à ce qu’un nombre maximal de récurrences soit atteint.

À compter de .NET Core 3,0, les implémentations personnalisées de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> doivent retourner des séquences de caractères convertibles en encodage de destination. Si les caractères substitués ne peuvent pas être transcodés dans l’encodage cible, une <xref:System.ArgumentException> est levée. Le runtime n’effectue plus d’appels récursifs dans l’instance <xref:System.Text.EncoderFallbackBuffer>.

Ce comportement s’applique uniquement lorsque les trois conditions suivantes sont remplies :

- Le runtime détecte une séquence UTF-16 ou UTF-16 incorrecte qui ne peut pas être convertie en l’encodage cible.
- Un @no__t personnalisé-0 a été spécifié.
- La @no__t personnalisée-0 tente de substituer une nouvelle séquence UTF-16 incorrecte ou non convertible.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La plupart des développeurs n’ont aucune action à effectuer.

Si une application utilise une classe <xref:System.Text.EncoderFallback> et <xref:System.Text.EncoderFallbackBuffer> personnalisée, assurez-vous que l’implémentation de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> remplit la mémoire tampon de secours avec des données UTF-16 bien formées qui sont directement convertibles en encodage cible lorsque la méthode <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> est appelée pour la première fois par le Language.

#### <a name="category"></a>Catégorie

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
