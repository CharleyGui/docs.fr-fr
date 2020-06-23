---
title: 'Procédure : créer un domaine d’application'
description: Consultez Comment créer un domaine d’application dans .NET. Vous pouvez créer un domaine d’application pour charger des assemblys pour gérer personnellement ou en créer un pour exécuter du code.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104805"
---
# <a name="how-to-create-an-application-domain"></a>Procédure : créer un domaine d’application
Un hôte Common Language Runtime crée automatiquement des domaines d’application quand ils sont nécessaires. Toutefois, vous pouvez créer vos propres domaines d’application et y charger les assemblys que vous souhaitez gérer personnellement. Vous pouvez également créer des domaines d’application à partir desquels vous exécutez du code.  
  
 Vous pouvez créer un domaine d’application à l’aide de l’une des méthodes **CreateDomain** surchargées dans la classe <xref:System.AppDomain?displayProperty=nameWithType>. Vous pouvez nommer le domaine d’application et le référencer par ce nom.  
  
 L’exemple suivant crée un domaine d’application et lui attribue le nom `MyDomain`, puis imprime le nom du domaine hôte et du domaine d’application enfant créé dans la console.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Programmation avec des domaines d’application](application-domains.md#programming-with-application-domains)
- [Utilisation des domaines d'application](use.md)
