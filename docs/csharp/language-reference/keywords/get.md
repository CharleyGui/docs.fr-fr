---
title: get - Référence C#
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: d6c0452a7890a6ade480054115c1383199a3f91c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713492"
---
# <a name="get-c-reference"></a><span data-ttu-id="97af1-102">get (référence C#)</span><span class="sxs-lookup"><span data-stu-id="97af1-102">get (C# Reference)</span></span>

<span data-ttu-id="97af1-103">Le mot clé `get` définit une méthode *Accessor* dans une propriété ou un indexeur qui retourne la valeur de la propriété ou l’élément de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="97af1-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="97af1-104">Pour plus d’informations, consultez [Propriétés](../../programming-guide/classes-and-structs/properties.md), [Propriétés implémentées automatiquement](../../programming-guide/classes-and-structs/auto-implemented-properties.md) et [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="97af1-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="97af1-105">L’exemple suivant définit un accesseur `get` et un accesseur `set` pour une propriété nommée `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="97af1-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="97af1-106">Il utilise un champ privé nommé `_seconds` pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="97af1-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="97af1-107">Souvent, l’accesseur `get` se compose d’une seule instruction qui retourne une valeur, comme dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="97af1-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="97af1-108">À compter de C# 7.0, vous pouvez implémenter l’accesseur `get` comme membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="97af1-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="97af1-109">L’exemple suivant implémente l’accesseur `get` et l’accesseur `set` en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="97af1-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="97af1-110">Pour les cas simples dans lesquels les accesseurs `get` et `set` d’une propriété n’effectuent aucune autre opération que la définition ou la récupération d’une valeur dans un champ de stockage privé, vous pouvez tirer parti de la prise en charge par le compilateur C# des propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="97af1-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="97af1-111">L’exemple suivant implémente `Hours` en tant que propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="97af1-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="97af1-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="97af1-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97af1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97af1-113">See also</span></span>

- [<span data-ttu-id="97af1-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="97af1-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97af1-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="97af1-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="97af1-116">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="97af1-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="97af1-117">Propriétés</span><span class="sxs-lookup"><span data-stu-id="97af1-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
