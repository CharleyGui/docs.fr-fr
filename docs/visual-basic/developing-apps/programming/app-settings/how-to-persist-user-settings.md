---
title: 'Procédure : rendre persistants les paramètres utilisateur'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 817111060259bdfbbb26d9f8eafeae439e1f651f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410151"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic

Vous pouvez utiliser la méthode `My.Settings.Save` pour rendre persistantes les modifications apportées aux paramètres utilisateur.  
  
 En règle générale, les applications sont conçues pour rendre persistantes les modifications apportées aux paramètres utilisateur quand l’application s’arrête. Cela est dû au fait que l’enregistrement des paramètres peut prendre, en fonction de plusieurs facteurs, plusieurs secondes.  
  
 Pour plus d’informations, consultez [My.Settings, objet](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Bien que vous puissiez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l’exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programmation. Vous pouvez changer les paramètres de portée application lors de la création de l’application, par l’intermédiaire du **Concepteur de projet**, ou en modifiant le fichier de configuration de l’application. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Exemple  

 Cet exemple change la valeur du paramètre utilisateur `LastChanged` et enregistre cette modification en appelant la méthode `My.Settings.Save`.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `LastChanged`, de type `Date`. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Voir aussi

- [My.Settings, objet](../../../language-reference/objects/my-settings-object.md)
- [Guide pratique pour lire des paramètres d’application en Visual Basic](how-to-read-application-settings.md)
- [Guide pratique pour modifier les paramètres utilisateur en Visual Basic](how-to-change-user-settings.md)
- [Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Gestion des paramètres d'une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
