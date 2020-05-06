---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021580"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Les instances EncoderFallbackBuffer personnalisées ne peuvent pas être rétablies de manière récursive

Les <xref:System.Text.EncoderFallbackBuffer> instances personnalisées ne peuvent pas être rétablies de manière récursive. L’implémentation de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> doit entraîner une séquence de caractères convertible en l’encodage de destination. Dans le cas contraire, une exception se produit.

#### <a name="change-description"></a>Description de la modification

Pendant une opération de transcodage de caractère à octet, le runtime détecte les séquences UTF-16 mal formées ou non convertibles et fournit ces caractères à <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> la méthode. La `Fallback` méthode détermine les caractères qui doivent être substitués aux données d’origine qui ne sont pas convertibles, et ces caractères <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> sont vidés en appelant dans une boucle.

Le runtime tente ensuite de transcoder ces caractères de substitution dans l’encodage cible. Si cette opération a échoué, le runtime continue à effectuer le transcodage à partir de l’endroit où il s’est arrêté dans la chaîne d’entrée d’origine.

Dans .NET Core Preview 7 et les versions antérieures, les implémentations <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> personnalisées de peuvent retourner des séquences de caractères qui ne sont pas convertibles en l’encodage de destination. Si les caractères substitués ne peuvent pas être transcodés en l’encodage cible, le runtime <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> appelle de nouveau la méthode avec les caractères de substitution, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> en attendant que la méthode retourne une nouvelle séquence de substitution. Ce processus se poursuit jusqu’à ce que le Runtime découvre une substitution correctement formée et convertible, ou jusqu’à ce qu’un nombre maximal de récurrences soit atteint.

À compter de .NET Core 3,0, les implémentations <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> personnalisées de doivent retourner des séquences de caractères convertibles en l’encodage de destination. Si les caractères substitués ne peuvent pas être transcodés en l’encodage <xref:System.ArgumentException> cible, une exception est levée. Le runtime n’effectue plus d’appels récursifs dans l' <xref:System.Text.EncoderFallbackBuffer> instance.

Ce comportement s’applique uniquement lorsque les trois conditions suivantes sont remplies :

- Le runtime détecte une séquence UTF-16 ou UTF-16 incorrecte qui ne peut pas être convertie en l’encodage cible.
- Un personnalisé <xref:System.Text.EncoderFallback> a été spécifié.
- Le personnalisé <xref:System.Text.EncoderFallback> tente de substituer une nouvelle séquence UTF-16 incorrecte ou non convertible.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La plupart des développeurs n’ont aucune action à effectuer.

Si une application utilise une classe <xref:System.Text.EncoderFallback> et <xref:System.Text.EncoderFallbackBuffer> personnalisée, assurez-vous <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> que l’implémentation de remplit la mémoire tampon de secours avec des données UTF-16 bien formées qui sont directement convertibles en l’encodage cible lorsque la <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> méthode est appelée pour la première fois par le Runtime.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
