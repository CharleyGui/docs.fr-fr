---
title: 'Procédure : Résoudre les conflits d’accès concurrentiel en fusionnant des valeurs de base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 18a7eceeec63d9caadefab8d98942f10d82c99ca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793350"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Procédure : Résoudre les conflits d’accès concurrentiel en fusionnant des valeurs de base de données
Pour harmoniser des différences entre des valeurs de base de données attendues et réelles avant de soumettre à nouveau vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.KeepChanges> pour fusionner des valeurs de base de données avec les valeurs de membre client actuelles. Pour plus d’informations, [consultez accès concurrentiel optimiste : Vue](optimistic-concurrency-overview.md)d’ensemble.  
  
> [!NOTE]
> Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données. Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.  
  
## <a name="example"></a>Exemple  
 Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications car User2 a modifié entre-temps les colonnes Assistant et Department. Le tableau suivant présente la situation.  
  
||Responsable|Assistant|department|  
|------|-------------|---------------|----------------|  
|État de la base de données d'origine lors d'une interrogation par User1 et User2.|Alfreds|Maria|Sales|  
|User1 s'apprête à soumettre ces modifications.|Alfred||Marketing|  
|User2 a déjà soumis ces modifications.||Mary|de diffusion en continu|  
  
 User1 décide de résoudre ce conflit en fusionnant des valeurs de base de données avec les valeurs de membre client actuelles. Les valeurs de base de données seront donc remplacées uniquement lorsque l'ensemble de modifications actuel aura également modifié cette valeur.  
  
 Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.KeepChanges>, le résultat dans la base de données se présente comme dans le tableau suivant :  
  
||Responsable|Assistant|department|  
|------|-------------|---------------|----------------|  
|Nouvel état après résolution du conflit.|Alfred<br /><br /> (de User1)|Mary<br /><br /> (de User2)|Marketing<br /><br /> (de User1)|  
  
 L'exemple suivant montre comment fusionner des valeurs de base de données avec les valeurs de membre client actuelles (à moins que le client ait également modifié cette valeur). Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Résoudre les conflits en remplaçant les valeurs de la base de données](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Guide pratique pour Résoudre les conflits en conservant les valeurs de la base de données](how-to-resolve-conflicts-by-retaining-database-values.md)
- [Guide pratique pour Gérer les conflits de modification](how-to-manage-change-conflicts.md)
