---
title: 'Comment : récupérer des informations sur les types et les membres à l’aide de la réflexion'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130217"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Comment : récupérer des informations sur les types et les membres à l’aide de la réflexion
L' <xref:System.Reflection> espace de noms contient de nombreuses méthodes pour obtenir des informations sur les types et leurs membres. Cet article illustre l’une de ces méthodes <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>,. Pour plus d’informations, consultez [vue d’ensemble](reflection.md)de la réflexion.
  
## <a name="example"></a>Exemple

L’exemple suivant obtient des informations sur les types et les membres à l’aide de la réflexion :

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Voir aussi

- [Programmer avec des domaines d’application](../app-domains/application-domains.md#programming-with-application-domains)
- [Réflexion](reflection.md)
- [Utiliser des domaines d’application](../app-domains/use.md)
