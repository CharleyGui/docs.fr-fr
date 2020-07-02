---
title: 'Procédure : référencer des types .NET à partir de COM'
description: Référencez des types .NET à partir de COM. Les clients VB peuvent afficher un objet .NET dans l’Explorateur d’objets, mais les clients C++ doivent faire référence à un fichier TLB avec la \# directive import.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: f8d052c7b9bac9c4bab61ab1950e9e89a7c73912
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618959"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="ce41f-104">Procédure : référencer des types .NET à partir de COM</span><span class="sxs-lookup"><span data-stu-id="ce41f-104">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="ce41f-105">Du point de vue du code client et serveur, les différences entre COM et le .NET Framework sont largement invisibles.</span><span class="sxs-lookup"><span data-stu-id="ce41f-105">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="ce41f-106">Les clients Microsoft Visual Basic peuvent afficher un objet .NET dans l’Explorateur d’objets, qui expose la syntaxe et les méthodes de l’objet, les propriétés et les champs exactement comme s’il s’agissait de tout autre objet COM.</span><span class="sxs-lookup"><span data-stu-id="ce41f-106">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="ce41f-107">Le processus d’importation d’une bibliothèque de types est légèrement plus compliqué pour les clients C++, même si vous utilisez les mêmes outils pour exporter des métadonnées vers une bibliothèque de types COM.</span><span class="sxs-lookup"><span data-stu-id="ce41f-107">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="ce41f-108">Pour référencer des membres d’objet .NET à partir d’un client C++ non managé, référencez le fichier TLB (produit à l’aide de Tlbexp.exe) avec la directive **#import**.</span><span class="sxs-lookup"><span data-stu-id="ce41f-108">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="ce41f-109">Lors du référencement d’une bibliothèque de types à partir de C++, vous devez soit spécifier l’option **raw_interfaces_only**, soit importer les définitions dans la bibliothèque de classes de base Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="ce41f-109">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="ce41f-110">Pour importer une bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ce41f-110">To import a library</span></span>  
  
- <span data-ttu-id="ce41f-111">Spécifiez l’option **raw_interfaces_only** dans la directive **#import**.</span><span class="sxs-lookup"><span data-stu-id="ce41f-111">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="ce41f-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ce41f-112">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="ce41f-113">-ou-</span><span class="sxs-lookup"><span data-stu-id="ce41f-113">-or-</span></span>  
  
- <span data-ttu-id="ce41f-114">Ajoutez une directive #import pour Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="ce41f-114">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="ce41f-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ce41f-115">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce41f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce41f-116">See also</span></span>

- [<span data-ttu-id="ce41f-117">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="ce41f-117">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="ce41f-118">Inscription d'assemblys dans COM</span><span class="sxs-lookup"><span data-stu-id="ce41f-118">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="ce41f-119">[Appeler un objet .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce41f-119">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="ce41f-120">[Déployer une application pour accéder à COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce41f-120">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
