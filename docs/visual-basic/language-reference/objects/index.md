---
title: Objets
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: e927f69b7606866a0a9e8eadd59270f51ffc5e2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414218"
---
# <a name="objects-visual-basic"></a>Objets (Visual Basic)
Cette rubrique fournit des liens vers d’autres rubriques qui documentent les objets runtime Visual Basic et contiennent des tables de leurs procédures, propriétés et événements membres.  
  
## <a name="visual-basic-run-time-objects"></a>Objets runtime Visual Basic  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Permet d’afficher facilement un groupe connexe d’éléments sous la forme d’un objet unique.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Contient des informations relatives aux erreurs d’exécution.|  
|L’objet `My.Application` est constitué des classes suivantes :<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> fournit des membres qui sont disponibles dans tous les projets.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> fournit des membres disponibles dans les applications Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> fournit des membres disponibles dans les applications console.|Fournit des données qui sont associées uniquement à l’application ou la DLL actuelle. Aucune information de niveau système ne peut être modifiée avec `My.Application`.<br /><br /> Certains membres sont disponibles uniquement pour les applications Windows Forms ou console.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Fournit des propriétés permettant d’obtenir des informations relatives à une application, telles que le numéro de version, la description, les assemblys chargés, etc.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Fournit une propriété et des méthodes pour écrire les informations des événements et des exceptions dans les écouteurs de journalisation de l’application.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Fournit des propriétés permettant de manipuler des composants informatiques tels que le son, l’horloge, le clavier, le système de fichiers, etc.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Fournit des méthodes permettant de lire des sons.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Fournit des méthodes permettant de manipuler le Presse-papiers.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Fournit des propriétés permettant d’accéder à l’heure locale actuelle et à l’heure UTC (Universal Coordinated Time), équivalent à l’heure GMT (Greenwich Mean Time), à partir de l’horloge système.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Fournit des propriétés et des méthodes destinées à être utilisées avec les lecteurs, les fichiers et les répertoires.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Fournit des propriétés utilisées pour accéder aux répertoires communément référencés.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Fournit des propriétés permettant d’obtenir des informations sur la mémoire, les assemblys chargés, le nom et le système d’exploitation de l’ordinateur.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Fournit des propriétés utilisées pour accéder à l’état actuel du clavier, par exemple pour savoir quelles touches sont actuellement utilisées, et fournit une méthode permettant d’envoyer des séquences de touches à la fenêtre active.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Fournit des propriétés permettant d’obtenir des informations sur le format et la configuration de la souris installée sur l’ordinateur local.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Fournit une propriété, un événement et des méthodes permettant d’interagir avec le réseau auquel l’ordinateur est connecté.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Fournit une propriété et une méthode permettant d’accéder aux ports série de l’ordinateur.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Fournit des propriétés et des méthodes permettant de manipuler le Registre.|  
|[My.Forms, objet](my-forms-object.md)|Fournit des propriétés permettant d’accéder à une instance de chaque Windows Form déclaré dans le projet actuel.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Fournit une propriété et des méthodes permettant d’écrire des informations sur les événements et les exceptions dans les écouteurs de journalisation de l’application pour les applications web.|  
|[My.Request, objet](my-request-object.md)|Obtient l’objet <xref:System.Web.HttpRequest> pour la page demandée. L’objet `My.Request` contient des informations sur la requête HTTP en cours.<br /><br /> L’objet `My.Request` est disponible uniquement pour les applications ASP.NET.|  
|[My.Resources, objet](my-resources-object.md)|Fournit des propriétés et des classes permettant d’accéder aux ressources d’une application.|  
|[My.Response, objet](my-response-object.md)|Obtient l'objet <xref:System.Web.HttpResponse> qui est associé à <xref:System.Web.UI.Page>. Cet objet vous permet d’envoyer des données de réponse HTTP à un client et contient des informations relatives à cette réponse.<br /><br /> L’objet `My.Response` est disponible uniquement pour les applications ASP.NET.|  
|[My.Settings, objet](my-settings-object.md)|Fournit des propriétés et des méthodes permettant d’accéder aux paramètres d’une application.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Permet d’accéder aux informations relatives à l’utilisateur actuel.|  
|[My.WebServices, objet](my-webservices-object.md)|Fournit des propriétés permettant de créer une instance unique de chaque service web qui est référencé par le projet actuel et d’y accéder.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Fournit des méthodes et des propriétés pour analyser des fichiers texte structurés.|  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage Visual Basic](../index.md)
