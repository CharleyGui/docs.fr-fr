---
title: 'Procédure : écrire dans le journal des événements de l’application'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 298d6d85f8b21176b72db8e676617577eb03fada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410034"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Comment : écrire dans le journal des événements de l'application (Visual Basic)

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour écrire des informations sur les événements qui se produisent dans votre application. Cet exemple montre comment configurer un écouteur de journalisation des événements pour que `My.Application.Log` écrive les informations de suivi dans le journal des événements de l’application.

Vous ne pouvez pas écrire dans le journal de sécurité. Pour pouvoir écrire dans le journal système, vous devez être membre du compte LocalSystem ou Administrateur.

Pour afficher un journal des événements, vous pouvez utiliser l’ **Explorateur de serveurs** ou l’ **Observateur d’événements Windows**. Pour plus d’informations, consultez [Événements ETW dans le .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Pour ajouter et configurer l’écouteur de journalisation des événements

1. Cliquez avec le bouton droit sur app.config dans l’ **Explorateur de solutions** et choisissez **Ouvrir**.

    \- ou -

    S’il n’existe pas de fichier app.config :

    1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

    2. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.

    3. Cliquez sur **Add**.

2. Recherchez la section `<listeners>` dans le fichier de configuration de l’application.

    Vous pouvez trouver la section `<listeners>` dans la section `<source>` avec l’attribut de nom « DefaultSource », qui est imbriquée dans la section `<system.diagnostics>` , elle-même imbriquée sous la section `<configuration>` de plus haut niveau.

3. Ajoutez cet élément à cette section `<listeners>` :

    ```xml
    <add name="EventLog"/>
    ```

4. Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.

5. Ajoutez cet élément à cette section `<sharedListeners>` :

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Remplacez `APPLICATION_NAME` par le nom de votre application.

    > [!NOTE]
    > En règle générale, une application écrit les erreurs seulement dans le journal des événements. Pour plus d’informations sur le filtrage de la sortie du journal, consultez [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Pour écrire des informations sur les événements dans le journal des événements

Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal des événements. Pour plus d’informations, consultez [Guide pratique pour écrire des messages de journal](how-to-write-log-messages.md) et [Guide pratique pour enregistrer des exceptions](how-to-log-exceptions.md).

Une fois l’écouteur de journalisation des événements configuré pour un assembly, il reçoit tous les messages écrits par `My.Application.Log` depuis cet assembly.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Utilisation des journaux des applications](working-with-application-logs.md)
- [Procédure : journaliser des exceptions](how-to-log-exceptions.md)
- [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md)
