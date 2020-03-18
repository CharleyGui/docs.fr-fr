---
title: Réflexion (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711659"
---
# <a name="reflection-c"></a><span data-ttu-id="6dfe8-102">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="6dfe8-102">Reflection (C#)</span></span>

<span data-ttu-id="6dfe8-103">Réflexion fournit des <xref:System.Type>objets (de type) qui décrivent les assemblages, les modules et les types.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="6dfe8-104">Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="6dfe8-105">Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="6dfe8-106">Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="6dfe8-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="6dfe8-107">Voici un exemple simple de <xref:System.Object.GetType> réflexion utilisant la méthode `Object` - héritée par tous les types de la classe de base - pour obtenir le type de variable :</span><span class="sxs-lookup"><span data-stu-id="6dfe8-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="6dfe8-108">Assurez-vous `using System;` d’ajouter et `using System.Reflection;` en haut de votre fichier *.cs.*</span><span class="sxs-lookup"><span data-stu-id="6dfe8-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="6dfe8-109">La sortie `System.Int32`est: .</span><span class="sxs-lookup"><span data-stu-id="6dfe8-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="6dfe8-110">L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="6dfe8-111">La sortie `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`est: .</span><span class="sxs-lookup"><span data-stu-id="6dfe8-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="6dfe8-112">Les mots clés C# `protected` et `internal` n’ont aucune signification en langage intermédiaire et ne sont pas utilisés dans les API de réflexion.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="6dfe8-113">Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="6dfe8-114">Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="6dfe8-115">Pour identifier une méthode `protected internal`, utilisez <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="6dfe8-116">Aperçu de la réflexion</span><span class="sxs-lookup"><span data-stu-id="6dfe8-116">Reflection overview</span></span>

<span data-ttu-id="6dfe8-117">La réflexion est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dfe8-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="6dfe8-118">Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="6dfe8-119">Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6dfe8-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="6dfe8-120">Pour examiner et instancier des types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="6dfe8-121">Pour créer de nouveaux types au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-121">For building new types at runtime.</span></span> <span data-ttu-id="6dfe8-122">Utilisez des classes dans <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="6dfe8-123">Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6dfe8-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="6dfe8-124">Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="6dfe8-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="6dfe8-125">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="6dfe8-125">Related sections</span></span>

<span data-ttu-id="6dfe8-126">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="6dfe8-126">For more information:</span></span>

- [<span data-ttu-id="6dfe8-127">Réflexion</span><span class="sxs-lookup"><span data-stu-id="6dfe8-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="6dfe8-128">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="6dfe8-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="6dfe8-129">Réflexion et types génériques</span><span class="sxs-lookup"><span data-stu-id="6dfe8-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="6dfe8-130">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="6dfe8-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="6dfe8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfe8-131">See also</span></span>

- [<span data-ttu-id="6dfe8-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6dfe8-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6dfe8-133">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="6dfe8-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
