---
title: "Comment : lire des paramètres au moment de l'exécution avec C#"
description: Apprenez à lire à la fois les paramètres de portée application et de portée utilisateur au moment de l’exécution avec C# via l’objet Properties.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903349"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Comment : lire des paramètres au moment de l’exécution avec C\#

Vous pouvez lire les paramètres de portée application et de portée utilisateur au moment de l'exécution via l'objet Propriétés. L’objet Properties expose tous les paramètres par défaut du projet via le membre Properties. Settings. default dans l’espace de noms par défaut du projet dans lequel ils sont définis.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Pour lire les paramètres au moment de l’exécution avec C\#
  
Accédez au paramètre approprié via le membre Properties.Settings.Default. L'exemple suivant montre comment affecter un paramètre nommé `myColor` à une propriété BackColor. Au préalable, vous devez avoir créé un fichier de paramètres contenant un paramètre nommé `myColor` de type `System.Drawing.Color`. Pour plus d’informations sur la création d’un fichier de paramètres, consultez [Comment : créer un nouveau paramètre au moment du design](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de paramètres d'application et de paramètres utilisateur](using-application-settings-and-user-settings.md)
- [Guide pratique pour écrire des paramètres utilisateur au moment de l'exécution avec C#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Vue d’ensemble des paramètres d’application](application-settings-overview.md)
