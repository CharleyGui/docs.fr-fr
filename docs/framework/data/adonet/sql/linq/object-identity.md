---
title: Identité d'un objet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 1a1617b4fb15a6adf94c0241c3ba577308c51a8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169425"
---
# <a name="object-identity"></a>Identité d'un objet

Les identités des objets du runtime sont uniques. Deux variables qui font référence au même objet font en réalité référence à la même instance de l'objet. Par conséquent, les modifications que vous apportez avec un chemin d'accès via une variable sont immédiatement visibles via l'autre variable.  
  
 Les lignes d'une table de bases de données relationnelle n'ont pas d'identités uniques. Étant donné que chaque ligne a une clé primaire unique, deux lignes ne peuvent pas partager la même valeur de clé. Toutefois, cela concerne uniquement le contenu de la table de base de données.  
  
 Dans la réalité, les données sont souvent extraites de la base de données vers une couche différente où une application fonctionne avec celles-ci. Il s'agit du modèle que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge. Lorsque des données sont extraites de la base de données comme lignes, il est peu probable que deux lignes qui représentent les mêmes données correspondent réellement aux mêmes instances de ligne. Si vous interrogez un client spécifique deux fois, vous obtenez deux lignes de données. Chaque ligne contient les mêmes informations.  
  
 Vous souhaitez obtenir quelque chose de très différent avec les objets. Si vous demandez à plusieurs reprises les mêmes informations au <xref:System.Data.Linq.DataContext>, vous vous attendez à ce que celui-ci vous donne la même instance d'objet. Ce comportement est attendu, étant donné que les objets ont une signification particulière pour votre application, et vous vous attendez à ce qu'ils se comportent comme des objets. Vous les avez conçus comme des hiérarchies ou des graphiques. Vous comptez les récupérer comme tels et ne pas recevoir de nombreuses instances répliquées uniquement parce que vous avez effectué la même demande plusieurs fois.  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], le <xref:System.Data.Linq.DataContext> gère l'identité de l'objet. À chaque fois que vous récupérez une nouvelle ligne de la base de données, elle est entrée dans une table d'identités par sa clé primaire et un objet est créé. À chaque fois que vous récupérez cette ligne, l'instance d'objet d'origine est remise à l'application. De cette façon, le <xref:System.Data.Linq.DataContext> traduit le concept d'identité tel que la base de données l'a vu (autrement dit, des clés primaire) en concept d'identité vu par le langage (autrement dit, des instances). L'application voit uniquement l'objet dans l'état dans lequel il a été récupéré la première fois. Si les nouvelles données sont différentes, elles sont ignorées. Pour plus d’informations, consultez [récupération d’objets à partir du cache d’identité](retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise cette approche pour gérer l’intégrité des objets locaux afin de prendre en charge les mises à jour optimistes. Étant donné que les seules modifications qui se produisent une fois que l'objet a été créé sont celles effectuées par l'application, le rôle de l'application est correctement défini. Si un tiers extérieur a effectué des modifications dans l'intervalle, elles sont identifiées au moment où `SubmitChanges()` est appelé.  
  
> [!NOTE]
> Si l'objet demandé par la requête est facilement identifiable comme un objet déjà récupéré, aucune requête n'est exécutée. La table d'identités agit en tant que cache de tous les objets récupérés précédemment.  
  
## <a name="examples"></a>Exemples  
  
### <a name="object-caching-example-1"></a>Exemple 1 de la mise en cache d'objets  

 Dans cet exemple, si vous exécutez les mêmes requêtes deux fois, vous recevez une référence au même objet en mémoire à chaque fois.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Exemple 2 de la mise en cache d'objets  

 Dans cet exemple, si vous exécutez des requêtes différentes qui retournent la même ligne de la base de données, vous recevez une référence au même objet en mémoire à chaque fois.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
