---
title: Interopérabilité - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: b568bdc149123b490f3b058afc668aabcf558d55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585463"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="b0c10-102">Interopérabilité (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b0c10-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="b0c10-103">L’interopérabilité vous permet de préserver et de tirer parti d’investissements existants en code non managé.</span><span class="sxs-lookup"><span data-stu-id="b0c10-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="b0c10-104">Le code qui s’exécute sous le contrôle du common language runtime (CLR) est appelé *code managé*, et le code qui s’exécute en dehors du CLR est appelé *code non managé*.</span><span class="sxs-lookup"><span data-stu-id="b0c10-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="b0c10-105">COM, COM+, les composants C++, les composants ActiveX et l’API Microsoft Windows sont des exemples de code non managé.</span><span class="sxs-lookup"><span data-stu-id="b0c10-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="b0c10-106">Le .NET Framework permet l’interopérabilité avec du code non managé par des services d’appel de code non managé, l’espace de noms <xref:System.Runtime.InteropServices>, l’interopérabilité C++ et l’interopérabilité COM (COM Interop).</span><span class="sxs-lookup"><span data-stu-id="b0c10-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0c10-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b0c10-107">In This Section</span></span>  
 [<span data-ttu-id="b0c10-108">Vue d’ensemble de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="b0c10-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="b0c10-109">Décrit les méthodes qui permettent l’interopérabilité entre le code managé et le code non managé en C#.</span><span class="sxs-lookup"><span data-stu-id="b0c10-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="b0c10-110">Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#</span><span class="sxs-lookup"><span data-stu-id="b0c10-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="b0c10-111">Décrit les fonctionnalités introduites dans Visual C# pour faciliter la programmation Office.</span><span class="sxs-lookup"><span data-stu-id="b0c10-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="b0c10-112">Guide pratique pour utiliser des propriétés indexées dans la programmation COM Interop</span><span class="sxs-lookup"><span data-stu-id="b0c10-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="b0c10-113">Explique comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.</span><span class="sxs-lookup"><span data-stu-id="b0c10-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="b0c10-114">Guide pratique pour utiliser l’appel de code non managé pour lire un fichier audio</span><span class="sxs-lookup"><span data-stu-id="b0c10-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="b0c10-115">Explique comment utiliser des services d’appel de code non managé pour lire un fichier son .wav sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="b0c10-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="b0c10-116">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="b0c10-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="b0c10-117">Montre comment créer un classeur Excel et un document Word qui contient un lien vers le classeur.</span><span class="sxs-lookup"><span data-stu-id="b0c10-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="b0c10-118">Exemple de classe COM</span><span class="sxs-lookup"><span data-stu-id="b0c10-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="b0c10-119">Montre comment exposer une classe C# en tant qu’objet COM.</span><span class="sxs-lookup"><span data-stu-id="b0c10-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b0c10-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b0c10-120">C# Language Specification</span></span>  

<span data-ttu-id="b0c10-121">Pour plus d’informations, consultez [Concepts de base](~/_csharplang/spec/unsafe-code.md) dans la [Spécification du langage C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0c10-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="b0c10-122">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="b0c10-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b0c10-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0c10-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b0c10-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b0c10-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b0c10-125">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="b0c10-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)
- [<span data-ttu-id="b0c10-126">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="b0c10-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
