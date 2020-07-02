---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621063"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Autoriser les caractères Unicode dans les URI qui ressemblent à des partages UNC

#### <a name="details"></a>Détails

Dans <xref:System.Uri?displayProperty=fullName>, la construction d’un URI de fichier contenant à la fois un nom de partage UNC et des caractères Unicode n’aboutit plus à un URI présentant un état interne non valide. Le comportement change uniquement quand toutes les conditions suivantes sont vraies :<ul><li>L’URI a le schéma <code>file:</code> et est suivi d’au moins quatre barres obliques.</li><li>Le nom d’hôte commence par un trait de soulignement ou un autre symbole non réservé.</li><li>L’URI contient des caractères Unicode.</li></ul>

#### <a name="suggestion"></a>Suggestion

Les applications qui utilisent des URI contenant systématiquement des caractères Unicode sont susceptibles de suivre ce comportement pour interdire les références à des partages UNC. Ces applications doivent utiliser <xref:System.Uri.IsUnc> à la place.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.7.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
