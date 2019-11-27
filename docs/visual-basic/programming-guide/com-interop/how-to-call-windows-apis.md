---
title: 'Comment : appeler des API Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 6f3c53243d7aeb73be81796d5ca185c3a3c41c72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348700"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="ccdca-102">Comment : appeler des API Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccdca-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="ccdca-103">Cet exemple définit et appelle la fonction `MessageBox` dans User32. dll, puis passe une chaîne à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="ccdca-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccdca-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ccdca-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccdca-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ccdca-105">Compiling the Code</span></span>  
 <span data-ttu-id="ccdca-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="ccdca-106">This example requires:</span></span>  
  
- <span data-ttu-id="ccdca-107">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="ccdca-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ccdca-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ccdca-108">Robust Programming</span></span>  
 <span data-ttu-id="ccdca-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="ccdca-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ccdca-110">La méthode n’est pas statique, est abstraite ou a été définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="ccdca-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="ccdca-111">Le type parent est une interface, ou la longueur de *Name* ou de *DllName* est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ccdca-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="ccdca-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="ccdca-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="ccdca-113">Le *nom* ou le *DllName* est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ccdca-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="ccdca-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="ccdca-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="ccdca-115">Le type conteneur a déjà été créé à l’aide de `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="ccdca-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="ccdca-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="ccdca-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccdca-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccdca-117">See also</span></span>

- [<span data-ttu-id="ccdca-118">Présentation détaillée de l’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="ccdca-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="ccdca-119">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="ccdca-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="ccdca-120">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="ccdca-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="ccdca-121">[Définition d’une méthode avec l’émission de réflexion](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ccdca-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="ccdca-122">Procédure pas à pas : appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="ccdca-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="ccdca-123">COM Interop</span><span class="sxs-lookup"><span data-stu-id="ccdca-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
