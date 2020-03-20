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
ms.openlocfilehash: 358d1ce662d56b8c31124f4b3264ec25a0f94586
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181319"
---
# <a name="platform-invoke-examples"></a>Exemples d'appel de code non managé
Les exemples suivants montrent comment définir et appeler la fonction **MessageBox** dans User32.dll, en passant une chaîne simple en tant qu’argument. Dans ces exemples, le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> est défini sur **Automatique** pour permettre à la plateforme cible de déterminer la largeur des caractères et le marshaling des chaînes.  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 Pour obtenir des exemples supplémentaires, consultez [Marshaling de données à l’aide de l’appel de code managé](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Création de prototypes dans du code managé](creating-prototypes-in-managed-code.md)
- [Spécification d’un jeu de caractères](specifying-a-character-set.md)
