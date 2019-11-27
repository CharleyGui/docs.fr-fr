---
title: Directives
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343808"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="aab90-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aab90-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="aab90-103">Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aab90-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aab90-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aab90-104">In This Section</span></span>  

 <span data-ttu-id="aab90-105">[Directive #Const](../../../visual-basic/language-reference/directives/const-directive.md) : définir une constante de compilation</span><span class="sxs-lookup"><span data-stu-id="aab90-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="aab90-106">[Directive de #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) --indiquer un mappage entre les lignes sources et le texte externe à la source</span><span class="sxs-lookup"><span data-stu-id="aab90-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="aab90-107">[#If... Then... #Else directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --compiler les blocs de code sélectionnés</span><span class="sxs-lookup"><span data-stu-id="aab90-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="aab90-108">[Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md) --réduire et masquer des sections de code dans l’éditeur Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aab90-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="aab90-109">**#Disable, #Enable** --désactiver et activer des avertissements spécifiques pour les régions de code.</span><span class="sxs-lookup"><span data-stu-id="aab90-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="aab90-110">Vous pouvez désactiver et activer une liste séparée par des virgules de codes d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="aab90-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aab90-111">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="aab90-111">Related Sections</span></span>  

 [<span data-ttu-id="aab90-112">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aab90-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="aab90-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aab90-113">Visual Basic</span></span>](../../../visual-basic/index.md)
