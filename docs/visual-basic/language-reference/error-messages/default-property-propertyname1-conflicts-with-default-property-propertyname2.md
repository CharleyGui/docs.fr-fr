---
title: La propriété par défaut '<propertyname1>' est en conflit avec la propriété par défaut '<propertyname2>' de la classe '<classname>' et devrait donc être déclarée 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b857a9ae7875a156179602cbe77558333d07b7b9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874511"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="10be2-102">La propriété par défaut '\<propertyname1>' est en conflit avec la propriété par défaut '\<propertyname2>' de la classe '\<classname>' et devrait donc être déclarée 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="10be2-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>

<span data-ttu-id="10be2-103">Une propriété est déclarée avec le même nom qu’une propriété définie dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="10be2-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="10be2-104">Dans ce cas, la propriété de cette classe doit occulter la propriété de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="10be2-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="10be2-105">Ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="10be2-105">This message is a warning.</span></span> <span data-ttu-id="10be2-106">`Shadows` est supposé par défaut.</span><span class="sxs-lookup"><span data-stu-id="10be2-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="10be2-107">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="10be2-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="10be2-108">**ID d’erreur :** BC40007</span><span class="sxs-lookup"><span data-stu-id="10be2-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10be2-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="10be2-109">To correct this error</span></span>  
  
- <span data-ttu-id="10be2-110">Ajoutez le `Shadows` mot clé à la déclaration ou modifiez le nom de la propriété déclarée.</span><span class="sxs-lookup"><span data-stu-id="10be2-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10be2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10be2-111">See also</span></span>

- [<span data-ttu-id="10be2-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="10be2-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="10be2-113">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10be2-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
