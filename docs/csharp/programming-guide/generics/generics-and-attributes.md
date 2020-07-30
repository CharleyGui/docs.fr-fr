---
title: Génériques et attributs - Guide de programmation C#
description: En savoir plus sur l’application d’attributs aux types génériques. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299875"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="ffec2-104">Génériques et attributs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ffec2-104">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="ffec2-105">Les attributs peuvent être appliqués aux types génériques de la même manière qu’aux types non génériques.</span><span class="sxs-lookup"><span data-stu-id="ffec2-105">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="ffec2-106">Pour plus d’informations sur l’application des attributs, consultez [Attributs](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ffec2-106">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="ffec2-107">Les attributs personnalisés sont uniquement autorisés à référencer des types génériques ouverts, qui sont des types génériques pour lesquels aucun argument de type n’est fourni, et des types génériques construits fermés, qui fournissent des arguments pour tous les paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="ffec2-107">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="ffec2-108">Les exemples suivants utilisent cet attribut personnalisé :</span><span class="sxs-lookup"><span data-stu-id="ffec2-108">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="ffec2-109">Un attribut peut référencer un type générique ouvert :</span><span class="sxs-lookup"><span data-stu-id="ffec2-109">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="ffec2-110">Spécifiez plusieurs paramètres de type à l’aide du nombre approprié de virgules.</span><span class="sxs-lookup"><span data-stu-id="ffec2-110">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="ffec2-111">Dans cet exemple, `GenericClass2` a deux paramètres de type :</span><span class="sxs-lookup"><span data-stu-id="ffec2-111">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="ffec2-112">Un attribut peut référencer un type générique construit fermé :</span><span class="sxs-lookup"><span data-stu-id="ffec2-112">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="ffec2-113">Un attribut qui référence un paramètre de type générique entraîne une erreur de compilation :</span><span class="sxs-lookup"><span data-stu-id="ffec2-113">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="ffec2-114">Un type générique ne peut pas hériter d’<xref:System.Attribute> :</span><span class="sxs-lookup"><span data-stu-id="ffec2-114">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="ffec2-115">Pour obtenir des informations sur un type générique ou un paramètre de type au moment de l’exécution, vous pouvez utiliser les méthodes de <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="ffec2-115">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="ffec2-116">Pour plus d’informations, consultez [Génériques et réflexion](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="ffec2-116">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffec2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffec2-117">See also</span></span>

- [<span data-ttu-id="ffec2-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ffec2-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ffec2-119">Génériques</span><span class="sxs-lookup"><span data-stu-id="ffec2-119">Generics</span></span>](./index.md)
- [<span data-ttu-id="ffec2-120">Attributs</span><span class="sxs-lookup"><span data-stu-id="ffec2-120">Attributes</span></span>](../../../standard/attributes/index.md)
