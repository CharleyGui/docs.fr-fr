---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617204"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>L’analyse des objets System.Uri respecte la norme RFC 3987

#### <a name="details"></a>Détails

L’analyse URI a changé à différents niveaux dans .NET Framework 4.5. Notez, cependant, que ces changements affectent uniquement le code qui cible .NET Framework 4.5. Si un fichier binaire cible .NET Framework 4.0, l’ancien comportement est appliqué. Les changements appliqués à l’analyse URI dans .NET Framework 4.5 sont les suivants :

- L’analyse des URI effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.
- Le formulaire C de normalisation Unicode n’est appliqué que sur la partie hôte de l’URI.
- Les URI mailto: non valides génèrent désormais une exception.
- Les espaces à la fin d’un segment de chemin sont désormais conservés.
- Les URI `file://` n’échappent pas le caractère `?`.
- Les caractères de contrôle Unicode allant de `U+0080` à `U+009F` ne sont pas pris en charge.
- Les virgules `,` ou `%2c` ne sont pas automatiquement sans séquence d’échappement.

#### <a name="suggestion"></a>Suggestion

Si l’ancienne sémantique d’analyse URI de .NET Framework 4.0 est nécessaire (et c’est souvent le cas), elle peut être utilisée en ciblant .NET Framework 4.0. Pour cela, utilisez un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> sur l’assembly ou modifiez les propriétés du projet dans l’interface utilisateur du système de projet de Visual Studio.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
