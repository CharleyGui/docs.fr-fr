---
title: marshaler des données avec COM Interop
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16f94e8b85a1bedb8b7791c2b7fcaf6d154ba1b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833521"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="5ed35-102">marshaler des données avec COM Interop</span><span class="sxs-lookup"><span data-stu-id="5ed35-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="5ed35-103">COM Interop prend en charge l'utilisation des objets COM à partir de code managé, ainsi que l'exposition des objets managés à COM.</span><span class="sxs-lookup"><span data-stu-id="5ed35-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="5ed35-104">La prise en charge du marshaling des données vers et depuis COM est complète et fournit quasiment toujours le comportement de marshaling approprié.</span><span class="sxs-lookup"><span data-stu-id="5ed35-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="5ed35-105">Le Kit de développement logiciel (SDK) Windows inclut les outils COM interop suivants :</span><span class="sxs-lookup"><span data-stu-id="5ed35-105">The Windows Software Development Kit (SDK) includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="5ed35-106">[Importateur de bibliothèques de types (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), qui convertit une bibliothèque de types COM en un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="5ed35-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="5ed35-107">À partir de cet assembly, le service de marshaling d'interopérabilité génère des wrappers qui effectuent le marshaling des données entre la mémoire managée et non managée.</span><span class="sxs-lookup"><span data-stu-id="5ed35-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="5ed35-108">[Exportateur de bibliothèques de types (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), qui produit une bibliothèque de types COM à partir d’un assembly et génère un wrapper qui effectue le marshaling lors des appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="5ed35-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="5ed35-109">Les sections suivantes fournissent des liens vers des rubriques qui décrivent les processus de personnalisation des wrappers d’interopérabilité quand vous pouvez (ou devez) fournir au marshaleur des informations supplémentaires concernant les types.</span><span class="sxs-lookup"><span data-stu-id="5ed35-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ed35-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ed35-110">In This Section</span></span>  
<span data-ttu-id="5ed35-111">[Guide pratique pour créer manuellement des wrappers](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="5ed35-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="5ed35-112">Décrit comment créer manuellement un wrapper COM dans du code source managé.</span><span class="sxs-lookup"><span data-stu-id="5ed35-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="5ed35-113">Guide pratique pour migrer du code DCOM managé vers WCF</span><span class="sxs-lookup"><span data-stu-id="5ed35-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="5ed35-114">Décrit comment migrer du code DCOM managé vers WCF pour obtenir la solution la plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="5ed35-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ed35-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="5ed35-115">Related Sections</span></span>  
 <span data-ttu-id="5ed35-116">[Types de données COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-116">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-117">Fournit les types de données managés et non managés correspondants.</span><span class="sxs-lookup"><span data-stu-id="5ed35-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="5ed35-118">[Personnalisation des wrappers CCW (COM Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-118">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-119">Décrit comment marshaler explicitement des types de données à l’aide de l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> au moment du design.</span><span class="sxs-lookup"><span data-stu-id="5ed35-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="5ed35-120">[Personnalisation des wrappers RCW (Runtime Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-120">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-121">Décrit comment ajuster le comportement de marshaling des types dans un assembly d'interopérabilité et comment définir des types COM manuellement.</span><span class="sxs-lookup"><span data-stu-id="5ed35-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="5ed35-122">[Interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-122">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-123">Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ed35-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="5ed35-124">[Récapitulatif de la conversion d’un assembly en bibliothèque de types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-124">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-125">Décrit le processus d'exportation et de conversion d'un assembly en une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="5ed35-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="5ed35-126">[Récapitulatif de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-126">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-127">Décrit le processus d'importation et de conversion d'une bibliothèque de types en un assembly.</span><span class="sxs-lookup"><span data-stu-id="5ed35-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="5ed35-128">[Interopérabilité à l’aide de types génériques](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ed35-128">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="5ed35-129">Décrit les actions prises en charge lors de l'utilisation de types génériques pour l'interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="5ed35-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
