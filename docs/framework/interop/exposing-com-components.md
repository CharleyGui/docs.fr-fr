---
title: Exposition de composants COM au .NET Framework
description: Découvrez le processus d’exposition des composants COM à .NET. Les composants COM sont utiles dans du code managé en tant qu’applications métier de couche intermédiaire ou fonctionnalités isolées.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 4e18e3f49dacbb3a358aa7e9785a5dda93206164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267063"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="b3acd-104">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3acd-104">Exposing COM Components to the .NET Framework</span></span>

<span data-ttu-id="b3acd-105">Cette section résume le processus nécessaire pour exposer un composant COM existant à du code managé.</span><span class="sxs-lookup"><span data-stu-id="b3acd-105">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="b3acd-106">Pour plus d’informations sur l’écriture de serveurs COM qui s’intègrent étroitement au .NET Framework, consultez [Considérations de design pour l’interopérabilité](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b3acd-106">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="b3acd-107">Les composants COM existants sont des ressources importantes dans le code managé, en tant qu’applications métier de couche intermédiaire ou en tant que fonctionnalités isolées.</span><span class="sxs-lookup"><span data-stu-id="b3acd-107">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="b3acd-108">Un composant idéal a un assembly PIA et se conforme étroitement aux normes de programmation imposées par COM.</span><span class="sxs-lookup"><span data-stu-id="b3acd-108">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="b3acd-109">Pour exposer des composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3acd-109">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="b3acd-110">[Importation d’une bibliothèque de types sous la forme d’un assembly](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="b3acd-110">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="b3acd-111">Le common language runtime nécessite des métadonnées pour tous les types, y compris les types COM.</span><span class="sxs-lookup"><span data-stu-id="b3acd-111">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="b3acd-112">Il existe plusieurs manières d’obtenir un assembly contenant des types COM importés en tant que métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b3acd-112">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="b3acd-113">[Utilisation de types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b3acd-113">[Use COM types in managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="b3acd-114">Vous pouvez inspecter des types COM, activer des instances et appeler des méthodes sur l’objet COM de la même façon que vous le feriez pour n’importe quel type managé.</span><span class="sxs-lookup"><span data-stu-id="b3acd-114">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="b3acd-115">[Compilation d’un projet d’interopérabilité](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="b3acd-115">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="b3acd-116">Le SDK Windows fournit des compilateurs pour plusieurs langages conformes à la spécification CLS (Common Language Specification), notamment Visual Basic, C# et C++.</span><span class="sxs-lookup"><span data-stu-id="b3acd-116">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="b3acd-117">[Déploiement d’une application d’interopérabilité](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="b3acd-117">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="b3acd-118">La meilleure façon de déployer des applications d’interopérabilité est de le faire en tant qu’assemblys signés [avec nom fort](../../standard/assembly/strong-named.md) dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b3acd-118">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3acd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3acd-119">See also</span></span>

- [<span data-ttu-id="b3acd-120">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="b3acd-120">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="b3acd-121">[Considérations relatives à la conception de l’interopérabilité](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b3acd-121">[Design Considerations for Interoperation](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="b3acd-122">Exemple COM Interop : client .NET et serveur COM</span><span class="sxs-lookup"><span data-stu-id="b3acd-122">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="b3acd-123">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="b3acd-123">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="b3acd-124">Gacutil.exe (Outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="b3acd-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
