---
title: Intégration de l’aide de l’utilisateur
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: c402615d68c75327613d21bd35f1587b10f1dbf3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731565"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="f4bdc-102">Intégration de l'aide d'utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4bdc-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="f4bdc-103">Un aspect essentiel, mais souvent négligé, de la création d’applications Windows est le système d’aide, car il s’agit de l’endroit où les utilisateurs activent l’assistance en cas de confusion.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="f4bdc-104">Windows Forms prendre en charge deux types d’aide différents, chacun étant fourni par le [composant HelpProvider](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f4bdc-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="f4bdc-105">La première consiste à faire pointer l’utilisateur vers un fichier d’aide HTML ou HTML Help 1. format *x* ou supérieur.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="f4bdc-106">Le deuxième peut afficher un bref « qu’est-ce que c’est »-tapez de l’aide sur des contrôles individuels. Cela s’avère particulièrement utile dans les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="f4bdc-107">Les deux types d’aide peuvent être utilisés sur le même formulaire.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="f4bdc-108">En outre, le [composant ToolTip](../controls/tooltip-component-windows-forms.md) peut être utilisé pour fournir une aide individuelle pour les contrôles sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4bdc-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f4bdc-109">In This Section</span></span>  
 [<span data-ttu-id="f4bdc-110">Guide pratique pour fournir de l'aide dans une application Windows</span><span class="sxs-lookup"><span data-stu-id="f4bdc-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="f4bdc-111">Explique comment utiliser le composant `HelpProvider` pour lier des contrôles à des fichiers dans un système d’aide.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="f4bdc-112">Guide pratique pour afficher l’aide contextuelle</span><span class="sxs-lookup"><span data-stu-id="f4bdc-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="f4bdc-113">Explique comment utiliser le composant `HelpProvider` pour afficher l’aide contextuelle sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="f4bdc-114">Affichage sous forme d’info-bulles de l’aide relative aux contrôles</span><span class="sxs-lookup"><span data-stu-id="f4bdc-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="f4bdc-115">Décrit l’utilisation du composant `ToolTip` pour afficher l’aide spécifique au contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f4bdc-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="f4bdc-116">Related Sections</span></span>  
 [<span data-ttu-id="f4bdc-117">HelpProvider, composant</span><span class="sxs-lookup"><span data-stu-id="f4bdc-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="f4bdc-118">Explique les principes de base du composant `HelpProvider`.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="f4bdc-119">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="f4bdc-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="f4bdc-120">Explique les principes de base du composant `ToolTip`.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="f4bdc-121">Vue d'ensemble des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4bdc-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="f4bdc-122">Explique les notions de base de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="f4bdc-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4bdc-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="f4bdc-124">Fournit une vue d’ensemble de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f4bdc-124">Provides an overview of Windows Forms.</span></span>
