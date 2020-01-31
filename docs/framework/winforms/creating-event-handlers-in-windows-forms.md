---
title: Créer des gestionnaires d’événements
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 90acb3c7691acbcb528ae66692af67c2fb28eeaf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742335"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="a14cf-102">Création de gestionnaires d'événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a14cf-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="a14cf-103">Un gestionnaire d'événements est une procédure de votre code qui détermine les actions à effectuer quand un événement se produit, par exemple, quand un utilisateur clique sur un bouton ou une file d'attente reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="a14cf-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="a14cf-104">Au déclenchement de l'événement, le ou les gestionnaires d'événements qui reçoivent l'événement sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="a14cf-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="a14cf-105">Des événements peuvent être affectés à plusieurs gestionnaires et les méthodes qui gèrent des événements particuliers peuvent être modifiées de façon dynamique.</span><span class="sxs-lookup"><span data-stu-id="a14cf-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="a14cf-106">Vous pouvez également utiliser la Concepteur Windows Forms dans Visual Studio pour créer des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="a14cf-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a14cf-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a14cf-107">In This Section</span></span>

 <span data-ttu-id="a14cf-108">[Vue d’ensemble des événements](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-108">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="a14cf-109">Présente le modèle d'événement et explique le rôle des délégués.</span><span class="sxs-lookup"><span data-stu-id="a14cf-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="a14cf-110">[Vue d’ensemble des gestionnaires d’événements](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="a14cf-111">Explique comment gérer les événements.</span><span class="sxs-lookup"><span data-stu-id="a14cf-111">Describes how to handle events.</span></span>

 <span data-ttu-id="a14cf-112">[Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="a14cf-113">Explique comment répondre dynamiquement aux événements système ou utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a14cf-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="a14cf-114">[Comment : connecter plusieurs événements à un même gestionnaire d’événements dans Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="a14cf-115">Explique comment assigner la même fonctionnalité à plusieurs contrôles par le biais d'événements.</span><span class="sxs-lookup"><span data-stu-id="a14cf-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="a14cf-116">[Ordre des événements dans Windows Forms](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="a14cf-117">Décrit l'ordre dans lequel les événements sont déclenchés dans les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a14cf-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="a14cf-118">[Comment : créer des gestionnaires d’événements à l’aide du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Décrit comment utiliser l’Concepteur Windows Forms pour créer des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="a14cf-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a14cf-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a14cf-119">Related Sections</span></span>

 <span data-ttu-id="a14cf-120">[Événements](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-120">[Events](../../standard/events/index.md)</span></span>\
 <span data-ttu-id="a14cf-121">Fournit des liens vers des rubriques sur la gestion et le déclenchement d’événements à l’aide de l' .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a14cf-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="a14cf-122">[Dépannage des gestionnaires d’événements hérités en Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="a14cf-122">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="a14cf-123">Répertorie les problèmes courants qui surviennent avec les gestionnaires d'événements dans les composants hérités.</span><span class="sxs-lookup"><span data-stu-id="a14cf-123">Lists common issues that occur with event handlers in inherited components.</span></span>
