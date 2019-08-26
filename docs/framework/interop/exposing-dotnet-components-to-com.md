---
title: Exposition de composants .NET Framework à COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48d550a526336cf3e9de9cb53a16ddcf86f3af5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946513"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="db08a-102">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="db08a-102">Exposing .NET Framework Components to COM</span></span>

<span data-ttu-id="db08a-103">L’écriture d’un type .NET et l’utilisation de ce type à partir de code non managé sont deux activités distinctes pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="db08a-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="db08a-104">Cette section contient plusieurs conseils pour l’écriture de code managé interagissant avec des clients COM :</span><span class="sxs-lookup"><span data-stu-id="db08a-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="db08a-105">[Qualification des types .NET pour l’interopérabilité](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="db08a-105">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="db08a-106">Tous les types, méthodes, propriétés, champs et événements managés que vous voulez exposer à COM doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="db08a-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="db08a-107">Les types doivent avoir un constructeur public sans paramètre, qui est le seul constructeur pouvant être appelé dans COM.</span><span class="sxs-lookup"><span data-stu-id="db08a-107">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="db08a-108">[Application d’attributs d’interopérabilité](../../standard/native-interop/apply-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="db08a-108">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="db08a-109">Les attributs personnalisés dans du code managé peuvent améliorer l’interopérabilité d’un composant.</span><span class="sxs-lookup"><span data-stu-id="db08a-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="db08a-110">[Empaquetage d’un assembly pour COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="db08a-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="db08a-111">Les développeurs COM peuvent vous demander de résumer les étapes impliquées dans le référencement et le déploiement de vos assemblys.</span><span class="sxs-lookup"><span data-stu-id="db08a-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="db08a-112">De plus, cette section identifie les tâches relatives à la consommation d’un type managé à partir d’un client COM.</span><span class="sxs-lookup"><span data-stu-id="db08a-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="db08a-113">Pour consommer un type managé à partir de COM</span><span class="sxs-lookup"><span data-stu-id="db08a-113">To consume a managed type from COM</span></span>

1. <span data-ttu-id="db08a-114">[Inscription d’assemblys auprès de COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="db08a-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="db08a-115">Les types d’un assembly (et des bibliothèques de types) doivent être inscrits au moment du design.</span><span class="sxs-lookup"><span data-stu-id="db08a-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="db08a-116">Si un programme d’installation n’inscrit pas l’assembly, indiquez aux développeurs COM qu’ils doivent utiliser Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="db08a-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="db08a-117">[Référencer des types .NET à partir de COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)</span><span class="sxs-lookup"><span data-stu-id="db08a-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="db08a-118">Les développeurs COM peuvent référencer des types dans un assembly en utilisant les mêmes outils et techniques que ceux qu’ils utilisent aujourd’hui.</span><span class="sxs-lookup"><span data-stu-id="db08a-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="db08a-119">[Appel d’un objet .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db08a-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="db08a-120">Les développeurs COM peuvent appeler des méthodes sur l’objet .NET de la même façon qu’ils appellent des méthodes sur un type non managé.</span><span class="sxs-lookup"><span data-stu-id="db08a-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="db08a-121">Par exemple, l’API **CoCreateInstance** de COM active des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="db08a-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="db08a-122">[Déploiement d’une application pour accéder à COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db08a-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="db08a-123">Un assembly avec nom fort peut être installé dans le Global Assembly Cache et nécessite une signature de son éditeur.</span><span class="sxs-lookup"><span data-stu-id="db08a-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="db08a-124">Les assemblys qui n’ont pas de nom fort doivent être installés dans le répertoire de l’application du client.</span><span class="sxs-lookup"><span data-stu-id="db08a-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="db08a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db08a-125">See also</span></span>

- [<span data-ttu-id="db08a-126">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="db08a-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="db08a-127">COM Interop, exemple : client COM et serveur .NET</span><span class="sxs-lookup"><span data-stu-id="db08a-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
