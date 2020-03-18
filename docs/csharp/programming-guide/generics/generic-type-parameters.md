---
title: Paramètres de type générique - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712180"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="7004f-102">Paramètres de type générique (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7004f-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="7004f-103">Dans une définition de méthode ou de type générique, le paramètre de type représente un espace réservé pour un type spécifié par le client au moment de créer une instance du type générique.</span><span class="sxs-lookup"><span data-stu-id="7004f-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="7004f-104">Une classe générique, telle que `GenericList<T>` répertoriée dans [Introduction aux génériques](./index.md), ne peut pas être utilisée en l’état car il ne s’agit pas vraiment d’un type, mais plutôt d’un modèle pour un type.</span><span class="sxs-lookup"><span data-stu-id="7004f-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="7004f-105">Pour utiliser `GenericList<T>`, le code client doit déclarer et instancier un type construit en spécifiant un argument de type à l’intérieur de crochets pointus.</span><span class="sxs-lookup"><span data-stu-id="7004f-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="7004f-106">L’argument de type pour cette classe particulière peut être tout type reconnu par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="7004f-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="7004f-107">Il est possible de créer un nombre quelconque d’instances de type construit, chacune avec un argument de type différent, comme suit :</span><span class="sxs-lookup"><span data-stu-id="7004f-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="7004f-108">Dans chacune de ces instances de `GenericList<T>`, chaque occurrence de `T` dans la classe est remplacée à l’exécution par l’argument de type.</span><span class="sxs-lookup"><span data-stu-id="7004f-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="7004f-109">Par cette substitution, nous avons créé trois objets distincts de type sécurisé et efficaces à l’aide d’une seule définition de classe.</span><span class="sxs-lookup"><span data-stu-id="7004f-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="7004f-110">Pour plus d’informations sur la façon dont cette substitution est exécutée par le CLR, consultez [Génériques dans le runtime](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="7004f-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="7004f-111">Recommandations concernant le nom des paramètres de type</span><span class="sxs-lookup"><span data-stu-id="7004f-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="7004f-112">**Nommez** les paramètres de type générique avec des noms descriptifs, sauf si un nom composé d’une seule lettre est suffisamment évocateur et qu’un nom descriptif n’apporte rien de plus.</span><span class="sxs-lookup"><span data-stu-id="7004f-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="7004f-113">**Envisagez** l’utilisation de T comme nom de paramètre de type pour les types ayant un paramètre de type d’une seule lettre.</span><span class="sxs-lookup"><span data-stu-id="7004f-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="7004f-114">**Préfixez** les noms des paramètres de type descriptifs avec « T ».</span><span class="sxs-lookup"><span data-stu-id="7004f-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="7004f-115">**Pensez** à indiquer les contraintes placées sur un paramètre de type dans le nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="7004f-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="7004f-116">Par exemple, un paramètre limité à `ISession` peut être appelé `TSession`.</span><span class="sxs-lookup"><span data-stu-id="7004f-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="7004f-117">La règle d’analyse du code [CA1715](/visualstudio/code-quality/ca1715) vérifie que les paramètres de type sont correctement nommés.</span><span class="sxs-lookup"><span data-stu-id="7004f-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7004f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7004f-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="7004f-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7004f-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7004f-120">Génériques</span><span class="sxs-lookup"><span data-stu-id="7004f-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="7004f-121">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="7004f-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
