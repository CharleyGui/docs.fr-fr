---
title: 'Procédure pas à pas : création d’une application Windows accessible'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: c324e4956d6db29e4de12bd7639a69daaf65d872
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665926"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="6100e-102">Procédure pas à pas : création d’une application Windows accessible</span><span class="sxs-lookup"><span data-stu-id="6100e-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="6100e-103">La création d'une application accessible implique de nombreuses contraintes pour l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6100e-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="6100e-104">De nombreux gouvernements ont mis en place une réglementation relative à l'accessibilité pour l'achat des logiciels.</span><span class="sxs-lookup"><span data-stu-id="6100e-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="6100e-105">Le logo Certifié pour Windows inclut des normes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="6100e-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="6100e-106">Rien qu’aux États-Unis, on estime à 30 millions le nombre de personnes affectées par l’accessibilité des logiciels, dont beaucoup sont des clients potentiels.</span><span class="sxs-lookup"><span data-stu-id="6100e-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="6100e-107">Cette procédure pas à pas traite des cinq critères d’accessibilité pour le logo Certifié pour Windows.</span><span class="sxs-lookup"><span data-stu-id="6100e-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="6100e-108">Selon ces critères, une application accessible doit :</span><span class="sxs-lookup"><span data-stu-id="6100e-108">According to these requirements, an accessible application will:</span></span>  
  
- <span data-ttu-id="6100e-109">prendre en charge les paramètres de taille, de couleurs, de police et d'entrée du Panneau de configuration ;</span><span class="sxs-lookup"><span data-stu-id="6100e-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="6100e-110">La barre de menus, la barre de titre, les bordures et la barre d'état sont redimensionnés automatiquement quand l'utilisateur modifie les paramètres du Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="6100e-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="6100e-111">Aucune autre modification des contrôles ou du code n'est nécessaire dans cette application.</span><span class="sxs-lookup"><span data-stu-id="6100e-111">No additional changes to the controls or code are required in this application.</span></span>  
  
- <span data-ttu-id="6100e-112">prendre en charge le mode de contraste élevé ;</span><span class="sxs-lookup"><span data-stu-id="6100e-112">Support High Contrast mode.</span></span>  
  
- <span data-ttu-id="6100e-113">fournir un accès au clavier documenté à toutes les fonctionnalités ;</span><span class="sxs-lookup"><span data-stu-id="6100e-113">Provide documented keyboard access to all features.</span></span>  
  
