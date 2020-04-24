---
title: 'Procédure : créer des grilles de propriétés pour les paramètres utilisateur'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329613"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="93b7b-102">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93b7b-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="93b7b-103">Vous pouvez créer une grille de propriétés pour les paramètres utilisateur en remplissant un contrôle <xref:System.Windows.Forms.PropertyGrid> avec les propriétés des paramètres utilisateur de l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="93b7b-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93b7b-104">Pour que cet exemple fonctionne, les paramètres utilisateur de votre application doivent être configurés.</span><span class="sxs-lookup"><span data-stu-id="93b7b-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="93b7b-105">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="93b7b-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="93b7b-106">L’objet `My.Settings` expose chaque paramètre en tant que propriété.</span><span class="sxs-lookup"><span data-stu-id="93b7b-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="93b7b-107">Le nom de la propriété est le même que le nom du paramètre, et le type de la propriété est le même que le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="93b7b-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="93b7b-108">La **portée** du paramètre détermine si la propriété est en lecture seule. La propriété d’un paramètre de portée **Application** est en lecture seule, tandis que la propriété d’un paramètre de portée **Utilisateur** est en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="93b7b-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="93b7b-109">Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="93b7b-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93b7b-110">Vous ne pouvez pas changer ou enregistrer les valeurs des paramètres de portée application au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="93b7b-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="93b7b-111">Les paramètres de portée application peuvent être changés uniquement lors de la création de l’application (par l’intermédiaire du **Concepteur de projet**) ou en modifiant le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="93b7b-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="93b7b-112">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="93b7b-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="93b7b-113">Cet exemple utilise un contrôle <xref:System.Windows.Forms.PropertyGrid> pour accéder aux propriétés des paramètres utilisateur de l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="93b7b-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="93b7b-114">Par défaut, <xref:System.Windows.Forms.PropertyGrid> affiche toutes les propriétés de l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="93b7b-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="93b7b-115">Toutefois, les propriétés des paramètres utilisateur ont l’attribut <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="93b7b-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="93b7b-116">Cet exemple affecte la valeur <xref:System.Configuration.UserScopedSettingAttribute> à la propriété <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> de <xref:System.Windows.Forms.PropertyGrid> pour afficher uniquement les propriétés des paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93b7b-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="93b7b-117">Pour ajouter une grille de propriétés de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="93b7b-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="93b7b-118">Faites glisser le contrôle **PropertyGrid** de la **boîte à outils** vers l’aire de conception de votre application, que l’on suppose être ici `Form1`.</span><span class="sxs-lookup"><span data-stu-id="93b7b-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="93b7b-119">Le nom par défaut du contrôle de grille de propriétés est `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="93b7b-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="93b7b-120">Double-cliquez sur l’aire de conception de `Form1` pour ouvrir le code du gestionnaire d’événements de chargement de formulaire.</span><span class="sxs-lookup"><span data-stu-id="93b7b-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="93b7b-121">Définissez l’objet `My.Settings` comme objet sélectionné pour la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="93b7b-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="93b7b-122">Configurez la grille de propriétés pour afficher uniquement les paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93b7b-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="93b7b-123">Pour afficher uniquement les paramètres de portée application, utilisez l’attribut <xref:System.Configuration.ApplicationScopedSettingAttribute> au lieu de <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="93b7b-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="93b7b-124">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="93b7b-124">Robust Programming</span></span>  

 <span data-ttu-id="93b7b-125">L’application enregistre les paramètres utilisateur quand elle s’arrête.</span><span class="sxs-lookup"><span data-stu-id="93b7b-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="93b7b-126">Pour enregistrer les paramètres immédiatement, appelez la méthode `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="93b7b-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="93b7b-127">Pour plus d’informations, consultez [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="93b7b-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b7b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93b7b-128">See also</span></span>

- [<span data-ttu-id="93b7b-129">My.Settings, objet</span><span class="sxs-lookup"><span data-stu-id="93b7b-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="93b7b-130">Guide pratique pour lire des paramètres d’application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93b7b-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="93b7b-131">Guide pratique pour modifier les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93b7b-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="93b7b-132">Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93b7b-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="93b7b-133">Gestion des paramètres d'une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="93b7b-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
