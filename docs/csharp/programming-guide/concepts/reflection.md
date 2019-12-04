---
title: Réflexion (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711659"
---
# <a name="reflection-c"></a><span data-ttu-id="41622-102">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="41622-102">Reflection (C#)</span></span>

<span data-ttu-id="41622-103">La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent les assemblys, les modules et les types.</span><span class="sxs-lookup"><span data-stu-id="41622-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="41622-104">Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="41622-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="41622-105">Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="41622-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="41622-106">Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="41622-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="41622-107">Voici un exemple simple de réflexion à l’aide de la méthode <xref:System.Object.GetType>, héritée par tous les types de la classe de base `Object`, pour obtenir le type d’une variable :</span><span class="sxs-lookup"><span data-stu-id="41622-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="41622-108">Veillez à ajouter `using System;` et `using System.Reflection;` en haut de votre fichier *. cs* .</span><span class="sxs-lookup"><span data-stu-id="41622-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="41622-109">La sortie est la suivante : `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="41622-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="41622-110">L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="41622-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="41622-111">La sortie est la suivante : `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="41622-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="41622-112">Les mots clés C# `protected` et `internal` n’ont aucune signification en langage intermédiaire et ne sont pas utilisés dans les API de réflexion.</span><span class="sxs-lookup"><span data-stu-id="41622-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="41622-113">Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="41622-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="41622-114">Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="41622-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="41622-115">Pour identifier une méthode `protected internal`, utilisez <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="41622-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="41622-116">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="41622-116">Reflection overview</span></span>

<span data-ttu-id="41622-117">La réflexion est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="41622-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="41622-118">Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme.</span><span class="sxs-lookup"><span data-stu-id="41622-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="41622-119">Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="41622-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="41622-120">Pour examiner et instancier des types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="41622-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="41622-121">Pour créer de nouveaux types au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="41622-121">For building new types at runtime.</span></span> <span data-ttu-id="41622-122">Utilisez des classes dans <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="41622-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="41622-123">Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="41622-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="41622-124">Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="41622-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="41622-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="41622-125">Related sections</span></span>

<span data-ttu-id="41622-126">Pour plus d'informations, consultez .</span><span class="sxs-lookup"><span data-stu-id="41622-126">For more information:</span></span>

- [<span data-ttu-id="41622-127">Réflexion</span><span class="sxs-lookup"><span data-stu-id="41622-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="41622-128">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="41622-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="41622-129">Réflexion et types génériques</span><span class="sxs-lookup"><span data-stu-id="41622-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="41622-130">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="41622-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="41622-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41622-131">See also</span></span>

- [<span data-ttu-id="41622-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="41622-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41622-133">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="41622-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
