---
title: My.Settings (objet) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9533e8e1ccc51078fefcf6bf73feb2683ae8febb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625285"
---
# <a name="mysettings-object"></a>My.Settings, objet
Fournit des propriétés et méthodes permettant d’accéder aux paramètres de l’application.  
  
## <a name="remarks"></a>Notes  
 Le `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et récupérer des paramètres de propriété et d’autres informations pour votre application de manière dynamique. Pour plus d'informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Properties  
 Les propriétés de l’objet `My.Settings` fournissent l’accès aux paramètres de votre application. Pour ajouter ou supprimer des paramètres, utilisez le **Concepteur de paramètres**.  
  
 Chaque paramètre a un **nom**, **Type**, **étendue**, et **valeur**, et ces paramètres déterminent comment la propriété qui accède à chaque paramètre s’affiche dans le `My.Settings` objet :  
  
- **Nom** détermine le nom de la propriété.  
  
- **Type** détermine le type de la propriété.  
  
- **Étendue** indique si la propriété est en lecture seule. Si la valeur est **Application**, la propriété est en lecture seule ; si la valeur est **utilisateur**, la propriété est en lecture-écriture.  
  
- **Valeur** est la valeur par défaut de la propriété.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|---|---|  
|`Reload`|Recharge les paramètres utilisateur à partir des dernières valeurs enregistrées.|  
|`Save`|Enregistre les paramètres utilisateur actuels.|  
  
 Le `My.Settings` objet fournit également des propriétés avancées et des méthodes héritées à partir de la <xref:System.Configuration.ApplicationSettingsBase> classe.  
  
## <a name="tasks"></a>Tâches  
 Le tableau suivant répertorie des exemples de tâches impliquant la `My.Settings` objet.  
  
|À|Voir|  
|---|---|  
|Lire un paramètre d’application|[Guide pratique pour lire des paramètres d’application en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Modifier un paramètre utilisateur|[Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Conserver des paramètres utilisateur|[Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Créer une grille de propriétés pour les paramètres utilisateur|[Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche la valeur du paramètre `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.ApplicationSettingsBase>
- [Guide pratique pour lire des paramètres d’application en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
