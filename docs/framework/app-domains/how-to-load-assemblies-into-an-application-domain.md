---
title: 'Procédure : charger des assemblys dans un domaine d’application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f21126361ce69ab14d18e12d2787b2c264116b02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921534"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="a9a84-102">Procédure : charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="a9a84-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="a9a84-103">Il existe plusieurs façons de charger un assembly dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a9a84-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="a9a84-104">La procédure recommandée consiste à utiliser la méthode `static` (`Shared` en Visual Basic) <xref:System.Reflection.Assembly.Load%2A> de la classe <xref:System.Reflection.Assembly?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9a84-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a9a84-105">Vous pouvez aussi adopter les approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9a84-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="a9a84-106">La méthode <xref:System.Reflection.Assembly.LoadFrom%2A> de la classe <xref:System.Reflection.Assembly> charge un assembly en fonction de son emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="a9a84-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="a9a84-107">Le chargement des assemblys avec cette méthode utilise un contexte de chargement différent.</span><span class="sxs-lookup"><span data-stu-id="a9a84-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="a9a84-108">Les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> chargent un assembly dans le contexte de réflexion uniquement.</span><span class="sxs-lookup"><span data-stu-id="a9a84-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="a9a84-109">Les assemblys chargés dans ce contexte peuvent être examinés mais pas exécutés, ce qui permet d’examiner des assemblys qui ciblent d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="a9a84-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="a9a84-110">Voir [Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="a9a84-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9a84-111">Le contexte de réflexion uniquement est une nouveauté du .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="a9a84-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="a9a84-112">Les méthodes telles que <xref:System.AppDomain.CreateInstance%2A> et <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> de la classe <xref:System.AppDomain> peuvent charger des assemblys dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a9a84-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="a9a84-113">La méthode <xref:System.Type.GetType%2A> de la classe <xref:System.Type> peut charger des assemblys.</span><span class="sxs-lookup"><span data-stu-id="a9a84-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="a9a84-114">La méthode <xref:System.AppDomain.Load%2A> de la classe <xref:System.AppDomain?displayProperty=nameWithType> peut charger des assemblys, mais est utilisée principalement pour l’interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="a9a84-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="a9a84-115">Vous ne devez pas l’utiliser pour charger des assemblys dans un domaine d’application autre que celui à partir duquel elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="a9a84-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9a84-116">À compter du .NET Framework version 2.0, le runtime ne charge pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est supérieur au runtime chargé actuellement.</span><span class="sxs-lookup"><span data-stu-id="a9a84-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="a9a84-117">Cela s’applique à la combinaison des composants majeurs et mineurs du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="a9a84-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="a9a84-118">Vous pouvez spécifier la façon dont le code compilé juste-à-temps (JIT) des assemblys chargés est partagé entre les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="a9a84-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="a9a84-119">Pour plus d’informations, consultez [Domaines d’application et assemblys](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="a9a84-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9a84-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="a9a84-120">Example</span></span>  
 <span data-ttu-id="a9a84-121">Le code suivant charge un assembly nommé « example.exe » ou « example.dll » dans le domaine d’application actuel, obtient un type nommé `Example` à partir de l’assembly, obtient une méthode sans paramètre nommée `MethodA` pour ce type, et exécute la méthode.</span><span class="sxs-lookup"><span data-stu-id="a9a84-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="a9a84-122">Pour obtenir une description complète de l’obtention d’informations à partir d’un assembly chargé, consultez [Chargement et utilisation dynamiques des types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9a84-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a9a84-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9a84-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="a9a84-124">Programmation avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="a9a84-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="a9a84-125">Réflexion</span><span class="sxs-lookup"><span data-stu-id="a9a84-125">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="a9a84-126">Utilisation des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="a9a84-126">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
- <span data-ttu-id="a9a84-127">[Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="a9a84-127">[How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)</span></span>
- [<span data-ttu-id="a9a84-128">Domaines d’application et assemblys</span><span class="sxs-lookup"><span data-stu-id="a9a84-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
