---
title: détermination de l’emplacement des informations My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 00b543dbe96ca99446f6797a13b66ee62c422b93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398277"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log (Visual Basic)

L’objet `My.Application.Log` peut écrire des informations dans plusieurs écouteurs de journalisation. Les écouteurs de journalisation sont configurés par le fichier de configuration de l’ordinateur et peuvent être remplacés par un fichier de configuration d’une application. Cette rubrique décrit les paramètres par défaut et explique comment déterminer les paramètres de votre application.

Pour plus d’informations sur les emplacements de sortie par défaut, consultez [Utilisation des journaux des applications](working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Pour déterminer les écouteurs de My.Application.Log

1. Recherchez le fichier de configuration de l’assembly. Si vous développez l’assembly, vous pouvez accéder au fichier app.config dans Visual Studio à partir de l’**Explorateur de solutions**. Sinon, le nom du fichier de configuration est le nom de l’assembly suivi de « .config ». Il se trouve dans le même répertoire que l’assembly.

    > [!NOTE]
    > Tous les assemblys n’ont pas un fichier de configuration.

    Le fichier de configuration est un fichier XML.

2. Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », qui se trouve dans la section `<sources>` . La section `<sources>` se trouve dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.

    Si ces sections n’existent pas, le fichier de configuration de l’ordinateur peut configurer les écouteurs de journalisation de `My.Application.Log` . Les étapes suivantes décrivent comment déterminer ce que définit le fichier de configuration de l’ordinateur :

    1. Recherchez le fichier machine.config de l’ordinateur. En général, il se trouve dans le répertoire *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG*, où `SystemRoot` est le répertoire du système d’exploitation et `frameworkVersion` est la version du .NET Framework.

        Les paramètres de machine.config peuvent être remplacés par le fichier de configuration d’une application.

        Si les éléments facultatifs répertoriés ci-dessous n’existent pas, vous pouvez les créer.

    2. Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », dans la section `<sources>` , dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.

        Si ces sections n’existent pas, `My.Application.Log` a seulement les écouteurs de journalisation par défaut.

3. Recherchez les éléments <`add>` dans la section <`listeners>`.

     Ces éléments ajoutent les écouteurs de journalisation nommés à la source de `My.Application.Log` .

4. Recherchez les éléments `<add>` avec les noms des écouteurs de journalisation dans la `<sharedListeners>` section, dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.

5. Pour de nombreux types d’écouteurs partagés, les données d’initialisation de l’écouteur comprennent une description de l’endroit où l’écouteur dirige les données :

    - Un écouteur <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> écrit dans un fichier journal, comme décrit dans l’introduction.

    - Un écouteur <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> écrit les informations dans le journal des événements de l’ordinateur spécifié par le paramètre `initializeData` . Pour afficher un journal des événements, vous pouvez utiliser l’ **Explorateur de serveurs** ou l’ **Observateur d’événements Windows**. Pour plus d’informations, consultez [Événements ETW dans le .NET Framework](../../../../framework/performance/etw-events.md).

    - Les écouteurs <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> et <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> écrivent dans le fichier spécifié par le paramètre `initializeData` .

    - Un écouteur <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> écrit dans la console de ligne de commande.

    - Pour plus d’informations sur les emplacements où d’autres types d’écouteurs de journalisation écrivent les informations, consultez la documentation de ce type.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Utilisation des journaux des applications](working-with-application-logs.md)
- [Procédure : journaliser des exceptions](how-to-log-exceptions.md)
- [Procédure : écrire des messages de journal](how-to-write-log-messages.md)
- [Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](walkthrough-changing-where-my-application-log-writes-information.md)
- [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md)
- [Résolution des problèmes : Écouteurs de journalisation](troubleshooting-log-listeners.md)
