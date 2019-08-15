---
title: Conséquences de la modification de l'aspect d'un formulaire de base
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040137"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="bf902-102">Effets de la modification de l’apparence d’un formulaire de base</span><span class="sxs-lookup"><span data-stu-id="bf902-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="bf902-103">Pendant le développement d’applications, vous êtes souvent amené à modifier l’apparence du formulaire de base dont héritent d’autres formulaires du projet (ou d’autres projets).</span><span class="sxs-lookup"><span data-stu-id="bf902-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="bf902-104">Au moment du design, les modifications apportées à l’aspect du formulaire de base (qu’il s’agisse de la définition de propriétés ou de l’addition et de la soustraction de contrôles) sont répercutées dans les formulaires hérités lors de la génération du projet contenant le formulaire de base.</span><span class="sxs-lookup"><span data-stu-id="bf902-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="bf902-105">Il ne suffit pas d’enregistrer les modifications apportées au formulaire de base.</span><span class="sxs-lookup"><span data-stu-id="bf902-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="bf902-106">Pour générer un projet, sélectionnez **Générer** dans le menu **Générer**.</span><span class="sxs-lookup"><span data-stu-id="bf902-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="bf902-107">Les modifications apportées au formulaire à l’exécution n’ont aucune incidence sur les formulaires hérités déjà instanciés.</span><span class="sxs-lookup"><span data-stu-id="bf902-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf902-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf902-108">See also</span></span>

- [<span data-ttu-id="bf902-109">base</span><span class="sxs-lookup"><span data-stu-id="bf902-109">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="bf902-110">Guide pratique : Hériter Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf902-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="bf902-111">Héritage visuel des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf902-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
