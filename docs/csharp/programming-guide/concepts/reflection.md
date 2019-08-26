---
title: Réflexion (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 9b4322d83ad43cd3e49647df49c15bb5c917e1be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924088"
---
# <a name="reflection-c"></a><span data-ttu-id="292b7-102">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="292b7-102">Reflection (C#)</span></span>
<span data-ttu-id="292b7-103">La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent des assemblys, des modules et des types.</span><span class="sxs-lookup"><span data-stu-id="292b7-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="292b7-104">Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="292b7-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="292b7-105">Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="292b7-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="292b7-106">Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="292b7-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="292b7-107">Voici un exemple simple de réflexion utilisant la méthode statique `GetType`, héritée par tous les types à partir de la classe de base `Object`, pour obtenir le type d’une variable :</span><span class="sxs-lookup"><span data-stu-id="292b7-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="292b7-108">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="292b7-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="292b7-109">L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="292b7-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="292b7-110">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="292b7-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> <span data-ttu-id="292b7-111">Les mots clés C# `protected` et `internal` n’ont aucune signification en langage intermédiaire et ne sont pas utilisés dans les API de réflexion.</span><span class="sxs-lookup"><span data-stu-id="292b7-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="292b7-112">Les termes correspondants en langage intermédiaire sont *Family* et *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="292b7-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="292b7-113">Pour identifier une méthode `internal` à l’aide de la réflexion, utilisez la propriété <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="292b7-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="292b7-114">Pour identifier une méthode `protected internal`, utilisez <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="292b7-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="292b7-115">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="292b7-115">Reflection Overview</span></span>  
 <span data-ttu-id="292b7-116">La réflexion est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="292b7-116">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="292b7-117">Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme.</span><span class="sxs-lookup"><span data-stu-id="292b7-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="292b7-118">Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="292b7-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="292b7-119">Pour examiner et instancier des types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="292b7-119">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="292b7-120">Pour créer de nouveaux types au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="292b7-120">For building new types at runtime.</span></span> <span data-ttu-id="292b7-121">Utilisez des classes dans <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="292b7-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="292b7-122">Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="292b7-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="292b7-123">Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="292b7-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="292b7-124">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="292b7-124">Related Sections</span></span>  
 <span data-ttu-id="292b7-125">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="292b7-125">For more information:</span></span>  
  
- [<span data-ttu-id="292b7-126">Réflexion</span><span class="sxs-lookup"><span data-stu-id="292b7-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="292b7-127">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="292b7-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="292b7-128">Réflexion et types génériques</span><span class="sxs-lookup"><span data-stu-id="292b7-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="292b7-129">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="292b7-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="292b7-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="292b7-130">See also</span></span>

- [<span data-ttu-id="292b7-131">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="292b7-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="292b7-132">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="292b7-132">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
