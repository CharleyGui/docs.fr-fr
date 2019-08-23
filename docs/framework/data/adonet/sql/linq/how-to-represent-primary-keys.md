---
title: 'Procédure : Représenter les clés primaires'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 28c62798f965edfcffe1a156213c2481a8193b49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943526"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="6524f-102">Procédure : Représenter les clés primaires</span><span class="sxs-lookup"><span data-stu-id="6524f-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="6524f-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> propriété sur l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner une propriété ou un champ afin de représenter la clé primaire d’une colonne de base de données.</span><span class="sxs-lookup"><span data-stu-id="6524f-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="6524f-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="6524f-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6524f-105">ne prend pas en charge les colonnes calculées en tant que clés primaires.</span><span class="sxs-lookup"><span data-stu-id="6524f-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="6524f-106">Pour désigner une propriété ou un champ comme clé primaire</span><span class="sxs-lookup"><span data-stu-id="6524f-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="6524f-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6524f-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="6524f-108">Affectez la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6524f-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6524f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6524f-109">See also</span></span>

- [<span data-ttu-id="6524f-110">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6524f-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="6524f-111">Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="6524f-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
