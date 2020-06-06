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
ms.openlocfilehash: b6791ae0666aeb0ac02d8a38ca419d7de2b263cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289601"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="c5ab0-103">Comment déterminer si un objet .NET Standard est sérialisable</span><span class="sxs-lookup"><span data-stu-id="c5ab0-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="c5ab0-104">Le .NET Standard est une spécification qui définit les types et les membres qui doivent être présents sur des implémentations .NET spécifiques qui se conforment à cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="c5ab0-105">Toutefois, le .NET Standard ne définit pas si un type est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="c5ab0-106">Les types définis dans la bibliothèque de .NET Standard ne sont pas marqués avec l' <xref:System.SerializableAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="c5ab0-107">Au lieu de cela, des implémentations .NET spécifiques, telles que les .NET Framework et .NET Core, sont libres de déterminer si un type particulier est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="c5ab0-108">Si vous avez développé une bibliothèque qui cible le .NET Standard, votre bibliothèque peut être consommée par n’importe quelle implémentation .NET qui prend en charge le .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="c5ab0-109">Cela signifie que vous ne pouvez pas savoir à l’avance si un type particulier est sérialisable ; vous pouvez uniquement déterminer si elle est sérialisable au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="c5ab0-110">Vous pouvez déterminer si un objet est sérialisable au moment de l’exécution en extrayant la valeur de la <xref:System.Type.IsSerializable> propriété d’un <xref:System.Type> objet qui représente le type de cet objet.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="c5ab0-111">L’exemple suivant fournit une implémentation.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-111">The following example provides one implementation.</span></span> <span data-ttu-id="c5ab0-112">Il définit une `IsSerializable(Object)` méthode d’extension qui indique si une <xref:System.Object> instance de peut être sérialisée.</span><span class="sxs-lookup"><span data-stu-id="c5ab0-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="c5ab0-113">Vous pouvez ensuite passer n’importe quel objet à la méthode pour déterminer s’il peut être sérialisé et désérialisé sur l’implémentation .NET actuelle, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c5ab0-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c5ab0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5ab0-114">See also</span></span>

- [<span data-ttu-id="c5ab0-115">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="c5ab0-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
