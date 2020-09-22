---
title: My.Settings, objet
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: f3348e9eea5bdd7f4fd911150877c9aefdd66bcc
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867295"
---
# <a name="mysettings-object"></a>My.Settings, objet

Fournit des propriétés et des méthodes pour accéder aux paramètres de l’application.  
  
## <a name="remarks"></a>Notes  

 L' `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et de récupérer dynamiquement des paramètres de propriété et d’autres informations pour votre application. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Propriétés  

 Les propriétés de l’objet `My.Settings` fournissent l’accès aux paramètres de votre application. Pour ajouter ou supprimer des paramètres, utilisez le **Concepteur de paramètres**.  
  
 Chaque paramètre a un **nom**, un **type**, une **étendue**et une **valeur**, et ces paramètres déterminent la façon dont la propriété pour accéder à chaque paramètre apparaît dans l' `My.Settings` objet :  
  
- **Nom** détermine le nom de la propriété.  
  
- **Type** détermine le type de la propriété.  
  
- L' **étendue** indique si la propriété est en lecture seule. Si la valeur est **application**, la propriété est en lecture seule ; Si la valeur est **User**, la propriété est en lecture-écriture.  
  
- La **valeur** est la valeur par défaut de la propriété.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|---|---|  
|`Reload`|Recharge les paramètres utilisateur à partir des dernières valeurs enregistrées.|  
|`Save`|Enregistre les paramètres utilisateur actuels.|  
  
 L' `My.Settings` objet fournit également des propriétés et des méthodes avancées, héritées de la <xref:System.Configuration.ApplicationSettingsBase> classe.  
  
## <a name="tasks"></a>Tâches  

 Le tableau suivant répertorie des exemples de tâches impliquant l' `My.Settings` objet.  
  
|À|Consultez|  
|---|---|  
|Lire un paramètre d’application|[Guide pratique pour lire des paramètres d’application en Visual Basic](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Modifier un paramètre utilisateur|[Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Conserver les paramètres utilisateur|[Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Créer une grille des propriétés pour les paramètres utilisateur|[Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Exemple  

 Cet exemple affiche la valeur du paramètre `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.ApplicationSettingsBase>
- [Guide pratique pour lire des paramètres d’application en Visual Basic](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gestion des paramètres d'une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
