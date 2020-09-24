---
title: 'Procédure : Représenter des tables en tant que classes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: c02922351909b097dc06085eefbcc0f131350505
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166220"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="0b452-102">Procédure : Représenter des tables en tant que classes</span><span class="sxs-lookup"><span data-stu-id="0b452-102">How to: Represent Tables as Classes</span></span>

<span data-ttu-id="0b452-103">Utilisez l' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribut pour désigner une classe comme classe d’entité associée à une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="0b452-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="0b452-104">Pour mapper une classe à une table de base de données</span><span class="sxs-lookup"><span data-stu-id="0b452-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="0b452-105">Ajoutez l'attribut <xref:System.Data.Linq.Mapping.TableAttribute> à la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="0b452-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b452-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="0b452-106">Example</span></span>  

 <span data-ttu-id="0b452-107">Le code suivant établit la classe `Customer` comme une classe d'entité associée à la table de base de données `Customers`.</span><span class="sxs-lookup"><span data-stu-id="0b452-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="0b452-108">Il n'est pas nécessaire de spécifier la propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> si le nom peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="0b452-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="0b452-109">Si vous ne spécifiez pas de nom, on considère qu'il s'agit du même nom que pour la propriété ou le champ.</span><span class="sxs-lookup"><span data-stu-id="0b452-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b452-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b452-110">See also</span></span>

- [<span data-ttu-id="0b452-111">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0b452-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="0b452-112">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="0b452-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
