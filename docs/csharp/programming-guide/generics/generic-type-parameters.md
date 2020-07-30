---
title: Paramètres de type générique - Guide de programmation C#
description: En savoir plus sur la définition de type générique en C#, où un paramètre de type est un espace réservé pour un type que le client spécifie pour une instance du type générique.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: dc37029378ac1e9ec194d95b561787761d69a9fd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299251"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="73526-103">Paramètres de type générique (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="73526-103">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="73526-104">Dans une définition de méthode ou de type générique, le paramètre de type représente un espace réservé pour un type spécifié par le client au moment de créer une instance du type générique.</span><span class="sxs-lookup"><span data-stu-id="73526-104">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="73526-105">Une classe générique, telle que `GenericList<T>` répertoriée dans [Introduction aux génériques](./index.md), ne peut pas être utilisée en l’état car il ne s’agit pas vraiment d’un type, mais plutôt d’un modèle pour un type.</span><span class="sxs-lookup"><span data-stu-id="73526-105">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="73526-106">Pour utiliser `GenericList<T>`, le code client doit déclarer et instancier un type construit en spécifiant un argument de type à l’intérieur de crochets pointus.</span><span class="sxs-lookup"><span data-stu-id="73526-106">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="73526-107">L’argument de type pour cette classe particulière peut être tout type reconnu par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="73526-107">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="73526-108">Il est possible de créer un nombre quelconque d’instances de type construit, chacune avec un argument de type différent, comme suit :</span><span class="sxs-lookup"><span data-stu-id="73526-108">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="73526-109">Dans chacune de ces instances de `GenericList<T>`, chaque occurrence de `T` dans la classe est remplacée à l’exécution par l’argument de type.</span><span class="sxs-lookup"><span data-stu-id="73526-109">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="73526-110">Par cette substitution, nous avons créé trois objets distincts de type sécurisé et efficaces à l’aide d’une seule définition de classe.</span><span class="sxs-lookup"><span data-stu-id="73526-110">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="73526-111">Pour plus d’informations sur la façon dont cette substitution est exécutée par le CLR, consultez [Génériques dans le runtime](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="73526-111">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="73526-112">Recommandations concernant le nom des paramètres de type</span><span class="sxs-lookup"><span data-stu-id="73526-112">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="73526-113">**Nommez** les paramètres de type générique avec des noms descriptifs, sauf si un nom composé d’une seule lettre est suffisamment évocateur et qu’un nom descriptif n’apporte rien de plus.</span><span class="sxs-lookup"><span data-stu-id="73526-113">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="73526-114">**Envisagez** l’utilisation de T comme nom de paramètre de type pour les types ayant un paramètre de type d’une seule lettre.</span><span class="sxs-lookup"><span data-stu-id="73526-114">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="73526-115">**Préfixez** les noms des paramètres de type descriptifs avec « T ».</span><span class="sxs-lookup"><span data-stu-id="73526-115">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="73526-116">**Pensez** à indiquer les contraintes placées sur un paramètre de type dans le nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="73526-116">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="73526-117">Par exemple, un paramètre limité à `ISession` peut être appelé `TSession`.</span><span class="sxs-lookup"><span data-stu-id="73526-117">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="73526-118">La règle d’analyse du code [CA1715](/visualstudio/code-quality/ca1715) vérifie que les paramètres de type sont correctement nommés.</span><span class="sxs-lookup"><span data-stu-id="73526-118">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="73526-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73526-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="73526-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="73526-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="73526-121">Génériques</span><span class="sxs-lookup"><span data-stu-id="73526-121">Generics</span></span>](./index.md)
- [<span data-ttu-id="73526-122">Différences entre les modèles C++ et les génériques C#</span><span class="sxs-lookup"><span data-stu-id="73526-122">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
