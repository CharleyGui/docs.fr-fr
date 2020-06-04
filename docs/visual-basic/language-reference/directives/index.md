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
# <a name="directives-visual-basic"></a><span data-ttu-id="423a7-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="423a7-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="423a7-103">Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="423a7-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="423a7-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="423a7-104">In This Section</span></span>  

 <span data-ttu-id="423a7-105">[Directive #Const](const-directive.md) : définir une constante de compilation</span><span class="sxs-lookup"><span data-stu-id="423a7-105">[#Const Directive](const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="423a7-106">[Directive de #ExternalSource](externalsource-directive.md) --indiquer un mappage entre les lignes sources et le texte externe à la source</span><span class="sxs-lookup"><span data-stu-id="423a7-106">[#ExternalSource Directive](externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="423a7-107">[#If... Then... #Else directives](if-then-else-directives.md) --compiler les blocs de code sélectionnés</span><span class="sxs-lookup"><span data-stu-id="423a7-107">[#If...Then...#Else Directives](if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="423a7-108">[Directive #Region](region-directive.md) --réduire et masquer des sections de code dans l’éditeur Visual Studio</span><span class="sxs-lookup"><span data-stu-id="423a7-108">[#Region Directive](region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="423a7-109">**#Disable, #Enable** --désactiver et activer des avertissements spécifiques pour les régions de code.</span><span class="sxs-lookup"><span data-stu-id="423a7-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="423a7-110">Vous pouvez désactiver et activer une liste séparée par des virgules de codes d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="423a7-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="423a7-111">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="423a7-111">Related Sections</span></span>  

 [<span data-ttu-id="423a7-112">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="423a7-112">Visual Basic Language Reference</span></span>](../index.md)  
  