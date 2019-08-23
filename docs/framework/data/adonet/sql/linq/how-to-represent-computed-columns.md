---
title: 'Procédure : Représenter des colonnes calculées'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943543"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="f9b76-102">Procédure : Représenter des colonnes calculées</span><span class="sxs-lookup"><span data-stu-id="f9b76-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="f9b76-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> propriété sur un <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour représenter une colonne dont le contenu est le résultat d’un calcul.</span><span class="sxs-lookup"><span data-stu-id="f9b76-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="f9b76-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9b76-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f9b76-105">ne prend pas en charge les colonnes calculées en tant que clés primaires.</span><span class="sxs-lookup"><span data-stu-id="f9b76-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="f9b76-106">Pour représenter une colonne calculée</span><span class="sxs-lookup"><span data-stu-id="f9b76-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="f9b76-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9b76-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="f9b76-108">Assignez une représentation sous forme de chaîne de la formule à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9b76-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b76-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9b76-109">See also</span></span>

- [<span data-ttu-id="f9b76-110">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f9b76-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="f9b76-111">Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="f9b76-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
