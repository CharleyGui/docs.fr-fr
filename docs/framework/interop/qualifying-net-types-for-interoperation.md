---
title: Qualification des types .NET en vue d'une interopérabilité
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
ms.openlocfilehash: 8b2e14a7508d4a5e8069a3b98dee38a0ac62750c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363984"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="f040d-102">Qualification des types .NET en vue d'une interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f040d-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="f040d-103">Si vous envisagez d’exposer les types d’un assembly à des applications COM, prenez en compte les exigences COM Interop au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="f040d-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="f040d-104">Les types managés (classe, interface, structure et énumération) s’intègrent parfaitement aux types COM lorsque vous respectez les consignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f040d-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="f040d-105">Les classes doivent implémenter les interfaces de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="f040d-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="f040d-106">Même si COM Interop fournit un mécanisme permettant de générer automatiquement une interface contenant tous les membres de la classe et de sa classe de base, il est fortement recommandé de fournir des interfaces explicites.</span><span class="sxs-lookup"><span data-stu-id="f040d-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="f040d-107">L’interface générée automatiquement est appelée « interface de classe ».</span><span class="sxs-lookup"><span data-stu-id="f040d-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="f040d-108">Pour obtenir des instructions, consultez [Présentation de l’interface de classe](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="f040d-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="f040d-109">Vous pouvez utiliser Visual Basic, C# et C++ pour incorporer des définitions d’interface dans votre code, au lieu du langage IDL (ou équivalent).</span><span class="sxs-lookup"><span data-stu-id="f040d-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="f040d-110">Pour plus d’informations sur la syntaxe, consultez la documentation relative à votre langage.</span><span class="sxs-lookup"><span data-stu-id="f040d-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="f040d-111">Les types managés doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="f040d-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="f040d-112">Seuls les types publics d’un assembly sont inscrits et exportés vers la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="f040d-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="f040d-113">Par conséquent, seuls les types publics sont visibles par COM.</span><span class="sxs-lookup"><span data-stu-id="f040d-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="f040d-114">Les types managés exposent des fonctionnalités à un autre code managé qui peut ne pas être exposé à COM.</span><span class="sxs-lookup"><span data-stu-id="f040d-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="f040d-115">Par exemple, les constructeurs paramétrables, les méthodes statiques et les champs constants ne sont pas exposés aux clients COM.</span><span class="sxs-lookup"><span data-stu-id="f040d-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="f040d-116">De plus, comme le runtime marshale les données d’un type à un autre, les données peuvent être copiées ou transformées.</span><span class="sxs-lookup"><span data-stu-id="f040d-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="f040d-117">Les méthodes, les propriétés, les champs et les événements doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="f040d-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="f040d-118">Les membres des types publics doivent également être publics pour être visibles par COM.</span><span class="sxs-lookup"><span data-stu-id="f040d-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="f040d-119">Vous pouvez restreindre la visibilité d’un assembly, d’un type public ou de membres publics d’un type public en appliquant <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f040d-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="f040d-120">Par défaut, tous les membres et types publics sont visibles.</span><span class="sxs-lookup"><span data-stu-id="f040d-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="f040d-121">Les types doivent avoir un constructeur sans paramètre public pour être activés dans COM.</span><span class="sxs-lookup"><span data-stu-id="f040d-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="f040d-122">Les types publics managés sont visibles par COM.</span><span class="sxs-lookup"><span data-stu-id="f040d-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="f040d-123">Toutefois, sans constructeur public sans paramètre (constructeur sans arguments), les clients COM ne peuvent pas créer le type.</span><span class="sxs-lookup"><span data-stu-id="f040d-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="f040d-124">Les clients COM peuvent toujours utiliser le type s’il est activé par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="f040d-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="f040d-125">Les types ne peuvent pas être abstraits.</span><span class="sxs-lookup"><span data-stu-id="f040d-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="f040d-126">Ni les clients COM ni les clients .NET ne peuvent créer de types abstraits.</span><span class="sxs-lookup"><span data-stu-id="f040d-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="f040d-127">Lors de l’exportation vers COM, la hiérarchie d’héritage d’un type managé est aplatie.</span><span class="sxs-lookup"><span data-stu-id="f040d-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="f040d-128">Le contrôle de version est également différent dans les environnements managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="f040d-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="f040d-129">Les types exposés à COM n’ont pas les mêmes caractéristiques de contrôle de version que les autres types managés.</span><span class="sxs-lookup"><span data-stu-id="f040d-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f040d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f040d-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="f040d-131">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="f040d-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="f040d-132">Présentation de l’interface de classe</span><span class="sxs-lookup"><span data-stu-id="f040d-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="f040d-133">Application d’attributs d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f040d-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="f040d-134">Empaquetage d'un assembly pour COM</span><span class="sxs-lookup"><span data-stu-id="f040d-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
