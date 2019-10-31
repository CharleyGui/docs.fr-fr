---
title: "Comment : décharger un domaine d'application"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
ms.openlocfilehash: 4d5f98229c3a9da69a350ae325cd42e8deb6b7bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119843"
---
# <a name="how-to-unload-an-application-domain"></a>Comment : décharger un domaine d'application
Quand vous avez fini d’utiliser un domaine d’application, déchargez-le à l’aide de la méthode <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>. La méthode **Unload** arrête de façon correcte le domaine d’application spécifié. Au cours du processus de déchargement, aucun nouveau thread ne peut accéder au domaine d’application, et toutes les structures de données spécifiques au domaine d’application sont libérées.  
  
 Les assemblys chargés dans le domaine d’application sont supprimés et ne sont plus disponibles. Si un assembly dans le domaine d’application est indépendant du domaine, les données de l’assembly restent en mémoire jusqu’à ce que l’ensemble du processus soit arrêté. Pour décharger un assembly indépendant du domaine, il n’existe pas d’autre mécanisme que l’arrêt de l’ensemble du processus. Il existe des cas où la demande de déchargement d’un domaine d’application ne fonctionne pas et provoque une exception <xref:System.CannotUnloadAppDomainException>.  
  
 L’exemple suivant crée un nouveau domaine d’application appelé `MyDomain`, imprime certaines informations dans la console, puis décharge le domaine d’application. Remarquez que le code tente ensuite d’imprimer le nom convivial du domaine d’application déchargé dans la console. Cette action génère une exception qui est gérée par les instructions try/catch à la fin du programme.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Programmation avec des domaines d’application](application-domains.md#programming-with-application-domains)
- [Guide pratique pour créer un domaine d’application](how-to-create-an-application-domain.md)
- [Utilisation des domaines d’application](use.md)
