---
title: Enregistrement d’informations provenant de l’application
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410021"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Enregistrement d'informations provenant de l'application (Visual Basic)

Cette section contient des rubriques sur l’enregistrement d’informations provenant de l’application à l’aide de l’objet `My.Application.Log` ou `My.Log`, et sur l’extension des fonctionnalités de journalisation de l’application.  
  
 L’objet `Log` fournit des méthodes pour écrire des informations dans les écouteurs de journalisation de l’application, et la propriété `TraceSource` avancée de l’objet `Log` fournit des informations de configuration détaillées. L’objet `Log` est configuré par le fichier de configuration de l’application.  
  
 L’objet `My.Log` est disponible uniquement pour les applications ASP.NET. Pour les applications clientes, utilisez `My.Application.Log`. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Tâches  
  
|À|Consultez|  
|--------|---------|  
|Écrire des informations sur les événements dans les journaux de l’application.|[Procédure : écrire des messages de journal](how-to-write-log-messages.md)|  
|Écrire des informations sur les exceptions dans les journaux de l’application.|[Procédure : journaliser des exceptions](how-to-log-exceptions.md)|  
|Écrire des informations de traçage dans les journaux de l’application quand l’application démarre et s’arrête.|[Procédure : enregistrer des messages quand l’application démarre ou s’arrête](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Configurer `My.Application.Log` pour écrire des informations dans un fichier texte.|[Procédure : écrire des informations sur les événements dans un fichier texte](how-to-write-event-information-to-a-text-file.md)|  
|Configurer `My.Application.Log` pour écrire des informations dans un journal des événements.|[Procédure : écrire dans le journal des événements de l’application](how-to-write-to-an-application-event-log.md)|  
|Changer l’emplacement où `My.Application.Log` écrit les informations.|[Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](walkthrough-changing-where-my-application-log-writes-information.md)|  
|Déterminer l’emplacement où `My.Application.Log` écrit les informations.|[Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md)|  
|Créer un écouteur de journalisation personnalisé pour `My.Application.Log`.|[Procédure pas à pas : création d’écouteurs de journalisation personnalisés](walkthrough-creating-custom-log-listeners.md)|  
|Filtrer la sortie des journaux `My.Application.Log`.|[Procédure pas à pas : filtrage de la sortie de My.Application.Log](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Utilisation des journaux des applications](working-with-application-logs.md)
- [Résolution des problèmes : Écouteurs de journalisation](troubleshooting-log-listeners.md)
