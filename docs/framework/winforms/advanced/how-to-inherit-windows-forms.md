---
title: Héritage de formulaire
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: cc3a4cc75fd13e8f193a6920ed5b4a9bc8fd5d74
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743324"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="59892-102">Comment : hériter des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59892-102">How to: Inherit Windows Forms</span></span>

<span data-ttu-id="59892-103">Créer des Windows Forms en héritant de formulaires de base est un moyen pratique de dupliquer vos efforts sans avoir à recréer entièrement un formulaire chaque fois que vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="59892-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>

<span data-ttu-id="59892-104">Pour plus d’informations sur l’héritage des formulaires au moment du design à l’aide de la boîte de dialogue **Sélecteur d’héritage** et sur la façon d’effectuer une distinction visuelle entre les niveaux de sécurité des contrôles hérités, consultez [Comment : hériter de formulaires à l’aide de la boîte de dialogue Sélecteur d’héritage](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="59892-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>

> [!NOTE]
> <span data-ttu-id="59892-105">Pour hériter d’un formulaire, le fichier ou l’espace de noms contenant ce formulaire doit avoir été intégré à un fichier exécutable ou une DLL.</span><span class="sxs-lookup"><span data-stu-id="59892-105">In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="59892-106">Pour générer le projet, choisissez **Générer** dans le menu **Générer**.</span><span class="sxs-lookup"><span data-stu-id="59892-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="59892-107">De plus, une référence à l'espace de noms doit être ajoutée à la classe héritant du formulaire.</span><span class="sxs-lookup"><span data-stu-id="59892-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span>

## <a name="inherit-a-form-programmatically"></a><span data-ttu-id="59892-108">Hériter d’un formulaire par programmation</span><span class="sxs-lookup"><span data-stu-id="59892-108">Inherit a form programmatically</span></span>

1. <span data-ttu-id="59892-109">Dans votre classe, ajoutez une référence à l'espace de noms contenant le formulaire dont vous voulez hériter.</span><span class="sxs-lookup"><span data-stu-id="59892-109">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>

2. <span data-ttu-id="59892-110">Dans la définition de classe, ajoutez une référence au formulaire à partir duquel hériter.</span><span class="sxs-lookup"><span data-stu-id="59892-110">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="59892-111">Cette référence doit inclure l'espace de noms qui contient le formulaire, suivi d'un point, puis du nom du formulaire de base proprement dit.</span><span class="sxs-lookup"><span data-stu-id="59892-111">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 <span data-ttu-id="59892-112">Lors de l'héritage de formulaires, n'oubliez pas que des problèmes peuvent survenir car les gestionnaires d'événements peuvent être appelés deux fois (chaque événement étant géré par la classe de base et par la classe héritée).</span><span class="sxs-lookup"><span data-stu-id="59892-112">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="59892-113">Pour plus d’informations sur la façon d’éviter ce problème, consultez [Dépannage des gestionnaires d’événements hérités dans Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="59892-113">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59892-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59892-114">See also</span></span>

- [<span data-ttu-id="59892-115">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="59892-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="59892-116">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="59892-116">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="59892-117">using</span><span class="sxs-lookup"><span data-stu-id="59892-117">using</span></span>](../../../csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="59892-118">Conséquences de la modification de l’aspect d’un formulaire de base</span><span class="sxs-lookup"><span data-stu-id="59892-118">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="59892-119">Héritage visuel des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59892-119">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
