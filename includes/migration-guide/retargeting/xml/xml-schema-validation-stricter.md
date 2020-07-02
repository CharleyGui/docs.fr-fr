---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617240"
---
### <a name="xml-schema-validation-is-stricter"></a>La validation du schéma XML est plus stricte

#### <a name="details"></a>Détails

Dans .NET Framework 4.5, la validation du schéma XML est plus stricte. Si vous utilisez xsd:anyURI pour valider un URI tel qu'un protocole mailto, la validation échoue si l'URI contient des espaces. Dans les versions antérieures du .NET Framework, la validation réussissait. Le changement affecte uniquement les applications qui ciblent .NET Framework 4.5.

#### <a name="suggestion"></a>Suggestion

Si une validation moins précise de .NET Framework 4.0 est nécessaire, l’application de validation peut cibler la version 4.0 du .NET Framework. Toutefois, si .NET Framework 4.5 est reciblé, effectuez une revue du code pour vérifier que les URI non valides (avec des espaces) ne sont pas attendus comme valeurs d’attribut avec le type de données anyURI.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,5         |
| Type    | Reciblage |
