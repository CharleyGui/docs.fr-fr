---
title: 'Procédure : modifier les paramètres utilisateur'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: c9b89459f9b443c3a447edce90fee3437bbf1b6a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410177"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Guide pratique pour modifier les paramètres utilisateur en Visual Basic

Vous pouvez modifier un paramètre utilisateur en assignant une nouvelle valeur à la propriété du paramètre de l’objet `My.Settings`.  
  
 L’objet `My.Settings` expose chaque paramètre en tant que propriété. Le nom de la propriété est le même que le nom du paramètre, et le type de la propriété est le même que le type du paramètre. La **portée** du paramètre détermine si la propriété est en lecture seule : la propriété d’un paramètre de portée **application**est en lecture seule, tandis que la propriété d’un paramètre de portée **utilisateur**est en lecture-écriture. Pour plus d’informations, consultez [My.Settings, objet](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Bien que vous puissiez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l’exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programmation. Vous pouvez changer les paramètres de portée application lors de la création de l’application, à l’aide du **Concepteur de projet**, ou en modifiant le fichier de configuration de l’application. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Exemple  

 Dans cet exemple, la valeur du paramètre utilisateur `Nickname` est modifiée.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `Nickname`, de type `String`.  
  
 L’application enregistre les paramètres utilisateur quand elle s’arrête. Pour enregistrer les paramètres immédiatement, appelez la méthode `My.Settings.Save`. Pour plus d’informations, consultez [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Voir aussi

- [My.Settings, objet](../../../language-reference/objects/my-settings-object.md)
- [Guide pratique pour lire des paramètres d’application en Visual Basic](how-to-read-application-settings.md)
- [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](how-to-persist-user-settings.md)
- [Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Gestion des paramètres d'une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
