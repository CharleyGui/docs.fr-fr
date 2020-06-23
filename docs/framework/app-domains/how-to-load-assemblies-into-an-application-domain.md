---
title: 'Procédure : charger des assemblys dans un domaine d’application'
description: Découvrez comment charger des assemblys dans un domaine d’application dans .NET. La méthode recommandée consiste à utiliser la méthode Load statique (ou Shared) dans System. Reflection. assembly.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c91c70625b79002e9297755dfdfac8aa6e283208
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104755"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="470c2-104">Procédure : charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="470c2-104">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="470c2-105">Il existe plusieurs façons de charger un assembly dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="470c2-105">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="470c2-106">La procédure recommandée consiste à utiliser la méthode `static` (`Shared` en Visual Basic) <xref:System.Reflection.Assembly.Load%2A> de la classe <xref:System.Reflection.Assembly?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="470c2-106">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="470c2-107">Vous pouvez aussi adopter les approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="470c2-107">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="470c2-108">La méthode <xref:System.Reflection.Assembly.LoadFrom%2A> de la classe <xref:System.Reflection.Assembly> charge un assembly en fonction de son emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="470c2-108">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="470c2-109">Le chargement des assemblys avec cette méthode utilise un contexte de chargement différent.</span><span class="sxs-lookup"><span data-stu-id="470c2-109">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="470c2-110">Les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> chargent un assembly dans le contexte de réflexion uniquement.</span><span class="sxs-lookup"><span data-stu-id="470c2-110">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="470c2-111">Les assemblys chargés dans ce contexte peuvent être examinés mais pas exécutés, ce qui permet d’examiner des assemblys qui ciblent d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="470c2-111">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="470c2-112">Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="470c2-112">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="470c2-113">Le contexte de réflexion uniquement est une nouveauté du .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="470c2-113">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="470c2-114">Les méthodes telles que <xref:System.AppDomain.CreateInstance%2A> et <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> de la classe <xref:System.AppDomain> peuvent charger des assemblys dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="470c2-114">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="470c2-115">La méthode <xref:System.Type.GetType%2A> de la classe <xref:System.Type> peut charger des assemblys.</span><span class="sxs-lookup"><span data-stu-id="470c2-115">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="470c2-116">La méthode <xref:System.AppDomain.Load%2A> de la classe <xref:System.AppDomain?displayProperty=nameWithType> peut charger des assemblys, mais est utilisée principalement pour l’interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="470c2-116">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="470c2-117">Vous ne devez pas l’utiliser pour charger des assemblys dans un domaine d’application autre que celui à partir duquel elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="470c2-117">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="470c2-118">À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime actuellement chargé.</span><span class="sxs-lookup"><span data-stu-id="470c2-118">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="470c2-119">Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="470c2-119">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="470c2-120">Vous pouvez spécifier la façon dont le code compilé juste-à-temps (JIT) des assemblys chargés est partagé entre les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="470c2-120">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="470c2-121">Pour plus d’informations, consultez [domaines d’application et assemblys](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="470c2-121">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="470c2-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="470c2-122">Example</span></span>  
 <span data-ttu-id="470c2-123">Le code suivant charge un assembly nommé « example.exe » ou « example.dll » dans le domaine d’application actuel, obtient un type nommé `Example` à partir de l’assembly, obtient une méthode sans paramètre nommée `MethodA` pour ce type, et exécute la méthode.</span><span class="sxs-lookup"><span data-stu-id="470c2-123">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="470c2-124">Pour obtenir une description complète de l’obtention d’informations à partir d’un assembly chargé, consultez [Chargement et utilisation dynamiques des types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="470c2-124">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="470c2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="470c2-125">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="470c2-126">Programmation avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="470c2-126">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="470c2-127">Réflexion</span><span class="sxs-lookup"><span data-stu-id="470c2-127">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="470c2-128">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="470c2-128">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="470c2-129">Procédure : charger des assemblys dans le contexte de réflexion uniquement</span><span class="sxs-lookup"><span data-stu-id="470c2-129">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="470c2-130">Domaines d’application et assemblys</span><span class="sxs-lookup"><span data-stu-id="470c2-130">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
