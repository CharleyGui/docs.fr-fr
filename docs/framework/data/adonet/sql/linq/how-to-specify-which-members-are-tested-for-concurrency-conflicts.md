---
title: 'Procédure : Spécifier les membres dont les conflits d’accès concurrentiel doivent être vérifiés'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: e774935827934ae73873247def049b4045535272
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197142"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Procédure : Spécifier les membres dont les conflits d’accès concurrentiel doivent être vérifiés

Appliquez l’un des trois enums à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> propriété sur un <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour spécifier les membres à inclure dans les vérifications de mise à jour pour la détection des conflits d’accès concurrentiel optimiste.  
  
 La propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (mappée au moment du design) est utilisée avec des fonctionnalités d’accès concurrentiel à l’exécution dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Pour plus d’informations, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Les valeurs membres d'origine sont comparées avec l'état actuel de la base de données tant qu'aucun membre n'est désigné comme `IsVersion=true`. Pour plus d'informations, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Pour utiliser systématiquement ce membre pour détecter les conflits  
  
1. Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2. Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à la propriété `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Pour ne jamais utiliser ce membre pour détecter des conflits  
  
1. Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2. Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à la propriété `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Pour utiliser ce membre pour détecter des conflits uniquement lorsque l'application a modifié la valeur du membre  
  
1. Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2. Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à la propriété `WhenChanged`.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant spécifie que les objets `HomePage` ne doivent jamais être testés pendant des contrôles de mise à jour. Pour plus d'informations, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Gérer les conflits de changement](how-to-manage-change-conflicts.md)
- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
