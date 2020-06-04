---
title: Variables objets
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410333"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="29e4b-102">Variables objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29e4b-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="29e4b-103">Outre le stockage direct des valeurs, une variable peut faire référence à un objet.</span><span class="sxs-lookup"><span data-stu-id="29e4b-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="29e4b-104">Vous assignez un objet à une variable pour les mêmes raisons que vous attribuez une valeur à une variable :</span><span class="sxs-lookup"><span data-stu-id="29e4b-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="29e4b-105">Un nom de variable est souvent plus concis et plus facile à mémoriser que le chemin complet des méthodes et propriétés nécessaires pour accéder à l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="29e4b-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="29e4b-106">L’utilisation d’une variable qui fait référence à un objet est plus efficace que l’accès répété à l’objet lui-même par le biais des méthodes ou propriétés nécessaires.</span><span class="sxs-lookup"><span data-stu-id="29e4b-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="29e4b-107">Vous pouvez modifier une variable pour faire référence à d’autres objets pendant l’exécution de votre code.</span><span class="sxs-lookup"><span data-stu-id="29e4b-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="29e4b-108">Rendre le code plus concis</span><span class="sxs-lookup"><span data-stu-id="29e4b-108">Making Code Shorter</span></span>

<span data-ttu-id="29e4b-109">Vous pouvez utiliser des variables d’objet pour raccourcir le code que vous devez taper.</span><span class="sxs-lookup"><span data-stu-id="29e4b-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="29e4b-110">L’exemple suivant utilise le chemin d’accès complet des méthodes et des propriétés pour accéder à un <xref:System.Windows.Forms.Control> objet.</span><span class="sxs-lookup"><span data-stu-id="29e4b-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="29e4b-111">Vous pouvez raccourcir ce code et accélérer l’exécution, si vous utilisez une variable objet pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="29e4b-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="29e4b-112">Vous devez déclarer la variable objet avec la classe spécifique que vous souhaitez lui assigner ( `Control` dans ce cas).</span><span class="sxs-lookup"><span data-stu-id="29e4b-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="29e4b-113">Une fois que vous affectez un objet à la variable, vous pouvez le traiter exactement de la même façon que vous traitez l’objet auquel il fait référence.</span><span class="sxs-lookup"><span data-stu-id="29e4b-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="29e4b-114">Vous pouvez définir ou récupérer les propriétés de l’objet ou utiliser l’une de ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="29e4b-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="29e4b-115">L’exemple suivant utilise une variable objet pour simplifier le code de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="29e4b-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="29e4b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29e4b-116">See also</span></span>

- [<span data-ttu-id="29e4b-117">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="29e4b-117">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="29e4b-118">Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long</span><span class="sxs-lookup"><span data-stu-id="29e4b-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="29e4b-119">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="29e4b-119">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="29e4b-120">Affectation des variables objets</span><span class="sxs-lookup"><span data-stu-id="29e4b-120">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="29e4b-121">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="29e4b-121">Object Variable Values</span></span>](object-variable-values.md)
