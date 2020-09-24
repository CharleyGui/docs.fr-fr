---
title: 'Procédure : Mapper des hiérarchies d’héritage'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: c0709fde96a5d2f39f04a08ccd24ddf90c782f30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166415"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="9816c-102">Procédure : Mapper des hiérarchies d’héritage</span><span class="sxs-lookup"><span data-stu-id="9816c-102">How to: Map Inheritance Hierarchies</span></span>

<span data-ttu-id="9816c-103">Pour implémenter le mappage d’héritage dans LINQ, vous devez spécifier les attributs et les propriétés d’attribut sur la classe racine de la hiérarchie d’héritage, comme décrit dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="9816c-103">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="9816c-104">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour mapper des hiérarchies d’héritage.</span><span class="sxs-lookup"><span data-stu-id="9816c-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="9816c-105">Consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="9816c-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9816c-106">Les sous-classes ne requièrent pas de propriétés ni d'attributs spéciaux.</span><span class="sxs-lookup"><span data-stu-id="9816c-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="9816c-107">Notez surtout que les sous-classes n'ont pas l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9816c-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="9816c-108">Pour mapper une hiérarchie d'héritage</span><span class="sxs-lookup"><span data-stu-id="9816c-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="9816c-109">Ajoutez l'attribut <xref:System.Data.Linq.Mapping.TableAttribute> à la classe racine.</span><span class="sxs-lookup"><span data-stu-id="9816c-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="9816c-110">Ajoutez-lui également un attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> pour chaque classe dans la structure hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="9816c-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="9816c-111">Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, définissez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="9816c-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="9816c-112">Cette propriété contient une valeur qui apparaît dans la table de base de données dans la colonne <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour indiquer à quelle classe ou sous-classe appartient cette ligne de données.</span><span class="sxs-lookup"><span data-stu-id="9816c-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="9816c-113">Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, ajoutez également une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="9816c-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="9816c-114">Cette propriété contient une valeur qui spécifie la classe ou la sous-classe que la valeur de clé désigne.</span><span class="sxs-lookup"><span data-stu-id="9816c-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="9816c-115">Ajoutez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> à un seul des attributs <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.</span><span class="sxs-lookup"><span data-stu-id="9816c-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="9816c-116">Cette propriété sert à désigner un mappage de *secours* lorsque la valeur de discriminateur de la table de base de données ne correspond à aucune <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valeur dans les mappages d’héritage.</span><span class="sxs-lookup"><span data-stu-id="9816c-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="9816c-117">Ajoutez une propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9816c-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="9816c-118">Cette propriété signifie qu'il s'agit de la colonne qui contient la valeur <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="9816c-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9816c-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9816c-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9816c-120">Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour configurer l’héritage.</span><span class="sxs-lookup"><span data-stu-id="9816c-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="9816c-121">Consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="9816c-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="9816c-122">Dans l’exemple de code suivant, `Vehicle` est défini en tant que classe racine, et les étapes précédentes ont été implémentées pour décrire la hiérarchie pour Linq.</span><span class="sxs-lookup"><span data-stu-id="9816c-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9816c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9816c-123">See also</span></span>

- [<span data-ttu-id="9816c-124">Prise en charge de l'héritage</span><span class="sxs-lookup"><span data-stu-id="9816c-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="9816c-125">Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code</span><span class="sxs-lookup"><span data-stu-id="9816c-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