- <span data-ttu-id="6100e-114">exposer l'emplacement du focus clavier visuellement et par programmation ;</span><span class="sxs-lookup"><span data-stu-id="6100e-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
- <span data-ttu-id="6100e-115">éviter de transmettre des informations importantes uniquement par voie sonore.</span><span class="sxs-lookup"><span data-stu-id="6100e-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="6100e-116">Pour plus d’informations, consultez [Ressources pour la conception d’applications accessibles](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="6100e-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="6100e-117">Pour plus d’informations sur la prise en charge des différentes dispositions du clavier, consultez [Bonnes pratiques pour développer des applications mondialisables](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="6100e-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6100e-118">Création du projet</span><span class="sxs-lookup"><span data-stu-id="6100e-118">Creating the Project</span></span>  
 <span data-ttu-id="6100e-119">Cette procédure pas à pas crée l'interface utilisateur pour une application de commande de pizza.</span><span class="sxs-lookup"><span data-stu-id="6100e-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="6100e-120">Elle se compose d'un <xref:System.Windows.Forms.TextBox> pour le nom du client, d'un groupe <xref:System.Windows.Forms.RadioButton> pour sélectionner la taille de la pizza, d'un <xref:System.Windows.Forms.CheckedListBox> pour sélectionner les ingrédients, de deux contrôles bouton étiquetés Commande et Annuler et d'un menu avec une commande Quitter.</span><span class="sxs-lookup"><span data-stu-id="6100e-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="6100e-121">L'utilisateur entre le nom du client, la taille de la pizza et les ingrédients souhaités.</span><span class="sxs-lookup"><span data-stu-id="6100e-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="6100e-122">Quand l'utilisateur clique sur le bouton de commande, un résumé de la commande et son prix sont affichés dans une boîte de message et les contrôles sont effacés et prêts pour la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="6100e-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="6100e-123">Quand l'utilisateur clique sur le bouton Annuler, les contrôles sont effacés et prêts pour la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="6100e-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="6100e-124">Quand l'utilisateur clique sur l'élément de menu Quitter, le programme se ferme.</span><span class="sxs-lookup"><span data-stu-id="6100e-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="6100e-125">L'objectif principal de cette procédure pas à pas n'est pas d'illustrer le code pour un système de commande de vente au détail, mais l'accessibilité de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6100e-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="6100e-126">La procédure pas à pas illustre les fonctionnalités d'accessibilité de plusieurs contrôles courants, y compris les boutons, les cases d'option, les zones de texte et les étiquettes.</span><span class="sxs-lookup"><span data-stu-id="6100e-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="6100e-127">Pour commencer à créer l'application</span><span class="sxs-lookup"><span data-stu-id="6100e-127">To begin making the application</span></span>  
  
- <span data-ttu-id="6100e-128">Créez une Application Windows en Visual Basic ou Visual C#.</span><span class="sxs-lookup"><span data-stu-id="6100e-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="6100e-129">Nommez le projet **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="6100e-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="6100e-130">(Pour plus d’informations, consultez [Création de projets et de solutions](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="6100e-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="6100e-131">Ajout des contrôles au formulaire</span><span class="sxs-lookup"><span data-stu-id="6100e-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="6100e-132">Lors de l'ajout des contrôles à un formulaire, veillez à respecter les consignes d'accessibilité suivantes :</span><span class="sxs-lookup"><span data-stu-id="6100e-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
- <span data-ttu-id="6100e-133">Définissez les propriétés <xref:System.Windows.Forms.Control.AccessibleDescription%2A> et <xref:System.Windows.Forms.Control.AccessibleName%2A>.</span><span class="sxs-lookup"><span data-stu-id="6100e-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="6100e-134">Dans cet exemple, le paramètre Default pour <xref:System.Windows.Forms.Control.AccessibleRole%2A> est suffisant.</span><span class="sxs-lookup"><span data-stu-id="6100e-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="6100e-135">Pour plus d’informations sur les propriétés d’accessibilité, consultez [Informations d’accessibilité sur les contrôles d’un Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="6100e-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
- <span data-ttu-id="6100e-136">Définissez la taille de police sur 10 points ou plus.</span><span class="sxs-lookup"><span data-stu-id="6100e-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6100e-137">Si vous affectez la valeur 10 à la taille de police du formulaire quand vous commencez, tous les contrôles qui seront ensuite ajoutés au formulaire auront une taille de police de 10.</span><span class="sxs-lookup"><span data-stu-id="6100e-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
- <span data-ttu-id="6100e-138">Assurez-vous que tous les contrôles Label qui décrivent un contrôle TextBox précèdent immédiatement le contrôle TextBox dans l'ordre de tabulation.</span><span class="sxs-lookup"><span data-stu-id="6100e-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
- <span data-ttu-id="6100e-139">Ajouter une clé d’accès, à l’aide du caractère « & », à la <xref:System.Windows.Forms.Control.Text%2A> propriété de n’importe quel contrôle de l’utilisateur doit pouvoir accéder à.</span><span class="sxs-lookup"><span data-stu-id="6100e-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
- <span data-ttu-id="6100e-140">Ajouter une clé d’accès, à l’aide du caractère « & », à la <xref:System.Windows.Forms.Control.Text%2A> propriété de l’étiquette qui précède un contrôle auquel l’utilisateur doit pouvoir accéder à.</span><span class="sxs-lookup"><span data-stu-id="6100e-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="6100e-141">Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> des étiquettes pour que le focus soit défini sur le contrôle suivant dans l'ordre de tabulation quand l'utilisateur appuie sur la touche d'accès.</span><span class="sxs-lookup"><span data-stu-id="6100e-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
- <span data-ttu-id="6100e-142">Ajoutez des touches d'accès rapide à tous les éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="6100e-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="6100e-143">Pour rendre votre application Windows accessible</span><span class="sxs-lookup"><span data-stu-id="6100e-143">To make your Windows Application accessible</span></span>  
  
- <span data-ttu-id="6100e-144">Ajoutez les contrôles au formulaire et définissez les propriétés comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6100e-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="6100e-145">Pour obtenir un modèle décrivant comment organiser les contrôles sur le formulaire, consultez l'image à la fin du tableau.</span><span class="sxs-lookup"><span data-stu-id="6100e-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="6100e-146">Object</span><span class="sxs-lookup"><span data-stu-id="6100e-146">Object</span></span>|<span data-ttu-id="6100e-147">Propriété</span><span class="sxs-lookup"><span data-stu-id="6100e-147">Property</span></span>|<span data-ttu-id="6100e-148">Value</span><span class="sxs-lookup"><span data-stu-id="6100e-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="6100e-149">Form1</span><span class="sxs-lookup"><span data-stu-id="6100e-149">Form1</span></span>|<span data-ttu-id="6100e-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-150">AccessibleDescription</span></span>|<span data-ttu-id="6100e-151">Formulaire de commande</span><span class="sxs-lookup"><span data-stu-id="6100e-151">Order form</span></span>|  
    ||<span data-ttu-id="6100e-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-152">AccessibleName</span></span>|<span data-ttu-id="6100e-153">Formulaire de commande</span><span class="sxs-lookup"><span data-stu-id="6100e-153">Order form</span></span>|  
    ||<span data-ttu-id="6100e-154">Taille de police</span><span class="sxs-lookup"><span data-stu-id="6100e-154">Font Size</span></span>|<span data-ttu-id="6100e-155">10</span><span class="sxs-lookup"><span data-stu-id="6100e-155">10</span></span>|  
    ||<span data-ttu-id="6100e-156">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-156">Text</span></span>|<span data-ttu-id="6100e-157">Formulaire de commande de pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="6100e-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="6100e-158">PictureBox</span></span>|<span data-ttu-id="6100e-159">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-159">Name</span></span>|<span data-ttu-id="6100e-160">logo</span><span class="sxs-lookup"><span data-stu-id="6100e-160">logo</span></span>|  
    ||<span data-ttu-id="6100e-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-161">AccessibleDescription</span></span>|<span data-ttu-id="6100e-162">Une tranche de pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="6100e-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-163">AccessibleName</span></span>|<span data-ttu-id="6100e-164">Logo de la société</span><span class="sxs-lookup"><span data-stu-id="6100e-164">Company logo</span></span>|  
    ||<span data-ttu-id="6100e-165">Image</span><span class="sxs-lookup"><span data-stu-id="6100e-165">Image</span></span>|<span data-ttu-id="6100e-166">Une icône ou bitmap quelconque</span><span class="sxs-lookup"><span data-stu-id="6100e-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="6100e-167">Etiquette</span><span class="sxs-lookup"><span data-stu-id="6100e-167">Label</span></span>|<span data-ttu-id="6100e-168">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-168">Name</span></span>|<span data-ttu-id="6100e-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="6100e-169">companyLabel</span></span>|  
    ||<span data-ttu-id="6100e-170">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-170">Text</span></span>|<span data-ttu-id="6100e-171">Bonne Pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="6100e-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-172">TabIndex</span></span>|<span data-ttu-id="6100e-173">1</span><span class="sxs-lookup"><span data-stu-id="6100e-173">1</span></span>|  
    ||<span data-ttu-id="6100e-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-174">AccessibleDescription</span></span>|<span data-ttu-id="6100e-175">Nom de la société</span><span class="sxs-lookup"><span data-stu-id="6100e-175">Company name</span></span>|  
    ||<span data-ttu-id="6100e-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-176">AccessibleName</span></span>|<span data-ttu-id="6100e-177">Nom de la société</span><span class="sxs-lookup"><span data-stu-id="6100e-177">Company name</span></span>|  
    ||<span data-ttu-id="6100e-178">BackColor</span><span class="sxs-lookup"><span data-stu-id="6100e-178">Backcolor</span></span>|<span data-ttu-id="6100e-179">Bleu</span><span class="sxs-lookup"><span data-stu-id="6100e-179">Blue</span></span>|  
    ||<span data-ttu-id="6100e-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="6100e-180">Forecolor</span></span>|<span data-ttu-id="6100e-181">Jaune</span><span class="sxs-lookup"><span data-stu-id="6100e-181">Yellow</span></span>|  
    ||<span data-ttu-id="6100e-182">Taille de police</span><span class="sxs-lookup"><span data-stu-id="6100e-182">Font size</span></span>|<span data-ttu-id="6100e-183">18</span><span class="sxs-lookup"><span data-stu-id="6100e-183">18</span></span>|  
    |<span data-ttu-id="6100e-184">Label</span><span class="sxs-lookup"><span data-stu-id="6100e-184">Label</span></span>|<span data-ttu-id="6100e-185">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-185">Name</span></span>|<span data-ttu-id="6100e-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="6100e-186">customerLabel</span></span>|  
    ||<span data-ttu-id="6100e-187">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-187">Text</span></span>|<span data-ttu-id="6100e-188">&Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-188">&Name</span></span>|  
    ||<span data-ttu-id="6100e-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-189">TabIndex</span></span>|<span data-ttu-id="6100e-190">2</span><span class="sxs-lookup"><span data-stu-id="6100e-190">2</span></span>|  
    ||<span data-ttu-id="6100e-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-191">AccessibleDescription</span></span>|<span data-ttu-id="6100e-192">Étiquette du nom de client</span><span class="sxs-lookup"><span data-stu-id="6100e-192">Customer name label</span></span>|  
    ||<span data-ttu-id="6100e-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-193">AccessibleName</span></span>|<span data-ttu-id="6100e-194">Étiquette du nom de client</span><span class="sxs-lookup"><span data-stu-id="6100e-194">Customer name label</span></span>|  
    ||<span data-ttu-id="6100e-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="6100e-195">UseMnemonic</span></span>|<span data-ttu-id="6100e-196">True</span><span class="sxs-lookup"><span data-stu-id="6100e-196">True</span></span>|  
    |<span data-ttu-id="6100e-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="6100e-197">TextBox</span></span>|<span data-ttu-id="6100e-198">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-198">Name</span></span>|<span data-ttu-id="6100e-199">CustomerName</span><span class="sxs-lookup"><span data-stu-id="6100e-199">customerName</span></span>|  
    ||<span data-ttu-id="6100e-200">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-200">Text</span></span>|<span data-ttu-id="6100e-201">(aucune)</span><span class="sxs-lookup"><span data-stu-id="6100e-201">(none)</span></span>|  
    ||<span data-ttu-id="6100e-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-202">TabIndex</span></span>|<span data-ttu-id="6100e-203">3</span><span class="sxs-lookup"><span data-stu-id="6100e-203">3</span></span>|  
    ||<span data-ttu-id="6100e-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-204">AccessibleDescription</span></span>|<span data-ttu-id="6100e-205">Nom du client</span><span class="sxs-lookup"><span data-stu-id="6100e-205">Customer name</span></span>|  
    ||<span data-ttu-id="6100e-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-206">AccessibleName</span></span>|<span data-ttu-id="6100e-207">Nom du client</span><span class="sxs-lookup"><span data-stu-id="6100e-207">Customer name</span></span>|  
    |<span data-ttu-id="6100e-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="6100e-208">GroupBox</span></span>|<span data-ttu-id="6100e-209">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-209">Name</span></span>|<span data-ttu-id="6100e-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="6100e-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="6100e-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-211">AccessibleDescription</span></span>|<span data-ttu-id="6100e-212">Options de taille de pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="6100e-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-213">AccessibleName</span></span>|<span data-ttu-id="6100e-214">Options de taille de pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="6100e-215">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-215">Text</span></span>|<span data-ttu-id="6100e-216">Taille de la pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-216">Pizza size</span></span>|  
    ||<span data-ttu-id="6100e-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-217">TabIndex</span></span>|<span data-ttu-id="6100e-218">4</span><span class="sxs-lookup"><span data-stu-id="6100e-218">4</span></span>|  
    |<span data-ttu-id="6100e-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6100e-219">RadioButton</span></span>|<span data-ttu-id="6100e-220">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-220">Name</span></span>|<span data-ttu-id="6100e-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="6100e-221">smallPizza</span></span>|  
    ||<span data-ttu-id="6100e-222">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-222">Text</span></span>|<span data-ttu-id="6100e-223">&Petite €6,00</span><span class="sxs-lookup"><span data-stu-id="6100e-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="6100e-224">Activé</span><span class="sxs-lookup"><span data-stu-id="6100e-224">Checked</span></span>|<span data-ttu-id="6100e-225">True</span><span class="sxs-lookup"><span data-stu-id="6100e-225">True</span></span>|  
    ||<span data-ttu-id="6100e-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-226">TabIndex</span></span>|<span data-ttu-id="6100e-227">0</span><span class="sxs-lookup"><span data-stu-id="6100e-227">0</span></span>|  
    ||<span data-ttu-id="6100e-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-228">AccessibleDescription</span></span>|<span data-ttu-id="6100e-229">Petite pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-229">Small pizza</span></span>|  
    ||<span data-ttu-id="6100e-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-230">AccessibleName</span></span>|<span data-ttu-id="6100e-231">Petite pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-231">Small pizza</span></span>|  
    |<span data-ttu-id="6100e-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6100e-232">RadioButton</span></span>|<span data-ttu-id="6100e-233">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-233">Name</span></span>|<span data-ttu-id="6100e-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="6100e-234">largePizza</span></span>|  
    ||<span data-ttu-id="6100e-235">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-235">Text</span></span>|<span data-ttu-id="6100e-236">&Grande €10,00</span><span class="sxs-lookup"><span data-stu-id="6100e-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="6100e-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-237">TabIndex</span></span>|<span data-ttu-id="6100e-238">1</span><span class="sxs-lookup"><span data-stu-id="6100e-238">1</span></span>|  
    ||<span data-ttu-id="6100e-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-239">AccessibleDescription</span></span>|<span data-ttu-id="6100e-240">Grande pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-240">Large pizza</span></span>|  
    ||<span data-ttu-id="6100e-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-241">AccessibleName</span></span>|<span data-ttu-id="6100e-242">Grande pizza</span><span class="sxs-lookup"><span data-stu-id="6100e-242">Large pizza</span></span>|  
    |<span data-ttu-id="6100e-243">Etiquette</span><span class="sxs-lookup"><span data-stu-id="6100e-243">Label</span></span>|<span data-ttu-id="6100e-244">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-244">Name</span></span>|<span data-ttu-id="6100e-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="6100e-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="6100e-246">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-246">Text</span></span>|<span data-ttu-id="6100e-247">&Garniture (€0,75 chacune)</span><span class="sxs-lookup"><span data-stu-id="6100e-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="6100e-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-248">TabIndex</span></span>|<span data-ttu-id="6100e-249">5</span><span class="sxs-lookup"><span data-stu-id="6100e-249">5</span></span>|  
    ||<span data-ttu-id="6100e-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-250">AccessibleDescription</span></span>|<span data-ttu-id="6100e-251">Étiquette de garniture</span><span class="sxs-lookup"><span data-stu-id="6100e-251">Toppings label</span></span>|  
    ||<span data-ttu-id="6100e-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-252">AccessibleName</span></span>|<span data-ttu-id="6100e-253">Étiquette de garniture</span><span class="sxs-lookup"><span data-stu-id="6100e-253">Toppings label</span></span>|  
    ||<span data-ttu-id="6100e-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="6100e-254">UseMnemonic</span></span>|<span data-ttu-id="6100e-255">True</span><span class="sxs-lookup"><span data-stu-id="6100e-255">True</span></span>|  
    |<span data-ttu-id="6100e-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="6100e-256">CheckedListBox</span></span>|<span data-ttu-id="6100e-257">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-257">Name</span></span>|<span data-ttu-id="6100e-258">Garniture</span><span class="sxs-lookup"><span data-stu-id="6100e-258">toppings</span></span>|  
    ||<span data-ttu-id="6100e-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-259">TabIndex</span></span>|<span data-ttu-id="6100e-260">6</span><span class="sxs-lookup"><span data-stu-id="6100e-260">6</span></span>|  
    ||<span data-ttu-id="6100e-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-261">AccessibleDescription</span></span>|<span data-ttu-id="6100e-262">Garniture disponible</span><span class="sxs-lookup"><span data-stu-id="6100e-262">Available toppings</span></span>|  
    ||<span data-ttu-id="6100e-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-263">AccessibleName</span></span>|<span data-ttu-id="6100e-264">Garniture disponible</span><span class="sxs-lookup"><span data-stu-id="6100e-264">Available toppings</span></span>|  
    ||<span data-ttu-id="6100e-265">Éléments</span><span class="sxs-lookup"><span data-stu-id="6100e-265">Items</span></span>|<span data-ttu-id="6100e-266">Pepperoni, Saucisson, Champignons</span><span class="sxs-lookup"><span data-stu-id="6100e-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="6100e-267">Button</span><span class="sxs-lookup"><span data-stu-id="6100e-267">Button</span></span>|<span data-ttu-id="6100e-268">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-268">Name</span></span>|<span data-ttu-id="6100e-269">order</span><span class="sxs-lookup"><span data-stu-id="6100e-269">order</span></span>|  
    ||<span data-ttu-id="6100e-270">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-270">Text</span></span>|<span data-ttu-id="6100e-271">&Commande</span><span class="sxs-lookup"><span data-stu-id="6100e-271">&Order</span></span>|  
    ||<span data-ttu-id="6100e-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-272">TabIndex</span></span>|<span data-ttu-id="6100e-273">7</span><span class="sxs-lookup"><span data-stu-id="6100e-273">7</span></span>|  
    ||<span data-ttu-id="6100e-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-274">AccessibleDescription</span></span>|<span data-ttu-id="6100e-275">Total de la commande</span><span class="sxs-lookup"><span data-stu-id="6100e-275">Total the order</span></span>|  
    ||<span data-ttu-id="6100e-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-276">AccessibleName</span></span>|<span data-ttu-id="6100e-277">Total de la commande</span><span class="sxs-lookup"><span data-stu-id="6100e-277">Total order</span></span>|  
    |<span data-ttu-id="6100e-278">Bouton</span><span class="sxs-lookup"><span data-stu-id="6100e-278">Button</span></span>|<span data-ttu-id="6100e-279">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-279">Name</span></span>|<span data-ttu-id="6100e-280">cancel</span><span class="sxs-lookup"><span data-stu-id="6100e-280">cancel</span></span>|  
    ||<span data-ttu-id="6100e-281">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-281">Text</span></span>|<span data-ttu-id="6100e-282">Annu&ler</span><span class="sxs-lookup"><span data-stu-id="6100e-282">&Cancel</span></span>|  
    ||<span data-ttu-id="6100e-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="6100e-283">TabIndex</span></span>|<span data-ttu-id="6100e-284">8</span><span class="sxs-lookup"><span data-stu-id="6100e-284">8</span></span>|  
    ||<span data-ttu-id="6100e-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="6100e-285">AccessibleDescription</span></span>|<span data-ttu-id="6100e-286">Annuler la commande</span><span class="sxs-lookup"><span data-stu-id="6100e-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="6100e-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="6100e-287">AccessibleName</span></span>|<span data-ttu-id="6100e-288">Annuler la commande</span><span class="sxs-lookup"><span data-stu-id="6100e-288">Cancel order</span></span>|  
    |<span data-ttu-id="6100e-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="6100e-289">MainMenu</span></span>|<span data-ttu-id="6100e-290">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-290">Name</span></span>|<span data-ttu-id="6100e-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="6100e-291">theMainMenu</span></span>|  
    |<span data-ttu-id="6100e-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6100e-292">MenuItem</span></span>|<span data-ttu-id="6100e-293">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-293">Name</span></span>|<span data-ttu-id="6100e-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="6100e-294">fileCommands</span></span>|  
    ||<span data-ttu-id="6100e-295">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-295">Text</span></span>|<span data-ttu-id="6100e-296">&Fichier</span><span class="sxs-lookup"><span data-stu-id="6100e-296">&File</span></span>|  
    |<span data-ttu-id="6100e-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6100e-297">MenuItem</span></span>|<span data-ttu-id="6100e-298">Nom</span><span class="sxs-lookup"><span data-stu-id="6100e-298">Name</span></span>|<span data-ttu-id="6100e-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="6100e-299">exitApp</span></span>|  
    ||<span data-ttu-id="6100e-300">Texte</span><span class="sxs-lookup"><span data-stu-id="6100e-300">Text</span></span>|<span data-ttu-id="6100e-301">&Quitter</span><span class="sxs-lookup"><span data-stu-id="6100e-301">E&xit</span></span>|
    
      Your form will look something like the following image:
    
      ![The pizza order form with a name textbox, and size and toppings selection.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="6100e-302">Prise en charge du mode de contraste élevé</span><span class="sxs-lookup"><span data-stu-id="6100e-302">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="6100e-303">Le mode de contraste élevé est un paramètre système Windows qui améliore la lisibilité en utilisant des couleurs contrastées et des tailles de polices adaptées aux personnes malvoyantes.</span><span class="sxs-lookup"><span data-stu-id="6100e-303">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="6100e-304">Le <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> propriété est fournie pour déterminer si le mode de contraste élevé est activé.</span><span class="sxs-lookup"><span data-stu-id="6100e-304">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="6100e-305">Si SystemInformation.HighContrast a la valeur `true`, l'application doit :</span><span class="sxs-lookup"><span data-stu-id="6100e-305">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
- <span data-ttu-id="6100e-306">afficher tous les éléments d'interface utilisateur à l'aide du modèle de couleurs système ;</span><span class="sxs-lookup"><span data-stu-id="6100e-306">Display all user interface elements using the system color scheme</span></span>  
  
- <span data-ttu-id="6100e-307">transmettre via des signaux visuels ou sonores toute information qui est transmise via une couleur.</span><span class="sxs-lookup"><span data-stu-id="6100e-307">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="6100e-308">Par exemple, si certains éléments de liste sont mis en surbrillance à l'aide d'une police rouge, vous pourriez également ajouter la mise en gras pour que l'utilisateur ait un autre indicateur que la couleur ;</span><span class="sxs-lookup"><span data-stu-id="6100e-308">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
- <span data-ttu-id="6100e-309">omettre toutes les images ou tous les motifs derrière le texte.</span><span class="sxs-lookup"><span data-stu-id="6100e-309">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="6100e-310">L'application doit vérifier le paramètre de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> quand elle démarre et répond à l'événement système <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="6100e-310">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="6100e-311">L'événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> est déclenché chaque fois que la valeur de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> change.</span><span class="sxs-lookup"><span data-stu-id="6100e-311">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="6100e-312">Dans notre application, le seul élément qui n’utilise pas les paramètres système pour la couleur est `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="6100e-312">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="6100e-313">Le <xref:System.Drawing.SystemColors> classe est utilisée pour modifier les paramètres de couleur de l’étiquette pour les couleurs système sélectionnées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6100e-313">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="6100e-314">Pour activer le mode de contraste élevé de manière efficace</span><span class="sxs-lookup"><span data-stu-id="6100e-314">To enable High Contrast mode in an effective way</span></span>  
  
1. <span data-ttu-id="6100e-315">Créez une méthode pour affecter les couleurs système comme couleurs de l'étiquette.</span><span class="sxs-lookup"><span data-stu-id="6100e-315">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2. <span data-ttu-id="6100e-316">Appelez la procédure `SetColorScheme` dans le constructeur de formulaire (`Public Sub New()` en Visual Basic et `public class Form1` en Visual C#).</span><span class="sxs-lookup"><span data-stu-id="6100e-316">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="6100e-317">Pour accéder au constructeur en Visual Basic, vous devez développer la région nommée **Code généré par le Concepteur Windows Form**.</span><span class="sxs-lookup"><span data-stu-id="6100e-317">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3. <span data-ttu-id="6100e-318">Créez une procédure événementielle, avec la signature appropriée, pour répondre à l'événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="6100e-318">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4. <span data-ttu-id="6100e-319">Ajoutez du code au constructeur de formulaire, après l’appel à `InitializeComponents`, pour raccorder la procédure événementielle à l’événement système.</span><span class="sxs-lookup"><span data-stu-id="6100e-319">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="6100e-320">Cette méthode appelle la procédure `SetColorScheme`.</span><span class="sxs-lookup"><span data-stu-id="6100e-320">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5. <span data-ttu-id="6100e-321">Ajoutez du code à la méthode <xref:System.Windows.Forms.Control.Dispose%2A> du formulaire, avant l’appel à la méthode <xref:System.Windows.Forms.Control.Dispose%2A> de la classe de base, pour libérer l’événement quand l’application se ferme.</span><span class="sxs-lookup"><span data-stu-id="6100e-321">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="6100e-322">Pour accéder à la méthode <xref:System.Windows.Forms.Control.Dispose%2A> en Visual Basic, vous devez développer la région étiquetée Code généré par le Concepteur Windows Form.</span><span class="sxs-lookup"><span data-stu-id="6100e-322">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6100e-323">Le code d'événement système exécute un thread distinct de l'application principale.</span><span class="sxs-lookup"><span data-stu-id="6100e-323">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="6100e-324">Si vous ne libérez pas l'événement, le code que vous raccordez à l'événement s'exécute même après la fermeture du programme.</span><span class="sxs-lookup"><span data-stu-id="6100e-324">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6. <span data-ttu-id="6100e-325">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="6100e-325">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="6100e-326">Communication d'informations importantes par un moyen autre que le son</span><span class="sxs-lookup"><span data-stu-id="6100e-326">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="6100e-327">Dans cette application, aucune information n'est communiquée que par du son.</span><span class="sxs-lookup"><span data-stu-id="6100e-327">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="6100e-328">Si vous utilisez du son dans votre application, vous devez aussi fournir des informations par d'autres moyens.</span><span class="sxs-lookup"><span data-stu-id="6100e-328">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="6100e-329">Pour fournir des informations par d'autres moyens que le son</span><span class="sxs-lookup"><span data-stu-id="6100e-329">To supply information by some other means than sound</span></span>  
  
1. <span data-ttu-id="6100e-330">Faites clignoter la barre de titre à l'aide de la fonction d'API Windows FlashWindow.</span><span class="sxs-lookup"><span data-stu-id="6100e-330">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="6100e-331">Pour obtenir un exemple montrant comment appeler des fonctions API de Windows, consultez [procédure pas à pas : Appel d’API de Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="6100e-331">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6100e-332">L'utilisateur a peut-être activé le service SoundSentry Windows, qui provoque aussi le clignotement de la fenêtre quand des sons système sont lus par le haut-parleur intégré de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6100e-332">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2. <span data-ttu-id="6100e-333">Affichez les informations importantes dans une fenêtre non modale, pour que l'utilisateur puisse y répondre.</span><span class="sxs-lookup"><span data-stu-id="6100e-333">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3. <span data-ttu-id="6100e-334">Affichez une boîte de message qui acquiert le focus clavier.</span><span class="sxs-lookup"><span data-stu-id="6100e-334">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="6100e-335">Évitez cette méthode quand l'utilisateur est susceptible de taper du texte au clavier.</span><span class="sxs-lookup"><span data-stu-id="6100e-335">Avoid this method when the user may be typing.</span></span>  
  
4. <span data-ttu-id="6100e-336">Affichez un indicateur d’état dans la zone de notification d’état de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="6100e-336">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="6100e-337">Pour plus d’informations, consultez [Ajout d’icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="6100e-337">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="6100e-338">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="6100e-338">Testing the Application</span></span>  
 <span data-ttu-id="6100e-339">Avant de déployer l'application, vous devez tester les fonctionnalités d'accessibilité que vous avez implémentées.</span><span class="sxs-lookup"><span data-stu-id="6100e-339">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="6100e-340">Pour tester les fonctionnalités d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="6100e-340">To test accessibility features</span></span>  
  
1. <span data-ttu-id="6100e-341">Pour tester l'accès au clavier, débranchez la souris et parcourez l'interface utilisateur pour chaque fonctionnalité en utilisant uniquement le clavier.</span><span class="sxs-lookup"><span data-stu-id="6100e-341">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="6100e-342">Assurez-vous que toutes les tâches peuvent être effectuées en utilisant seulement le clavier.</span><span class="sxs-lookup"><span data-stu-id="6100e-342">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2. <span data-ttu-id="6100e-343">Pour tester la prise en charge du contraste élevé, choisissez l'icône Options d'accessibilité dans le Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="6100e-343">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="6100e-344">Cliquez sur l'onglet Affichage et cochez la case Utiliser le contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="6100e-344">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="6100e-345">Parcourez tous les éléments d'interface utilisateur pour vous assurer que les modifications de couleur et de police sont répercutées.</span><span class="sxs-lookup"><span data-stu-id="6100e-345">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="6100e-346">Assurez-vous également que les images et les motifs placés derrière le texte sont omis.</span><span class="sxs-lookup"><span data-stu-id="6100e-346">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6100e-347">Le Panneau de configuration de Windows NT 4 ne contient pas d'icône Options d'accessibilité.</span><span class="sxs-lookup"><span data-stu-id="6100e-347">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="6100e-348">Ainsi, cette procédure de modification du paramètre SystemInformation.HighContrast ne fonctionne pas dans Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="6100e-348">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3. <span data-ttu-id="6100e-349">D'autres outils sont disponibles pour tester l'accessibilité d'une application.</span><span class="sxs-lookup"><span data-stu-id="6100e-349">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4. <span data-ttu-id="6100e-350">Pour tester l'exposition du focus clavier, exécutez la Loupe.</span><span class="sxs-lookup"><span data-stu-id="6100e-350">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="6100e-351">(Pour l’ouvrir, cliquez sur le menu **Démarrer**, pointez sur **Programmes**, sur **Accessoires**, sur **Accessibilité**, puis cliquez sur **Loupe**.)</span><span class="sxs-lookup"><span data-stu-id="6100e-351">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="6100e-352">Parcourez l'interface utilisateur à l'aide de la tabulation de clavier et de la souris.</span><span class="sxs-lookup"><span data-stu-id="6100e-352">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="6100e-353">Vérifiez que tous les déplacements sont correctement suivis dans la **Loupe**.</span><span class="sxs-lookup"><span data-stu-id="6100e-353">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5. <span data-ttu-id="6100e-354">Pour tester l'exposition des éléments à l'écran, exécutez Inspect et utilisez la souris et la touche de tabulation pour atteindre chaque élément.</span><span class="sxs-lookup"><span data-stu-id="6100e-354">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="6100e-355">Assurez-vous que les informations présentées dans les champs Name, State, Role, Location et Value de la fenêtre Inspect sont significatives pour l'utilisateur pour chaque objet de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6100e-355">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
