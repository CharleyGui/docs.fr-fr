---
title: 'Procédure : hériter de la classe UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f4055c2374103b7df941d9a9bef24ed5e6cb27c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015844"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="75e17-102">Procédure : hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="75e17-102">How to: Inherit from the UserControl Class</span></span>

<span data-ttu-id="75e17-103">Pour combiner les fonctionnalités d’un ou de plusieurs contrôles Windows Forms avec du code personnalisé, vous pouvez créer un *contrôle utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="75e17-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="75e17-104">Les contrôles utilisateur allient le développement rapide de contrôles, les fonctionnalités des contrôles Windows Forms standard et la polyvalence des propriétés et méthodes personnalisées.</span><span class="sxs-lookup"><span data-stu-id="75e17-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="75e17-105">Lorsque vous créez un contrôle utilisateur, un concepteur visible, sur lequel vous pouvez placer des contrôles Windows Forms standard, s’affiche.</span><span class="sxs-lookup"><span data-stu-id="75e17-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="75e17-106">Ces contrôles conservent toutes leurs fonctionnalités inhérentes, ainsi que l’apparence et le comportement de contrôles standard.</span><span class="sxs-lookup"><span data-stu-id="75e17-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="75e17-107">Une fois que ces contrôles sont générés dans le contrôle utilisateur, ils ne sont toutefois plus disponibles par le biais du code.</span><span class="sxs-lookup"><span data-stu-id="75e17-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="75e17-108">Le contrôle utilisateur effectue sa propre peinture et gère également toutes les fonctionnalités de base associées aux contrôles.</span><span class="sxs-lookup"><span data-stu-id="75e17-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="75e17-109">Pour créer un contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="75e17-109">To create a user control</span></span>

1. <span data-ttu-id="75e17-110">Créez un projet de **bibliothèque de contrôles Windows** dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75e17-110">Create a new **Windows Control Library** project in Visual Studio.</span></span>

   <span data-ttu-id="75e17-111">Un projet est créé avec un contrôle utilisateur vide.</span><span class="sxs-lookup"><span data-stu-id="75e17-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="75e17-112">Faites glisser des contrôles de l’onglet **Windows Forms** de la **boîte à outils** vers votre concepteur.</span><span class="sxs-lookup"><span data-stu-id="75e17-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="75e17-113">Positionnez et concevez ces contrôles comme vous souhaitez qu’ils apparaissent dans le contrôle utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="75e17-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="75e17-114">Si vous souhaitez permettre aux développeurs d’accéder aux contrôles constitutifs, vous devez les déclarer publics ou exposer de manière sélective les propriétés du contrôle constitutif.</span><span class="sxs-lookup"><span data-stu-id="75e17-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="75e17-115">Pour plus d’informations, consultez [Guide pratique pour Exposer les propriétés des contrôles](how-to-expose-properties-of-constituent-controls.md)constitutifs.</span><span class="sxs-lookup"><span data-stu-id="75e17-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="75e17-116">Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.</span><span class="sxs-lookup"><span data-stu-id="75e17-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="75e17-117">Appuyez sur **F5** pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="75e17-117">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="75e17-118">Pour plus d’informations, consultez [Guide pratique pour Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="75e17-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75e17-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75e17-119">See also</span></span>

- [<span data-ttu-id="75e17-120">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="75e17-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="75e17-121">Guide pratique : Hériter de la classe de contrôle</span><span class="sxs-lookup"><span data-stu-id="75e17-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="75e17-122">Guide pratique pour Hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="75e17-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="75e17-123">Guide pratique pour Créer des contrôles pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75e17-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="75e17-124">Résoudre les problèmes liés aux gestionnaires d’événements hérités dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75e17-124">Troubleshoot Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="75e17-125">Guide pratique pour Tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="75e17-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
