---
title: 'Procédure : Obtenir des informations de type et de membre à l’aide de la réflexion'
description: Découvrez comment obtenir des informations sur les types et les membres avec la réflexion, à l’aide de l’espace de noms System. Reflection.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865318"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Procédure : Obtenir des informations de type et de membre à l’aide de la réflexion
L' <xref:System.Reflection> espace de noms contient de nombreuses méthodes pour obtenir des informations sur les types et leurs membres. Cet article illustre l’une de ces méthodes, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> . Pour plus d’informations, consultez [vue d’ensemble](reflection.md)de la réflexion.
  
## <a name="example"></a>Exemple

L’exemple suivant obtient des informations sur les types et les membres à l’aide de la réflexion :

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Voir aussi

- [Programmer avec des domaines d’application](../app-domains/application-domains.md#programming-with-application-domains)
- [Réflexion](reflection.md)
- [Utiliser des domaines d’application](../app-domains/use.md)
