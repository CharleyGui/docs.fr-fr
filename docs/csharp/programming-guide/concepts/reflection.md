---
title: Réflexion (C#)
description: La réflexion fournit des objets qui décrivent les assemblys, les modules et les types en C#. Si votre code comprend des attributs, la réflexion vous permet d’y accéder.
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302800"
---
# <a name="reflection-c"></a><span data-ttu-id="f7543-104">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="f7543-104">Reflection (C#)</span></span>

<span data-ttu-id="f7543-105">La réflexion fournit des objets (de type <xref:System.Type> ) qui décrivent les assemblys, les modules et les types.</span><span class="sxs-lookup"><span data-stu-id="f7543-105">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="f7543-106">Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="f7543-106">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="f7543-107">Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="f7543-107">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="f7543-108">Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7543-108">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="f7543-109">Voici un exemple simple de réflexion à l’aide de la <xref:System.Object.GetType> méthode, héritée par tous les types de la `Object` classe de base, pour obtenir le type d’une variable :</span><span class="sxs-lookup"><span data-stu-id="f7543-109">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="f7543-110">Veillez à ajouter `using System;` et `using System.Reflection;` en haut de votre fichier *. cs* .</span><span class="sxs-lookup"><span data-stu-id="f7543-110">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="f7543-111">La sortie est : `System.Int32` .</span><span class="sxs-lookup"><span data-stu-id="f7543-111">The output is: `System.Int32`.</span></span>

<span data-ttu-id="f7543-112">L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="f7543-112">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="f7543-113">La sortie est : `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` .</span><span class="sxs-lookup"><span data-stu-id="f7543-113">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="f7543-114">Les mots clés C# `protected` et `internal` n’ont aucune signification en langage intermédiaire et ne sont pas utilisés dans les API de réflexion.</span><span class="sxs-lookup"><span data-stu-id="f7543-114">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="f7543-115">Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="f7543-115">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="f7543-116">Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7543-116">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="f7543-117">Pour identifier une méthode `protected internal`, utilisez <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7543-117">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="f7543-118">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="f7543-118">Reflection overview</span></span>

<span data-ttu-id="f7543-119">La réflexion est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7543-119">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="f7543-120">Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme.</span><span class="sxs-lookup"><span data-stu-id="f7543-120">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="f7543-121">Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f7543-121">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="f7543-122">Pour examiner et instancier des types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="f7543-122">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="f7543-123">Pour créer de nouveaux types au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7543-123">For building new types at runtime.</span></span> <span data-ttu-id="f7543-124">Utilisez des classes dans <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="f7543-124">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="f7543-125">Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7543-125">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="f7543-126">Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7543-126">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="f7543-127">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="f7543-127">Related sections</span></span>

<span data-ttu-id="f7543-128">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="f7543-128">For more information:</span></span>

- [<span data-ttu-id="f7543-129">Réflexion</span><span class="sxs-lookup"><span data-stu-id="f7543-129">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="f7543-130">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="f7543-130">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="f7543-131">Réflexion et types génériques</span><span class="sxs-lookup"><span data-stu-id="f7543-131">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="f7543-132">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="f7543-132">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="f7543-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7543-133">See also</span></span>

- [<span data-ttu-id="f7543-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f7543-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f7543-135">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="f7543-135">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
