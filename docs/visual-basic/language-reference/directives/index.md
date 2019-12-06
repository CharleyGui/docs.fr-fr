---
title: Directives
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5e857198351b30c0d7a38dce1a9e6d1209b5258
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838141"
---
# <a name="directives-visual-basic"></a>Directives (Visual Basic)

Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Directive #Const](../../../visual-basic/language-reference/directives/const-directive.md) : définir une constante de compilation  
  
 [Directive de #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) --indiquer un mappage entre les lignes sources et le texte externe à la source  
  
 [#If... Then... #Else directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --compiler les blocs de code sélectionnés  
  
 [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md) --réduire et masquer des sections de code dans l’éditeur Visual Studio  
  
 **#Disable, #Enable** --désactiver et activer des avertissements spécifiques pour les régions de code.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Vous pouvez désactiver et activer une liste séparée par des virgules de codes d'avertissement.  
  
## <a name="related-sections"></a>Sections connexes  

 [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md)  
  