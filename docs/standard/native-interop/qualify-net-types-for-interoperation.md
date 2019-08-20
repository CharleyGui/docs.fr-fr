---
title: Qualification des types .NET en vue de l’interopérabilité COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04ebdf5d3e5caf2c34823528703f75cf972f302f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631393"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="4a6af-102">Qualification des types .NET en vue de l’interopérabilité COM</span><span class="sxs-lookup"><span data-stu-id="4a6af-102">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="4a6af-103">Si vous envisagez d’exposer les types d’un assembly à des applications COM, prenez en compte les exigences COM Interop au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="4a6af-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="4a6af-104">Les types managés (classe, interface, structure et énumération) s’intègrent parfaitement aux types COM lorsque vous respectez les consignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a6af-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="4a6af-105">Les classes doivent implémenter les interfaces de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="4a6af-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="4a6af-106">Même si COM Interop fournit un mécanisme permettant de générer automatiquement une interface contenant tous les membres de la classe et de sa classe de base, il est fortement recommandé de fournir des interfaces explicites.</span><span class="sxs-lookup"><span data-stu-id="4a6af-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="4a6af-107">L’interface générée automatiquement est appelée « interface de classe ».</span><span class="sxs-lookup"><span data-stu-id="4a6af-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="4a6af-108">Pour obtenir des instructions, consultez [Présentation de l’interface de classe](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="4a6af-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="4a6af-109">Vous pouvez utiliser Visual Basic, C# et C++ pour incorporer des définitions d’interface dans votre code, au lieu du langage IDL (ou équivalent).</span><span class="sxs-lookup"><span data-stu-id="4a6af-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="4a6af-110">Pour plus d’informations sur la syntaxe, consultez la documentation relative à votre langage.</span><span class="sxs-lookup"><span data-stu-id="4a6af-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="4a6af-111">Les types managés doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="4a6af-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="4a6af-112">Seuls les types publics d’un assembly sont inscrits et exportés vers la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="4a6af-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="4a6af-113">Par conséquent, seuls les types publics sont visibles par COM.</span><span class="sxs-lookup"><span data-stu-id="4a6af-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="4a6af-114">Les types managés exposent des fonctionnalités à un autre code managé qui peut ne pas être exposé à COM.</span><span class="sxs-lookup"><span data-stu-id="4a6af-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="4a6af-115">Par exemple, les constructeurs paramétrables, les méthodes statiques et les champs constants ne sont pas exposés aux clients COM.</span><span class="sxs-lookup"><span data-stu-id="4a6af-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="4a6af-116">De plus, comme le runtime marshale les données d’un type à un autre, les données peuvent être copiées ou transformées.</span><span class="sxs-lookup"><span data-stu-id="4a6af-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="4a6af-117">Les méthodes, les propriétés, les champs et les événements doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="4a6af-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="4a6af-118">Les membres des types publics doivent également être publics pour être visibles par COM.</span><span class="sxs-lookup"><span data-stu-id="4a6af-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="4a6af-119">Vous pouvez restreindre la visibilité d’un assembly, d’un type public ou de membres publics d’un type public en appliquant <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4a6af-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="4a6af-120">Par défaut, tous les membres et types publics sont visibles.</span><span class="sxs-lookup"><span data-stu-id="4a6af-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="4a6af-121">Les types doivent avoir un constructeur sans paramètre public pour être activés dans COM.</span><span class="sxs-lookup"><span data-stu-id="4a6af-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="4a6af-122">Les types publics managés sont visibles par COM.</span><span class="sxs-lookup"><span data-stu-id="4a6af-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="4a6af-123">Toutefois, sans constructeur public sans paramètre (constructeur sans arguments), les clients COM ne peuvent pas créer le type.</span><span class="sxs-lookup"><span data-stu-id="4a6af-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="4a6af-124">Les clients COM peuvent toujours utiliser le type s’il est activé par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="4a6af-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="4a6af-125">Les types ne peuvent pas être abstraits.</span><span class="sxs-lookup"><span data-stu-id="4a6af-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="4a6af-126">Ni les clients COM ni les clients .NET ne peuvent créer de types abstraits.</span><span class="sxs-lookup"><span data-stu-id="4a6af-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="4a6af-127">Lors de l’exportation vers COM, la hiérarchie d’héritage d’un type managé est aplatie.</span><span class="sxs-lookup"><span data-stu-id="4a6af-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="4a6af-128">Le contrôle de version est également différent dans les environnements managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="4a6af-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="4a6af-129">Les types exposés à COM n’ont pas les mêmes caractéristiques de contrôle de version que les autres types managés.</span><span class="sxs-lookup"><span data-stu-id="4a6af-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6af-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a6af-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="4a6af-131">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="4a6af-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="4a6af-132">Présentation de l’interface de classe</span><span class="sxs-lookup"><span data-stu-id="4a6af-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="4a6af-133">Application d’attributs d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="4a6af-133">Applying Interop Attributes</span></span>](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [<span data-ttu-id="4a6af-134">Empaquetage d’un assembly .NET Framework pour COM</span><span class="sxs-lookup"><span data-stu-id="4a6af-134">Packaging a .NET Framework Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)