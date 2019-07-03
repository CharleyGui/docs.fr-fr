---
title: Exposition de composants COM au .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4472adf2c309803d4d5ac57f3522cc260782d85
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833669"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="d4c3a-102">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4c3a-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="d4c3a-103">Cette section résume le processus nécessaire pour exposer un composant COM existant à du code managé.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="d4c3a-104">Pour plus d’informations sur l’écriture de serveurs COM qui s’intègrent étroitement au .NET Framework, consultez [Considérations de design pour l’interopérabilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d4c3a-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="d4c3a-105">Les composants COM existants sont des ressources importantes dans le code managé, en tant qu’applications métier de couche intermédiaire ou en tant que fonctionnalités isolées.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="d4c3a-106">Un composant idéal a un assembly PIA et se conforme étroitement aux normes de programmation imposées par COM.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="d4c3a-107">Pour exposer des composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4c3a-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="d4c3a-108">[Importation d’une bibliothèque de types sous la forme d’un assembly](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d4c3a-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="d4c3a-109">Le common language runtime nécessite des métadonnées pour tous les types, y compris les types COM.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="d4c3a-110">Il existe plusieurs manières d’obtenir un assembly contenant des types COM importés en tant que métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="d4c3a-111">[Utilisation de types COM dans du code managé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d4c3a-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="d4c3a-112">Vous pouvez inspecter des types COM, activer des instances et appeler des méthodes sur l’objet COM de la même façon que vous le feriez pour n’importe quel type managé.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="d4c3a-113">[Compilation d’un projet d’interopérabilité](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="d4c3a-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="d4c3a-114">Le kit de développement logiciel (SDK) Windows fournit des compilateurs pour plusieurs langages conformes à la Common Language Specification (CLS), notamment Visual Basic, C# et C++.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-114">The Windows Software Development Kit (SDK) provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="d4c3a-115">[Déploiement d’une application d’interopérabilité](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="d4c3a-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="d4c3a-116">La meilleure façon de déployer des applications d’interopérabilité est de le faire en tant qu’assemblys signés [avec nom fort](../app-domains/strong-named-assemblies.md) dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="d4c3a-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c3a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4c3a-117">See also</span></span>

- [<span data-ttu-id="d4c3a-118">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="d4c3a-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="d4c3a-119">[Considérations de design pour l’interopérabilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4c3a-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="d4c3a-120">Exemple COM Interop : client .NET et serveur COM</span><span class="sxs-lookup"><span data-stu-id="d4c3a-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="d4c3a-121">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="d4c3a-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="d4c3a-122">Gacutil.exe (outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="d4c3a-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
