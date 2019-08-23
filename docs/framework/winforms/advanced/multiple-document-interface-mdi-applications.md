---
title: Applications d'interface multidocument (MDI, Multiple Document Interface)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956557"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="4a382-102">Applications d'interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="4a382-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="4a382-103">Les applications d’interface multidocument (MDI, multiple-document interface) vous permettent d’afficher plusieurs documents en même temps, chaque document étant affiché dans sa propre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4a382-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="4a382-104">Les applications MDI ont souvent un élément de menu fenêtre avec des sous-menus pour basculer entre les fenêtres ou les documents.</span><span class="sxs-lookup"><span data-stu-id="4a382-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a382-105">Il existe des différences de comportement entre les formulaires MDI et les fenêtres SDI (single-document interface) dans Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4a382-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="4a382-106">La `Opacity` propriété n’affecte pas l’apparence des formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="4a382-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="4a382-107">En outre, la <xref:System.Windows.Forms.Form.CenterToParent%2A> méthode n’affecte pas le comportement des formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="4a382-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a382-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4a382-108">In This Section</span></span>  
 [<span data-ttu-id="4a382-109">Guide pratique pour Créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="4a382-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="4a382-110">Explique comment créer le conteneur pour les documents multiples dans une application MDI.</span><span class="sxs-lookup"><span data-stu-id="4a382-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="4a382-111">Guide pratique pour Créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="4a382-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="4a382-112">Explique comment créer une ou plusieurs fenêtres qui fonctionnent dans un formulaire MDI parent.</span><span class="sxs-lookup"><span data-stu-id="4a382-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="4a382-113">Guide pratique pour Déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="4a382-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="4a382-114">Fournit des instructions pour vérifier la fenêtre enfant qui a le focus (et envoyer son contenu vers le presse-papiers).</span><span class="sxs-lookup"><span data-stu-id="4a382-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="4a382-115">Guide pratique pour Envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="4a382-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="4a382-116">Explique comment transporter des informations vers la fenêtre enfant active.</span><span class="sxs-lookup"><span data-stu-id="4a382-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="4a382-117">Guide pratique pour Réorganiser les formulaires enfants MDI</span><span class="sxs-lookup"><span data-stu-id="4a382-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="4a382-118">Fournit des instructions pour la mosaïque, la cascade ou la réorganisation des fenêtres enfants d’une application MDI.</span><span class="sxs-lookup"><span data-stu-id="4a382-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
