---
title: 'Procédure : Représenter des colonnes en tant que colonnes timestamp ou version'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: cc8538ab7b2ecf5183cfb97995c04648493a369f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191747"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="0269f-102">Procédure : Représenter des colonnes en tant que colonnes timestamp ou version</span><span class="sxs-lookup"><span data-stu-id="0269f-102">How to: Represent Columns as Timestamp or Version Columns</span></span>

<span data-ttu-id="0269f-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> propriété de l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner un champ ou une propriété comme représentant une colonne de base de données qui contient les horodateurs de base de données ou les numéros de version.</span><span class="sxs-lookup"><span data-stu-id="0269f-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="0269f-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="0269f-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="0269f-105">Pour désigner un champ ou une propriété comme représentant d'une colonne timestamp ou version</span><span class="sxs-lookup"><span data-stu-id="0269f-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="0269f-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0269f-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0269f-107">Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="0269f-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0269f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0269f-108">See also</span></span>

- [<span data-ttu-id="0269f-109">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0269f-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="0269f-110">Procédure : Spécifier les membres dont les conflits d’accès concurrentiel doivent être vérifiés</span><span class="sxs-lookup"><span data-stu-id="0269f-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="0269f-111">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="0269f-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
