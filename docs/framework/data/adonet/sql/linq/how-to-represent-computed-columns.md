---
title: 'Procédure : Représenter des colonnes calculées'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: d952a6c22cd96bbc89aeebfa4b13e9727a363c73
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166324"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="429b6-102">Procédure : Représenter des colonnes calculées</span><span class="sxs-lookup"><span data-stu-id="429b6-102">How to: Represent Computed Columns</span></span>

<span data-ttu-id="429b6-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> propriété sur un <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour représenter une colonne dont le contenu est le résultat d’un calcul.</span><span class="sxs-lookup"><span data-stu-id="429b6-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="429b6-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="429b6-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="429b6-105">ne prend pas en charge les colonnes calculées en tant que clés primaires.</span><span class="sxs-lookup"><span data-stu-id="429b6-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="429b6-106">Pour représenter une colonne calculée</span><span class="sxs-lookup"><span data-stu-id="429b6-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="429b6-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="429b6-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="429b6-108">Assignez une représentation sous forme de chaîne de la formule à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="429b6-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429b6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="429b6-109">See also</span></span>

- [<span data-ttu-id="429b6-110">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="429b6-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="429b6-111">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="429b6-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
