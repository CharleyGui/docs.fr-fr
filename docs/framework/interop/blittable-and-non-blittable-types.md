---
title: types blittable et non blittable
description: En savoir plus sur les types blittables et non blittables. Les types de données blittables sont communément représentés dans la mémoire managée et non managée et n’ont pas besoin d’un traitement spécial.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: 8bbf9c72143033cec22b38cc26cbe8ceb44f790b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556269"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="92105-104">types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="92105-104">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="92105-105">La plupart des types de données ont une représentation commune à la fois dans la mémoire managée et non managée, et ne nécessitent pas de traitement particulier par le marshaleur d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="92105-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="92105-106">Ces types sont appelés *types blittables*, car ils ne nécessitent pas de conversion quand ils transitent entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="92105-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="92105-107">Les structures qui sont retournées par les appels de code non managé doivent être des types blittables.</span><span class="sxs-lookup"><span data-stu-id="92105-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="92105-108">L’appel de code non managé ne prend en charge aucune structure non blittable comme type de retour.</span><span class="sxs-lookup"><span data-stu-id="92105-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="92105-109">Les types suivants issus de l’espace de noms <xref:System> sont des types blittables :</span><span class="sxs-lookup"><span data-stu-id="92105-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
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
  
 <span data-ttu-id="92105-110">Les types complexes suivants sont également des types blittables :</span><span class="sxs-lookup"><span data-stu-id="92105-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="92105-111">Tableaux unidimensionnels de types blittables, comme un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="92105-111">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="92105-112">Toutefois, un type qui contient un tableau de variables de types blittables n’est pas lui-même blittable.</span><span class="sxs-lookup"><span data-stu-id="92105-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="92105-113">Types valeur mis en forme qui ne contiennent que des types blittables (et des classes s’ils sont marshalés comme types mis en forme).</span><span class="sxs-lookup"><span data-stu-id="92105-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="92105-114">Pour plus d’informations sur les types valeur mis en forme, consultez [Marshaling par défaut pour les types valeur](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="92105-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="92105-115">Les références d’objets ne sont pas blittables.</span><span class="sxs-lookup"><span data-stu-id="92105-115">Object references are not blittable.</span></span> <span data-ttu-id="92105-116">Cela inclut un tableau de références aux objets qui sont blittables en eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="92105-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="92105-117">Par exemple, vous pouvez définir une structure blittable, mais vous ne pouvez pas définir un type blittable contenant un tableau de références à ces structures.</span><span class="sxs-lookup"><span data-stu-id="92105-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="92105-118">Par souci d’optimisation, les tableaux de types et de classes blittables qui ne contiennent que des membres blittables sont [épinglés](copying-and-pinning.md) au lieu d’être copiés lors du marshaling.</span><span class="sxs-lookup"><span data-stu-id="92105-118">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="92105-119">Ces types semblent être marshalés en tant que paramètres en entrée/sortie quand l’appelant et l’appelé résident dans le même cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="92105-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="92105-120">Cependant, ces types sont en fait marshalés en tant que paramètres en entrée et vous devez appliquer les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> si vous voulez marshaler l’argument en tant que paramètre en entrée/sortie.</span><span class="sxs-lookup"><span data-stu-id="92105-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="92105-121">Certains types de données managés requièrent une représentation différente dans un environnement non managé.</span><span class="sxs-lookup"><span data-stu-id="92105-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="92105-122">Ces types de données non blittables doivent être convertis sous une forme qui peut être marshalée.</span><span class="sxs-lookup"><span data-stu-id="92105-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="92105-123">Par exemple, les chaînes managées sont des types non blittables parce qu’elles doivent être converties en objets String avant de pouvoir être marshalées.</span><span class="sxs-lookup"><span data-stu-id="92105-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="92105-124">Le tableau suivant répertorie des types non blittables issus de l’espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="92105-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="92105-125">Les [délégués](default-marshaling-behavior.md#default-marshaling-for-delegates), qui sont des structures de données qui réfèrent à une méthode statique ou à une instance de classe, sont également non blittables.</span><span class="sxs-lookup"><span data-stu-id="92105-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="92105-126">Type non blittable</span><span class="sxs-lookup"><span data-stu-id="92105-126">Non-blittable type</span></span>|<span data-ttu-id="92105-127">Description</span><span class="sxs-lookup"><span data-stu-id="92105-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="92105-128">System.Array</span><span class="sxs-lookup"><span data-stu-id="92105-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="92105-129">Convertit en tableau de style C ou en `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="92105-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="92105-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92105-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="92105-131">Convertit en valeur de 1, 2 ou 4 octets, la valeur `true` ayant pour valeur 1 ou -1.</span><span class="sxs-lookup"><span data-stu-id="92105-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="92105-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92105-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="92105-133">Convertit en caractère ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="92105-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="92105-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92105-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="92105-135">Convertit en interface de classe.</span><span class="sxs-lookup"><span data-stu-id="92105-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="92105-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="92105-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="92105-137">Convertit en interface ou en variant.</span><span class="sxs-lookup"><span data-stu-id="92105-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="92105-138">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="92105-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="92105-139">Convertit en tableau de style C ou en `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="92105-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="92105-140">System.String</span><span class="sxs-lookup"><span data-stu-id="92105-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="92105-141">Convertit en chaîne se terminant par une référence null ou en BSTR.</span><span class="sxs-lookup"><span data-stu-id="92105-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="92105-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92105-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="92105-143">Convertit en structure avec une disposition de mémoire fixe.</span><span class="sxs-lookup"><span data-stu-id="92105-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="92105-144">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="92105-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="92105-145">Convertit en tableau de style C ou en `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="92105-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="92105-146">Les types d’objets et de classes sont pris en charge uniquement par COM Interop.</span><span class="sxs-lookup"><span data-stu-id="92105-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="92105-147">Pour obtenir les types correspondants en Visual Basic, C# et C++, consultez [Vue d’ensemble de la bibliothèque de classes .NET Framework](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="92105-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92105-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92105-148">See also</span></span>

- [<span data-ttu-id="92105-149">comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="92105-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
