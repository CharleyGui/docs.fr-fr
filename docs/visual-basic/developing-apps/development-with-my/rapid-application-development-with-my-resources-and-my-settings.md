---
title: Développement rapide d’application avec My.Resources et My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: fd1ec25582e919b84235502f5921edfbc6e1dade
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990201"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Développement rapide d'application avec My.Resources et My.Settings (Visual Basic)

L' `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de récupérer de manière dynamique des ressources pour votre application.  
  
## <a name="retrieving-resources"></a>Récupération de ressources  

 Un certain nombre de ressources, telles que des fichiers audio, des icônes, des images et des chaînes, peuvent être récupérées par le biais de l' `My.Resources` objet. Par exemple, vous pouvez accéder aux fichiers de ressources propres à la culture de l’application. L’exemple suivant définit l’icône du formulaire sur l’icône nommée `Form1Icon` stockée dans le fichier de ressources de l’application.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 L' `My.Resources` objet expose uniquement les ressources globales. Il ne fournit pas d’accès aux fichiers de ressources associés aux formulaires. Accédez aux ressources du formulaire à partir du formulaire.  
  
 De même, l' `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et de récupérer dynamiquement des paramètres de propriété et d’autres informations pour votre application. Pour plus d’informations, consultez [My. Resources](../../language-reference/objects/my-resources-object.md) et [My. Settings (objet](../../language-reference/objects/my-settings-object.md)).  
  
## <a name="see-also"></a>Voir aussi

- [My.Resources, objet](../../language-reference/objects/my-resources-object.md)
- [My.Settings, objet](../../language-reference/objects/my-settings-object.md)
- [Accessing Application Settings](../programming/app-settings/index.md)
