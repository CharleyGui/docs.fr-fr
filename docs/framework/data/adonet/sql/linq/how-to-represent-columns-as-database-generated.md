---
title: 'Procédure : Représenter des colonnes en tant que colonnes générées par une base de données'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 914fdcb78efbaaddf08330e32e1d7f7c4e62436e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166311"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="84813-102">Procédure : Représenter des colonnes en tant que colonnes générées par une base de données</span><span class="sxs-lookup"><span data-stu-id="84813-102">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="84813-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriété sur l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner un champ ou une propriété comme représentant une colonne générée par la base de données.</span><span class="sxs-lookup"><span data-stu-id="84813-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="84813-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="84813-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="84813-105">Pour désigner un champ ou une propriété comme représentant d'une colonne générée par une base de données</span><span class="sxs-lookup"><span data-stu-id="84813-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="84813-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="84813-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="84813-107">Affectez la valeur `true` à la propriété.</span><span class="sxs-lookup"><span data-stu-id="84813-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84813-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84813-108">See also</span></span>

- [<span data-ttu-id="84813-109">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="84813-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="84813-110">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="84813-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
