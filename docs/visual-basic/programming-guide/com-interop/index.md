---
title: COM Interop
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: dcfdb5f3661292dda2e084eca22afab9bbec15d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348004"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="91dbc-102">COM Interop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91dbc-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="91dbc-103">Le modèle COM (Component Object Model) permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications.</span><span class="sxs-lookup"><span data-stu-id="91dbc-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="91dbc-104">La plupart des logiciels actuels incluent des objets COM.</span><span class="sxs-lookup"><span data-stu-id="91dbc-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="91dbc-105">Bien que les assemblys .NET représentent le meilleur choix pour les nouvelles applications, vous devrez peut-être parfois utiliser des objets COM.</span><span class="sxs-lookup"><span data-stu-id="91dbc-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="91dbc-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="91dbc-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91dbc-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="91dbc-107">In This Section</span></span>  
 [<span data-ttu-id="91dbc-108">Introduction à COM Interop</span><span class="sxs-lookup"><span data-stu-id="91dbc-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="91dbc-109">Fournit une vue d’ensemble de l’interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="91dbc-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="91dbc-110">Guide pratique pour référencer les objets COM à partir de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91dbc-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="91dbc-111">Décrit la procédure à suivre pour ajouter des références aux objets COM qui ont des bibliothèques de types.</span><span class="sxs-lookup"><span data-stu-id="91dbc-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="91dbc-112">Guide pratique : utiliser les contrôles ActiveX</span><span class="sxs-lookup"><span data-stu-id="91dbc-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="91dbc-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span><span class="sxs-lookup"><span data-stu-id="91dbc-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="91dbc-114">Procédure pas à pas : appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="91dbc-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="91dbc-115">Vous guide tout au long du processus d’appel des API qui font partie du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="91dbc-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="91dbc-116">Guide pratique : appeler des API Windows</span><span class="sxs-lookup"><span data-stu-id="91dbc-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="91dbc-117">Montre comment définir et appeler la fonction `MessageBox` dans User32.dll.</span><span class="sxs-lookup"><span data-stu-id="91dbc-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="91dbc-118">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="91dbc-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="91dbc-119">Montre comment appeler une fonction Windows qui a un paramètre de type non signé.</span><span class="sxs-lookup"><span data-stu-id="91dbc-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="91dbc-120">Procédure pas à pas : création d’objets COM avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91dbc-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="91dbc-121">Vous guide tout au long du processus de création d’objets COM avec et sans le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="91dbc-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="91dbc-122">Dépannage des problèmes liés à l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="91dbc-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="91dbc-123">Aborde certains des problèmes qui peuvent se poser lors de l’utilisation de COM.</span><span class="sxs-lookup"><span data-stu-id="91dbc-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="91dbc-124">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="91dbc-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="91dbc-125">Fournit une vue d’ensemble de l’utilisation d’objets COM et d’objets .NET Framework dans la même application.</span><span class="sxs-lookup"><span data-stu-id="91dbc-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="91dbc-126">Procédure pas à pas : implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="91dbc-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="91dbc-127">Décrit l’utilisation d’objets COM existants comme base des nouveaux objets.</span><span class="sxs-lookup"><span data-stu-id="91dbc-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="91dbc-128">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="91dbc-128">Related Sections</span></span>  
 [<span data-ttu-id="91dbc-129">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="91dbc-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="91dbc-130">Décrit les services d'interopérabilité fournis par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="91dbc-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="91dbc-131">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="91dbc-131">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="91dbc-132">Décrit le processus d’appel de types COM via COM Interop.</span><span class="sxs-lookup"><span data-stu-id="91dbc-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="91dbc-133">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="91dbc-133">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="91dbc-134">Décrit la préparation et l’utilisation de types managés à partir de COM.</span><span class="sxs-lookup"><span data-stu-id="91dbc-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="91dbc-135">Application d’attributs d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="91dbc-135">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="91dbc-136">Aborde les attributs que vous pouvez utiliser lors de l’utilisation de code non managé.</span><span class="sxs-lookup"><span data-stu-id="91dbc-136">Covers attributes you can use when working with unmanaged code.</span></span>
