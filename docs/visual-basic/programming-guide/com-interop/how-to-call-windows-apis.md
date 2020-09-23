---
title: 'Procédure : Appeler des API Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 40b40c1a489d514c82cbccdeacda27900d9ec87d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083356"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Comment : appeler des API Windows (Visual Basic)

Cet exemple définit et appelle la `MessageBox` fonction dans user32.dll puis passe une chaîne à celle-ci.  
  
## <a name="example"></a>Exemple  

 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Compiler le code  

 Cet exemple nécessite :  
  
- une référence à l'espace de noms <xref:System>.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- La méthode n’est pas statique, est abstraite ou a été définie précédemment. Le type parent est une interface, ou la longueur de *Name* ou de *DllName* est égale à zéro. (<xref:System.ArgumentException>)  
  
- Le *nom* ou le *DllName* est `Nothing` . (<xref:System.ArgumentNullException>)  
  
- Le type conteneur a déjà été créé à l’aide de `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Voir aussi

- [Présentation détaillée de l’appel de code non managé](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Exemples d'appel de code non managé](../../../framework/interop/platform-invoke-examples.md)
- [Consommation de fonctions DLL non managées](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Définition d'une méthode avec l'émission de réflexion](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Procédure pas à pas : Appel des API Windows](walkthrough-calling-windows-apis.md)
- [COM Interop](index.md)
