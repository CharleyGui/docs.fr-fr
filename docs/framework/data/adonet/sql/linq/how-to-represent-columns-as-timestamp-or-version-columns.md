---
title: 'Procédure : Représenter des colonnes en tant que colonnes timestamp ou version'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793500"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="ae898-102">Procédure : Représenter des colonnes en tant que colonnes timestamp ou version</span><span class="sxs-lookup"><span data-stu-id="ae898-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="ae898-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> propriété de l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner un champ ou une propriété comme représentant une colonne de base de données qui contient les horodateurs de base de données ou les numéros de version.</span><span class="sxs-lookup"><span data-stu-id="ae898-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="ae898-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae898-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="ae898-105">Pour désigner un champ ou une propriété comme représentant d'une colonne timestamp ou version</span><span class="sxs-lookup"><span data-stu-id="ae898-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="ae898-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ae898-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ae898-107">Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="ae898-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae898-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae898-108">See also</span></span>

- [<span data-ttu-id="ae898-109">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ae898-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ae898-110">Guide pratique pour Spécifier les membres qui sont testés pour les conflits d’accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="ae898-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="ae898-111">Guide pratique : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="ae898-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
