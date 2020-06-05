---
title: 'Procédure : Appeler des API Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 2c3bb599b79575180eb2b0ec89453f01901f94c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396841"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="7c679-102">Comment : appeler des API Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c679-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="7c679-103">Cet exemple définit et appelle la `MessageBox` fonction dans User32. dll, puis passe une chaîne à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="7c679-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c679-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c679-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="7c679-105">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="7c679-105">Compile the code</span></span>  
 <span data-ttu-id="7c679-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="7c679-106">This example requires:</span></span>  
  
- <span data-ttu-id="7c679-107">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="7c679-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7c679-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="7c679-108">Robust Programming</span></span>  
 <span data-ttu-id="7c679-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="7c679-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7c679-110">La méthode n’est pas statique, est abstraite ou a été définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="7c679-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="7c679-111">Le type parent est une interface, ou la longueur de *Name* ou de *DllName* est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="7c679-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="7c679-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="7c679-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="7c679-113">Le *nom* ou le *DllName* est `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="7c679-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="7c679-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="7c679-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="7c679-115">Le type conteneur a déjà été créé à l’aide de `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="7c679-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="7c679-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="7c679-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c679-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c679-117">See also</span></span>

- [<span data-ttu-id="7c679-118">Présentation détaillée de l’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="7c679-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="7c679-119">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="7c679-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="7c679-120">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="7c679-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="7c679-121">[Définition d'une méthode avec l'émission de réflexion](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7c679-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="7c679-122">Procédure pas à pas : Appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="7c679-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="7c679-123">COM Interop</span><span class="sxs-lookup"><span data-stu-id="7c679-123">COM Interop</span></span>](index.md)
