---
title: Empaquetage d’un assembly .NET Framework pour COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 6866da283cc7cdd180aada252007d67bd72cd862
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124093"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="1b21f-102">Empaquetage d’un assembly .NET Framework pour COM</span><span class="sxs-lookup"><span data-stu-id="1b21f-102">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="1b21f-103">Les développeurs COM peuvent tirer parti des informations suivantes sur les types managés qu’ils prévoient d’incorporer dans leur application :</span><span class="sxs-lookup"><span data-stu-id="1b21f-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="1b21f-104">Une liste des types que les applications COM peuvent consommer</span><span class="sxs-lookup"><span data-stu-id="1b21f-104">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="1b21f-105">Certains types managés ne sont pas visibles par COM, certains sont visibles mais ne peuvent pas être créés, et certains sont visibles et peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="1b21f-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="1b21f-106">Un assembly peut comprendre tout combinaison de types invisibles, visibles, ne pouvant pas être créés et pouvant être créés.</span><span class="sxs-lookup"><span data-stu-id="1b21f-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="1b21f-107">Par souci d’exhaustivité, identifiez les types dans un assembly que vous prévoyez d’exposer à COM, en particulier quand ces types sont un sous-ensemble des types exposés au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b21f-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="1b21f-108">Pour plus d’informations, consultez [Qualification des types .NET en vue d’une interopérabilité](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="1b21f-108">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="1b21f-109">Instructions de gestion de version</span><span class="sxs-lookup"><span data-stu-id="1b21f-109">Versioning instructions</span></span>

  <span data-ttu-id="1b21f-110">Les classes managées qui implémentent l’interface de classe (une interface COM générée par interop) sont soumises aux restrictions de gestion de version.</span><span class="sxs-lookup"><span data-stu-id="1b21f-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="1b21f-111">Pour obtenir des instructions sur l’utilisation de l’interface de classe, consultez [Présentation de l’interface de classe](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="1b21f-111">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="1b21f-112">Instructions de déploiement</span><span class="sxs-lookup"><span data-stu-id="1b21f-112">Deployment instructions</span></span>

  <span data-ttu-id="1b21f-113">Les assemblys avec nom fort signés par un serveur de publication peuvent être installés dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="1b21f-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="1b21f-114">Les assemblys non signés doivent être installés sur la machine de l’utilisateur en tant qu’assemblys privés.</span><span class="sxs-lookup"><span data-stu-id="1b21f-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="1b21f-115">Pour plus d’informations, consultez [Aspects de la sécurité des assemblys](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="1b21f-115">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="1b21f-116">Inclusion de bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="1b21f-116">Type library inclusion</span></span>

  <span data-ttu-id="1b21f-117">La plupart des types nécessitent une bibliothèque de types en cas de consommation par une application COM.</span><span class="sxs-lookup"><span data-stu-id="1b21f-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="1b21f-118">Vous pouvez générer une bibliothèque de types ou demander aux développeurs COM d’effectuer cette tâche.</span><span class="sxs-lookup"><span data-stu-id="1b21f-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="1b21f-119">Le SDK Windows fournit les options suivantes pour générer une bibliothèque de types :</span><span class="sxs-lookup"><span data-stu-id="1b21f-119">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="1b21f-120">Exportateur de bibliothèques de types</span><span class="sxs-lookup"><span data-stu-id="1b21f-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="1b21f-121">Classe TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="1b21f-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="1b21f-122">Outil Assembly Registration Tool</span><span class="sxs-lookup"><span data-stu-id="1b21f-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="1b21f-123">Outil .NET Services Installation</span><span class="sxs-lookup"><span data-stu-id="1b21f-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="1b21f-124">Quel que soit le mécanisme que vous choisissez, seuls les types publics définis dans l’assembly que vous fournissez sont inclus dans la bibliothèque de types générée.</span><span class="sxs-lookup"><span data-stu-id="1b21f-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="1b21f-125">Pour obtenir des instructions, consultez [Guide pratique pour incorporer des bibliothèques de types comme des ressources Win32 dans les applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1b21f-125">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="1b21f-126">Exportateur de bibliothèques de types</span><span class="sxs-lookup"><span data-stu-id="1b21f-126">Type Library Exporter</span></span>

<span data-ttu-id="1b21f-127">L’outil en ligne de commande [Exporter.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md) permet de convertir les classes et les interfaces contenues dans un assembly en une bibliothèque de types COM.</span><span class="sxs-lookup"><span data-stu-id="1b21f-127">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="1b21f-128">Une fois les informations de type de la classe disponibles, les clients COM peuvent créer une instance de la classe .NET et appeler les méthodes de l’instance comme s’il s’agissait d’un objet COM.</span><span class="sxs-lookup"><span data-stu-id="1b21f-128">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="1b21f-129">Tlbexp.exe convertit un assembly entier à la fois.</span><span class="sxs-lookup"><span data-stu-id="1b21f-129">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="1b21f-130">Vous ne pouvez pas utiliser Tlbexp.exe pour générer des informations sur les types pour un sous-ensemble de types définis dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="1b21f-130">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="1b21f-131">Classe TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="1b21f-131">TypeLibConverter Class</span></span>

<span data-ttu-id="1b21f-132">La classe <xref:System.Runtime.InteropServices.TypeLibConverter>, qui se trouve dans l’espace de noms **System.Runtime.Interop**, convertit les classes et interfaces contenues dans un assembly en une bibliothèque de types COM.</span><span class="sxs-lookup"><span data-stu-id="1b21f-132">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="1b21f-133">Cette API produit les mêmes informations de type que l’outil Type Library Exporter décrit dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="1b21f-133">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="1b21f-134">La **classe TypeLibConverter** implémente le <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="1b21f-134">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="1b21f-135">Outil Assembly Registration Tool</span><span class="sxs-lookup"><span data-stu-id="1b21f-135">Assembly Registration Tool</span></span>

<span data-ttu-id="1b21f-136">L’[outil Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) peut générer et inscrire une bibliothèque de types quand vous appliquez l’option **/tlb:**.</span><span class="sxs-lookup"><span data-stu-id="1b21f-136">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="1b21f-137">Les clients COM exigent que les bibliothèques de types soient installées dans le Registre de Windows.</span><span class="sxs-lookup"><span data-stu-id="1b21f-137">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="1b21f-138">Sans cette option, Regasm.exe inscrit uniquement les types dans un assembly, pas la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="1b21f-138">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="1b21f-139">Inscrire les types dans un assembly et inscrire la bibliothèque de types sont deux activités distinctes.</span><span class="sxs-lookup"><span data-stu-id="1b21f-139">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="1b21f-140">Outil .NET Services Installation</span><span class="sxs-lookup"><span data-stu-id="1b21f-140">.NET Services Installation Tool</span></span>

<span data-ttu-id="1b21f-141">L’[Outil .NET Services Installation (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) ajoute des classes managées aux Services de composants Windows 2000 et combine plusieurs tâches dans un seul outil.</span><span class="sxs-lookup"><span data-stu-id="1b21f-141">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="1b21f-142">En plus de charger et d’inscrire un assembly, Regsvcs.exe peut générer, inscrire et installer la bibliothèque de types dans une application COM+ 1.0 existante.</span><span class="sxs-lookup"><span data-stu-id="1b21f-142">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b21f-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b21f-143">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="1b21f-144">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="1b21f-144">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="1b21f-145">Qualification des types .NET pour l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1b21f-145">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="1b21f-146">Présentation de l'interface de classe</span><span class="sxs-lookup"><span data-stu-id="1b21f-146">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="1b21f-147">Considérations sur la sécurité des assemblys</span><span class="sxs-lookup"><span data-stu-id="1b21f-147">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="1b21f-148">Tlbexp. exe (exportateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="1b21f-148">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="1b21f-149">Inscription d’assemblys dans COM</span><span class="sxs-lookup"><span data-stu-id="1b21f-149">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="1b21f-150">[Guide pratique pour incorporer des bibliothèques de types comme des ressources Win32 dans les applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b21f-150">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
