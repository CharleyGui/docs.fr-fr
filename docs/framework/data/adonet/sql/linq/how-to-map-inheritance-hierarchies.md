---
title: 'Procédure : Mapper des hiérarchies d’héritage'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: e0ff3fe98fcd9ced0063d2bec85928504ea19bab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743190"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="041b3-102">Procédure : Mapper des hiérarchies d’héritage</span><span class="sxs-lookup"><span data-stu-id="041b3-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="041b3-103">Pour implémenter un mappage d'héritage dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage, comme décrit dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="041b3-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="041b3-104">Les développeurs qui utilisent Visual Studio peuvent utiliser le concepteur objet/relationnel pour mapper des hiérarchies d’héritage.</span><span class="sxs-lookup"><span data-stu-id="041b3-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="041b3-105">Voir [Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="041b3-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="041b3-106">Les sous-classes ne requièrent pas de propriétés ni d'attributs spéciaux.</span><span class="sxs-lookup"><span data-stu-id="041b3-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="041b3-107">Notez surtout que les sous-classes n'ont pas l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="041b3-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="041b3-108">Pour mapper une hiérarchie d'héritage</span><span class="sxs-lookup"><span data-stu-id="041b3-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="041b3-109">Ajoutez l'attribut <xref:System.Data.Linq.Mapping.TableAttribute> à la classe racine.</span><span class="sxs-lookup"><span data-stu-id="041b3-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="041b3-110">Ajoutez-lui également un attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> pour chaque classe dans la structure hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="041b3-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="041b3-111">Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, définissez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="041b3-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="041b3-112">Cette propriété contient une valeur qui apparaît dans la table de base de données dans la colonne <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour indiquer à quelle classe ou sous-classe appartient cette ligne de données.</span><span class="sxs-lookup"><span data-stu-id="041b3-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="041b3-113">Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, ajoutez également une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="041b3-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="041b3-114">Cette propriété contient une valeur qui spécifie la classe ou la sous-classe que la valeur de clé désigne.</span><span class="sxs-lookup"><span data-stu-id="041b3-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="041b3-115">Ajoutez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> à un seul des attributs <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.</span><span class="sxs-lookup"><span data-stu-id="041b3-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="041b3-116">Cette propriété sert à désigner un *secours* mappage lorsque la valeur de discriminateur de la table de base de données ne correspond pas aux <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valeur dans les mappages d’héritage.</span><span class="sxs-lookup"><span data-stu-id="041b3-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="041b3-117">Ajoutez une propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="041b3-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="041b3-118">Cette propriété signifie qu'il s'agit de la colonne qui contient la valeur <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="041b3-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="041b3-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="041b3-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="041b3-120">Si vous utilisez Visual Studio, vous pouvez utiliser le concepteur objet/relationnel pour configurer l’héritage.</span><span class="sxs-lookup"><span data-stu-id="041b3-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="041b3-121">Voir [Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="041b3-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="041b3-122">Dans l'exemple de code suivant, `Vehicle` est défini comme classe racine. Les étapes précédentes ont été implémentées pour décrire la hiérarchie de [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="041b3-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="041b3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="041b3-123">See also</span></span>

- [<span data-ttu-id="041b3-124">Prise en charge de l’héritage</span><span class="sxs-lookup"><span data-stu-id="041b3-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="041b3-125">Guide pratique pour Personnaliser des Classes d’entité à l’aide de l’éditeur de Code</span><span class="sxs-lookup"><span data-stu-id="041b3-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
