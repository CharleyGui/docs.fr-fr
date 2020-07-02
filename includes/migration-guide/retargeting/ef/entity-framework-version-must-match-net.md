---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617190"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>La version d’Entity Framework doit correspondre à la version du .NET Framework

#### <a name="details"></a>Détails

La version d’Entity Framework (EF) doit être mise en correspondance avec la version de .NET Framework. Entity Framework 5 est recommandé pour .NET Framework 4.5. Il existe certains problèmes connus avec EF 4.x dans un projet .NET Framework 4.5 concernant <xref:System.ComponentModel.DataAnnotations>. Dans .NET Framework 4,5, ceux-ci ont été déplacés vers un autre assembly, ce qui signifie qu’il existe des problèmes pour déterminer les annotations à utiliser.

#### <a name="suggestion"></a>Suggestion

Mise à niveau vers Entity Framework 5 pour .NET Framework 4.5

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4,5         |
| Type    | Reciblage |
