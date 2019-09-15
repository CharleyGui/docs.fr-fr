---
title: 'Procédure : Récupération d’informations sur les types et les membres à l’aide de la réflexion'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972920"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Procédure : Récupération d’informations sur les types et les membres à l’aide de la réflexion
L' <xref:System.Reflection> espace de noms contient de nombreuses méthodes pour obtenir des informations sur les types et leurs membres. Cet article illustre l’une de ces méthodes <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>,. Pour plus d’informations, consultez [vue d’ensemble](reflection.md)de la réflexion.
  
## <a name="example"></a>Exemples

L’exemple suivant obtient des informations sur les types et les membres à l’aide de la réflexion :

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Voir aussi

- [Programmer avec des domaines d’application](../app-domains/application-domains.md#programming-with-application-domains)
- [Réflexion](reflection.md)
- [Utiliser des domaines d’application](../app-domains/use.md)
