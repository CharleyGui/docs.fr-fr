---
title: 'Comment : écrire des informations sur des événements dans un fichier texte'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352073"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Guide pratique pour écrire des informations sur des événements dans un fichier texte (Visual Basic)

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application. Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer des informations de traçage dans un fichier journal.

### <a name="to-add-and-configure-the-file-log-listener"></a>Pour ajouter et configurer l’écouteur de journalisation du fichier

1. Cliquez avec le bouton droit sur app.config dans l’ **Explorateur de solutions** et choisissez **Ouvrir**.

     \- ou -

     S’il n’existe pas de fichier app.config :

    1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

    2. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.

    3. Cliquez sur **Ajouter**.

2. Recherchez la section `<listeners>` dans le fichier de configuration de l’application.

     Vous pouvez trouver la section \<listeners> dans la section \<source> avec l’attribut de nom « DefaultSource », qui est imbriquée dans la section \<system.diagnostics>, elle-même imbriquée sous la section \<configuration> de plus haut niveau.

3. Ajoutez cet élément à cette section `<listeners>` :

    ```xml
    <add name="FileLogListener" />
    ```

4. Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>`, imbriquée dans la section `<configuration>` de plus haut niveau.

5. Ajoutez cet élément à cette section `<sharedListeners>` :

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     Remplacez la valeur de l’attribut `customlocation` par le répertoire du journal.

    > [!NOTE]
    > Pour définir la valeur d’une propriété d’écouteur, utilisez un attribut qui a le même nom que la propriété, en utilisant des minuscules. Par exemple, les attributs `location` et `customlocation` définissent les valeurs des propriétés <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> et <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.

### <a name="to-write-event-information-to-the-file-log"></a>Pour écrire des informations sur les événements dans le journal du fichier

Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal du fichier. Pour plus d’informations, consultez [Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) et [Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Une fois l’écouteur de journalisation du fichier configuré pour un assembly, il reçoit tous les messages écrits par `My.Application.Log` à partir de cet assembly.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Comment : enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
