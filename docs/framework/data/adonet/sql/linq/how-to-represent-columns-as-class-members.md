---
title: 'Procédure : Représenter des colonnes en tant que membres de classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793515"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="330be-102">Procédure : Représenter des colonnes en tant que membres de classe</span><span class="sxs-lookup"><span data-stu-id="330be-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="330be-103">Utilisez l' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour associer un champ ou une propriété à une colonne de base de données.</span><span class="sxs-lookup"><span data-stu-id="330be-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="330be-104">Pour mapper un champ ou une propriété à une colonne de base de données</span><span class="sxs-lookup"><span data-stu-id="330be-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="330be-105">Ajoutez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> à la déclaration de propriété ou de champ.</span><span class="sxs-lookup"><span data-stu-id="330be-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="330be-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="330be-106">Example</span></span>  
 <span data-ttu-id="330be-107">Le code suivant mappe le champ `CustomerID` de la classe `Customer` à la colonne `CustomerID` de la table de base de données `Customers`.</span><span class="sxs-lookup"><span data-stu-id="330be-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="330be-108">Il n'est pas nécessaire de spécifier la propriété <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> si le nom peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="330be-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="330be-109">Si vous ne spécifiez pas de nom, on considère qu'il s'agit du même nom que pour la propriété ou le champ.</span><span class="sxs-lookup"><span data-stu-id="330be-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330be-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="330be-110">See also</span></span>

- [<span data-ttu-id="330be-111">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="330be-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="330be-112">Guide pratique : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="330be-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
