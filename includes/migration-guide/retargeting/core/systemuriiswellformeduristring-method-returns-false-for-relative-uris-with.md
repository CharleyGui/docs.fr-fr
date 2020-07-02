---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617216"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>La méthode System.Uri.IsWellFormedUriString retourne la valeur false pour les URI relatifs comprenant un caractère deux-points dans le premier segment

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traite les URI relatifs comprenant un `:` dans leur premier segment comme n’étant pas bien formés. Il s’agit là d’un changement par rapport au comportement de <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> dans .NET Framework 4.0 qui a été apporté pour qu’il soit conforme à la norme RFC 3986.

#### <a name="suggestion"></a>Suggestion

Ce changement (comme de nombreux autres changements relatifs aux URI) affecte uniquement les applications qui ciblent .NET Framework 4.5 (ou les versions ultérieures). Pour continuer à utiliser l’ancien comportement, ciblez l’application sur .NET Framework 4.0. Si l’ancien comportement est souhaitable, vous pouvez également analyser les URI avant d’appeler <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> pour rechercher les caractères `:` que vous voulez supprimer à des fins de validation.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
