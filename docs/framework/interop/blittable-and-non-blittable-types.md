---
title: types blittable et non blittable
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: 816b854120f09efef69bd8ceb2d3650e5a8e7af0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123733"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="71c30-102">types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="71c30-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="71c30-103">La plupart des types de données ont une représentation commune à la fois dans la mémoire managée et non managée, et ne nécessitent pas de traitement particulier par le marshaleur d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="71c30-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="71c30-104">Ces types sont appelés *types blittables*, car ils ne nécessitent pas de conversion quand ils transitent entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="71c30-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="71c30-105">Les structures qui sont retournées par les appels de code non managé doivent être des types blittables.</span><span class="sxs-lookup"><span data-stu-id="71c30-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="71c30-106">L’appel de code non managé ne prend en charge aucune structure non blittable comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="71c30-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="71c30-107">Les types suivants issus de l’espace de noms <xref:System> sont des types blittables :</span><span class="sxs-lookup"><span data-stu-id="71c30-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="71c30-108">Les types complexes suivants sont également des types blittables :</span><span class="sxs-lookup"><span data-stu-id="71c30-108">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="71c30-109">Tableaux unidimensionnels de types blittables, comme un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="71c30-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="71c30-110">Toutefois, un type qui contient un tableau de variables de types blittables n’est pas lui-même blittable.</span><span class="sxs-lookup"><span data-stu-id="71c30-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="71c30-111">Types valeur mis en forme qui ne contiennent que des types blittables (et des classes s’ils sont marshalés comme types mis en forme).</span><span class="sxs-lookup"><span data-stu-id="71c30-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="71c30-112">Pour plus d’informations sur les types valeur mis en forme, consultez [Marshaling par défaut pour les types valeur](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="71c30-112">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="71c30-113">Les références d’objets ne sont pas blittables.</span><span class="sxs-lookup"><span data-stu-id="71c30-113">Object references are not blittable.</span></span> <span data-ttu-id="71c30-114">Cela inclut un tableau de références aux objets qui sont blittables en eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="71c30-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="71c30-115">Par exemple, vous pouvez définir une structure blittable, mais vous ne pouvez pas définir un type blittable contenant un tableau de références à ces structures.</span><span class="sxs-lookup"><span data-stu-id="71c30-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="71c30-116">Par souci d’optimisation, les tableaux de types et de classes blittables qui ne contiennent que des membres blittables sont [épinglés](copying-and-pinning.md) au lieu d’être copiés lors du marshaling.</span><span class="sxs-lookup"><span data-stu-id="71c30-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="71c30-117">Ces types semblent être marshalés en tant que paramètres en entrée/sortie quand l’appelant et l’appelé résident dans le même cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="71c30-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="71c30-118">Cependant, ces types sont en fait marshalés en tant que paramètres en entrée et vous devez appliquer les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> si vous voulez marshaler l’argument en tant que paramètre en entrée/sortie.</span><span class="sxs-lookup"><span data-stu-id="71c30-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="71c30-119">Certains types de données managés requièrent une représentation différente dans un environnement non managé.</span><span class="sxs-lookup"><span data-stu-id="71c30-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="71c30-120">Ces types de données non blittables doivent être convertis sous une forme qui peut être marshalée.</span><span class="sxs-lookup"><span data-stu-id="71c30-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="71c30-121">Par exemple, les chaînes managées sont des types non blittables parce qu’elles doivent être converties en objets String avant de pouvoir être marshalées.</span><span class="sxs-lookup"><span data-stu-id="71c30-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="71c30-122">Le tableau suivant répertorie des types non blittables issus de l’espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="71c30-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="71c30-123">Les [délégués](default-marshaling-behavior.md#default-marshaling-for-delegates), qui sont des structures de données qui réfèrent à une méthode statique ou à une instance de classe, sont également non blittables.</span><span class="sxs-lookup"><span data-stu-id="71c30-123">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="71c30-124">Type non blittable</span><span class="sxs-lookup"><span data-stu-id="71c30-124">Non-blittable type</span></span>|<span data-ttu-id="71c30-125">Description</span><span class="sxs-lookup"><span data-stu-id="71c30-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="71c30-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="71c30-126">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="71c30-127">Convertit en tableau de style C ou en `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="71c30-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="71c30-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71c30-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="71c30-129">Convertit en valeur de 1, 2 ou 4 octets, la valeur `true` ayant pour valeur 1 ou -1.</span><span class="sxs-lookup"><span data-stu-id="71c30-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="71c30-130">[System. Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71c30-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="71c30-131">Convertit en caractère ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="71c30-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="71c30-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71c30-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="71c30-133">Convertit en interface de classe.</span><span class="sxs-lookup"><span data-stu-id="71c30-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="71c30-134">System. Object</span><span class="sxs-lookup"><span data-stu-id="71c30-134">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="71c30-135">Convertit en interface ou en variant.</span><span class="sxs-lookup"><span data-stu-id="71c30-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="71c30-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="71c30-136">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="71c30-137">Convertit en tableau de style C ou en `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="71c30-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="71c30-138">System.String</span><span class="sxs-lookup"><span data-stu-id="71c30-138">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="71c30-139">Convertit en chaîne se terminant par une référence null ou en BSTR.</span><span class="sxs-lookup"><span data-stu-id="71c30-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="71c30-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71c30-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="71c30-141">Convertit en structure avec une disposition de mémoire fixe.</span><span class="sxs-lookup"><span data-stu-id="71c30-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="71c30-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="71c30-142">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="71c30-143">Convertit en tableau de style C ou en `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="71c30-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="71c30-144">Les types d’objets et de classes sont pris en charge uniquement par COM Interop.</span><span class="sxs-lookup"><span data-stu-id="71c30-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="71c30-145">Pour obtenir les types correspondants en Visual Basic, C# et C++, consultez [Vue d’ensemble de la bibliothèque de classes .NET Framework](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="71c30-145">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c30-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71c30-146">See also</span></span>

- [<span data-ttu-id="71c30-147">comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="71c30-147">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
