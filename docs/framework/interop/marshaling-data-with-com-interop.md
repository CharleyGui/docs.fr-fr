---
title: marshaler des données avec COM Interop
description: Consultez les articles traitant du marshaling de données avec COM Interop. Les outils Tlbimp.exe et Tlbexp.exe effectuent la conversion entre une bibliothèque de types COM et un assembly d’interopérabilité.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: bcbd2c50fcbd9af3f2eead57ac2e26f8db0c6ad6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275942"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="692ce-104">marshaler des données avec COM Interop</span><span class="sxs-lookup"><span data-stu-id="692ce-104">Marshaling Data with COM Interop</span></span>

<span data-ttu-id="692ce-105">COM Interop prend en charge l'utilisation des objets COM à partir de code managé, ainsi que l'exposition des objets managés à COM.</span><span class="sxs-lookup"><span data-stu-id="692ce-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="692ce-106">La prise en charge du marshaling des données vers et depuis COM est complète et fournit quasiment toujours le comportement de marshaling approprié.</span><span class="sxs-lookup"><span data-stu-id="692ce-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="692ce-107">Le SDK Windows comprend les outils d’interopérabilité COM suivants :</span><span class="sxs-lookup"><span data-stu-id="692ce-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="692ce-108">[Importateur de bibliothèques de types (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), qui convertit une bibliothèque de types COM en un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="692ce-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="692ce-109">À partir de cet assembly, le service de marshaling d'interopérabilité génère des wrappers qui effectuent le marshaling des données entre la mémoire managée et non managée.</span><span class="sxs-lookup"><span data-stu-id="692ce-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="692ce-110">[Exportateur de bibliothèques de types (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), qui produit une bibliothèque de types COM à partir d’un assembly et génère un wrapper qui effectue le marshaling lors des appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="692ce-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="692ce-111">Les sections suivantes fournissent des liens vers des rubriques qui décrivent les processus de personnalisation des wrappers d’interopérabilité quand vous pouvez (ou devez) fournir au marshaleur des informations supplémentaires concernant les types.</span><span class="sxs-lookup"><span data-stu-id="692ce-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="692ce-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="692ce-112">In This Section</span></span>  

<span data-ttu-id="692ce-113">[Comment : créer manuellement des wrappers](how-to-create-wrappers-manually.md) Décrit comment créer un wrapper COM manuellement dans du code source managé.</span><span class="sxs-lookup"><span data-stu-id="692ce-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="692ce-114">Procédure : Migrer du code DCOM managé vers WCF</span><span class="sxs-lookup"><span data-stu-id="692ce-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="692ce-115">Décrit comment migrer du code DCOM managé vers WCF pour obtenir la solution la plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="692ce-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="692ce-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="692ce-116">Related Sections</span></span>  

 <span data-ttu-id="692ce-117">[Types de données COM](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-117">[COM Data Types](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-118">Fournit les types de données managés et non managés correspondants.</span><span class="sxs-lookup"><span data-stu-id="692ce-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="692ce-119">[Personnalisation des wrappers CCW (COM Callable Wrapper)](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-119">[Customizing COM Callable Wrappers](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-120">Décrit comment marshaler explicitement des types de données à l’aide de l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> au moment du design.</span><span class="sxs-lookup"><span data-stu-id="692ce-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="692ce-121">[Personnaliser des wrappers RCW (Runtime Callable Wrapper)](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-121">[Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-122">Décrit comment ajuster le comportement de marshaling des types dans un assembly d'interopérabilité et comment définir des types COM manuellement.</span><span class="sxs-lookup"><span data-stu-id="692ce-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="692ce-123">[Interopérabilité COM avancée](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-123">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-124">Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="692ce-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="692ce-125">[Récapitulatif de la conversion d’un assembly en bibliothèque de types](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-125">[Assembly to Type Library Conversion Summary](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-126">Décrit le processus d'exportation et de conversion d'un assembly en une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="692ce-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="692ce-127">[Récapitulatif de la conversion d’une bibliothèque de types en assembly](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-127">[Type Library to Assembly Conversion Summary](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-128">Décrit le processus d'importation et de conversion d'une bibliothèque de types en un assembly.</span><span class="sxs-lookup"><span data-stu-id="692ce-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="692ce-129">[Interopérabilité à l’aide de types génériques](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="692ce-129">[Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="692ce-130">Décrit les actions prises en charge lors de l'utilisation de types génériques pour l'interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="692ce-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
