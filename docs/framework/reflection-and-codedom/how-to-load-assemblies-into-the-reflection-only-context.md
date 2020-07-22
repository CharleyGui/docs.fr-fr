---
title: 'Procédure : charger des assemblys dans le contexte de réflexion uniquement'
description: Consultez un exemple de chargement d’assemblys dans le contexte de réflexion uniquement dans .NET. Examinez les assemblys compilés pour d’autres plateformes ou versions .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865071"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="4b5f7-104">Procédure : charger des assemblys dans le contexte de réflexion uniquement</span><span class="sxs-lookup"><span data-stu-id="4b5f7-104">How to: Load Assemblies into the Reflection-Only Context</span></span>

<span data-ttu-id="4b5f7-105">Le contexte de chargement de réflexion uniquement permet d’examiner des assemblys compilés pour d’autres plateformes ou d’autres versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-105">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="4b5f7-106">Le code chargé dans ce contexte peut uniquement être examiné. Il ne peut pas être exécuté.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-106">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="4b5f7-107">Cela signifie que les objets ne peuvent pas être créés, car les constructeurs ne peut pas être exécutés.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-107">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="4b5f7-108">Le code ne pouvant pas être exécuté, les dépendances ne sont pas chargées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-108">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="4b5f7-109">Si vous devez les examiner, vous devez les charger vous-même.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-109">If you need to examine them, you must load them yourself.</span></span>

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="4b5f7-110">Pour charger un assembly dans le contexte de chargement de réflexion uniquement</span><span class="sxs-lookup"><span data-stu-id="4b5f7-110">To load an assembly into the reflection-only load context</span></span>

1. <span data-ttu-id="4b5f7-111">Utilisez la surcharge de méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> pour charger l’assembly d’après son nom complet, ou la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> pour charger l’assembly d’après son chemin.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-111">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="4b5f7-112">Si l’assembly est une image binaire, utilisez la surcharge de méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-112">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4b5f7-113">Vous ne pouvez pas utiliser le contexte de réflexion uniquement pour charger une version de mscorlib.dll à partir d’une version du .NET Framework autre que la version dans le contexte d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-113">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>

2. <span data-ttu-id="4b5f7-114">Si l’assembly a des dépendances, la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ne les charge pas.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-114">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="4b5f7-115">Si vous devez les examiner, vous devez les charger vous-même.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-115">If you need to examine them, you must load them yourself.</span></span>

3. <span data-ttu-id="4b5f7-116">Déterminez si un assembly est chargé dans le contexte de réflexion uniquement à l’aide de la propriété <xref:System.Reflection.Assembly.ReflectionOnly%2A> de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-116">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>

4. <span data-ttu-id="4b5f7-117">Si des attributs ont été appliqués à l’assembly ou à des types dans l’assembly, examinez ces attributs à l’aide de la classe <xref:System.Reflection.CustomAttributeData> pour vérifier qu’aucune tentative d’exécution du code dans le contexte de réflexion uniquement n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-117">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="4b5f7-118">Utilisez la surcharge appropriée de la méthode <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> pour obtenir des objets <xref:System.Reflection.CustomAttributeData> représentant les attributs appliqués à un assembly, un membre, un module ou un paramètre.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-118">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4b5f7-119">Les attributs appliqués à l’assembly ou à son contenu peuvent être définis dans l’assembly, ou ils peuvent être définis dans un autre assembly chargé dans le contexte de réflexion uniquement.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-119">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="4b5f7-120">Il n’existe aucun moyen de savoir à l’avance où les attributs sont définis.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-120">There is no way to tell in advance where the attributes are defined.</span></span>

## <a name="example"></a><span data-ttu-id="4b5f7-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b5f7-121">Example</span></span>

<span data-ttu-id="4b5f7-122">L’exemple de code suivant montre comment examiner les attributs appliqués à un assembly chargé dans le contexte de réflexion uniquement.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-122">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>

<span data-ttu-id="4b5f7-123">L’exemple de code définit un attribut personnalisé avec deux constructeurs et une propriété.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-123">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="4b5f7-124">L’attribut est appliqué à l’assembly, à un type déclaré dans l’assembly, à une méthode du type, et à un paramètre de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-124">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="4b5f7-125">Lors de son exécution, l’assembly se charge dans le contexte de réflexion uniquement et affiche des informations sur les attributs personnalisés qui ont été appliqués sur lui-même et sur les types et membres qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-125">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>

> [!NOTE]
> <span data-ttu-id="4b5f7-126">Pour simplifier l’exemple de code, l’assembly se charge et s’examine lui-même.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-126">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="4b5f7-127">En règle générale, vous ne trouverez pas le même assembly chargé dans le contexte d’exécution et dans le contexte de réflexion uniquement.</span><span class="sxs-lookup"><span data-stu-id="4b5f7-127">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4b5f7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b5f7-128">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
