---
title: Création de gestionnaires d'événements dans les Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 6b1d146dfd9d51641bc9eb5d8be4cd2508c223a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963478"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="3b8c2-102">Création de gestionnaires d'événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b8c2-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="3b8c2-103">Un gestionnaire d'événements est une procédure de votre code qui détermine les actions à effectuer quand un événement se produit, par exemple, quand un utilisateur clique sur un bouton ou une file d'attente reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="3b8c2-104">Au déclenchement de l'événement, le ou les gestionnaires d'événements qui reçoivent l'événement sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="3b8c2-105">Des événements peuvent être affectés à plusieurs gestionnaires et les méthodes qui gèrent des événements particuliers peuvent être modifiées de façon dynamique.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="3b8c2-106">Vous pouvez également utiliser la Concepteur Windows Forms dans Visual Studio pour créer des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3b8c2-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3b8c2-107">In This Section</span></span>

 <span data-ttu-id="3b8c2-108">[Vue d’ensemble des événements](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-108">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="3b8c2-109">Présente le modèle d'événement et explique le rôle des délégués.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="3b8c2-110">[Vue d’ensemble des gestionnaires d’événements](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="3b8c2-111">Explique comment gérer les événements.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-111">Describes how to handle events.</span></span>

 <span data-ttu-id="3b8c2-112">[Guide pratique : Créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="3b8c2-113">Explique comment répondre dynamiquement aux événements système ou utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="3b8c2-114">[Guide pratique : Connecter plusieurs événements à un même gestionnaire d’événements dans Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="3b8c2-115">Explique comment assigner la même fonctionnalité à plusieurs contrôles par le biais d'événements.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="3b8c2-116">[Ordre des événements dans Windows Forms](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="3b8c2-117">Décrit l'ordre dans lequel les événements sont déclenchés dans les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="3b8c2-118">[Guide pratique pour Créer des gestionnaires d’événements à l'](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) aide du concepteur décrit comment utiliser l’Concepteur Windows Forms pour créer des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3b8c2-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3b8c2-119">Related Sections</span></span>

 <span data-ttu-id="3b8c2-120">[Événements](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-120">[Events](../../standard/events/index.md)</span></span>\
 <span data-ttu-id="3b8c2-121">Fournit des liens vers des rubriques sur la gestion et le déclenchement d’événements à l’aide de l' .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="3b8c2-122">[Dépannage des gestionnaires d’événements hérités en Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="3b8c2-122">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="3b8c2-123">Répertorie les problèmes courants qui surviennent avec les gestionnaires d'événements dans les composants hérités.</span><span class="sxs-lookup"><span data-stu-id="3b8c2-123">Lists common issues that occur with event handlers in inherited components.</span></span>
