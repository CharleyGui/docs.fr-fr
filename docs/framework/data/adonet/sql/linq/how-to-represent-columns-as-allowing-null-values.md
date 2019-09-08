---
title: 'Procédure : Représenter des colonnes en tant que colonnes autorisant les valeurs Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781809"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="cfc09-102">Procédure : Représenter des colonnes en tant que colonnes autorisant les valeurs Null</span><span class="sxs-lookup"><span data-stu-id="cfc09-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="cfc09-103">Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> propriété sur l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour spécifier que la colonne de base de données associée peut contenir des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="cfc09-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="cfc09-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="cfc09-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="cfc09-105">Pour désigner une colonne comme autorisant des valeurs null</span><span class="sxs-lookup"><span data-stu-id="cfc09-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="cfc09-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cfc09-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="cfc09-107">Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="cfc09-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc09-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfc09-108">See also</span></span>

- [<span data-ttu-id="cfc09-109">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cfc09-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="cfc09-110">Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="cfc09-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
