---
title: Applications d'interface multidocument (MDI, Multiple Document Interface)
description: Découvrez comment Windows Forms des applications d’interface multidocument (MDI) vous permettent d’afficher plusieurs documents en même temps, chaque document étant affiché dans sa propre fenêtre.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174651"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="0585d-103">Applications d'interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="0585d-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="0585d-104">Les applications d’interface multidocument (MDI, multiple-document interface) vous permettent d’afficher plusieurs documents en même temps, chaque document étant affiché dans sa propre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0585d-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="0585d-105">Les applications MDI ont souvent un élément de menu fenêtre avec des sous-menus pour basculer entre les fenêtres ou les documents.</span><span class="sxs-lookup"><span data-stu-id="0585d-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0585d-106">Il existe des différences de comportement entre les formulaires MDI et les fenêtres SDI (single-document interface) dans Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0585d-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="0585d-107">La `Opacity` propriété n’affecte pas l’apparence des formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="0585d-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="0585d-108">En outre, la <xref:System.Windows.Forms.Form.CenterToParent%2A> méthode n’affecte pas le comportement des formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="0585d-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0585d-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0585d-109">In This Section</span></span>  
 [<span data-ttu-id="0585d-110">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="0585d-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="0585d-111">Explique comment créer le conteneur pour les documents multiples dans une application MDI.</span><span class="sxs-lookup"><span data-stu-id="0585d-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="0585d-112">Comment : créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="0585d-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="0585d-113">Explique comment créer une ou plusieurs fenêtres qui fonctionnent dans un formulaire MDI parent.</span><span class="sxs-lookup"><span data-stu-id="0585d-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="0585d-114">Comment : déterminer l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="0585d-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="0585d-115">Fournit des instructions pour vérifier la fenêtre enfant qui a le focus (et envoyer son contenu vers le presse-papiers).</span><span class="sxs-lookup"><span data-stu-id="0585d-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="0585d-116">Comment : envoyer des données à l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="0585d-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="0585d-117">Explique comment transporter des informations vers la fenêtre enfant active.</span><span class="sxs-lookup"><span data-stu-id="0585d-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="0585d-118">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="0585d-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="0585d-119">Fournit des instructions pour la mosaïque, la cascade ou la réorganisation des fenêtres enfants d’une application MDI.</span><span class="sxs-lookup"><span data-stu-id="0585d-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
