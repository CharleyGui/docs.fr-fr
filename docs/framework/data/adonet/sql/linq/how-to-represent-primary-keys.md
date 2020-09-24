---
title: 'Procédure : Représenter les clés primaires'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 02570176c8aef5cfdc7ba09fd6976f430900e8df
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166233"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="1e22e-102">Procédure : Représenter les clés primaires</span><span class="sxs-lookup"><span data-stu-id="1e22e-102">How to: Represent Primary Keys</span></span>

<span data-ttu-id="1e22e-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> propriété sur l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner une propriété ou un champ afin de représenter la clé primaire d’une colonne de base de données.</span><span class="sxs-lookup"><span data-stu-id="1e22e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="1e22e-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e22e-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1e22e-105">ne prend pas en charge les colonnes calculées en tant que clés primaires.</span><span class="sxs-lookup"><span data-stu-id="1e22e-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="1e22e-106">Pour désigner une propriété ou un champ comme clé primaire</span><span class="sxs-lookup"><span data-stu-id="1e22e-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="1e22e-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1e22e-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="1e22e-108">Affectez la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="1e22e-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e22e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e22e-109">See also</span></span>

- [<span data-ttu-id="1e22e-110">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e22e-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="1e22e-111">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="1e22e-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
