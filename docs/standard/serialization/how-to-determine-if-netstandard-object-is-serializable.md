---
title: Comment déterminer si un objet .NET Standard est sérialisable
description: Montre comment déterminer si un type de .NET Standard peut être sérialisé au moment de l’exécution.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: a425d44ac3b58a568bd51e638f28a2b76ced9dec
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223989"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="39b63-103">Comment déterminer si un objet .NET Standard est sérialisable</span><span class="sxs-lookup"><span data-stu-id="39b63-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="39b63-104">.NET Standard est une spécification qui définit les types et les membres qui doivent être présents sur des implémentations .NET spécifiques qui se conforment à cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="39b63-104">.NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="39b63-105">Toutefois, .NET Standard ne définit pas si un type est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="39b63-105">However, .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="39b63-106">Les types définis dans la bibliothèque de .NET Standard ne sont pas marqués avec l' <xref:System.SerializableAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="39b63-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="39b63-107">Au lieu de cela, des implémentations .NET spécifiques, telles que les .NET Framework et .NET Core, sont libres de déterminer si un type particulier est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="39b63-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="39b63-108">Si vous avez développé une bibliothèque qui cible .NET Standard, votre bibliothèque peut être consommée par n’importe quelle implémentation .NET qui prend en charge .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="39b63-108">If you've developed a library that targets .NET Standard, your library can be consumed by any .NET implementation that supports .NET Standard.</span></span> <span data-ttu-id="39b63-109">Cela signifie que vous ne pouvez pas savoir à l’avance si un type particulier est sérialisable ; vous pouvez uniquement déterminer si elle est sérialisable au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="39b63-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="39b63-110">Vous pouvez déterminer si un objet est sérialisable au moment de l’exécution en extrayant la valeur de la <xref:System.Type.IsSerializable> propriété d’un <xref:System.Type> objet qui représente le type de cet objet.</span><span class="sxs-lookup"><span data-stu-id="39b63-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="39b63-111">L’exemple suivant fournit une implémentation.</span><span class="sxs-lookup"><span data-stu-id="39b63-111">The following example provides one implementation.</span></span> <span data-ttu-id="39b63-112">Il définit une `IsSerializable(Object)` méthode d’extension qui indique si une <xref:System.Object> instance de peut être sérialisée.</span><span class="sxs-lookup"><span data-stu-id="39b63-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="39b63-113">Vous pouvez ensuite passer n’importe quel objet à la méthode pour déterminer s’il peut être sérialisé et désérialisé sur l’implémentation .NET actuelle, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="39b63-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="39b63-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39b63-114">See also</span></span>

- [<span data-ttu-id="39b63-115">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="39b63-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
