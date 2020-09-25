---
title: 'Procédure : Résoudre des conflits en remplaçant des valeurs de bases de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1dc112350451bde28d27c63961733b96f6fc84be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191708"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Procédure : Résoudre des conflits en remplaçant des valeurs de bases de données

Pour harmoniser des différences entre des valeurs de base de données attendues et réelles avant d'essayer de renvoyer vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> pour remplacer les valeurs de la base de données. Pour plus d’informations, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données. Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.  
  
## <a name="example"></a>Exemple  

 Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications, car User2 a modifié entre-temps les colonnes Assistant et Department. Le tableau suivant présente la situation.  
  
||Manager|Assistant|department|  
|------|-------------|---------------|----------------|  
|État de la base de données d'origine lors d'une interrogation par User1 et User2.|Alfreds|Maria|Sales|  
|User1 s'apprête à soumettre ces modifications.|Alfred||Marketing|  
|User2 a déjà soumis ces modifications.||Mary|Service|  
  
 User1 décide de résoudre ce conflit en remplaçant des valeurs de base de données par les valeurs de membre client actuelles.  
  
 Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, le résultat dans la base de données se présente comme dans le tableau suivant :  
  
||Manager|Assistant|department|  
|------|-------------|---------------|----------------|  
|Nouvel état après résolution du conflit.|Alfred<br /><br /> (de User1)|Maria<br /><br /> (d'origine)|Marketing<br /><br /> (de User1)|  
  
 L'exemple suivant montre comment remplacer des valeurs de base de données par des valeurs de membre client actuelles. Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Gérer les conflits de changement](how-to-manage-change-conflicts.md)
