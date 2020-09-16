---
title: 'Procédure : Appeler des API Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 863986e94855e02e9fd04685f7dc3e8e7f7b1cc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548063"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="715e2-102">Comment : appeler des API Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="715e2-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="715e2-103">Cet exemple définit et appelle la `MessageBox` fonction dans user32.dll puis passe une chaîne à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="715e2-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="715e2-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="715e2-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="715e2-105">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="715e2-105">Compile the code</span></span>  
 <span data-ttu-id="715e2-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="715e2-106">This example requires:</span></span>  
  
- <span data-ttu-id="715e2-107">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="715e2-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="715e2-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="715e2-108">Robust Programming</span></span>  
 <span data-ttu-id="715e2-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="715e2-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="715e2-110">La méthode n’est pas statique, est abstraite ou a été définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="715e2-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="715e2-111">Le type parent est une interface, ou la longueur de *Name* ou de *DllName* est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="715e2-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="715e2-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="715e2-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="715e2-113">Le *nom* ou le *DllName* est `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="715e2-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="715e2-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="715e2-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="715e2-115">Le type conteneur a déjà été créé à l’aide de `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="715e2-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="715e2-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="715e2-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="715e2-117">See also</span></span>

- [<span data-ttu-id="715e2-118">Présentation détaillée de l’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="715e2-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="715e2-119">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="715e2-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="715e2-120">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="715e2-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="715e2-121">[Définition d'une méthode avec l'émission de réflexion](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="715e2-121">[Defining a Method with Reflection Emit](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="715e2-122">Procédure pas à pas : Appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="715e2-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="715e2-123">COM Interop</span><span class="sxs-lookup"><span data-stu-id="715e2-123">COM Interop</span></span>](index.md)
