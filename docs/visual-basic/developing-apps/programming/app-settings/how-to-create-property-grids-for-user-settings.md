---
title: 'Guide pratique : créer des grilles de propriétés pour les paramètres utilisateur'
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
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic

Vous pouvez créer une grille de propriétés pour les paramètres utilisateur en remplissant un contrôle <xref:System.Windows.Forms.PropertyGrid> avec les propriétés des paramètres utilisateur de l’objet `My.Settings`.  
  
> [!NOTE]
> Pour que cet exemple fonctionne, les paramètres utilisateur de votre application doivent être configurés. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 L’objet `My.Settings` expose chaque paramètre en tant que propriété. Le nom de la propriété est le même que le nom du paramètre, et le type de la propriété est le même que le type du paramètre. La **portée** du paramètre détermine si la propriété est en lecture seule. La propriété d’un paramètre de portée **Application** est en lecture seule, tandis que la propriété d’un paramètre de portée **Utilisateur** est en lecture-écriture. Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Vous ne pouvez pas changer ou enregistrer les valeurs des paramètres de portée application au moment de l’exécution. Les paramètres de portée application peuvent être changés uniquement lors de la création de l’application (par l’intermédiaire du **Concepteur de projet**) ou en modifiant le fichier de configuration de l’application. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Cet exemple utilise un contrôle <xref:System.Windows.Forms.PropertyGrid> pour accéder aux propriétés des paramètres utilisateur de l’objet `My.Settings`. Par défaut, <xref:System.Windows.Forms.PropertyGrid> affiche toutes les propriétés de l’objet `My.Settings`. Toutefois, les propriétés des paramètres utilisateur ont l’attribut <xref:System.Configuration.UserScopedSettingAttribute>. Cet exemple affecte la valeur <xref:System.Configuration.UserScopedSettingAttribute> à la propriété <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> de <xref:System.Windows.Forms.PropertyGrid> pour afficher uniquement les propriétés des paramètres utilisateur.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Pour ajouter une grille de propriétés de paramètres utilisateur  
  
1. Faites glisser le contrôle **PropertyGrid** de la **boîte à outils** vers l’aire de conception de votre application, que l’on suppose être ici `Form1`.  
  
     Le nom par défaut du contrôle de grille de propriétés est `PropertyGrid1`.  
  
2. Double-cliquez sur l’aire de conception de `Form1` pour ouvrir le code du gestionnaire d’événements de chargement de formulaire.  
  
3. Définissez l’objet `My.Settings` comme objet sélectionné pour la grille des propriétés.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Configurez la grille de propriétés pour afficher uniquement les paramètres utilisateur.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Pour afficher uniquement les paramètres de portée application, utilisez l’attribut <xref:System.Configuration.ApplicationScopedSettingAttribute> au lieu de <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Programmation fiable  

 L’application enregistre les paramètres utilisateur quand elle s’arrête. Pour enregistrer les paramètres immédiatement, appelez la méthode `My.Settings.Save`. Pour plus d’informations, consultez [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Voir aussi

- [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Guide pratique pour lire des paramètres d’application en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Gestion des paramètres d'une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
