---
description: get - Référence C#
title: get - Référence C#
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139734"
---
# <a name="get-c-reference"></a><span data-ttu-id="f38bf-103">get (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f38bf-103">get (C# Reference)</span></span>

<span data-ttu-id="f38bf-104">Le mot clé `get` définit une méthode *Accessor* dans une propriété ou un indexeur qui retourne la valeur de la propriété ou l’élément de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="f38bf-104">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="f38bf-105">Pour plus d’informations, consultez [Propriétés](../../programming-guide/classes-and-structs/properties.md), [Propriétés implémentées automatiquement](../../programming-guide/classes-and-structs/auto-implemented-properties.md) et [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f38bf-105">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="f38bf-106">L’exemple suivant définit un accesseur `get` et un accesseur `set` pour une propriété nommée `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="f38bf-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="f38bf-107">Il utilise un champ privé nommé `_seconds` pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f38bf-107">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="f38bf-108">Souvent, l’accesseur `get` se compose d’une seule instruction qui retourne une valeur, comme dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="f38bf-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="f38bf-109">À compter de C# 7.0, vous pouvez implémenter l’accesseur `get` comme membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="f38bf-109">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="f38bf-110">L’exemple suivant implémente l’accesseur `get` et l’accesseur `set` en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="f38bf-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="f38bf-111">Pour les cas simples dans lesquels les accesseurs `get` et `set` de la propriété n’effectuent aucune autre opération que la définition ou la récupération d’une valeur dans un champ de stockage privé, vous pouvez tirer parti de la prise en charge des propriétés implémentées automatiquement fournies par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="f38bf-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="f38bf-112">L’exemple suivant implémente `Hours` en tant que propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="f38bf-112">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f38bf-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f38bf-113">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f38bf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f38bf-114">See also</span></span>

- [<span data-ttu-id="f38bf-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f38bf-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f38bf-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f38bf-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f38bf-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="f38bf-117">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f38bf-118">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f38bf-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
