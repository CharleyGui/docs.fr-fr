---
title: Directives
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409996"
---
# <a name="directives-visual-basic"></a>Directives (Visual Basic)

Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Directive #Const](const-directive.md) : définir une constante de compilation  
  
 [Directive de #ExternalSource](externalsource-directive.md) --indiquer un mappage entre les lignes sources et le texte externe à la source  
  
 [#If... Then... #Else directives](if-then-else-directives.md) --compiler les blocs de code sélectionnés  
  
 [Directive #Region](region-directive.md) --réduire et masquer des sections de code dans l’éditeur Visual Studio  
  
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

 [Informations de référence sur le langage Visual Basic](../index.md)  
  