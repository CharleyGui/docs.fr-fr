---
title: Exemples d'appel de code non managé
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: da157a40819ada3914cf1791c8ca3f7b30e8c837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124756"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="4b808-102">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="4b808-102">Platform Invoke Examples</span></span>
<span data-ttu-id="4b808-103">Les exemples suivants montrent comment définir et appeler la fonction **MessageBox** dans User32.dll, en passant une chaîne simple en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="4b808-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="4b808-104">Dans ces exemples, le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> est défini sur **Automatique** pour permettre à la plateforme cible de déterminer la largeur des caractères et le marshaling des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4b808-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="4b808-105">Pour obtenir des exemples supplémentaires, consultez [Marshaling de données à l’aide de l’appel de code managé](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="4b808-105">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b808-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b808-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="4b808-107">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="4b808-107">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="4b808-108">Spécification d'un jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="4b808-108">Specifying a Character Set</span></span>](specifying-a-character-set.md)
