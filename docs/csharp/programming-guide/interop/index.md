---
title: Interopérabilité - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e53465066cf27a5f46c66ac73ee242370be23395
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242005"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="5448e-102">Interopérabilité (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5448e-102">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="5448e-103">L’interopérabilité vous permet de préserver et de tirer parti d’investissements existants en code non managé.</span><span class="sxs-lookup"><span data-stu-id="5448e-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="5448e-104">Le code qui s’exécute sous le contrôle du common language runtime (CLR) est appelé *code managé*, et le code qui s’exécute en dehors du CLR est appelé *code non managé*.</span><span class="sxs-lookup"><span data-stu-id="5448e-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="5448e-105">COM, COM+, les composants C++, les composants ActiveX et l’API Microsoft Windows sont des exemples de code non managé.</span><span class="sxs-lookup"><span data-stu-id="5448e-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="5448e-106">.NET permet l’interopérabilité avec du code non managé via des services d’appel de code non managé, l' <xref:System.Runtime.InteropServices> espace de noms, l’interopérabilité C++ et l’interopérabilité COM (COM Interop).</span><span class="sxs-lookup"><span data-stu-id="5448e-106">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5448e-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5448e-107">In This Section</span></span>  
 [<span data-ttu-id="5448e-108">Vue d'ensemble de l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="5448e-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="5448e-109">Décrit les méthodes qui permettent l’interopérabilité entre le code managé et le code non managé en C#.</span><span class="sxs-lookup"><span data-stu-id="5448e-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="5448e-110">Comment accéder aux objets Office Interop à l’aide des fonctionnalités C#</span><span class="sxs-lookup"><span data-stu-id="5448e-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="5448e-111">Décrit les fonctionnalités introduites dans Visual C# pour faciliter la programmation Office.</span><span class="sxs-lookup"><span data-stu-id="5448e-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="5448e-112">Comment utiliser des propriétés indexées dans la programmation COM Interop</span><span class="sxs-lookup"><span data-stu-id="5448e-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="5448e-113">Explique comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.</span><span class="sxs-lookup"><span data-stu-id="5448e-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="5448e-114">Comment utiliser l’appel de code non managé pour lire un fichier WAV</span><span class="sxs-lookup"><span data-stu-id="5448e-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="5448e-115">Explique comment utiliser des services d’appel de code non managé pour lire un fichier son .wav sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="5448e-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="5448e-116">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="5448e-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="5448e-117">Montre comment créer un classeur Excel et un document Word qui contient un lien vers le classeur.</span><span class="sxs-lookup"><span data-stu-id="5448e-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="5448e-118">Exemple de classe COM</span><span class="sxs-lookup"><span data-stu-id="5448e-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="5448e-119">Montre comment exposer une classe C# en tant qu’objet COM.</span><span class="sxs-lookup"><span data-stu-id="5448e-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5448e-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5448e-120">C# Language Specification</span></span>  

<span data-ttu-id="5448e-121">Pour plus d’informations, consultez [Concepts de base](~/_csharplang/spec/unsafe-code.md) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="5448e-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5448e-122">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="5448e-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5448e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5448e-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5448e-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5448e-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5448e-125">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="5448e-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="5448e-126">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="5448e-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
