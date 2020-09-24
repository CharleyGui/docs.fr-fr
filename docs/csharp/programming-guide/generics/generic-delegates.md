---
title: Délégués génériques - Guide de programmation C#
description: En savoir plus sur l’utilisation de délégués génériques en C#. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: df417701feb77dc47cff1cdd68eb4c7405d15beb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157406"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="29874-104">Délégués génériques (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="29874-104">Generic Delegates (C# Programming Guide)</span></span>

<span data-ttu-id="29874-105">Un [délégué](../../language-reference/builtin-types/reference-types.md) peut définir ses propres paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="29874-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="29874-106">Le code qui référence le délégué générique peut spécifier l’argument de type pour créer un type construit fermé, comme lors de l’instanciation d’une classe générique ou d’un appel d’une méthode générique, ainsi que l’illustre l’exemple ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="29874-106">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="29874-107">Le langage C# version 2.0 propose une nouvelle fonctionnalité appelée conversion de groupe de méthodes, qui s’applique aussi bien aux types concrets qu’aux types délégués génériques et vous permet d’écrire la ligne précédente avec la syntaxe simplifiée suivante :</span><span class="sxs-lookup"><span data-stu-id="29874-107">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="29874-108">Les délégués définis dans une classe générique peuvent utiliser les paramètres de type de classe générique, à l’instar des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="29874-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="29874-109">Le code qui référence le délégué doit spécifier l’argument de type de la classe conteneur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="29874-109">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="29874-110">Les délégués génériques sont particulièrement utiles pour définir des événements basés sur le modèle de design type parce que l’argument de l’expéditeur peut être fortement typé et il n’est plus nécessaire d’en effectuer un cast vers et depuis <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="29874-110">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="29874-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29874-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="29874-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="29874-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29874-113">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="29874-113">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="29874-114">Méthodes génériques</span><span class="sxs-lookup"><span data-stu-id="29874-114">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="29874-115">Classes génériques</span><span class="sxs-lookup"><span data-stu-id="29874-115">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="29874-116">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="29874-116">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="29874-117">Délégués</span><span class="sxs-lookup"><span data-stu-id="29874-117">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="29874-118">Génériques</span><span class="sxs-lookup"><span data-stu-id="29874-118">Generics</span></span>](../../../standard/generics/index.md)
